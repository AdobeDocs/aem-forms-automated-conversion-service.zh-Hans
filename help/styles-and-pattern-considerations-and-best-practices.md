---
title: '最佳实践和注意事项 '
seo-title: '最佳实践和注意事项 '
description: automated forms conversion服务的最佳实践和注意事项
seo-description: 列表服务难以识别的源PDF forms中样式和模式的Automated forms conversion
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
translation-type: tm+mt
source-git-commit: e2298422e0af9b1c678e7604be3efb6da377d7dd
workflow-type: tm+mt
source-wordcount: '1259'
ht-degree: 2%

---


# 最佳实践和已知的复杂模式{#Best-practices-and-considerations2}

本文档提供了管理员、作者和开发人员在使用[!DNL Automated Forms Conversion service]时可从中受益的准则和建议。 它讨论了从准备源表单到修复复杂模式的最佳实践，这些复杂模式需要额外的努力才能实现自动转换。 这些最佳实践共同有助于[!DNL Automated Forms Conversion service]的整体性能和输出。

## 最佳实践

转换服务将AEM [!DNL Forms]实例上的可用PDF forms转换为自适应表单。 下面列出的最佳实践可以帮助您提高转化率和准确性。 此外，这些最佳实践可帮助您节省在转化活动后花费的时间。

### 上传源之前

您可以根据需要一次性或分阶段上传所有PDF forms。 上传表单之前，请注意以下几点：

* 将文件夹中的表单数保留在15以下，将文件夹中的页面总数保留在50以下。
* 将文件夹大小保持在10 MB以下。 请勿将表单放在子文件夹中。 
* 以少于15的形式保留页数。
* 将源文档组织成一批8-15文档。 在单个批中保留具有通用自适应表单片段的源表单。
* 请勿上传受保护的表单。 服务不会转换受密码保护和受保护的表单。
* 请勿上传[PDFPortfolio](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)。 服务不会将PDFPortfolio转换为自适应表单。
* 请勿上传扫描的、非英语的和已填写的表单。 此类表单不受支持。
* 请勿上传文件名中包含空格的源表单。 在上传表单之前，从文件名中删除空格。

使用XDP表单进行转换时，请在上传源XPD表单之前执行以下步骤：

