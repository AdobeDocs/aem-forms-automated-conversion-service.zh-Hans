---
title: 扩展默认元模型
seo-title: 扩展默认元模型
description: 扩展默认元模型以添加特定于贵组织的模式、验证和实体，并在运行Automated forms conversion服务时将配置应用到自适应表单字段。
seo-description: 扩展默认元模型以添加特定于贵组织的模式、验证和实体，并在运行Automated forms conversion服务时将配置应用到自适应表单字段。
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
exl-id: f679059c-18aa-4cb5-8368-ed27e96c20de
source-git-commit: 3f91fc0541f8fe8dbc997ae0b401c8a0a49347dd
workflow-type: tm+mt
source-wordcount: '2569'
ht-degree: 1%

---

# 扩展默认元模型 {#extend-the-default-meta-model}

automated forms conversion服务从源表单中标识和提取表单对象。 语义映射器有助于服务确定如何以自适应形式表示提取的对象。 例如，源表单可以具有多种不同类型的日期表示形式。 语义映射器帮助将源表单的日期表单对象的所有表示与自适应表单的日期组件进行映射。 语义映射器还允许服务在转换期间将验证、规则、数据模式、帮助文本和辅助功能属性预配置并应用于自适应表单组件。

![](assets/meta-model.gif)

元模型是JSON模式。 在开始使用元模型之前，请确保您精通JSON。 您必须具有创建、编辑和读取JSON格式保存的数据的经验。

## 缺省元模型 {#default-meta-model}

automated forms conversion服务具有默认的元模型。 它是JSON架构，并且与Adobe服务的其他组件一起驻留在Automated forms conversion云中。 您可以在本地AEM服务器上找到元模型的副本：http://&lt;server>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/metamodel/`global.schema.json`。 您也可以[单击此处](assets/en.globalschema.json)访问或下载英语架构。 [法语](assets/fr.globalschema.json)、[德语](assets/de.globalschema.json)和[西班牙语](assets/es.globalschema.json)语言的元模型也可供下载。

元模型的模式是从https://schema.org/docs/schemas.html上的模式实体派生的。 它具有人员、邮政地址、本地业务和更多实体，定义在https://schema.org上。 元模型的每个实体都与JSON模式对象类型相符。 以下代码表示一个示例元模型结构：

```
   "Entity": {
      "id": "Entity",
      "properties": {
        "name": {
          "type": "string"
        },

        "description": {
          "type": "string",
          "description": "Description of the item"
        }
      }
    }
```

## 下载默认元模型 {#download-the-default-meta-model}

执行以下步骤，将默认元模型下载到本地文件系统：

1. 登录到AEM Forms实例。
1. 导航到&#x200B;**[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** **>** **[!UICONTROL Meta Model]**&#x200B;文件夹。
1. 选择&#x200B;**[!UICONTROL global.schema.json]**&#x200B;文件，然后点按&#x200B;**[!UICONTROL Download]**。 将出现下载对话框。 选择&#x200B;**[!UICONTROL Download asset(s) as binary files]**&#x200B;选项。 点按 **[!UICONTROL Download]**. 将下载存档。

   <!--
   Comment Type: draft

   <li><p>Extract the archive and open the global.schema.json file for editing. </p> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

## 了解元模型 {#understanding-the-meta-model}

元模型是指包含实体的JSON架构文件。 JSON架构文件中的所有实体都包含名称和ID。 每个实体可以包含多个属性。 实体及其属性可能因域而异。 您可以使用关键字和字段配置来扩充架构文件，以将架构属性映射到自适应表单组件。

```
"Event": {
      "id": "Eventid",
      "allOf": [
        {
          "$ref": "#Entity"
        },
        {
          "properties": {
            "startDate": {
              "type": "string",
              "format": "date",
              "description": "Specify the start date and time of the event in ISO 8601 date format."
            },
            "endDate": {
              "type": "string",
              "format": "date",
              "description": "Specify the end date and time of the event in ISO 8601 date format."
            },
            "location": {
              "$ref": "#PostalAddress",
              "description": "Specify the location of the event."
            }
          }
        }
      ]
    }
```

在此示例中， **Event**&#x200B;表示实体的名称，该实体的值表示&#x200B;**id**&#x200B;为&#x200B;**Eventid**。 事件实体包括多个属性：

* startDate
* endDate
* 位置

元模型中的&#x200B;**allOf**&#x200B;结构支持实体之间的继承。

每个属性还可以包括：

