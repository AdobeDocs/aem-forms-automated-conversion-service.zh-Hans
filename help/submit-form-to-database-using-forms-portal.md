---
title: 使用Forms门户将自适应表单提交到数据库
description: 扩展默认元模型，以添加特定于您的组织的模式、验证和实体，并在运行Automated forms conversion服务时将配置应用到自适应表单字段。
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: ead1b4ee177029c60f095dc596b1f3db5878760e
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 1%

---


# 使用Forms门户{#submit-forms-to-database-using-forms-portal}将自适应表单与数据库集成

automated forms conversion服务允许您将非交互式PDF表单、Acro表单或基于XFA的PDF表单转换为自适应表单。 启动转换过程时，您可以选择生成带有或不带数据绑定的自适应表单。

如果选择生成不带数据绑定的自适应表单，则转换后可以将转换后的自适应表单与表单数据模型、XML模式或JSON模式集成。 但是，如果您生成具有数据绑定的自适应表单，转换服务会自动将自适应表单与JSON模式关联，并在自适应表单和JSON模式中可用的字段之间创建数据绑定。 然后，您可以将自适应表单与您选择的数据库集成，在表单中填写数据，并使用Forms门户将其提交到数据库。

下图描述了使用Forms门户将转换的自适应表单与数据库集成的不同阶段：

![数据库集成](assets/database_integration.gif)

本文描述了成功执行所有这些集成阶段的分步说明。

本文讨论的示例是定制数据和元数据服务的参考实现，以将Forms门户网页与数据库集成。 示例实现中使用的数据库是MySQL 5.6.24。但是，可以将Forms门户页面与您选择的任何数据库集成。

## 先决条件{#pre-requisites}