* 分析XDP表单并修复可视问题。 确保源文档使用预期的控件和结构。 例如，源表单可能包含复选框，而不是单选单选单选单选单选按钮。 将复选框更改为单选按钮，以生成包含预期组件的自适应表单。
* [在开始转换之前，](http://www.adobe.com/go/learn_aemforms_designer_65) 将绑定添加到XDP格式。当源XDP表单中有绑定可用时，服务在转换过程中自动将绑定应用到相应的自适应表单字段。 它为您节省手动应用绑定所需的时间。
* [将Adobe Sign](https://helpx.adobe.com/sign/using/text-tag.html) 语添加到XDP文件。该服务自动将Adobe Sign标签转换为相应的自适应表单字段。 自适应Forms支持有限数量的Adobe Sign字段。 有关受支持字段的完整列表，请参阅[在自适应表单中使用Adobe Sign](https://docs.adobe.com/content/help/en/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html)文档。
* 尽可能将XDP文档中的复杂表转换为简单表。 表单元格中具有表单字段、大小不均的单元格、行或列跨越单元格、合并单元格、部分边框或无可见边框的表被视为复杂表。 具有上述任何项的表被视为复杂表。
<!-- * Use sub-forms in XDP documents to create panels in adaptive forms. Service converts each sub-form to one or more adaptive form panels during conversion. -->

### 在开始转换之前

* 创建自适应表单模板。 模板有助于为组织或部门的表单指定统一的结构。
* 在自适应表单模板中指定页眉和页脚。 服务将忽略源文档的页眉和页脚，并使用在自适应表单模板中指定的页眉和页脚。
* 创建自适应表单主题。 主题有助于为组织或部门的表单提供统一的外观。
* 配置表单数据模型以从数据源保存和检索。 为表单数据模型创建和配置读写服务。
* 创建自适应表单片段并配置服务以使用自适应表单片段。
* 为需要业务流程自动化的表单准备常见工作流模型。
* 根据需要配置Adobe Analytics


## 了解复杂模式

AEM [!DNL Forms Automated Conversion service]使用人工智能和机器学习算法来了解源表单的布局和字段。 每项机器学习服务都会不断学习源数据，并在每次客户流失时生成更好的输出。 这些服务从人类经验中学习。

[!DNL Automated Forms Conversion service] 是用大量形式训练的。它可轻松识别源表单中的字段并生成自适应表单。 但是，PDF forms中有一些领域和风格，它们在人眼中很容易看到，但在服务中却很难理解。 服务可以将不同于适用的字段类型或面板分配给某些字段或样式。 下面列出了所有此类字段和样式模式。

该服务将开始识别正确的字段或面板并将其分配给这些模式，因为它会不断从源数据中学习。 目前，您可以使用[Review and Correct](review-correct-ui-edited.md)编辑器修复此类问题。 在开始修复问题或进一步阅读之前，请先熟悉[自适应表单组件](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)。

### 常规模式{#general}

| 图案 | 示例 |
|--- |--- |
| **PatternService** <br>不会将已填充的PDF forms转换为自适应表单。<br><br>**分辨** <br>率使用空的自适应表单。 | ![已填写表单](assets/best-practice-filled-forms.png) |
| **PatternService** <br>无法识别密集表单中的文本和字段。<br><br>**分** <br> 辨率开始转换之前，增加密集表单的文本和字段之间的宽度。 |  |
| **PatternService** <br>不支持扫描的表单。<br><br>**分辨** <br>率请勿使用扫描的表单。 | ![扫描表单](assets/scanned-forms.png) |
| **PatternService** <br>不提取图像和图像内的文本。<br><br>**分辨** <br> 率手动将图像或文本添加到转换的表单。 | ![带有文本表单的图像](assets/best-practice-image-with-text.png) |
| **具** <br>有点线或非清晰边界和边框的图案表不进行转换。<br><br>**分辨** <br>率使用具有清晰明确边界和边框的表。支持。 | ![非清除表格](assets/best-practice-table-dotted-non-clear.png) |
| **模** <br> 式自适应表单不支持现成的垂直文本。因此，该服务不会将垂直文本转换为相应的自适应Forms文本。 <br><br>**分** <br> 辨率根据需要，使用自适应表单编辑器添加垂直文本。 | ![非清除表格](assets/vertical-text.png) |



### 选择组{#choice-group}

| 图案 | 分辨率 |
|--- |--- |
| **除框** <br> 或圆形以外的形状的PatternChoice组选项不会转换为相应的自适应表单组件。<br><br>**分辨** <br> 率将选择的形状更改为框或圆，或使用“审阅并更正”编辑器来标识形状。 | ![Choice字段  ](assets/best-practice-choice-group-options.png) |

### 表单字段{#form-fields}

| 图案 | 分辨率 |
|--- |--- |
| **PatternService** <br> 不识别没有清晰边框的字段。<br><br>**解** <br> 决方案使用审阅和正确编辑器来标识此类字段。 | ![具有非清晰边界的域](assets/best-practice-fields-without-clear-borders.png) |
| **PatternService** <br> 可能无法识别某些选择的在表单底部或右侧带有字幕的组表单字段。<br><br>**解** <br> 决方案使用审阅和正确的编辑器来标识此类字段 | ![Choice字段](assets/best-practice-caption-bottom-right.png) |
| **PatternService** <br> 会将错误类型合并或指定到彼此非常靠近或没有清晰边框的某些表单字段。<br><br>**解** <br> 决方案使用审阅和正确编辑器来标识此类字段。 | ![Choice字段](assets/best-practice-placed-very-near.png) |
| **PatternService** <br> 无法识别带有远离字幕的字段或字幕和输入字段之间的虚线。<br><br>**解决方** <br> 法使用边界明确的表单字段或使用“审阅并更正”编辑器来修复此类问题。 | ![字幕字段之间的远离字段或虚线](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### 列表 {#lists}

| 图案 | 分辨率 |
|--- |--- |
| **模式包** <br>含表单字段的列表会合并或不转换为相应的自适应表单组件 <br><br>**** <br>解决方案使用具有清晰边界的表单字段，或使用“审阅并更正”编辑器来修复此类问题。 | ![列表包含选择组](assets/best-practice-lists-containing-form-fields.png) |
| **PatternService** <br>可以留下一些嵌套的列表，但这些的 <br><br>**** <br> 身份不明。请使用“审阅”和“正确”编辑器来修复此类问题。 | ![列表包含选择组](assets/best-practice-nested-lists.png) |
| **PatternService** <br> 将包含选择组的某些列表与彼此的Resolution <br><br>**** <br> 使用“审阅”和“更正”编辑器来修复此类问题。 | ![列表包含选择组](assets/best-practice-check-box-in-table-cells.png) |

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