* [JSON架构属性](#jsonschemaproperties)
* [基于关键字的搜索，用于将属性应用到生成的自适应表单字段](#keywordsearch)
* [其他属性](#additionalproperties)

![元模型属性](assets/meta_model_elements.gif)

根据使用&#x200B;**aem:affKeyword**&#x200B;引用的关键词，转换服务对源表单字段执行搜索操作。 转换服务将JSON架构属性和其他属性应用到满足搜索条件的字段。

在本例中，转换服务在源形式中搜索电话、电话、移动电话、工作电话、家庭电话、电话号码、电话号码和电话号码关键字。 根据包含这些关键词的字段，转化服务会在转化后将类型、模式和aem:afProperties应用到自适应表单字段。

### 生成的自适应表单字段的JSON架构属性 {#jsonschemaproperties}

元模型支持以下JSON模式通用属性，用于使用Automated forms conversion服务生成的自适应表单字段：

<table> 
 <tbody> 
  <tr> 
   <th><strong>属性名称</strong></th> 
   <th><strong>描述</strong></th> 
  </tr> 
  <tr> 
   <td><p>页面</p></td> 
   <td> 
    <p>元模型的标题属性中提及的文本将用作搜索关键字，以对生成的自适应表单字段执行操作。 例如，修改自适应表单字段的标签。 有关更多信息，请参阅<a href="#custommetamodelexamples">自定义元模型示例中的<strong>修改表单字段</strong>的标签。</a></p> </td> 
  </tr>
  <td><p>描述</p></td> 
   <td> 
    <p>描述属性为生成的自适应表单字段设置帮助文本。 有关更多信息，请参阅<a href="#custommetamodelexamples">自定义元模型示例中的<strong>将帮助文本添加到表单字段</strong>。</a></p> </td> 
  </tr>
  <td><p>类型</p></td> 
   <td> 
    <p>type属性为生成的自适应表单字段定义数据类型。 title属性的可能值包括：</p>
    <ul> 
     <li>字符串：生成文本数据类型的自适应表单字段。</li> 
     <li>数字：生成数字数据类型的自适应表单字段。</li>
     <li>整数：生成数值数据类型的自适应表单字段，并将子类型设置为整数。</li>
     <li>布尔值：生成交换机自适应表单组件。</li>
     </ul><p>有关在元模型中使用type属性的更多信息，请参阅<a href="#custommetamodelexamples">自定义元模型示例中的<strong>修改表单字段的类型</strong>。</a></p></td> 
  </tr>
  <td><p>图案</p></td> 
   <td> 
    <p>模式属性基于正则表达式限制生成的自适应表单字段的值。 例如，元模型中的以下代码将生成的自适应表单字段的值限制为10位：<br>"pattern":"/\\d{10}/"<br>同样，元模型中的以下代码会将字段值限制为特定日期格式。<br> "pattern":"date{DD MMMM， YYYY}",</p> </td> 
  </tr>
  <td><p>format</p></td> 
   <td> 
    <p>format属性基于命名模式而不是正则表达式来限制生成的自适应表单字段的值。 format属性的可能值包括：<ul><li>电子邮件：生成电子邮件自适应表单组件。</li><li>主机名：生成文本框自适应表单组件。</li></ul>有关在元模型中使用format属性的更多信息，请参阅<a href="#custommetamodelexamples">自定义元模型示例中的<strong>修改表单字段</strong>的格式。</a></p> </td> 
  </tr>
  <td><p>enum和enumNames</p></td> 
   <td> 
    <p>enum和enumNames属性将下拉列表、复选框或单选按钮字段的值限制为固定集。 enumNames中列出的值显示在用户界面上。 使用枚举属性列出的值将用于计算。<br>有关更多信息，请参 <strong>阅将表单字段转换为自适应表单中的多选复选框</strong>、 <strong>将文本字段转换为自适应表单中的下拉列表</strong>，以及 <strong>向下拉列表添加其他选项(</strong>  <a href="#custommetamodelexamples">自定义元模型示例)。</a></p> </td> 
  </tr>
 </tbody> 
</table>

### 基于关键字的搜索，用于将属性应用到生成的自适应表单字段 {#keywordsearch}

automated forms conversion服务在转换期间对源表单执行关键词搜索。 过滤满足搜索标准的字段后，转换服务会将元模型中为这些字段定义的属性应用到生成的自适应表单字段。

使用&#x200B;**aem:affKeyword**&#x200B;属性引用关键词。

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

在此示例中，转化服务使用&#x200B;**aem:affKeyword**&#x200B;中的文本作为搜索关键词。 在检索表单中的&#x200B;**银行帐号**&#x200B;文本后，转换服务会使用&#x200B;**type**&#x200B;属性将字段转换为&#x200B;**number**&#x200B;类型。

### 生成的自适应表单字段的其他属性 {#additionalproperties}

您可以使用元模型中的&#x200B;**aem:afProperties**&#x200B;属性，为使用Automated forms conversion服务生成的自适应表单字段定义以下其他属性：

<table> 
 <tbody> 
  <tr> 
   <th><strong>属性名称</strong></th> 
   <th><strong>描述</strong></th> 
  </tr> 
  <tr> 
   <td><p>multiLine</p></td> 
   <td> 
    <p>多行属性在转换后将源表单字段转换为自适应表单中的多行字段。 有关更多信息，请参阅<a href="#custommetamodelexamples">自定义元模型示例中的<strong>将字符串字段转换为多行字段</strong>。</a></p> </td> 
  </tr>
  <td><p>mandatory</p></td> 
   <td> 
    <p>“必填”属性将转换后自适应表单字段的输入设置为“必填”。<br>有关更多信息，请参 <strong>阅自定义元模型示例中</strong> 的 <a href="#custommetamodelexamples">向自适应表单字段添加验证。</a></p>
    </td> 
  </tr>
  <td><p>jcr:title</p></td> 
   <td> 
    <p>jcr:title属性（带有标题JSON模式属性）允许您在转换后修改自适应表单字段的标签。<br>有关更多信息，请参 <strong>阅自定义元模型示例中</strong> 的 <a href="#custommetamodelexamples">修改表单字段的标签。</a><br>请参 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html" target="_blank">阅使用JSON模式创</a> 建自适应表单，以了解有关可以使用JSON模式应用于自适应表单字段的更多属性的信息。</p>
    <p></p></td> 
  </tr>
  <td><p>sling:resourceType和guideNodeClass</p></td> 
   <td> 
    <p>sling:resourceType和guideNodeClass属性允许您将表单字段映射到相应的自适应表单组件。<br>有关更多信息，请 <strong>参阅自适应表单中的将表单字段转换为多选复选框，以及自</strong> 适应 <strong>表单中的将文本字段转换为下拉列表(自定义元</strong> 模型 <a href="#custommetamodelexamples">示例中)。</a></p> </td> 
  </tr>
  <td><p>validatePictureClause</p></td> 
   <td> 
    <p>validatePictureClause属性对转换后自适应表单字段中允许的格式设置验证。<br>有关更多信息，请参 <strong>阅自定义元模型示例中</strong> 的 <a href="#custommetamodelexamples">向自适应表单字段添加验证。</p> </td> 
  </tr>
 </tbody> 
</table>

## 使用您自己的语言创建自定义元模型{#language-specific-meta-model}

可以创建语言特定的元模型。 此类元模型可帮助您使用所选语言创建映射规则。 automated forms conversion服务允许您创建以下语言的元模型：

* 英语(en)
* 法语(fr)
* 德语(de)
* 西班牙语()

将&#x200B;*aem:Language*&#x200B;元标记添加到元模型顶部以指定其语言。 例如，

```JSON
"metaTags": {
        "aem:Language": "de"
    }
```

英语是元模型的默认语言。

### 创建语言特定元模型的注意事项

* 确保每个键的名称都使用英语。 例如， emailAddress。
* 确保所有&#x200B;*id*&#x200B;键的所有实体引用和预定义值均使用英语。 例如“id”：&quot;ContactPoint&quot; / &quot;$ref&quot;:“实体”。
* 确保以下键的元模型中包含的描述或消息与元模型的语言相对应：
   * aem:affKeyword
   * 页面
   * 描述
   * enumNames
   * shortDescription
   * validatePictureClauseMessage

   例如，当元模型的语言为法语(&quot;aem:Language&quot;)时：“fr”)，确保所有说明和消息都使用法语。

* 确保所有[JSON架构属性](#jsonschemaproperties)仅使用受支持的值。

下图显示了英语元模型和相应法语元模型的示例：

![](assets/language-specific-meta-model-comparison.png)

## 使用自定义元模型修改自适应表单字段 {#modify-adaptive-form-fields-using-custom-meta-model}

除了默认元模型中列出的模式和验证之外，您的组织还可以具有这些模式和验证。 您可以扩展默认元模型，以添加特定于贵组织的模式、验证和实体。 automated forms conversion服务在转换期间将自定义元模型应用到表单字段。 您可以随着发现特定于贵组织的新模式、验证和实体而不断更新元模型。

automated forms conversion服务使用保存在以下位置的默认元模型在转换期间将源表单字段映射到自适应表单字段：

http://&lt;服务器>:&lt;端口>/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json

但是，您可以将自定义元模型保存在文件夹中，并修改转换服务属性以在转换期间使用自定义元模型。

### 在转换期间使用自定义元模型 {#use-custom-meta-model-during-conversion}

执行以下步骤以在转换期间使用自定义元模型：

1. 在&#x200B;**[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**&#x200B;中创建文件夹，然后将自定义元模型JSON架构文件上传到该文件夹。
1. 使用以下方法打开转换服务属性：

   **[!UICONTROL Tools]** > >  **[!UICONTROL Cloud Services]** >  **[!UICONTROL Automated Forms Conversion Configuration]**>选 **&lt;>定配置的属性**>****

1. 在&#x200B;**[!UICONTROL Basic]**&#x200B;选项卡的&#x200B;**[!UICONTROL Custom Meta-model]**&#x200B;字段中指定自定义元模型的位置，然后点按&#x200B;**[!UICONTROL Save & Close]**。
1. [运行转](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) 换以将自定义元模型应用到转换过程。

### 自定义元模型示例 {#custommetamodelexamples}

使用自定义元模型修改自适应表单字段属性的一些常见示例包括：

* 修改表单字段的标签
* 修改表单字段的类型
* 将帮助文本添加到表单字段
* 在自适应表单中将表单字段转换为多选单选按钮
* 修改表单字段的格式
* 向自适应表单字段添加验证
* 在自适应表单中将表单字段转换为下拉列表选项
* 向下拉列表中添加其他选项
* 将字符串字段转换为多行字段

#### 修改表单字段的标签 {#modify-the-label-of-a-form-field}

**示例：** 在转换后，将表单中的银行帐号标签修改为自适应表单中的自定义帐号。

在此自定义元模型中，转换服务使用&#x200B;**title**&#x200B;属性作为搜索关键字。 在表单中检索&#x200B;**银行帐号**&#x200B;文本后，转换服务会将该文本替换为&#x200B;****&#x200B;字符串，该字符串在&#x200B;**aem:afProperties**&#x200B;部分中使用&#x200B;**jcr:title**&#x200B;属性提及。

```
{
  "numberfields": {
      "type": "number",
   "title": "Bank account number",
   "aem:afProperties" : {
    "jcr:title" : "Customer account number"
   }
   }
}
```

#### 修改表单字段的类型 {#modify-the-type-of-a-form-field}

**示例**:在转换 **后** ，将表单中文本类型的“银行帐号”字段修改为自适应表单中的数字类型字段。

在此自定义元模型中，转换服务使用&#x200B;**aem:affKeyword**&#x200B;中的文本作为搜索关键字。 在表单中检索&#x200B;**银行帐号**&#x200B;文本后，转换服务会使用&#x200B;**type**&#x200B;属性将字段转换为数字类型。

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

#### 将帮助文本添加到表单字段 {#add-help-text-to-a-form-field}

**示例**:在自适应表单的“银 **行帐** 号”字段中添加帮助文本。

在此自定义元模型中，转换服务使用&#x200B;**aem:affKeyword**&#x200B;中的文本作为搜索关键字。 在表单中检索&#x200B;**银行帐号**&#x200B;文本后，转换服务会使用&#x200B;**description**&#x200B;属性将帮助文本添加到自适应表单字段。

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "description": "Specify your bank account number."
 }
}
```

#### 将表单字段转换为自适应表单中的多选复选框 {#convert-a-form-field-to-multiple-choice-check-boxes-in-the-adaptive-form}

**示例**:在转换 **** 前，将表单中字符串类型的Countryfield转换为转换后自适应表单中的复选框。

在此自定义元模型中，转换服务使用&#x200B;**aem:affKeyword**&#x200B;中的文本作为搜索关键词。 在表单中检索&#x200B;**Country**&#x200B;文本后，转换服务会使用&#x200B;**enum**&#x200B;属性将字段转换为以下复选框：

* 印度
* 英格兰
* 澳大利亚
* 新西兰

**sling:** resourceTypeand  **** guideNodeClassproperties将表单字段映射到复选框自适应表单组件。

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidecheckbox",
      "guideNodeClass": "guidecheckbox"
    }
  }
}
```

#### 修改表单字段的格式 {#modify-the-format-of-a-form-field}

**示例**:将“电子邮件地址” **的** 格式修改为电子邮件格式。

在此自定义元模型中，转换服务使用&#x200B;**aem:affKeyword**&#x200B;中的文本作为搜索关键词。 在检索表单中的&#x200B;**电子邮件地址**&#x200B;文本后，转换服务会使用&#x200B;**format**&#x200B;属性将字段转换为电子邮件格式。

```
{
   "additionalDetails" : {
      "aem:affKeyword": ["E-mail Address"],
       "type" : "string",
       "format" : "email"
  } 
}
```

#### 向自适应表单字段添加验证 {#add-validations-to-adaptive-form-fields}

**示例1:** 向自适应表单的“邮 **政** 代码”字段添加验证。

在此自定义元模型中，转换服务使用&#x200B;**aem:affKeyword**&#x200B;中的文本作为搜索关键字。 在表单中检索&#x200B;**邮政编码**&#x200B;文本后，转换服务会使用&#x200B;**aem:afProperties**&#x200B;部分中定义的&#x200B;**validatePictureClause**&#x200B;属性向字段添加验证。 根据验证，您为自适应表单中的&#x200B;**邮政编码**&#x200B;字段指定的输入在转换后必须包含六个字符。

```
{
   "postalCode" : {
      "aem:affKeyword": ["Postal Code"],
      "type" : "string",
      "aem:afProperties" : {
        "validatePictureClause" : "\\d{6}"
      } 
   }
}
```

**示例2:** 向自适应表单的“银 **行** 帐号”字段添加验证。

在此自定义元模型中，转换服务使用&#x200B;**aem:affKeyword**&#x200B;中的文本作为搜索关键字。 在表单中检索&#x200B;**银行帐号**&#x200B;文本后，转换服务会使用&#x200B;**aem:afProperties**&#x200B;部分中定义的&#x200B;**mandatory**&#x200B;属性向字段添加验证。 在转换后提交表单之前，必须根据验证为&#x200B;**银行帐号**&#x200B;字段指定值。

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "aem:afProperties" : {
        "mandatory": "true"
      }   
   }
}
```

#### 在自适应表单中将文本字段转换为下拉列表 {#convert-a-text-field-to-drop-down-list-in-the-adaptive-form}

**示例**:在转换 **** 前，将表单中字符串类型的Countryfield转换为自适应表单中的下拉选项。

在此自定义元模型中，转换服务使用&#x200B;**aem:affKeyword**&#x200B;中的文本作为搜索关键字。 在表单中检索&#x200B;**Country**&#x200B;文本后，转换服务会使用&#x200B;**enum**&#x200B;属性将字段转换为以下下拉列表选项：

* 印度
* 英格兰
* 澳大利亚
* 新西兰

**sling:** resourceType和 **** guideNodeClassproperties将表单字段映射到下拉自适应表单组件。

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidedropdownlist",
      "guideNodeClass": "guideDropDownlist"
    }
  }
}
```

