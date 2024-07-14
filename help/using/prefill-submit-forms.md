---
title: 基于数据源的预填充和提交工作流建议（用于生成自适应表单）
description: 针对使用Automated forms conversion服务(AFCS)生成的自适应表单，基于数据源的预填充和提交工作流。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
contentOwner: khsingh
exl-id: 5deef8f5-5098-47c1-b696-b2db59e92931
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '2397'
ht-degree: 1%

---

# 基于数据源的预填充和提交工作流建议（用于生成自适应表单） {#recommended-data-source-btased-prefill-and-submit-workflows-for-adaptive-forms}

您可以对通过Automated forms conversion服务(AFCS)转换的自适应表单使用以下任何数据源：

* 表单数据模型、OData或任何其他第三方服务
* JSON架构
* XSD架构

根据数据源，您可以选择生成带或不带数据模型的自适应表单。

本文介绍了在选择数据源并使用转换服务生成自适应表单后，用于预填充字段值和提交选项的推荐工作流。

<table> 
 <tbody> 
  <tr> 
   <th><strong>数据源</strong></th> 
   <th><strong>推荐的工作流</strong></th> 
  </tr> 
  <tr> 
   <td><p>表单数据模型、OData或任何其他第三方服务</p></td> 
   <td> 
    <p><strong>选项1</strong>：选择表单数据模型、OData或任何其他第三方服务作为数据源。 您<a href="#generate-adaptive-forms-with-no-data-binding">使用Automated forms conversion服务(AFCS)生成没有数据绑定的自适应表单</a>。 您可以手动将自适应表单字段绑定到表单数据模型实体，并使用表单数据模型预填服务选项预填字段值。 使用“使用表单数据模型提交”选项提交自适应表单。</p></td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
   <p><strong>选项2</strong>：选择表单数据模型、OData或任何其他第三方服务作为数据源。 您<a href="#generate-adaptive-forms-with-no-data-binding">使用Automated forms conversion服务(AFCS)生成没有数据绑定的自适应表单</a>。 您可以使用规则编辑器绑定自适应表单字段以预填字段值。 如有必要，请修改字段值，并将数据提交到crx-repository。</p>
    </td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
    <p>有关执行这些工作流的逐步说明，请参阅<a href="#sqldatasource">使用数据库、OData或任何第三方服务作为数据源。</a></p> </td> 
  </tr>
  <tr>
  <td><p>JSON架构</p></td> 
   <td> 
    <p>选择JSON架构作为数据源。 基于所选数据源：</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>选项1</strong>：您<a href="#generate-adaptive-forms-with-no-data-binding">使用Automated forms conversion服务(AFCS)生成没有数据绑定的自适应表单</a>，并将JSON架构配置为数据源。 手动将自适应表单字段绑定到JSON架构，然后<a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">使用任何支持的协议</a>预填充字段值。 如有必要，请修改字段值，并将数据提交到crx-repository。</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>有关执行工作流的逐步说明，请参阅<a href="#jsondatasource">使用JSON架构作为数据源。</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>选项2</strong>：您<a href="#generate-adaptive-forms-with-json-binding">使用Automated forms conversion服务(AFCS)生成具有JSON数据绑定的自适应表单</a>。 预填服务和表单提交无缝运行。 您不需要任何配置步骤。</p> </td> 
  </tr>
   <tr>
  <td></td> 
   <td> 
    <p>有关执行工作流的逐步说明，请参阅<a href="#jsonwithdatabinding">使用JSON架构作为数据源。</a></p> </td> 
  </tr>
  <tr>
  <td><p>XSD架构</p></td> 
   <td> 
    <p>选择XSD架构作为数据源。 基于所选数据源，您<a href="#generate-adaptive-forms-with-no-data-binding">使用Automated forms conversion服务(AFCS)生成无数据绑定的自适应表单</a>，并将XSD架构配置为数据源。 手动将自适应表单字段绑定到XSD架构，并<a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">使用任何支持的协议</a>预填充字段值。 如有必要，请修改字段值，并将数据提交到crx-repository。</p>
    </td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>有关执行工作流的逐步说明，请参阅<a href="#xsddatasource">使用XSD架构作为数据源。</a></p>
    </td> 
  </tr>
 </tbody> 
