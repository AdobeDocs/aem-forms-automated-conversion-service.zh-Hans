---
title: '最佳实践和注意事项 '
seo-title: '最佳实践和注意事项 '
description: 自动表单转换服务的最佳实践和注意事项
seo-description: 自动表单转换服务发现难以识别的源PDF表单中的样式和模式列表
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
translation-type: tm+mt
source-git-commit: 0f413a8bc0bb444b6faaddaf32f84f36e38438a5

---


# 最佳实践和已知的复杂模式 {#Best-practices-and-considerations2}

本文档提供了管理员、作者和开发人员在使用自动表单转换服务时可从中受益的准则和建议。 它讨论了从准备源表单到修复复杂模式的最佳实践，这些模式需要额外的努力才能实现自动转化。 这些最佳实践共同有助于实现自动表单转换服务的整体性能和输出。

## 最佳实践

转换服务将AEM Forms实例中可用的PDF表单转换为自适应表单。 您可以根据需要一次性或分阶段上传所有PDF表单。 在上传表单之前，请考虑以下事项：

* 将表单数保留在小于15的文件夹中，将总页数保留在小于50的文件夹中。
* 将文件夹大小保持在10 MB以下。 请勿将表单保留在子文件夹中。
* 使表单中的页数保持在15以下。
* 请勿上传受保护的表单。 该服务不转换受口令保护和受保护的表单。
* 请勿上传 [PDF包](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)。 该服务不会将PDF包转换为自适应表单。
* 请勿上传扫描的、彩色的、非英语的表单和填写的表单。 不支持此类表单。
* 请勿上传文件名中包含空格的源表单。 在上传表单之前，从文件名中删除空格。
* 使用自适应表单模板为输出自适应表单指定页眉和页脚。 该服务忽略源PDF文档的页眉和页脚，并使用在自适应表单模板中指定的页眉和页脚。

## 了解复杂模式

AEM Forms Automated Conversion服务使用人工智能和机器学习算法来了解源表单的布局和字段。 每项机器学习服务都会持续学习源数据，并在每次客户流失时生成更好的输出。 这些服务从人类的体验中学习。

自动表单转换服务是针对大量表单进行培训的。 它可轻松识别源表单中的字段并生成自适应表单。 但是，PDF表单中有一些字段和样式，这些字段和样式在人眼中很容易可见，但对于服务来说却难以理解。 服务可以为某些字段或样式分配不同于适用字段类型或面板。 以下列出了所有此类字段和样式模式。

当该服务不断从源数据中学习时，它将开始识别正确的字段或面板并将其分配给这些模式。 目前，您可以使用“审阅”和“ [更正”编辑器](review-correct-ui-edited.md) ，修复此类问题。 在开始修复问题或进一步阅读之前，请先熟悉自适 [应表单组件](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)。

### 一般模式 {#general}

| 图案 | 分辨率 |
|--- |--- |
| **Pattern**<br> service不会将彩色PDF表单转换为自适应表单。 <br><br>**分辨率&#x200B;**<br>使用黑白或灰度PDF表单。 | ![彩色表单](assets/best-practice-coloured-forms.png) |
| **Pattern** <br>Service不会将已填写的PDF表单转换为自适应表单。 <br><br>**分辨率&#x200B;**<br>使用空的自适应表单。 | ![填写的表单](assets/best-practice-filled-forms.png) |
| **Pattern** <br>Service无法识别密集表单中的文本和字段。 <br><br>**分辨率&#x200B;**<br>在开始转换之前，增加密集表单的文本和字段之间的宽度。 |  |
| **Pattern** <br>Service不支持扫描的表单。 <br><br>**分辨率&#x200B;**<br>请勿使用扫描的表单。 | ![扫描的表单](assets/scanned-forms.png) |
| **Pattern** <br>Service不提取图像中的图像和文本。 <br><br>**分辨率&#x200B;**<br>手动向转换的表单添加图像或文本。 | ![带有文本表单的图像](assets/best-practice-image-with-text.png) |
| **具有**<br>点线或非清晰边界和边框的图案表不进行转换。 <br><br>**分辨率&#x200B;**<br>使用具有清晰明确边界和边框的表。 支持。 | ![表格不清](assets/best-practice-table-dotted-non-clear.png) |
| **图案**<br> 自适应表单不支持现成的垂直文本。 因此，该服务不会将垂直文本转换为相应的自适应表单文本。 <br><br>**分辨率&#x200B;**<br>根据需要使用自适应表单编辑器添加垂直文本。 | ![表格不清](assets/vertical-text.png) |



### 选择组 {#choice-group}

| 图案 | 分辨率 |
|--- |--- |
| **除框**<br> 或圆形之外的形状的“图案选择”组选项不会转换为相应的自适应表单组件。 <br><br>**分辨率&#x200B;**<br>将选择的形状选项更改为框或圆形，或使用“审阅并更正”编辑器来标识形状。 | ![选择字段 ](assets/best-practice-choice-group-options.png) |

### 表单字段 {#form-fields}

| 图案 | 分辨率 |
|--- |--- |
| **模式**<br> 服务不识别没有清晰边框的字段。 <br><br>**分辨率&#x200B;**<br>使用“审阅”和“正确”编辑器来标识此类字段。 | ![具有非清晰边界的域](assets/best-practice-fields-without-clear-borders.png) |
| **Pattern**<br> service可能无法识别某些选择的组表单字段，这些字段在表单的底部或右侧带有字幕。 <br><br>**Resolution **Use<br>Review and Correct editor to identify the fields | ![选择字段](assets/best-practice-caption-bottom-right.png) |
| **Pattern**<br> service会将错误类型合并或指定到某些表单字段，这些字段彼此非常靠近或没有清晰的边框。 <br><br>**分辨率&#x200B;**<br>使用“审阅”和“正确”编辑器来标识此类字段。 | ![选择字段](assets/best-practice-placed-very-near.png) |
| **模式**<br> 服务无法识别带有远距离字幕的字段或字幕和输入字段之间的虚线。 <br><br>**解决方&#x200B;**<br>案使用边界明确的表单字段，或使用“审阅并更正”编辑器修复此类问题。 | ![字幕字段之间的远距离字段或虚线](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### 列表 {#lists}

| 图案 | 分辨率 |
|--- |--- |
| **模式**<br><br><br>****<br>包含表单字段的列表会被合并或不会转换为相应的自适应表单组件解决方案使用具有清晰边界的表单字段，或使用“审阅并更正”编辑器来修复此类问题。 | ![包含选择组的列表](assets/best-practice-lists-containing-form-fields.png) |
| **Pattern** <br>Service可以留下几个嵌套列表，但不能通过“ <br><br>**Resolution **<br>Use Review”（使用审阅）和“Correct”（更正）编辑器来修复此类问题。 | ![包含选择组的列表](assets/best-practice-nested-lists.png) |
| **Pattern**<br> service将包含选择组的某些列表与彼此的“ <br><br>**Resolution **Use Review”(分辨率<br>)和“Correct”（正确）编辑器合并，以修复此类问题。 | ![包含选择组的列表](assets/best-practice-check-box-in-table-cells.png) |

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