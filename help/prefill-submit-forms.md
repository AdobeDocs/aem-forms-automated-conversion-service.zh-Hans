---
title: 基于数据源的预填充和提交工作流建议（用于生成自适应表单）
seo-title: 自适应表单的预填和提交选项
description: 针对使用自动表单转换服务生成的自适应表单的基于数据源的预填和提交工作流程。
seo-description: 针对使用自动表单转换服务生成的自适应表单的基于数据源的预填和提交工作流程。
uuid: 91409a82-141c-4233-82b1-1539a0b250f8
contentOwner: khsingh
topic-tags: forms
discoiquuid: cad34fff-7f9f-4a27-8b5c-d0a523903eec
privatebeta: true
translation-type: tm+mt
source-git-commit: caccb547a5741eb0e70ddf75630a661f8fe75cb3

---


# 基于数据源的预填充和提交工作流建议（用于生成自适应表单） {#recommended-data-source-btased-prefill-and-submit-workflows-for-adaptive-forms}

您可以将以下任意数据源与使用“自动表单转换”服务转换的自适应表单一起使用：

* 表单数据模型、OData或任何其他第三方服务
* JSON架构
* XSD架构

根据数据源，您可以选择生成带有或不带数据模型的自适应表单。

本文描述了在选择数据源并使用转换服务生成自适应表单之后预填充字段值和提交选项的推荐工作流。

<table> 
 <tbody> 
  <tr> 
   <th><strong>数据源</strong></th> 
   <th><strong>推荐的工作流</strong></th> 
  </tr> 
  <tr> 
   <td><p>表单数据模型、OData或任何其他第三方服务</p></td> 
   <td> 
    <p><strong>选项1</strong>:您选择表单数据模型、OData或任何其他第三方服务作为数据源。 您可 <a href="#generate-adaptive-forms-with-no-data-binding">以使用“自动表单转换”服务生成没有数据绑定的</a> 自适应表单。 您可以手动将自适应表单字段绑定到表单数据模型实体，并使用“表单数据模型预填服务”选项预填字段值。 使用“使用表单数据模型提交”选项提交自适应表单。</p></td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
   <p><strong>选项2</strong>:您选择表单数据模型、OData或任何其他第三方服务作为数据源。 您可 <a href="#generate-adaptive-forms-with-no-data-binding">以使用“自动表单转换”服务生成没有数据绑定的</a> 自适应表单。 您可以使用规则编辑器绑定自适应表单字段以预填字段值。 根据需要修改字段值，并将数据提交到crx-repository。</p>
    </td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
    <p>有关执行这些工作流的分步说明，请参 <a href="#sqldatasource">阅使用数据库、OData或任何第三方服务作为数据源。</a></p> </td> 
  </tr>
  <tr>
  <td><p>JSON架构</p></td> 
   <td> 
    <p>您选择JSON架构作为数据源。 根据所选数据源：</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>选项1</strong>:您可 <a href="#generate-adaptive-forms-with-no-data-binding">以使用自动表单转换服务生成没有数据绑定的自适应表单</a> ，并将JSON架构配置为数据源。 您可以手动将自适应表单字段绑定到JSON架 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">构，并使用任何支持的协议</a> 来预填字段值。 根据需要修改字段值，并将数据提交到crx-repository。</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>有关执行工作流的分步说明，请参 <a href="#jsondatasource">阅使用JSON架构作为数据源。</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>选项2</strong>:您可 <a href="#generate-adaptive-forms-with-json-binding">以使用“自动表单转换”服务生成具有JSON数据绑定的</a> 自适应表单。 预填服务和表单提交功能无缝衔接。 您不需要任何配置步骤。</p> </td> 
  </tr>
   <tr>
  <td></td> 
   <td> 
    <p>有关执行工作流的分步说明，请参 <a href="#jsonwithdatabinding">阅使用JSON架构作为数据源。</a></p> </td> 
  </tr>
  <tr>
  <td><p>XSD架构</p></td> 
   <td> 
    <p>选择XSD架构作为数据源。 根据所选数据源，您可以使 <a href="#generate-adaptive-forms-with-no-data-binding">用“自动表单转换”服务生成没有数据绑定的自适应表单</a> ，并将XSD架构配置为数据源。 您可以手动将自适应表单字段绑定到XSD架 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">构，并使用任何支持的协议</a> 来预填字段值。 根据需要修改字段值，并将数据提交到crx-repository。</p>
    </td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>有关执行工作流的分步说明，请参 <a href="#xsddatasource">阅使用XSD架构作为数据源。</a></p>
    </td> 
  </tr>
 </tbody> 
