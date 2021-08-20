---
title: '最佳实践和注意事项 '
seo-title: '最佳实践和注意事项 '
description: 有关Automated forms conversion服务的最佳实践和注意事项
seo-description: 源PDF forms中Automated forms conversion服务发现难以识别的样式和模式列表
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
exl-id: 9ada091a-e7c6-40e9-8196-c568f598fc2a
source-git-commit: 65b0d6f6568ce7915b1a8bd85981bead967d869c
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 3%

---

# 最佳实践和已知的复杂模式 {#Best-practices-and-considerations2}

本文档提供了管理员、作者和开发人员在使用[!DNL Automated Forms Conversion service]时可从中受益的准则和建议。 它讨论了从准备源表单到修复复杂模式（自动化转换需要额外努力）的最佳实践。 这些最佳做法对[!DNL Automated Forms Conversion service]的整体性能和输出有共同的贡献。

## 最佳实践

转换服务会将AEM [!DNL Forms]实例上可用的PDF forms转换为自适应表单。 下面列出的最佳实践可帮助您提高转化速度和准确性。 此外，这些最佳实践还可帮助您节省在转化活动后花费的时间。

### 上传源之前

您可以根据需要一次或分阶段上传所有PDF forms。 上传表单之前，请注意以下几点：

* 将文件夹中的表单数量保留在15个以下，将文件夹中的总页数保留在50个以下。
* 将文件夹的大小保持在10 MB以下。 请勿将表单放在子文件夹中。 
* 格式为的页数少于15页。
* 将源文档整理成一批8-15个文档。 在单个批次中保留具有通用自适应表单片段的源表单。
* 请勿上载受保护的表单。 该服务无法转换受密码保护和安全的表单。
* 请勿上传[PDFPortfolio](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)。 该服务无法将PDFPortfolio转换为自适应表单。
* 请勿以英语、法语、德语和西班牙语以外的任何语言上传扫描、填写和表单。 此类表单不受支持。
* 请勿上载文件名中带空格的源表单。 在上传表单之前，从文件名中删除空格。

使用XDP表单进行转换时，请在上载源XPD表单之前执行以下步骤：

