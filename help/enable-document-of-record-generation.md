---
title: 在转换过程中生成记录文档
seo-title: 在转换过程中生成记录文档
description: 根据用于转换的源表单类型生成DoR的建议路径。
seo-description: 根据用于转换的源表单类型生成DoR的建议路径。
page-status-flag: never-activated
uuid: 7f0f5bf3-21be-449a-b23e-5946a9fd7ed4
contentOwner: khsingh
discoiquuid: 75f6e6bc-7636-4b40-919c-8b20a6ccbb1f
translation-type: tm+mt
source-git-commit: 640d72d7961ef0c2393bf0ae6745d918e388a056

---


# 为自适应表单启用记录文档生成的推荐工作流程 {#recommended-workflows-dor-generation}

记录文档(DoR)允许您以自适应形式保留您提供和提交的信息的记录，以便您以后可以参考它。
DoR使用基本模板来定义其布局。 您可以使用默认模板或将任何其他模板与自适应表单相关联来生成DoR。

![生成的记录文档](assets/document_of_record.gif)

有关生成DoR的详细信息，请参 [阅为自适应表单生成记录文档](https://helpx.adobe.com/experience-manager/6-5/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.html)。

自动 [化表单转换服务将](../help/introduction.md) 下列源表单转换为自适应表单：

* 非交互式PDF表单
* Acro Forms
* 基于XFA的PDF表单

根据用于转换的源表单，您可以使用以下方式生成DoR:

* 默认模板
* 源表单作为模板——如果选择此选项，转换服务会自动将源表单与转换后的自适应表单关联为DoR模板。
* 将任何其他模板与转换后的自适应表单相关联

下表说明了您使用的DoR模板如何影响生成的DoR的布局：

<table> 
 <tbody>
 <tr>
  <td><p><strong>源表单</strong></p></td>
  <td><p><strong>生成的DoR</strong></p></td> 
   </tr>
  <tr>
   <td><img src="assets/source_xdp_updated.png"/></td>
   <td><p>如果使用默认模板生成DoR:</br><img src="assets/source_form_default_updated.png"/></td>
   </tr>
   <tr>
   <td></td>
   <td><p>如果您使用源表单作为模板来生成DoR:</br></p><img src="assets/source_form_dor_updated.png"/></td>
   </tr>
  </tbody>
</table>

如表中所示，如果您使用源表单作为模板，DoR将保留源表单的布局。
本文介绍了根据三种类型的源表单生成DoR的建议路径。

<table> 
 <tbody> 
  <tr> 
   <th><strong>源表单</strong></th> 
   <th><strong>生成DoR的方法</strong></th> 
  </tr> 
  <tr> 
   <td><p>非交互式PDF表单</p></td> 
   <td> 
    <ul> 
     <li><a href="#generate-document-of-record-using-cloud-configuration">在自适应表单转换之前启用DoR生成，以使用默认模板生成DoR</a></li> 
     <li><a href="#edit-adaptive-form-properties-generate-document-of-record">在自适应表单转换后编辑自适应表单属性，以启用使用默认或任何其他表单模板生成DoR</a></li> 
    </ul> </td> 
  </tr>
  <tr> 
   <td><p>Acro表单或基于XFA的PDF表单</p></td> 
   <td> 
    <ul> 
     <li><a href="#use-input-form-as-template-to-generate-document-of-record">在自适应表单转换之前启用DoR生成，以使用源表单作为模板生成DoR</a></li> 
     <li><a href="#edit-adaptive-form-properties-to-generate-document-of-record">在自适应表单转换后编辑自适应表单属性，以启用使用默认模板、源表单作为模板或任何其他表单模板生成DoR</a></li> 
    </ul> </td> 
  </tr>    
 </tbody> 
</table>

## 为非交互式PDF表单生成记录文档 {#generate-document-of-record-non-interactive-pdf}

如果您使用非交互式PDF表单作为自动表单转换服务的源表单，您可以：

* 在自适应表单转换之前启用DoR生成，以使用默认模板生成DoR
* 或在自适应表单转换后编辑自适应表单属性，以启用使用默认或任何其他表单模板生成DoR

### 在转换前启用DoR生成，以使用默认模板生成DoR {#generate-document-of-record-using-cloud-configuration}

1. 选择 **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** >用于转换的云配置的属性> **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** 选项。

   ![使用云配置生成记录文档](assets/generate_dor_cloud_config.gif)

1. 点 **[!UICONTROL Save & Close]** 按以保存设置。

1. [运行转换](../help/convert-existing-forms-to-adaptive-forms.md)。 确保您使用在这些说明的步骤1中编辑的云配置。
在提交转换后的自适应表单时，DoR会使用默认模板自动生成。

### 转换后编辑自适应表单属性以启用DoR生成 {#edit-adaptive-form-properties-generate-document-of-record}

如果在将源表单转换为自适应表单之前不启用DoR生成，则在转换后仍可以启用。

1. [在非交互式](../help/convert-existing-forms-to-adaptive-forms.md) PDF表单上运行转换以生成自适应表单。

1. 在文件夹中选择自适应表 **[!UICONTROL output]** 单，然后点按 **[!UICONTROL Properties]**。

1. 在选 **[!UICONTROL Form Model]** 项卡中，展开部 **[!UICONTROL Document of Record Template Configuration]** 分并选择 **[!UICONTROL Generate Document of Record]**。

   ![生成记录文档](assets/generate_dor_af_properties.png)

1. 点 **[!UICONTROL Save & Close]** 按以保存设置。

在提交转换后的自适应表单时，DoR会使用默认模板自动生成。 如果要将任何其他DoR模板与转换后的自适应表单关联，可选择 **[!UICONTROL Associate form template as the Document of Record template]** 选项。

## 为Acro表单或基于XFA的PDF表单生成记录文档 {#generate-document-of-record-acroform-xfaform}

如果您使用Acro Form或基于XFA的PDF表单作为自动表单转换服务的源表单，您可以：

* 在自适应表单转换之前启用DoR生成，以使用源表单作为模板生成DoR

* 或在自适应表单转换后编辑自适应表单属性，以启用使用默认模板、源表单作为模板或任何其他表单模板生成DoR

### 在转换前启用DoR生成，以使用源表单模板生成DoR {#use-input-form-as-template-to-generate-document-of-record}

1. 选择 **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** >用于转换的云配置的属性> **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** 选项。

1. 点 **[!UICONTROL Save & Close]** 按以保存设置。

1. [运行转换](../help/convert-existing-forms-to-adaptive-forms.md)。 确保您使用在这些说明的步骤1中编辑的云配置。
转换服务会自动将Acro表单或基于XFA的PDF表单与转换后的自适应表单关联为DoR模板。
您可以打开自适应表单属性，以在选项卡的部分中查 **[!UICONTROL Document of Record Template Configuration]** 看DoR **[!UICONTROL Form Model]** 模板。

   ![编辑自适应表单属性以生成记录文档](assets/generate_dor_af_properties_xdp_acro.png)

   在提交转换后的自适应表单时，DoR会使用源表单模板自动生成。

### 转换后编辑自适应表单属性以启用DoR生成 {#edit-adaptive-form-properties-to-generate-document-of-record}

1. [在非交互式](../help/convert-existing-forms-to-adaptive-forms.md) PDF表单上运行转换以生成自适应表单。

1. 在文件夹中选择自适应表 **[!UICONTROL output]** 单，然后点按 **[!UICONTROL Properties]**。

1. 在选项 **[!UICONTROL Form Model]** 卡中，展开该部 **[!UICONTROL Document of Record Template Configuration]** 分，然后选择以 **[!UICONTROL Generate Document of Record]** 启用使用默认模板的DoR生成。
您还可以选择该选 **[!UICONTROL Associate form template as the Document of Record template]** 项并选择模板，以启用使用源表单模板或任何其他表单模板生成DoR。

1. 点 **[!UICONTROL Save & Close]** 按以保存设置。
