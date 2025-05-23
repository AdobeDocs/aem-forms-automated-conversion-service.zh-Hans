---
title: 最佳实践和注意事项
description: automated forms conversion服务(AFCS)的最佳实践和注意事项
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
exl-id: 9ada091a-e7c6-40e9-8196-c568f598fc2a
source-git-commit: 4b227a2cd0253b8ab471007b41787de60c2a1851
workflow-type: tm+mt
source-wordcount: '1229'
ht-degree: 2%

---

# 最佳实践和已知的复杂模式 {#Best-practices-and-considerations2}

本文档提供了表单管理员、作者和开发人员在使用[!DNL Automated Forms Conversion service] (AFCS)时可以从中受益的准则和建议。 该文档讨论了从准备源表单到修复复杂模式的最佳实践，这些模式需要为自动化转换付出一些额外的努力。 这些最佳做法共同对[!DNL Automated Forms Conversion service] (AFCS)的整体性能和输出做出了贡献。

## 最佳实践

转换服务将AEM [!DNL Forms]实例上的可用PDF forms转换为自适应表单。 下面列出的最佳实践可帮助您提高转换速度和准确性。 此外，这些最佳实践还可帮助您节省在转化活动后所花费的时间。

### 上传源之前

您可以根据需要一次性上传所有PDF forms，也可以分阶段上传。 上传表单之前，请注意以下几点：