* 分析XDP表单并修复可视化问题。 确保源文档使用预期的控件和结构。 例如，源表单可能包含复选框，而不是单选按钮。 将复选框更改为单选按钮，以生成包含预期组件的自适应表单。
* [在开始转换之前，将](http://www.adobe.com/go/learn_aemforms_designer_65) 绑定添加到XDP格式。当源XDP表单中有绑定可用时，服务会在转换期间自动将绑定应用到相应的自适应表单字段。 它可节省手动应用绑定所需的时间。
* [将Adobe Sign](https://helpx.adobe.com/sign/using/text-tag.html) 标记添加到XDP文件。该服务会自动将Adobe Sign标记转换为相应的自适应表单字段。 自适应Forms支持有限数量的Adobe Sign字段。 有关受支持字段的完整列表，请参阅[在自适应表单中使用Adobe Sign](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html?lang=en)文档。
* 尽可能将XDP文档中的复杂表转换为简单表。 表格单元格中具有表单字段、大小不均的单元格、行或列跨越的单元格、合并的单元格、部分边框或无可见边框的表格被视为复杂表格。 包含上述任何一项的表被视为复杂表。
<!-- * Use sub-forms in XDP documents to create panels in adaptive forms. Service converts each sub-form to one or more adaptive form panels during conversion. -->

### 开始转化之前

* 创建自适应表单模板。 模板有助于为组织或部门的表单指定统一的结构。
* 在自适应表单模板中指定页眉和页脚。 该服务忽略源文档的页眉和页脚，并使用在自适应表单模板中指定的页眉和页脚。
* 创建自适应表单主题。 主题有助于为组织或部门的形式提供统一的外观。
* 配置表单数据模型以从数据源保存和检索。 为表单数据模型创建和配置读写服务。
* 创建自适应表单片段并配置服务以使用自适应表单片段。
* 为需要业务流程自动化的表单准备常见的工作流模型。
* 配置Adobe Analytics（如果需要）


## 了解复杂模式

AEM [!DNL Forms Automated Conversion service]使用人工智能和机器学习算法来了解源表单的布局和字段。 每项机器学习服务都会不断学习源数据，并在每次流失时产生改进的输出。 这些服务从人类经验中学习。

[!DNL Automated Forms Conversion service] 接受了大量形式的培训。它可轻松识别源表单中的字段并生成自适应表单。 但是，PDF forms中有一些字段和样式很容易被人们看到，但很难理解这些字段和样式。 该服务可以为某些字段或样式分配不同于适用字段类型或面板。 下面列出了所有此类字段和样式模式。

该服务将开始识别并为这些模式分配正确的字段或面板，因为它会不断从源数据中学习。 目前，您可以使用[Review and Crect](review-correct-ui-edited.md)编辑器来修复此类问题。 在开始修复问题或进一步阅读之前，请熟悉[自适应表单组件](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)。

### 一般模式 {#general}

| 图案 | 示例 |
|--- |--- |
| **** <br>PatternService不会将填充的PDF forms转换为自适应表单。<br><br>**** <br>解决办法使用空的自适应表单。 | ![填写的表单](assets/best-practice-filled-forms.png) |
| **** <br>PatternService无法识别密集形式的文本和字段。<br><br>**** <br> 解决办法在开始转换之前，增加密集表单的文本和字段之间的宽度。 |  |
| **** <br>PatternService不支持扫描的表单。<br><br>**** <br>解决办法请勿使用扫描的表单。 | ![扫描的表单](assets/scanned-forms.png) |
| **** <br>PatternService不提取图像和图像内的文本。<br><br>**** <br> 分辨率手动将图像或文本添加到已转换的表单。 | ![包含文本表单的图像](assets/best-practice-image-with-text.png) |
| **** <br>具有点线或非清除边界和边框的图案表格不会转换。<br><br>**** <br>解决办法使用具有明确边界和边界的表。受支持。 | ![非清单表单](assets/best-practice-table-dotted-non-clear.png) |
| **** <br> 模式自适应表单不支持开箱即用的垂直文本。因此，该服务不会将垂直文本转换为相应的自适应Forms文本。 <br><br>**** <br> 解决办法根据需要使用自适应表单编辑器添加垂直文本。 | ![非清单表单](assets/vertical-text.png) |



### 选择组  {#choice-group}

| 图案 | 分辨率 |
|--- |--- |
| **** <br> 除框或圆以外形状的PatternChoice组选项不会转换为相应的自适应表单组件。<br><br>**** <br> 分辨率将选择的形状更改为框或圆，或使用“审阅并更正”编辑器来识别形状。 | ![选择字段  ](assets/best-practice-choice-group-options.png) |

### 表单字段 {#form-fields}

| 图案 | 分辨率 |
|--- |--- |
| **** <br> PatternService不识别没有明确边框的字段。<br><br>**** <br> 解决办法使用审阅和更正编辑器来标识此类字段。 | ![具有非清除边界的字段](assets/best-practice-fields-without-clear-borders.png) |
| **** <br> PatternService可能无法识别表单底部或右侧带有字幕的某些选择组表单字段。<br><br>**** <br> 解决办法使用审阅和更正编辑器来标识此类字段 | ![选择字段](assets/best-practice-caption-bottom-right.png) |
| **** <br> PatternService将合并或分配错误类型给彼此非常靠近或没有明确边框的某些表单字段。<br><br>**** <br> 解决办法使用审阅和更正编辑器来标识此类字段。 | ![选择字段](assets/best-practice-placed-very-near.png) |
| **** <br> PatternService无法识别带有远距离字幕的字段或字幕与输入字段之间的虚线。<br><br>**** <br> 解决办法使用边界明确的表单字段，或使用“审阅并更正”编辑器来解决此类问题。 | ![字幕字段之间的远离字段或虚线](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### 列表 {#lists}

| 图案 | 分辨率 |
|--- |--- |
| **** <br>包含表单字段的模式列表会合并或不会转换为相应的自适应表单组件解决方案使用具有清晰边界的表 <br><br>**** <br>单字段，或使用“审阅并更正”编辑器来修复此类问题。 | ![包含选择组的列表](assets/best-practice-lists-containing-form-fields.png) |
| **** <br>PatternService可以保留一些未识别的嵌套列表，使用 <br><br>**** <br> “审阅”和“更正”编辑器来修复此类问题。 | ![包含选择组的列表](assets/best-practice-nested-lists.png) |
| **** <br> PatternService会将一些包含选择组的列表彼此合并解决方 <br><br>**** <br> 案使用审阅和更正编辑器来解决此类问题。 | ![包含选择组的列表](assets/best-practice-check-box-in-table-cells.png) |

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fields without borders are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->
