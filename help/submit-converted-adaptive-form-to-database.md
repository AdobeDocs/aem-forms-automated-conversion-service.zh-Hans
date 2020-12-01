---
title: 使用JSON模式将转换后的自适应表单提交到数据库
description: 通过创建表单模式模型并在AEM工作流中引用它，将转换后的自适应表单（带有JSON）提交到数据库。
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: c552f4073ac88ca9016a746116a27a5898df7f7d
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 2%

---


# 使用 AEM 工作流实现自适应表单与数据库集成 {#submit-forms-to-database-using-forms-portal}

automated forms conversion服务允许您将非交互式PDF表单、Acro表单或基于XFA的PDF表单转换为自适应表单。 启动转换过程时，您可以选择生成带有或不带数据绑定的自适应表单。

如果选择生成不带数据绑定的自适应表单，则转换后可以将转换后的自适应表单与表单数据模型、XML模式或JSON模式集成。 对于表单数据模型，您需要手动将自适应表单字段与表单数据模型绑定。 但是，如果您生成具有数据绑定的自适应表单，转换服务会自动将自适应表单与JSON模式关联，并在自适应表单和JSON模式中可用的字段之间创建数据绑定。 然后，您可以将自适应表单与您选择的数据库集成，在表单中填写数据，并将其提交到数据库。 同样，在成功与数据库集成后，您可以配置转换的自适应表单中的字段，从数据库检索值并预填自适应表单字段。

下图描述了将转换的自适应表单与数据库集成的不同阶段：

![数据库集成](assets/integrate-adaptive-form-with-database.png)

本文描述了成功执行所有这些集成阶段的分步说明。

## 先决条件{#pre-requisites}