* 设置AEM 6.4或6.5作者实例
* 为AEM实例安装[最新的Service Pack](https://helpx.adobe.com/cn/experience-manager/aem-releases-updates.html)
* 最新版本的AEM Forms加载项包
* 配置[Automated forms conversion服务](configure-service.md)
* 设置数据库。 示例实现中使用的数据库是MySQL 5.6.24。但是，可以将转换后的自适应表单与您选择的任何数据库集成。

## 在AEM实例和数据库{#set-up-connection-aem-instance-database}之间设置连接

在AEM实例和MYSQL数据库之间设置连接由以下部分组成：

* [安装MYSQL连接器包](#install-mysql-connector-java-file)

* [在模式库中创建和表](#create-schema-and-tables-in-database)

* [配置连接设置](#configure-connection-between-aem-instance-and-database)

* [为Forms门户集成设置和配置示例包](#set-up-and-configure-sample)

### 安装mysql-connector-java-5.1.39-bin.jar文件{#install-mysql-connector-java-file}

对所有作者实例和发布实例执行以下步骤以安装mysql-connector-java-5.1.39-bin.jar文件：

1. 导航到http://[server]:[port]/system/console/depfinder并搜索com.mysql.jdbc包。
1. 在“导出依据”列中，检查包是否由任何捆绑导出。 如果包未由任何包导出，请继续。
1. 导航到http://[server]:[port]/system/console/bundles，然后单击&#x200B;**[!UICONTROL Install/Update]**。
1. 单击&#x200B;**[!UICONTROL Choose File]**&#x200B;并浏览以选择mysql-connector-java-5.1.39-bin.jar文件。 此外，选择&#x200B;**[!UICONTROL Start Bundle]**&#x200B;和&#x200B;**[!UICONTROL Refresh Packages]**&#x200B;复选框。
1. 单击&#x200B;**[!UICONTROL Install]**&#x200B;或&#x200B;**[!UICONTROL Update]**。 完成后，重新启动服务器。
1. （仅限Windows）关闭操作系统的系统防火墙。

### 在模式库{#create-schema-and-tables-in-database}中创建和表

执行以下步骤以在模式库中创建数据和表：

1. 使用以下SQL语句在模式库中创建一个：

   ```sql
   CREATE SCHEMA `formsportal` ;
   ```

   其中&#x200B;**formsportal**&#x200B;指模式的名称。

1. 使用以下SQL语句在数据库模式中创建&#x200B;**data**&#x200B;表：

   ```sql
    CREATE TABLE `data` (
        `owner` varchar(255) DEFAULT NULL,
        `data` longblob,
        `metadataId` varchar(45) DEFAULT NULL,
        `id` varchar(45) NOT NULL,
        PRIMARY KEY (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. 使用以下SQL语句在数据库模式中创建&#x200B;**元数据**&#x200B;表：

   ```sql
   CREATE TABLE `metadata` (
       `formPath` varchar(1000) DEFAULT NULL,
       `formType` varchar(100) DEFAULT NULL,
       `description` text,
       `formName` varchar(255) DEFAULT NULL,
       `owner` varchar(255) DEFAULT NULL,
       `enableAnonymousSave` varchar(45) DEFAULT NULL,
       `renderPath` varchar(1000) DEFAULT NULL,
       `nodeType` varchar(45) DEFAULT NULL,
       `charset` varchar(45) DEFAULT NULL,
       `userdataID` varchar(45) DEFAULT NULL,
       `status` varchar(45) DEFAULT NULL,
       `formmodel` varchar(45) DEFAULT NULL,
       `markedForDeletion` varchar(45) DEFAULT NULL,
       `showDorClass` varchar(255) DEFAULT NULL,
       `sling:resourceType` varchar(1000) DEFAULT NULL,
       `attachmentList` longtext,
       `draftID` varchar(45) DEFAULT NULL,
       `submitID` varchar(45) DEFAULT NULL,
       `id` varchar(60) NOT NULL,
       `profile` varchar(255) DEFAULT NULL,
       `submitUrl` varchar(1000) DEFAULT NULL,
       `xdpRef` varchar(1000) DEFAULT NULL,
       `agreementId` varchar(255) DEFAULT NULL,
       `nextSigners` varchar(255) DEFAULT NULL,
       `eSignStatus` varchar(45) DEFAULT NULL,
       `pendingSignID` varchar(45) DEFAULT NULL,
       `agreementDataId` varchar(255) DEFAULT NULL,
       `enablePortalSubmit` varchar(45) DEFAULT NULL,
       `submitType` varchar(45) DEFAULT NULL,
       `dataType` varchar(45) DEFAULT NULL,
       `jcr:lastModified` varchar(45) DEFAULT NULL,
       PRIMARY KEY (`id`),
       UNIQUE KEY `ID_UNIQUE` (`id`)
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. 使用以下SQL语句在数据库模式中创建&#x200B;**additionalmetadatatable**&#x200B;表：

   ```sql
   CREATE TABLE `additionalmetadatatable` (
       `value` text,
       `key` varchar(255) NOT NULL,
       `id` varchar(60) NOT NULL,
       PRIMARY KEY (`id`,`key`),
       CONSTRAINT ‘additionalmetadatatable_fk’ FOREIGN KEY (`id`) REFERENCES `metadata` (`id`) ON DELETE CASCADE
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. 使用以下SQL语句在数据库模式中创建&#x200B;**commenttable**&#x200B;表：

   ```sql
   CREATE TABLE `commenttable` (
       `commentId` varchar(255) DEFAULT NULL,
       `comment` text DEFAULT NULL,
       `ID` varchar(255) DEFAULT NULL,
       `commentowner` varchar(255) DEFAULT NULL,
       `time` varchar(255) DEFAULT NULL);
   ```

### 配置AEM实例与数据库{#configure-connection-between-aem-instance-and-database}之间的连接

执行以下配置步骤以在AEM实例和MYSQL数据库之间创建连接：

1. 转至AEM Web控制台配置页，网址为&#x200B;*http://[host]:[port]/system/console/configMgr*。
1. 单击以在编辑模式下打开&#x200B;**[!UICONTROL Forms Portal Draft and Submission Configuration]**。
1. 如下表所述，指定属性的值：

   <table> 
    <tbody> 
    <tr> 
    <th><strong>属性</strong></th> 
    <th><strong>描述</strong></th>
    <th><strong>值</strong></th> 
    </tr> 
    <tr> 
    <td><p>Forms门户数据服务草稿</p></td> 
    <td><p>草稿数据服务的标识符</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms门户元数据服务草稿</p></td> 
    <td><p>草稿元数据服务的标识符</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms门户提交数据服务</p></td> 
    <td><p>提交数据服务的标识符</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms门户提交元数据服务</p></td> 
    <td><p>提交元数据服务的标识符</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms门户正在等待签名数据服务</p></td> 
    <td><p>挂起签名数据服务的标识符</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms门户待签名元数据服务</p></td> 
    <td><p>待签名元数据服务的标识符</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    </tbody> 
    </table>
1. 保留其他配置，然后单击&#x200B;**[!UICONTROL Save]**。
1. 查找并单击以在Web控制台配置的编辑模式下打开&#x200B;**[!UICONTROL Apache Sling Connection Pooled DataSource]**。 如下表所述，指定属性的值：

   <table> 
    <tbody> 
    <tr> 
    <th><strong>属性</strong></th> 
    <th><strong>值</strong></th> 
    </tr> 
    <tr> 
    <td><p>数据源名称</p></td> 
    <td><p>用于从数据源池过滤驱动程序的数据源名称。 示例实现使用FormsPortal作为数据源名称。</p></td>
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

### 设置并配置示例{#set-up-and-configure-sample}

对所有作者和发布实例执行以下步骤以安装和配置示例：

1. 将以下&#x200B;**aem-fp-db-integration-sample-pkg-6.1.2.zip**&#x200B;软件包下载到您的文件系统。

   [获取文件](assets/aem-fp-db-integration-sample-pkg-6.1.2.zip)

1. 转到位于&#x200B;*http://[host]的AEM包管理器：[port]/crx/packmgr/*。
1. 单击 **[!UICONTROL Upload Package]**.
1. 浏览以选择&#x200B;**aem-fp-db-integration-sample-pkg-6.1.2.zip**&#x200B;包，然后单击&#x200B;**[!UICONTROL OK]**。
1. 单击程序包旁的&#x200B;**[!UICONTROL Install]**&#x200B;以安装该程序包。

## 为Forms门户集成配置转换的自适应表单{#configure-converted-adaptive-form-for-forms-portal-integration}

执行以下步骤，以启用使用Forms门户页面提交自适应表单：
1. [运行转](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) 换，将源表单转换为自适应表单。
1. 在编辑模式下打开自适应表单。
1. 点按表单容器，然后选择配置![配置自适应表单](assets/configure-adaptive-form.png)。
1. 在&#x200B;**[!UICONTROL Submission]**&#x200B;部分，从&#x200B;**[!UICONTROL Submit Action]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Forms Portal Submit Action]**。
1. 点按![保存模板策略](assets/edit_template_done.png)以保存设置。

## 创建和配置Forms门户页面{#create-configure-forms-portal-page}

请执行以下步骤创建Forms门户页面并进行配置，以便您可以使用此页提交自适应表单：

1. 登录到AEM作者实例，然后点按&#x200B;**[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Sites]**。
1. 选择要保存新的Forms门户页面的位置，然后点按&#x200B;**[!UICONTROL Create]** > **[!UICONTROL Page]**。
1. 选择页面的模板，点按&#x200B;**[!UICONTROL Next]**，指定页面的标题，然后点按&#x200B;**[!UICONTROL Create]**。
1. 点按&#x200B;**[!UICONTROL Edit]**&#x200B;以配置页面。
1. 在页面标题中，点按![编辑模板](assets/edit_template_sites.png) > **[!UICONTROL Edit Template]**&#x200B;以打开页面的模板。
1. 点按布局容器，然后点按![编辑模板策略](assets/edit_template_policy.png)。 在&#x200B;**[!UICONTROL Allowed Components]**&#x200B;选项卡中，启用&#x200B;**[!UICONTROL Document Services]**&#x200B;和&#x200B;**[!UICONTROL Document Services Predicates]**&#x200B;选项，然后点按![保存模板策略](assets/edit_template_done.png)。
1. 在页面中插入&#x200B;**[!UICONTROL Search & Lister]**&#x200B;组件。 因此，页面上会列出AEM实例上可用的所有现有自适应表单。
1. 在页面中插入&#x200B;**[!UICONTROL Drafts & Submissions]**&#x200B;组件。 两个选项卡&#x200B;**[!UICONTROL Draft Forms]**&#x200B;和&#x200B;**[!UICONTROL Submitted Forms]**&#x200B;显示在Forms门户页面上。 **[!UICONTROL Draft Forms]**&#x200B;选项卡还显示使用[为Forms门户集成配置转换的自适应表单中所述的步骤生成的转换的自适应表单。](#configure-converted-adaptive-form-for-forms-portal-integration)

1. 点按&#x200B;**[!UICONTROL Preview]**，点按转换的自适应表单，指定自适应表单字段的值并提交。 您为自适应表单字段指定的值将提交到集成数据库。