</table>


有关自动表单转换服务的详细信息，请参阅以下文章：

* [自动化表单转换服务简介](introduction.md)
* [配置自动化表单转换服务](configure-service.md)
* [将打印表单转换为自适应表单](convert-existing-forms-to-adaptive-forms.md)
* [审阅并修正转换后的表单](review-correct-ui-edited.md)

本文提供的信息基于以下假设：阅读该信息的任何人都具有关于自适应表单概念的基本知识。

## Pre-requisites {#pre-requisites}

* 配置 [AEM作者实例](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html)
* 在AEM [作者实例上配置Automated Forms Conversion服务](configure-service.md)

## 范例自适应表单 {#sample-adaptive-form}

要执行用例以在自适应表单中预填字段值并将它们提交到数据源，请下载以下范例PDF文件。

贷款申请表示例

[获取文件](assets/sample_loan_application_form.pdf)

PDF文件用作“自动表单转换”服务的输入。 该服务将此文件转换为自适应表单。 下图以PDF格式描述了示例贷款应用程序。

![示例贷款申请表](assets/sample_form_new.png)

## 为表单模型准备数据 {#prepare-data-for-form-model}

AEM Forms Data Integration允许您配置并连接到不同的数据源。 在使用转换过程生成自适应表单后，您可以基于表单数据模型、XSD或JSON架构定义表单模型。 您可以使用数据库、Microsoft Dynamics或任何其他第三方服务创建表单数据模型。

本教程使用MySQL数据库作为源创建表单数据模型。 在数据 **库中创建** loanapplication架构，并根据自适应表单中可用的字段将 **applicant** 表添加到架构中。

![示例数据mysql](assets/sample_data_mysql.png)

您可以使用以下DDL语句在数据库中创 **建** “申请人表”。

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

如果使用XSD架构作为表单模型来执行用例，请创建一个包含以下文本的XSD文件：

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

或将XSD架构下载到本地文件系统。

示例贷款应用程序XSD架构

[获取文件](assets/loanapplication.xsd)

有关在自适应表单中使用XSD架构作为表单模型的详细信息，请参阅 [使用XML架构创建自适应表单](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-xml-schema-form-model.html)。

如果您使用JSON架构作为表单模型来执行用例，请使用以下文本创建一个JSON文件：

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

或将JSON架构下载到本地文件系统。

示例贷款应用程序JSON架构

[获取文件](assets/demo_schema.json)

有关在自适应表单中将JSON架构用作表单模型的详细信息，请参阅 [使用JSON架构创建自适应表单](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html)。

## 生成无数据绑定的自适应表单 {#generate-adaptive-forms-with-no-data-binding}