* 设置AEM 6.4或6.5作者实例
* 为AEM实例安装[最新的Service Pack](https://helpx.adobe.com/cn/experience-manager/aem-releases-updates.html)
* 最新版本的AEM Forms加载项包
* 配置[Automated forms conversion服务](configure-service.md)
* 设置数据库。 示例实现中使用的数据库是MySQL 5.6.24。但是，可以将转换后的自适应表单与您选择的任何数据库集成。

## 自适应表单示例{#sample-adaptive-form}

要执行用例以使用AEM工作流将转换的自适应表单与数据库集成，请下载以下范例PDF文件。

您可以使用以下方式下载示例联系我们表单：

[获取文件](assets/sample_contact_us_form.pdf)

PDF文件用作Automated forms conversion服务的输入。 服务将此文件转换为自适应表单。 下图以PDF格式描述了示例联系人表单。

![示例贷款申请表](assets/sample_contact_us_form.png)

## 安装mysql-connector-java-5.1.39-bin.jar文件{#install-mysql-connector-java-file}

对所有作者实例和发布实例执行以下步骤以安装mysql-connector-java-5.1.39-bin.jar文件：

1. 导航到`http://server:port/system/console/depfinder`并搜索com.mysql.jdbc包。
1. 在“导出依据”列中，检查包是否由任何捆绑导出。 如果包未由任何包导出，请继续。
1. 导航到`http://server:port/system/console/bundles`并单击&#x200B;**[!UICONTROL Install/Update]**。
1. 单击&#x200B;**[!UICONTROL Choose File]**&#x200B;并浏览以选择mysql-connector-java-5.1.39-bin.jar文件。 此外，选择&#x200B;**[!UICONTROL Start Bundle]**&#x200B;和&#x200B;**[!UICONTROL Refresh Packages]**&#x200B;复选框。
1. 单击&#x200B;**[!UICONTROL Install]**&#x200B;或&#x200B;**[!UICONTROL Update]**。 完成后，重新启动服务器。
1. （仅限Windows）关闭操作系统的系统防火墙。

## 为表单型号{#prepare-data-for-form-model}准备数据

AEM Forms数据集成允许您配置和连接不同的数据源。 在使用转换过程生成自适应表单后，您可以根据表单数据模型、XSD或JSON模式定义表单模型。 您可以使用数据库、Microsoft Dynamics或任何其他第三方服务创建表单数据模型。

本教程使用MySQL数据库作为源创建表单数据模型。 在模式库中创建模式，并根据自适应表单中可用的字段将&#x200B;**contacts**&#x200B;表添加到。

![示例数据mysql](assets/db_entries_sample_form.png)

可以使用以下DDL语句在数据库中创建&#x200B;**contacts**&#x200B;表。

```sql
CREATE TABLE `contactus` (
   `name` varchar(45) NOT NULL,
   `email` varchar(45) NOT NULL,
   `phonenumber` varchar(10) DEFAULT NULL,
   `issuedesc` varchar(1000) DEFAULT NULL,
   PRIMARY KEY (`email`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

## 配置AEM实例与数据库{#configure-connection-between-aem-instance-and-database}之间的连接

执行以下配置步骤以在AEM实例和MYSQL数据库之间创建连接：

1. 转到位于`http://server:port/system/console/configMgr`的AEM Web控制台配置页。
1. 查找并单击以在Web控制台配置的编辑模式下打开&#x200B;**[!UICONTROL Apache Sling Connection Pooled DataSource]**。 如下表所述，指定属性的值：

   <table> 
    <tbody> 
    <tr> 
    <th><strong>属性</strong></th> 
    <th><strong>值</strong></th> 
    </tr> 
    <tr> 
    <td><p>数据源名称</p></td> 
    <td><p>用于从数据源池过滤驱动程序的数据源名称。</p></td>
    </tr>
    <tr> 
    <td><p>JDBC驱动程序类</p></td> 
    <td><p>com.mysql.jdbc.Driver</p></td>
    </tr>
    <tr> 
    <td><p>JDBC连接URI</p></td> 
    <td><p>jdbc:mysql://[host]:[port]/[模式名]</p></td>
    </tr>
    <tr> 
    <td><p>用户名</p></td> 
    <td><p>对数据库表进行身份验证和执行操作的用户名</p></td>
    </tr>
    <tr> 
    <td><p>密码</p></td> 
    <td><p>与用户名关联的口令</p></td>
    </tr>
    <tr> 
    <td><p>事务隔离</p></td> 
    <td><p>READ_COMMITTED</p></td>
    </tr>
    <tr> 
    <td><p>最大活动连接数</p></td> 
    <td><p>1000</p></td>
    </tr>
    <tr> 
    <td><p>最大空闲连接数</p></td> 
    <td><p>100</p></td>
    </tr>
    <tr> 
    <td><p>最小空闲连接数</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>初始大小</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>最大等待</p></td> 
    <td><p>100000</p></td>
    </tr>
     <tr> 
    <td><p>借阅测试</p></td> 
    <td><p>已选中</p></td>
    </tr>
     <tr> 
    <td><p>空闲时测试</p></td> 
    <td><p>已选中</p></td>
    </tr>
     <tr> 
    <td><p>验证查询</p></td> 
    <td><p>示例值为SELECT 1(mysql)、从dual(oracle)、SELECT 1(MS Sql Server)(validationQuery)中选择1</p></td>
    </tr>
     <tr> 
    <td><p>验证查询超时</p></td> 
    <td><p>10000</p></td>
    </tr>
    </tbody> 
    </table>

## 创建表单数据模型{#create-form-data-model}

将MYSQL配置为数据源后，请执行以下步骤以创建表单数据模型：

1. 在AEM作者实例中，导航到&#x200B;**[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]**。

1. 点按 **[!UICONTROL Create]** > **[!UICONTROL Form Data Model]**.

1. 在&#x200B;**[!UICONTROL Create Form Data Model]**&#x200B;向导中，指定&#x200B;**workflow_submit**&#x200B;作为表单数据模型的名称。 点按 **[!UICONTROL Next]**.

1. 选择您在上一节中配置的MYSQL数据源，然后点按&#x200B;**[!UICONTROL Create]**。

1. 点按&#x200B;**[!UICONTROL Edit]**&#x200B;并展开左窗格中列出的数据源以选择&#x200B;**contacts**&#x200B;表、**[!UICONTROL get]**&#x200B;和&#x200B;**[!UICONTROL insert]**&#x200B;服务，然后点按&#x200B;**[!UICONTROL Add Selected]**。

   ![示例数据mysql](assets/fdm_details_workfdlow_submit.png)

1. 在右窗格中选择数据模型对象，然后点按&#x200B;**[!UICONTROL Edit Properties]**。 从&#x200B;**[!UICONTROL Read Service]**&#x200B;和&#x200B;**[!UICONTROL Write Service]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL get]**&#x200B;和&#x200B;**[!UICONTROL insert]**。 指定读取服务的参数，然后点按&#x200B;**[!UICONTROL Done]**。

1. 在&#x200B;**[!UICONTROL Services]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL get]**&#x200B;服务并点按&#x200B;**[!UICONTROL Edit Properties]**。 选择&#x200B;**[!UICONTROL Output Model Object]**，禁用&#x200B;**[!UICONTROL Return array]**&#x200B;切换，然后点按&#x200B;**[!UICONTROL Done]**。

1. 选择&#x200B;**[!UICONTROL Insert]**&#x200B;服务并点按&#x200B;**[!UICONTROL Edit Properties]**。 选择&#x200B;**[!UICONTROL Input Model Object]**&#x200B;并点按&#x200B;**[!UICONTROL Done]**。

1. 点按&#x200B;**[!UICONTROL Save]**&#x200B;以保存表单数据模型。

您可以使用以下方式下载示例表单数据模型：

[获取文件](assets/DownloadedFormsPackage_1497728018502500.zip)

## 生成具有JSON绑定{#generate-adaptive-forms-with-json-binding}的自适应表单

使用[Automated forms conversion服务将[联系我们表单](#sample-adaptive-form)转换为具有数据绑定的自适应表单。 ](convert-existing-forms-to-adaptive-forms.md)确保在生成自适应表单时不选中&#x200B;**[!UICONTROL Generate adaptive form(s) without data bindings]**&#x200B;复选框。

![具有JSON绑定的自适应表单](assets/generate_af_with_data_bindings.png)

在&#x200B;**[!UICONTROL Forms & Documents]**&#x200B;的&#x200B;**[!UICONTROL output]**&#x200B;文件夹中选择已转换的&#x200B;**联系我们表单**，然后点按&#x200B;**[!UICONTROL Edit]**。 点按&#x200B;**[!UICONTROL Preview]**，在自适应表单字段中输入值，然后点按&#x200B;**[!UICONTROL Submit]**。

登录&#x200B;**crx-repository**&#x200B;并导航至&#x200B;*/content/forms/fp/admin/submit/data*&#x200B;以JSON格式视图提交的值。 以下是提交转换后的&#x200B;**联系我们**&#x200B;自适应表单时JSON格式的示例数据：

```json
{
  "afData": {
    "afUnboundData": {
      "data": {}
    },
    "afBoundData": {
      "data": {
        "name1": "Gloria",
        "email": "abc@xyz.com",
        "phone_number": "2346578965",
        "issue_description": "Test message"
      }
    },
    "afSubmissionInfo": {
      "computedMetaInfo": {},
      "stateOverrides": {},
      "signers": {},
      "afPath": "/content/dam/formsanddocuments/docs_conversion/output/sample_form_json",
      "afSubmissionTime": "20191204014007"
    }
  }
}
```

您现在需要创建一个工作流模型，该模型可以处理此数据，并使用您在前几节中创建的表单数据模型将其提交到MYSQL数据库。

## 创建工作流模型以处理JSON数据{#create-workflow-model}

执行以下步骤以创建工作流模型，将自适应表单数据提交到数据库：

1. 打开工作流模型控制台。 默认URL为`https://server:port/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`。

1. 选择&#x200B;**[!UICONTROL Create]**，然后选择&#x200B;**[!UICONTROL Create Model]**。 出现&#x200B;**[!UICONTROL Add Workflow Model]**&#x200B;对话框。

1. 输入&#x200B;**[!UICONTROL Title]**&#x200B;和&#x200B;**[!UICONTROL Name]**（可选）。 例如，**workflow_json_submit**。 点按&#x200B;**[!UICONTROL Done]**&#x200B;以创建模型。

1. 选择工作流模型并点按&#x200B;**[!UICONTROL Edit]**&#x200B;以在编辑模式下打开模型。 点按+并将&#x200B;**[!UICONTROL Invoke Form Data Model Service]**&#x200B;步骤添加到工作流模型。

1. 点按&#x200B;**[!UICONTROL Invoke Form Data Model Service]**&#x200B;步骤，然后点按![配置](assets/configure_icon.png)。

1. 在&#x200B;**[!UICONTROL Form Data Model]**&#x200B;选项卡中，选择您在&#x200B;**[!UICONTROL Form Data Model path]**&#x200B;字段中创建的表单数据模型，然后从&#x200B;**[!UICONTROL Service]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL insert]**。

1. 在&#x200B;**[!UICONTROL Input for Service]**&#x200B;选项卡中，从下拉列表中选择&#x200B;**[!UICONTROL Provide input data using literal, variable, or a workflow metadata, and a JSON file]**，选中&#x200B;**[!UICONTROL Map input fields from input JSON]**&#x200B;复选框，选择&#x200B;**[!UICONTROL Relative to payload]**，并提供&#x200B;**data.xml**&#x200B;作为&#x200B;**[!UICONTROL Select input JSON document using]**&#x200B;字段的值。

1. 在&#x200B;**[!UICONTROL Service Arguments]**&#x200B;部分，为表单数据模型参数提供以下值：

   ![调用表单数据模型服务](assets/invoke_form_data_model_service.png)

   请注意，表单数据模型字段（例如，contactus点名）已映射到&#x200B;**afData.afBoundData.data.name1**，它指提交的自适应表单的JSON模式绑定。

## 配置自适应表单提交{#configure-adaptive-form-submission}

执行以下步骤，将自适应表单提交到您在上一节中创建的工作流模型：

1. 在&#x200B;**[!UICONTROL Forms & Documents]**&#x200B;的&#x200B;**[!UICONTROL output]**&#x200B;文件夹中选择已转换的“联系我们”表单，然后点按&#x200B;**[!UICONTROL Edit]**。

1. 点按&#x200B;**[!UICONTROL Form Container]**&#x200B;然后点按![配置](assets/configure_icon.png)，打开自适应表单属性。

1. 在&#x200B;**[!UICONTROL Submission]**&#x200B;部分，从&#x200B;**[!UICONTROL Submit Action]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Invoke an AEM workflow]**，选择您在上一节中创建的工作流模型，并在&#x200B;**[!UICONTROL Data File Path]**&#x200B;字段中指定&#x200B;**data.xml**。

1. 点按![保存](assets/save_icon.png)以保存属性。

1. 点按&#x200B;**[!UICONTROL Preview]**，在自适应表单字段中输入值，然后点按&#x200B;**[!UICONTROL Submit]**。 提交的值现在显示在MYSQL数据库表中，而不是&#x200B;**crx-repository**。

## 配置自适应表单以从数据库预填值

执行以下步骤，根据表中定义的主键（本例中为“电子邮件”）配置自适应表单以预填MYSQL数据库中的值：

1. 点按自适应表单中的&#x200B;**电子邮件**&#x200B;字段，然后点按![编辑规则](assets/edit-rules.png)。

1. 点按&#x200B;**[!UICONTROL Create]**&#x200B;并从&#x200B;**[!UICONTROL When]**&#x200B;部分的&#x200B;**[!UICONTROL Select State]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL is changed]**。

1. 在&#x200B;**[!UICONTROL Then]**&#x200B;部分，选择&#x200B;**[!UICONTROL Invoke Service]**&#x200B;和&#x200B;**get**&#x200B;作为您在本文上一节中创建的表单数据模型的服务。

1. 在&#x200B;**[!UICONTROL Input]**&#x200B;部分选择&#x200B;**电子邮件**，在&#x200B;**[!UICONTROL Output]**&#x200B;部分选择表单数据模型的其余三个字段：**名称**、**电话号码**&#x200B;和&#x200B;**问题说明**。 点按&#x200B;**[!UICONTROL Done]**&#x200B;以保存设置。

   ![配置电子邮件预填设置](assets/email_prefill_settings.png)

   因此，根据MYSQL数据库中现有的电子邮件条目，您可以在自适应表单的&#x200B;**[!UICONTROL Preview]**&#x200B;模式中预填其余三个字段的值。 例如，如果在&#x200B;**电子邮件**&#x200B;字段中指定aya.tan@xyz.com（基于本文[准备表单数据模型](#prepare-data-for-form-model)部分中的现有数据）并跳出字段，则其余三个字段&#x200B;**名称**、**电话号码**&#x200B;和&#x200B;**问题description**&#x200B;在自适应表单中自动显示。

您可以使用以下方式下载转换的自适应表单示例：

[获取文件](assets/DownloadedFormsPackage_1498226829041200.zip)