</table>


有关Automated forms conversion服务(AFCS)的更多信息，请参阅以下文章：

* [automated forms conversion服务简介](introduction.md)
* [配置Automated forms conversion服务](configure-service.md)
* [将打印表单转换为自适应表单](convert-existing-forms-to-adaptive-forms.md)
* [查看并更正转换后的表单](review-correct-ui-edited.md)

本文提供的信息基于这样一种假设，即任何阅读者都具备自适应表单概念的基本知识。

## 先决条件 {#pre-requisites}

* 配置[AEM创作实例](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html)
* 在AEMAutomated forms conversion](configure-service.md)上配置[创作服务(AFCS)

## 自适应表单示例 {#sample-adaptive-form}

要执行用例以预填自适应表单中的字段值并将它们提交到数据源，请下载以下示例PDF文件。

贷款申请表示例

[获取文件](assets/sample_loan_application_form.pdf)

PDF文件用作Automated forms conversion服务(AFCS)的输入。 服务会将此文件转换为自适应表单。 下图以PDF格式描述了示例贷款申请。

![贷款申请表示例](assets/sample_form_new.png)

## 为表单模型准备数据 {#prepare-data-for-form-model}

AEM Forms数据集成允许您配置并连接到不同的数据源。 使用转换过程生成自适应表单后，您可以根据表单数据模型、XSD或JSON架构定义表单模型。 您可以使用数据库、Microsoft Dynamics或任何其他第三方服务来创建表单数据模型。

本教程使用MySQL数据库作为创建表单数据模型的源。 在数据库中创建&#x200B;**loanapplication**&#x200B;架构，并根据自适应表单中可用的字段将&#x200B;**applicator**&#x200B;表添加到架构中。

![示例数据mysql](assets/sample_data_mysql.png)

您可以使用以下DDL语句在数据库中创建&#x200B;**申请人**&#x200B;表。

```sql
CREATE TABLE `applicant` (
   `name` varchar(45) DEFAULT NULL,
   `address` varchar(45) DEFAULT NULL,
   `phonenumber` int(11) NOT NULL,
   `email` varchar(45) DEFAULT NULL,
   `occupation` varchar(45) DEFAULT NULL,
   `annualsalary` varchar(45) DEFAULT NULL,
   `familymembers` int(11) DEFAULT NULL,
   PRIMARY KEY (`phonenumber`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

如果使用XSD架构作为表单模型来执行用例，请创建包含以下文本的XSD文件：

```xml
<?xml version="1.0" encoding="utf-8" ?>
    <xs:schema targetNamespace="http://adobe.com/sample.xsd"
                    xmlns="http://adobe.com/sample.xsd"
                    xmlns:xs="http://www.w3.org/2001/XMLSchema">

<xs:element name="sample" type="SampleType"/>

  <xs:complexType name="SampleType">
    <xs:sequence>
      <xs:element name="name" type="xs:string"/>
   <xs:element name="address" type="xs:string"/>
   <xs:element name="phonenumber" type="xs:int"/>
   <xs:element name="email" type="xs:string"/>
   <xs:element name="occupation" type="xs:string"/>
   <xs:element name="annualsalary" type="xs:string"/>
   <xs:element name="familymembers" type="xs:string"/>
 </xs:sequence>
  </xs:complexType>

  </xs:schema>
```

或者将XSD架构下载到本地文件系统。

示例贷款申请XSD架构

[获取文件](assets/loanapplication.xsd)

有关将XSD架构用作自适应表单中的表单模型的详细信息，请参阅[使用XML架构创建自适应表单](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-xml-schema-form-model.html)。

如果您使用JSON架构作为表单模型来执行用例，请创建包含以下文本的JSON文件：

```JSON
{
    "$schema": "http://json-schema.org/draft-04/schema#",
    "definitions": {
        "loanapplication": {
            "type": "object",
            "properties": {
                "name": {
                    "type": "string"
                },
                "address": {
                    "type": "string"
                },
    "phonenumber": {
                    "type": "number"
                },
    "email": {
                    "type": "string"
                },
    "occupation": {
                    "type": "string"
                },
    "annualsalary": {
                    "type": "string"
                },
    "familymembers": {
                    "type": "number"
                }
            }
        }
 },
 "type": "object",
    "properties": {
        "employee": {
            "$ref": "#/definitions/loanapplication"
        }
    }
}
```

或者将JSON架构下载到本地文件系统。

示例贷款应用程序JSON架构

[获取文件](assets/demo_schema.json)

有关在自适应表单中使用JSON架构作为表单模型的更多信息，请参阅[使用JSON架构创建自适应表单](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html)。

## 生成无数据绑定的自适应表单 {#generate-adaptive-forms-with-no-data-binding}

使用[Automated forms conversion服务将](convert-existing-forms-to-adaptive-forms.md) [示例贷款申请表单](#sample-adaptive-form)转换为无数据绑定的自适应表单。 确保选中&#x200B;**[!UICONTROL Generate adaptive form(s) without data bindings]**&#x200B;复选框以生成无数据绑定的自适应表单。

![无数据绑定的自适应表单](assets/generate_af_without_binding.png)

生成无数据绑定的自适应表单后，为该自适应表单选择数据源：

* [数据库、 OData或任何第三方服务](#sqldatasource)
* [JSON架构](#jsondatasource)
* [XSD架构](#xsddatasource)

>[!NOTE]
> 如果使用Automated forms conversion服务(AFCS)转换的自适应表单包含多个同名字段，请确保这些字段已绑定到数据源实体，以避免在提交期间可能的数据丢失。
>

### 使用数据库、OData或任何第三方服务作为数据源 {#sqldatasource}

用例：使用Automated forms conversion服务(AFCS)生成无数据绑定的自适应表单，并将MYSQL数据库配置为数据源。 手动将自适应表单字段绑定到表单数据模型实体，并使用&#x200B;**[!UICONTROL Form Data Model Prefill Service]**&#x200B;选项预填充字段值。 您使用&#x200B;**[!UICONTROL Submit using Form Data Model]**&#x200B;选项提交自适应表单。

在执行用例之前：

* [将MySQL数据库配置为数据源](https://helpx.adobe.com/experience-manager/6-5/forms/using/configure-data-sources.html#configurerelationaldatabase)
* [创建表单数据模型](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html)

根据用例，创建&#x200B;**loanapplication**&#x200B;表单数据模型并将读取服务参数绑定到&#x200B;**[!UICONTROL Literal]**&#x200B;值。 电话号码文字值必须是在MySQL数据库的&#x200B;**申请人**&#x200B;架构中配置的记录之一。 服务使用该值作为参数从数据源获取详细信息。 您还可以从&#x200B;**[!UICONTROL Binding To]**&#x200B;下拉列表中选择[用户配置文件属性或请求属性](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html#bindargument)

![配置表单数据模型](assets/configure_model_object.png)

>[!NOTE]
>
>在执行用例之前，请确保将&#x200B;**get**&#x200B;和&#x200B;**insert**&#x200B;服务添加到表单数据模型、配置并测试这些服务。

执行以下步骤：

1. 选择&#x200B;**[!UICONTROL output]**&#x200B;文件夹中提供的转换后的&#x200B;**示例贷款申请表**，然后点按&#x200B;**[!UICONTROL Properties]**。
1. 点按&#x200B;**[!UICONTROL Form Model]**&#x200B;选项卡，从&#x200B;**[!UICONTROL Select From]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Form Data Model]**，然后点按&#x200B;**[!UICONTROL Select Form Data Model]**&#x200B;以选择&#x200B;**贷款应用程序**&#x200B;表单数据模型。 点按&#x200B;**[!UICONTROL Save & Close]**&#x200B;以保存表单。
1. 选择&#x200B;**示例贷款申请表**&#x200B;并点按&#x200B;**[!UICONTROL Edit]**。
1. 在&#x200B;**[!UICONTROL Content]**&#x200B;选项卡中，点按配置图标：

   ![配置表单容器](assets/configure_form_container.png)

   1. 在&#x200B;**[!UICONTROL Basic]**&#x200B;部分中，从&#x200B;**[!UICONTROL Prefill Service]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Form Data Model Prefill service]**。

   1. 在&#x200B;**[!UICONTROL Submission]**&#x200B;部分中，从&#x200B;**[!UICONTROL Submit Action]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Submit using Form Data Model]**。

   1. 使用&#x200B;**[!UICONTROL Data Model to submit]**&#x200B;字段选择数据模型。
   1. 点按![完成图标](assets/save_icon.svg)以保存属性。

1. 点按“申请人姓名”文本框并选择![配置图标](assets/configure_icon.svg) （配置）。

   1. 在“绑定引用”字段中，选择&#x200B;**申请人** > **名称**，然后点按![完成图标](assets/save_icon.svg)以保存属性。 同样，为&#x200B;**地址**、**电话号码**、**电子邮件**、**职业**、**年薪（美元）**&#x200B;和&#x200B;**否，创建数据绑定。 具有表单数据模型实体的依赖家庭成员**&#x200B;字段。

   ![绑定引用](assets/bind_references.png)

1. 点按&#x200B;**[!UICONTROL Preview]**&#x200B;以查看预填充的自适应表单字段值。
1. 修改字段值（如有必要），并提交自适应表单。 字段值将提交到MySQL数据库。 您可以刷新数据库中的&#x200B;**申请人**&#x200B;表以查看表中更新的值。

**用例：**&#x200B;使用Automated forms conversion服务(AFCS)生成无数据绑定的自适应表单，并将MYSQL数据库配置为数据源。 您可以使用规则编辑器绑定自适应表单字段以预填字段值。 如有必要，请修改字段值，并将数据提交到crx-repository。

执行以下步骤以使用[规则编辑器](https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html)调用表单数据模型服务来绑定自适应表单中的字段和预填充值：

1. 选择&#x200B;**[!UICONTROL output]**&#x200B;文件夹中的&#x200B;**示例贷款申请表**，然后点按&#x200B;**[!UICONTROL Edit]**。
1. 在&#x200B;**[!UICONTROL Content]**&#x200B;选项卡中，点按配置图标：

   ![配置表单容器](assets/configure_form_container.png)

   在&#x200B;**[!UICONTROL Basic]**&#x200B;部分中，从&#x200B;**[!UICONTROL Prefill Service]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Form Data Model Prefill service]**。

1. 点按&#x200B;**[!UICONTROL Applicant Name]**&#x200B;文本框并点按&#x200B;**[!UICONTROL Edit Rules]**。

   ![编辑规则以创建数据绑定](assets/edit_rules_bind_reference.png)

1. 点按“规则编辑器”页面上的&#x200B;**[!UICONTROL Create]**。
1. 在&#x200B;**[!UICONTROL Rule Editor]**&#x200B;页面上：

   1. 选择“申请人姓名”文本框的州。 例如，**[!UICONTROL is initialized]**，当您在&#x200B;**[!UICONTROL Preview]**&#x200B;模式下呈现表单时，这将导致执行&#x200B;**[!UICONTROL Then]**&#x200B;条件。

   1. 在&#x200B;**[!UICONTROL Then]**&#x200B;部分中，从&#x200B;**[!UICONTROL Select Action]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Invoke Service]**。 Forms实例上的所有服务都将显示在下拉列表中。

   1. 从列出表单数据模型的部分中选择&#x200B;**[!UICONTROL Get]**&#x200B;服务。 输入字段显示&#x200B;**phonenumber**，它是为&#x200B;**申请人**&#x200B;数据模型定义的主键。 系统会根据此字段检索和预填充输出部分中字段的自适应表单中的值。

   1. 使用输出部分创建自适应表单字段与表单数据模型实体的绑定。 例如，用&#x200B;**name**&#x200B;实体绑定&#x200B;**[!UICONTROL Applicant Name]**&#x200B;自适应表单字段。

   1. 点击&#x200B;**[!UICONTROL Done]**。在规则编辑器页面上再次点按&#x200B;**[!UICONTROL Done]**。

   ![用于绑定引用的规则编辑器](assets/rule_editor_bind_references.png)

1. 点按&#x200B;**[!UICONTROL Preview]**&#x200B;以查看预填充的自适应表单字段值。

   >[!NOTE]
   >
   >请确保在与自适应表单关联的表单数据模型中，**get**&#x200B;服务属性的&#x200B;**[!UICONTROL Return Array]**&#x200B;属性设置为OFF。

1. 修改字段值（如有必要），并提交自适应表单。 提交的数据可在crx-repository中的以下位置找到：

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### 使用JSON架构作为数据源 {#jsondatasource}

**用例：**&#x200B;使用Automated forms conversion服务(AFCS)生成无数据绑定的自适应表单，并将JSON架构配置为数据源。 您手动将自适应表单字段绑定到JSON架构，并使用&#x200B;**预览数据**&#x200B;选项预填充字段值。 如有必要，请修改字段值，并将数据提交到crx-repository。

在执行用例之前，请确保您具有：

* [与JSON架构结构兼容的有效JSON架构](#prepare-data-for-form-model)
* [无数据绑定的自适应表单](#generate-adaptive-forms-with-no-data-binding)

执行以下步骤：

1. 选择&#x200B;**输出**&#x200B;文件夹中可用的已转换的&#x200B;**示例贷款申请表单**，然后点按&#x200B;**[!UICONTROL Properties]**。
1. 点按&#x200B;**[!UICONTROL Form Model]**&#x200B;选项卡，从&#x200B;**[!UICONTROL Select From]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Schema]**，然后点按&#x200B;**[!UICONTROL Select Schema]**&#x200B;以上传保存在本地文件系统上的&#x200B;**demo.schema JSON**&#x200B;架构。 点按&#x200B;**[!UICONTROL Save & Close]**&#x200B;以保存表单。
1. 选择&#x200B;**示例贷款申请表**&#x200B;并点按&#x200B;**[!UICONTROL Edit]**。
1. 点按“申请人姓名”文本框并选择![配置图标](assets/configure_icon.svg) （配置）。

   在“绑定引用”字段中，选择&#x200B;**申请人** > **名称**，然后点按![完成图标](assets/save_icon.svg)以保存属性。 同样，为&#x200B;**地址**、**电话号码**、**电子邮件**、**职业**、**年薪（美元）**&#x200B;和&#x200B;**否，创建数据绑定。 具有JSON架构实体的依赖家庭成员**&#x200B;字段。

1. 再次选择&#x200B;**[!UICONTROL output]**&#x200B;文件夹中提供的转换的&#x200B;**示例贷款申请表**，然后选择&#x200B;**[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**。</br>

   下载示例数据文件</br>

   [获取文件](assets/json_data_file.txt)</br>

1. 修改字段值（如有必要），并提交自适应表单。 提交的数据可在crx-repository中的以下位置找到：

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### 使用XSD架构作为数据源 {#xsddatasource}

**用例：**&#x200B;使用Automated forms conversion服务(AFCS)生成无数据绑定的自适应表单，并将XSD架构配置为数据源。 您手动将自适应表单字段绑定到XSD架构，并使用&#x200B;**带有数据的预览**&#x200B;预填充字段值。 如有必要，请修改字段值，并将数据提交到crx-repository。

在执行用例之前，请确保您具有：

* [与XML架构结构兼容的有效XSD架构](#prepare-data-for-form-model)
* [无数据绑定的自适应表单](#generate-adaptive-forms-with-no-data-binding)

执行以下步骤：

1. 选择&#x200B;**[!UICONTROL output]**&#x200B;文件夹中提供的转换后的&#x200B;**示例贷款申请表**，然后点按&#x200B;**[!UICONTROL Properties]**。
1. 点按&#x200B;**[!UICONTROL Form Model]**&#x200B;选项卡，从&#x200B;**[!UICONTROL Select From]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Schema]**，然后点按&#x200B;**[!UICONTROL Select Schema]**&#x200B;以上传保存在本地文件系统上的&#x200B;**loanapplication** XSD架构。 为XSD架构选择根元素并点按&#x200B;**[!UICONTROL Save & Close]**&#x200B;以保存表单。
1. 选择&#x200B;**示例贷款申请表**&#x200B;并点按&#x200B;**[!UICONTROL Edit]**。
1. 点按“申请人姓名”文本框并选择![配置图标](assets/configure_icon.svg) （配置）。
在“绑定引用”字段中，选择**申请人** > **名称**，然后点按![完成图标](assets/save_icon.svg)以保存属性。 同样，为&#x200B;**地址**、**电话号码**、**电子邮件**、**职业**、**年薪（美元）**&#x200B;和&#x200B;**否，创建数据绑定。 具有XSD架构实体的依赖家庭成员**&#x200B;字段。

1. 再次选择&#x200B;**输出**&#x200B;文件夹中提供的转换后的&#x200B;**贷款申请表单**，然后选择&#x200B;**[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**。</br>

   下载示例数据文件</br>

   [获取文件](assets/loan-application-data-xml-data.zip)</br>


1. 修改字段值（如有必要），并提交自适应表单。 提交的数据可在crx-repository中的以下位置找到：

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## 生成具有JSON绑定的自适应表单 {#generate-adaptive-forms-with-json-binding}

使用[Automated forms conversion服务(AFCS)将](convert-existing-forms-to-adaptive-forms.md) [示例贷款申请表单](#sample-adaptive-form)转换为具有数据绑定的自适应表单。 确保在生成自适应表单时未选中&#x200B;**[!UICONTROL Generate adaptive form(s) without data bindings]**&#x200B;复选框。

具有JSON绑定的![自适应表单](assets/generate_af_with_data_bindings.png)

### 使用JSON架构作为数据源 {#jsonwithdatabinding}

**用例：**&#x200B;使用Automated forms conversion服务(AFCS)生成具有JSON数据绑定的自适应表单。 预填服务和表单提交无缝运行。 您不需要任何配置步骤。

在执行用例之前，请确保您具有[带有数据绑定的自适应表单](#generate-adaptive-forms-with-json-binding)。

执行以下步骤：

1. 再次选择&#x200B;**[!UICONTROL output]**&#x200B;文件夹中提供的转换的&#x200B;**示例贷款申请表**，然后选择&#x200B;**[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**。</br>

   下载示例数据文件</br>

   [获取文件](assets/loan_application_data_source_json_data_binding.txt)</br>

1. 修改字段值（如有必要），并提交自适应表单。 提交的数据可在crx-repository中的以下位置找到：

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## 将提交的自适应表单JSON数据转换为XML格式 {#convert-submitted-adaptive-form-data-to-xml}

在自适应表单字段中输入值并提交时，数据在crx存储库中以JSON格式提供。 您可以使用[org.apache.sling.commons.json.xml](https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString) API或以下示例代码将JSON数据的格式转换为XML：

```
import org.apache.sling.commons.json.JSONException;
import org.apache.sling.commons.json.JSONObject;
import org.apache.sling.commons.json.xml.XML;
 
public class ConversionUtils {
 
    public static String jsonToXML(String jsonString) throws JSONException {
        //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
        //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
        //Note: Need to extract boundData part before converting to XML
        return XML.toString(new JSONObject(jsonString));
    }
}
```