* 将文件夹中的表单数保持在15个以下，将文件夹中的总页数保持在50个以下。
* 将文件夹的大小保持在10 MB以下。 不要将表单放在子文件夹中。
* 将表单中的页数保持在15页以下。
* 将源文档整理成一批8-15个文档。 将带有通用自适应表单片段的源表单保留在单个批次中。
* 请勿上传受保护的表单。 该服务无法转换受密码保护和受保护的表单。
* 请勿上传[PDFPortfolio](https://helpx.adobe.com/cn/acrobat/using/overview-pdf-portfolios.html)。 该服务无法将PDFPortfolio转换为自适应表单。
* 请勿上载文件名中带有空格的源表单。 在上传表单之前，从文件名称中删除空格。
* 除英语、法语、德语、西班牙语、意大利语和葡萄牙语外，请勿上传任何语言的扫描、填写和表单。 此类表单不受支持。

使用XDP表单进行转换时，请先执行以下步骤，然后再上传源XPD表单：

* 分析XDP表单并修复视觉问题。 确保源文档使用预期的控制和结构。 例如，源表单可能具有复选框而不是单选单选按钮。 将复选框更改为单选按钮以生成具有预期组件的自适应表单。
* [在开始转换之前将绑定添加到XDP表单](http://www.adobe.com/go/learn_aemforms_designer_65_cn)。 当绑定在源XDP表单中可用时，该服务在转换期间自动将绑定应用于相应的自适应表单字段。 这样可节省手动应用绑定所需的时间。
* [将Adobe Sign标记](https://helpx.adobe.com/cn/sign/using/text-tag.html)添加到XDP文件。 该服务会自动将Adobe Sign标签转换为相应的自适应表单字段。 自适应Forms支持有限数量的Adobe Sign字段。 有关支持的字段的完整列表，请参阅[在自适应表单中使用Adobe Sign](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html?lang=zh-Hans)文档。
* 如果可能，将XDP文档中的复杂表转换为简单表。 如果表格单元格中有表单字段、大小不一的单元格、跨行或跨列单元格、合并的单元格、部分边框或没有可见边框，则这些表格被视为复杂表格。 具有上述任一项目的表被视为复杂表。
<!-- * Use sub-forms in XDP documents to create panels in adaptive forms. Service converts each sub-form to one or more adaptive form panels during conversion. -->

### 开始转换之前

* 创建自适应表单模板。 模板有助于为组织或部门的表单指定统一结构。
* 在自适应表单模板中指定页眉和页脚。 该服务忽略源文档的页眉 — 页脚，并使用在自适应表单模板中指定的页眉 — 页脚。
* 创建自适应表单主题。 主题有助于为组织或部门的各种形式提供统一的外观和风格。
* 配置表单数据模型以保存和检索数据源。 为表单数据模型创建和配置读写服务。
* 创建自适应表单片段并将服务配置为使用您的自适应表单片段。
* 为需要业务流程自动化的表单准备通用工作流模型。
* 配置Adobe Analytics（如果需要）


## 了解复杂模式

AEM [!DNL Forms Automated Conversion service]使用人工智能和机器学习算法来了解源表单的布局和字段。 每个机器学习服务都不断从源数据中学习，并在每次流失时产生改进的输出。 这些服务就像人类一样从经验中学习。

[!DNL Automated Forms Conversion service]已接受大量表单培训。 它可以轻松识别源表单中的字段并生成自适应表单。 然而，PDF forms中有些领域和风格是肉眼容易看到，但服务起来却很难理解的。 该服务可以为某些字段或样式分配与适用的字段类型或面板不同的类型。 下面列出了所有此类字段和样式模式。

当该服务不断从源数据中学习时，它将开始为这些模式标识和分配正确的字段或面板。 目前，您可以使用[查看和更正](review-correct-ui-edited.md)编辑器来修复此类问题。 在开始修复问题或进一步阅读之前，请熟悉[自适应表单组件](https://helpx.adobe.com/cn/experience-manager/6-5/forms/using/introduction-forms-authoring.html)。

### 常规模式 {#general}

| 图案 | 示例 |
|--- |--- |
| **模式** <br>服务未将已填充的PDF forms转换为自适应表单。 <br><br>**分辨率** <br>使用空的自适应表单。 | ![已填写表单](assets/best-practice-filled-forms.png) |
| **模式** <br>服务可能无法识别密集表单中的文本和字段。 <br><br>**分辨率** <br>在开始转换之前，增加密集表单文本和字段之间的宽度。 |  |
| **模式** <br>服务不支持扫描的表单。 <br><br>**分辨率** <br>不使用扫描的表单。 | ![扫描的表单](assets/scanned-forms.png) |
| **模式** <br>服务未提取图像中的图像和文本。 <br><br>**分辨率** <br>手动将图像或文本添加到转换后的表单。 | ![带文本表单的图像](assets/best-practice-image-with-text.png) |
| **图案** <br>带有点状或不清楚边界和边框的表格不转换。 <br><br>**分辨率** <br>使用具有明确边界和边框的表。 受支持。 | ![未清除表格表单](assets/best-practice-table-dotted-non-clear.png) |
| **模式** <br>自适应表单不支持开箱即用的垂直文本。 因此，该服务不会将垂直文本转换为相应的自适应Forms文本。 <br><br>**分辨率** <br>如果需要，请使用自适应表单编辑器添加垂直文本。 | ![未清除表格表单](assets/vertical-text.png) |



### 选择组  {#choice-group}

| 图案 | 解决方法 |
|--- |--- |
| **图案** <br>具有框或圆以外的形状的选择组选项未转换为相应的自适应表单组件。 <br><br>**分辨率** <br>将选择选项形状更改为方框或圆形，或者使用“审核并更正”编辑器来标识形状。 | ![选择字段](assets/best-practice-choice-group-options.png) |

### 表单字段 {#form-fields}

| 图案 | 解决方法 |
|--- |--- |
| **模式** <br>服务不识别没有明确边框的字段。 <br><br>**解决方法** <br>使用“审核并更正”编辑器标识此类字段。 | ![具有非清除边界的字段](assets/best-practice-fields-without-clear-borders.png) |
| **模式** <br>服务可能无法识别某些选择组表单字段，这些字段在表单的底部或右侧带有标题。 <br><br>**分辨率** <br>使用“审核并更正”编辑器标识此类字段 | ![选择字段](assets/best-practice-caption-bottom-right.png) |
| **模式** <br>服务合并或分配了错误类型给一些彼此非常接近或没有清晰边框的表单字段。 <br><br>**解决方法** <br>使用“审核并更正”编辑器标识此类字段。 | ![选择字段](assets/best-practice-placed-very-near.png) |
| **模式** <br>服务可能无法识别带有遥远字幕的字段或字幕与输入字段之间的虚线。 <br><br>**解决办法** <br>使用具有明确边界的表单字段或使用审阅和更正编辑器修复此类问题。 | ![标题字段之间的远距字段或虚线](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### 列表 {#lists}

| 图案 | 解决方法 |
|--- |--- |
| **模式** <br>包含表单字段的列表已合并或未转换为相应的自适应表单组件&#x200B;<br><br>**分辨率** <br>使用具有明确边界的表单字段或使用审阅和更正编辑器来修复此类问题。 | ![个包含选择组的列表](assets/best-practice-lists-containing-form-fields.png) |
| **模式** <br>服务可能会留下一些未识别的嵌套列表&#x200B;<br><br>**解决方案** <br>使用审阅和更正编辑器修复此类问题。 | ![个包含选择组的列表](assets/best-practice-nested-lists.png) |
| **模式** <br>服务将某些包含选择组的列表相互合并&#x200B;<br><br>**解决方案** <br>使用审阅和更正编辑器修复此类问题。 | ![个包含选择组的列表](assets/best-practice-check-box-in-table-cells.png) |

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
