---
title: '最佳实践和注意事项 '
description: 不发布
seo-description: 不发布
page-status-flag: never-activated
uuid: c2821264-39e2-44f8-b234-835c46f33fd5
topic-tags: introduction
discoiquuid: b786e40a-202e-4e17-a2f5-1f77c46538c2
privatebeta: true
index: false
source-git-commit: b2d29c22a275f2dc6a82593cf5e441c8da0bba13
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 4%

---


# 最佳实践和注意事项 {#do-not-publish-best-practices-and-considerations}

<!--
[DO NOT PUBLISH]
-->

AEM Forms自动转换服务将PDF表单转换为自适应表单。 该服务使用人工智能和机器学习算法来了解源表单的布局和领域。 每项机器学习服务都会不断学习源数据，并在每次流失时产生改进的输出。 这些服务从人类的体验中学习。

automated forms conversion服务是在大量表单上进行培训的。 它可轻松识别源表单中的字段并生成自适应表单。 但是，PDF forms中有一些字段和样式很容易被人们看到，但很难理解这些字段和样式。 该服务可以为某些字段或样式分配与适用字段类型或面板不同的内容。 下面列出了所有此类字段和样式模式。

该服务将开始识别并为这些模式分配正确的字段或面板，因为它会不断从源数据中学习。 目前，您可以使用[Review and Crect](review-correct-ui-edited.md)编辑器来修复此类问题。 在开始修复问题或进一步阅读之前，请熟悉[自适应表单组件](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)。

## 常规 {#general}

<table border="1" cellpadding="1" cellspacing="0" style="border-collapse: separate; border-spacing: 0px;" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">已知模式和分辨率</td> 
   <td width="70%">示例</td> 
  </tr>
   <td><p><strong>图案</strong></p> <p>服务不会将已填充的PDF forms转换为自适应表单。</p> <p> </p> <p><strong>分辨率</strong></p> <p>使用空的自适应表单。</p> </td> 
   <td style="text-align: left;"><img src="assets/pre-filled-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>图案</strong></p> <p>服务无法识别密集形式的文本和字段。</p> <p> </p> <p><strong>分辨率</strong></p> <p>在开始转换之前，增加密集表单的文本和字段之间的宽度。</p> </td> 
   <td style="text-align: left;"><img src="assets/dense%20form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>图案</strong></p> <p>服务不支持扫描的表单。</p> <p> </p> <p><strong>分辨率</strong></p> <p>请勿使用扫描的表单。 </p> </td> 
   <td><img src="assets/scanned-form.jpg" /></td> 
  </tr>
  <tr>
   <td><p><strong>图案</strong></p> <p>服务不会提取图像和图像内的文本。 </p> <p> </p> <p><strong>分辨率</strong></p> <p>手动向转换的表单添加图像或文本。</p> </td> 
   <td><img src="assets/image-in-adaptive-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>图案</strong></p> <p>具有点线或非清除边界和边框的表将不会转换。</p> <p><strong>分辨率</strong></p> <p>使用具有清晰明确边界和边界的表。 受支持。</p> </td> 
   <td><img src="assets/border-less-tables.png" /></td> 
  </tr>
 </tbody>
</table>

## 选择组{#choice-group}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">图案</td> 
   <td width="70%">示例</td> 
  </tr>
  <tr>
   <td><p><strong>图案</strong></p> <p>除框或圆以外形状的选择组选项不会转换为相应的自适应表单组件。 </p> <p> </p> <p><strong>分辨率</strong></p> <p>将选择选项形状更改为框或圆，或使用“审阅并更正”编辑器来识别形状。</p> </td> 
   <td><img src="assets/shaded-box-patterns.png" /> </td> 
  </tr>
 </tbody>
</table>

## 表单字段{#form-fields}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">图案</td> 
   <td width="70%">示例</td> 
  </tr>
  <tr>
   <td width="25%"><p><strong>图案</strong></p> <p>服务不会识别没有明确边框的字段。</p> <p> </p> <p><strong>分辨率</strong></p> <p>使用审阅和更正编辑器来标识此类字段。</p> <p> </p> <p> </p> </td> 
   <td width="50%"><br /> <img src="assets/fields-without-clear-borders.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>图案</strong></p> <p>服务会在某些表单字段的底部或右侧留下未识别字幕的字段。</p> <p> </p> <p><strong>分辨率</strong></p> <p>使用审阅和更正编辑器来标识此类字段</p> </td> 
   <td><br /> <img src="assets/forms-with-clear-borders-scale.png" /><br /> </td> 
  </tr>
  <tr>
   <td><p><strong>图案</strong></p> <p>服务会合并或为某些表单字段分配错误类型，这些字段彼此非常接近或没有清晰的边框。 </p> <p> </p> <p><strong>分辨率</strong></p> <p>使用审阅和更正编辑器来标识此类字段。</p> </td> 
   <td><img src="assets/forms-with-fields-placed-nearby.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>图案</strong></p> <p>服务无法识别带有远距离字幕的字段或字幕与输入字段之间的虚线。</p> <p> </p> <p><strong>分辨率</strong></p> <p>使用边界清晰的表单字段，或使用“审阅并更正”编辑器来修复此类问题。</p> </td> 
   <td><img src="assets/form-fields-with-far-away-captions.png" /></td> 
  </tr>
 </tbody>
</table>

## 列表 {#lists}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">图案</td> 
   <td width="70%">示例</td> 
  </tr>
  <tr>
   <td><p><strong>图案</strong></p> <p>包含表单字段的列表会被合并或不会转换为相应的自适应表单组件</p> <p><strong>分辨率</strong></p> <p>使用边界清晰的表单字段，或使用“审阅并更正”编辑器来修复此类问题。</p> </td> 
   <td><img src="assets/lists-with-fields.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>图案</strong></p> <p>服务可能会将一些嵌套列表保留为未识别状态</p> <p> </p> <p><strong>分辨率</strong></p> <p>使用“审阅”和“更正”编辑器来修复此类问题。</p> </td> 
   <td><img src="assets/nested-lists.png" /> </td> 
  </tr>
  <tr>
   <td><p><strong>图案</strong></p> <p>服务会合并一些包含选择组的列表</p> <p><strong>分辨率</strong></p> <p>使用“审阅”和“更正”编辑器来修复此类问题。</p> </td> 
   <td><img src="assets/lists-containing-choice-groups.png" /> </td> 
  </tr>
 </tbody>
</table>

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fiields without bordes are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->