#### 向下拉列表中添加其他选项 {#add-additional-options-to-the-drop-down-list}

**示例：** 使用 **自** 定义元模型将Sri Lankaas作为额外选项添加到现有下拉列表中。

要添加额外选项，请使用新选项更新&#x200B;**enum**&#x200B;属性。 在此示例中，使用&#x200B;**斯里兰卡**&#x200B;作为额外选项更新&#x200B;**enum**&#x200B;属性。 **enum**&#x200B;属性中列出的值显示在下拉列表中。

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand",
   "Sri Lanka"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidecheckbox",
      "guideNodeClass": "guidecheckbox"
    }
  }
}
```

#### 将字符串字段转换为多行字段 {#convert-a-string-field-to-a-multi-line-field}

**示例：** 转换 **** 后，将字符串类型的地址字段转换为表单中的多行字段。

在此自定义元模型中，转换服务使用&#x200B;**aem:affKeyword**&#x200B;中的文本作为搜索关键字。 在检索表单中的&#x200B;**Address**&#x200B;文本后，该服务使用&#x200B;**aem:afProperties**&#x200B;部分中定义的&#x200B;**multiLine**&#x200B;属性将文本字段转换为多行字段。

```
{
 "multiLine" : {
   "aem:affKeyword": [
      "Address"
    ],
    "type" : "string",
    "aem:afProperties": {
      "multiLine": "true"
    }
  }
}
```