使用“自 [动表单转换”服务](convert-existing-forms-to-adaptive-forms.md) ，将示 [例贷款申请表转换为无数据绑定的自适应表单](#sample-adaptive-form) 。 确保选中该复选框 **[!UICONTROL Generate adaptive form(s) without data bindings]** 以生成没有数据绑定的自适应表单。

![无数据绑定的自适应表单](assets/generate_af_without_binding.png)

在生成没有数据绑定的自适应表单后，为自适应表单选择数据源：

* [数据库、OData或任何第三方服务](#sqldatasource)
* [JSON架构](#jsondatasource)
* [XSD架构](#xsddatasource)

>[!NOTE]
> 如果您使用“自动表单转换”服务转换的自适应表单包含多个具有相同名称的字段，请确保这些字段绑定到数据源实体以避免在提交过程中可能发生数据丢失。


### 使用数据库、OData或任何第三方服务作为数据源 {#sqldatasource}

用例：使用“自动表单转换”服务生成没有数据绑定的自适应表单，并将MYSQL数据库配置为数据源。 您可以手动将自适应表单字段绑定到表单数据模型实体，并使用 **[!UICONTROL Form Data Model Prefill Service]** 选项预填字段值。 您可以使用 **[!UICONTROL Submit using Form Data Model]** 选项提交自适应表单。

执行用例之前：

* [将MySQL数据库配置为数据源](https://helpx.adobe.com/experience-manager/6-5/forms/using/configure-data-sources.html#configurerelationaldatabase)
* [创建表单数据模型](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html)

根据用例，创建Loanapplication表 **单数据模型** ，并将读取服务参数绑定到某个 **[!UICONTROL Literal]** 值。 电话号码文本值必须是在MySQL数据库的 **applicant** schema中配置的记录之一。 服务将该值用作从数据源获取详细信息的参数。 您还可以从下 [拉列表中选择用户配置文件属性](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html#bindargument)**[!UICONTROL Binding To]** 或请求属性

![配置表单数据模型](assets/configure_model_object.png)

>[!NOTE]
>
>确保在执行 **用例****之前，向表单数据模型添加get** 和insert服务，配置和测试服务。

执行以下步骤：

1. 选择文件夹中 **可用的转换的贷款申请表** ，然 **[!UICONTROL output]** 后点按 **[!UICONTROL Properties]**。
1. 点按选 **[!UICONTROL Form Model]** 项卡，从 **[!UICONTROL Form Data Model]** 下拉列 **[!UICONTROL Select From]** 表中进行选择，然后点按以 **[!UICONTROL Select Form Data Model]** 选择Loan Application **** Form Data Model。 点 **[!UICONTROL Save & Close]** 按以保存表单。
1. 选择示 **例贷款申请表** ，然后点按 **[!UICONTROL Edit]**。
1. 在选项卡 **[!UICONTROL Content]** 中，点按配置图标：

   ![配置表单容器](assets/configure_form_container.png)

   1. 在部 **[!UICONTROL Basic]** 分中，从 **[!UICONTROL Form Data Model Prefill service]** 下拉列 **[!UICONTROL Prefill Service]** 表中选择。

   1. 在部 **[!UICONTROL Submission]** 分中，从 **[!UICONTROL Submit using Form Data Model]** 下拉列 **[!UICONTROL Submit Action]** 表中选择。

   1. 使用字段选择数据 **[!UICONTROL Data Model to submit]** 模型。
   1. 点按 ![完成图标](assets/save_icon.svg) ，以保存属性。

1. 点按申请人姓名文本框，然后选择 ![配置图标](assets/configure_icon.svg) （配置）。

   1. 在“绑定引用”字段中，选择“ **申请人** ”>“ **名称**”，然后点 ![](assets/save_icon.svg) 按完成图标以保存属性。 同样，为地址、电话号码、电子邮 **件**、 **占领、年薪(美元**) **************、和否(No)创建数据绑定。 表单数据模型实体** ，包含从属族成员字段。
   ![绑定引用](assets/bind_references.png)

1. 点按 **[!UICONTROL Preview]** 以查看预填的自适应表单字段值。
1. 根据需要修改字段值，然后提交自适应表单。 字段值将提交到MySQL数据库。 您可以刷新数据 **库中的** “申请人表”，以查看表中的更新值。

**用例：** 使用“自动表单转换”服务生成没有数据绑定的自适应表单，并将MYSQL数据库配置为数据源。 您可以使用规则编辑器绑定自适应表单字段以预填字段值。 根据需要修改字段值，并将数据提交到crx-repository。

执行以下步骤以使用规 [则编辑器](https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html) ，调用表单数据模型服务以绑定自适应表单中的字段和预填值：

1. 选择文 **件夹中的贷款申请表** ，然 **[!UICONTROL output]** 后点按 **[!UICONTROL Edit]**。
1. 在选项卡 **[!UICONTROL Content]** 中，点按配置图标：

   ![配置表单容器](assets/configure_form_container.png)

   在部 **[!UICONTROL Basic]** 分中，从 **[!UICONTROL Form Data Model Prefill service]** 下拉列 **[!UICONTROL Prefill Service]** 表中选择。

1. 点按文 **[!UICONTROL Applicant Name]** 本框并点按 **[!UICONTROL Edit Rules]**。

   ![编辑规则以创建数据绑定](assets/edit_rules_bind_reference.png)

1. 点按 **[!UICONTROL Create]** 规则编辑器页面。
1. 在页 **[!UICONTROL Rule Editor]** 面上：

   1. 为“申请人姓名”文本框选择一个状态。 例如，这 **[!UICONTROL is initialized]**&#x200B;会导致在以模式渲染表 **[!UICONTROL Then]** 单时执行条件 **[!UICONTROL Preview]** 。

   1. 在部 **[!UICONTROL Then]** 分中，从 **[!UICONTROL Invoke Service]** 下拉列 **[!UICONTROL Select Action]** 表中选择。 Forms实例上的所有服务都显示在下拉列表中。

   1. 从列出 **[!UICONTROL Get]** 表单数据模型的部分中选择服务。 “输入”字段显 **示电话号码**，该号码是为申请人数据模型定义的 **主要键** 。 系统会根据此字段检索并预填充自适应表单中“输出”部分中字段的值。

   1. 使用“输出”部分为具有表单数据模型实体的自适应表单字段创建绑定。 例如，将自适 **[!UICONTROL Applicant Name]** 应表单字段与名称 **实体绑定** 。

   1. 点按 **[!UICONTROL Done]**. 再次 **[!UICONTROL Done]** 点按“规则编辑器”页面。
   ![用于绑定引用的规则编辑器](assets/rule_editor_bind_references.png)

1. 点按 **[!UICONTROL Preview]** 以查看预填的自适应表单字段值。

   >[!NOTE]
   >
   >确保在与自适 **[!UICONTROL Return Array]** 应表单关联的表单数据模型中， **get** service属性的“属性”设置为“关”。

1. 根据需要修改字段值，然后提交自适应表单。 提交的数据位于crx-repository中的以下位置：

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### 使用JSON架构作为数据源 {#jsondatasource}

**用例：** 您可以使用自动表单转换服务生成没有数据绑定的自适应表单，并将JSON架构配置为数据源。 您可以手动将自适应表单字段绑定到JSON架构，并使用“ **预览数据** ”选项预填字段值。 根据需要修改字段值，并将数据提交到crx-repository。

在执行用例之前，请确保您具有：

* [符合JSON架构结构的有效JSON架构](#prepare-data-for-form-model)
* [无数据绑定的自适应表单](#generate-adaptive-forms-with-no-data-binding)

执行以下步骤：

1. 选择输出文 **件夹中可用的已转换** 的贷款申请表 **,** 然后点按 **[!UICONTROL Properties]**。
1. 点按选 **[!UICONTROL Form Model]** 项卡，从 **[!UICONTROL Schema]** 下拉列 **[!UICONTROL Select From]** 表中进行选择，然后点按以上 **[!UICONTROL Select Schema]** 传保存在本地文件系统上的 **** demo.schema JSON架构。 点 **[!UICONTROL Save & Close]** 按以保存表单。
1. 选择示 **例贷款申请表** ，然后点按 **[!UICONTROL Edit]**。
1. 点按申请人姓名文本框，然后选择 ![配置图标](assets/configure_icon.svg) （配置）。

   在“绑定引用”字段中，选择“ **申请人** ”>“ **名称**”，然后点 ![](assets/save_icon.svg) 按完成图标以保存属性。 同样，为地址、电话号码、电子邮 **件**、 **占领、年薪(美元**) **************、和否(No)创建数据绑定。 具有JSON架构实体的** “从属系列成员”字段。

1. 再次选择文 **件夹中可用的转换的贷款申请表** , **[!UICONTROL output]** 然后选择 **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**。</br>

   下载范例数据文件</br>

   [获取文件](assets/json_data_file.txt)</br>

1. 根据需要修改字段值，然后提交自适应表单。 提交的数据位于crx-repository中的以下位置：

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### 使用XSD架构作为数据源 {#xsddatasource}

**用例：** 使用“自动表单转换”服务生成没有数据绑定的自适应表单，并将XSD架构配置为数据源。 您可以手动将自适应表单字段绑定到XSD架构，并使用带有数 **据的预览** 来预填字段值。 根据需要修改字段值，并将数据提交到crx-repository。

在执行用例之前，请确保您具有：

* [符合XML架构结构的有效XSD架构](#prepare-data-for-form-model)
* [无数据绑定的自适应表单](#generate-adaptive-forms-with-no-data-binding)

执行以下步骤：

1. 选择文件夹中 **可用的转换的贷款申请表** ，然 **[!UICONTROL output]** 后点按 **[!UICONTROL Properties]**。
1. 点按选 **[!UICONTROL Form Model]** 项卡，从 **[!UICONTROL Schema]** 下拉列 **[!UICONTROL Select From]** 表中选择，然后点按以上 **[!UICONTROL Select Schema]** 传保存在本地文件系统上的 **Loanapplication** XSD架构。 为XSD架构选择根元素，然后点 **[!UICONTROL Save & Close]** 按以保存表单。
1. 选择示 **例贷款申请表** ，然后点按 **[!UICONTROL Edit]**。
1. 点按申请人姓名文本框，然后选择 ![配置图标](assets/configure_icon.svg) （配置）。
在“绑定引用”字段中，选择“ **申请人** ”>“ **名称**”，然后点按 ![](assets/save_icon.svg) 完成图标以保存属性。 同样，为地址、电话号码、电子邮 **件**、 **占领、年薪(美元**) **************、和否(No)创建数据绑定。 包含XSD架构实体的** “从属系列成员”字段。

1. 再次选择输出 **文件夹中可用的已转换的示例贷** 款申请表 **，然后选择** > **[!UICONTROL Preview]****[!UICONTROL Preview with Data]**。</br>

   下载范例数据文件</br>

   [获取文件](assets/loan-application-data-xml-data.zip)</br>


1. 根据需要修改字段值，然后提交自适应表单。 提交的数据位于crx-repository中的以下位置：

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## 生成具有JSON绑定的自适应表单 {#generate-adaptive-forms-with-json-binding}

使用“自 [动表单转换”服务将示例贷](convert-existing-forms-to-adaptive-forms.md) 款申请表转换为具有数据绑定的自适应表单 [](#sample-adaptive-form) 。 确保在生成自适应表单时 **[!UICONTROL Generate adaptive form(s) without data bindings]** 不选中该复选框。

![具有JSON绑定的自适应表单](assets/generate_af_with_data_bindings.png)

### 使用JSON架构作为数据源 {#jsonwithdatabinding}

**用例：** 您可以使用自动表单转换服务生成具有JSON数据绑定的自适应表单。 预填服务和表单提交功能无缝衔接。 您不需要任何配置步骤。

在执行用例之前，请确保您有一个具 [有数据绑定的自适应表单](#generate-adaptive-forms-with-json-binding)。

执行以下步骤：

1. 再次选择文 **件夹中可用的转换的贷款申请表** , **[!UICONTROL output]** 然后选择 **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**。</br>

   下载范例数据文件</br>

   [获取文件](assets/loan_application_data_source_json_data_binding.txt)</br>

1. 根据需要修改字段值，然后提交自适应表单。 提交的数据位于crx-repository中的以下位置：

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## 将提交的自适应表单JSON数据转换为XML格式 {#convert-submitted-adaptive-form-data-to-xml}

在自适应表单字段中输入值并提交它时，crx-repository中的数据将以JSON格式提供。 您可以使用 [org.apache.sling.commons.json.xml](https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString) API或以下示例代码将JSON数据的格式转换为XML:

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
