---
title: 已知问题
description: automated forms conversion服务(AFCS)的已知问题和限制
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: introduction
role: Admin, Developer
level: Beginner, Intermediate
exl-id: 35f59e02-e38e-473a-94c8-123e0a85ac8e
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 1%

---

# 已知问题和限制 {#known-issues-limitations}

在开始使用AEM FormsAutomated forms conversion服务(AFCS)之前，请查看以下已知问题和限制：

## 已知问题 {#known-issues}

* 包含待转换表单的文件夹中的表单不应超过15个，并且总页数不应超过50页。 源文件夹的大小不应超过10 MB。 不要在源文件夹中创建子文件夹。
* 某些形式的对象易于人眼看到，但 [服务难以识别](styles-and-pattern-considerations-and-best-practices.md). 使用 [查看并更正编辑器](review-correct-ui-edited.md) 标识和转换此类表单对象。
* 查看并更正编辑器：

   * 没有撤消操作。 “保存”按钮将永久保存更改。
   * 不支持基于XFA表单的可重复面板。
   * 如果使用“审阅并更正”编辑器修改表格中的列表，则行宽不会自动调整，并且文本可能会溢出到表格的下一行。
   * 此 **[!UICONTROL Auto-detect multi-column layout from input forms]** 功能不适用于审阅和更正编辑器和表单片段。
   * 无法为发布的自适应表单加载使用审阅和更正编辑器创建的涂写签名。


* 对于基于XFA的表单：
   * 不支持从基于XFA的表单中提取片段。
   * 不支持XFA脚本。 例如，用于为下拉组件自动生成值的脚本。
   * 元模型不适用于选择组
   * 带有单个字符的“选择组”选项无法识别
   * 当源文档是动态XFA (.XDP)并且它是 [在自适应表单中定义XFA属性的行为](https://helpx.adobe.com/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr)，则不遵循源文档的presence属性。 例如，源文档中的某个字段被标记为隐藏，并且脚本使该字段可见，则该字段在输出自适应表单中保持可见。

* 当您使用 **将输入AcroForm用作所生成自适应表单的记录文档(DoR)** 选项，请考虑以下事项：

<table>
    <tr>
        <td>复合文本字段的绑定和数据将丢失。 复合文本字段有多个文本框相互对齐。 例如，在AcroForm中，一个信用卡号被拆分为多个文本框，每个文本框都有一个单独的绑定。 将AcroForm转换为自适应表单时，转换后的自适应表单对所有文本框仅有一个绑定。 作为解决方法，在将AcroForm转换为自适应表单之前，请修改AcroForm以使用单个文本框来接受信用卡号码。</td>
        <td><img  src="assets/creditCard_Composite.png"/>                                                            </td>
    </tr>
    <tr>
        <td>复合日期字段的绑定和数据丢失。 复合日期字段由三个不同的字段组成。 例如，AcroForm中的出生日期字段被拆分为三个单独的字段。 自适应表单提供现成的日期选取器组件。 要使用自适应表单的日期选取器组件同时保留AcroForm的绑定，请在将AcroForm转换为自适应表单之前，修改AcroForm以使用单个日期字段。</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>如果复选框的大小大于随附文本，则不会检测到复选框，并且AcroForm中的绑定将丢失。 修改AcroForm以使复选框的大小小于随附的文本。</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>如果输入字段未与相应的文本字段对齐，则不会检测到输入字段。  </td>
        <td><img  src="assets/non-alingned-fields.png"/></td>
    </tr>
    <tr >
        <td>该服务将AcroForm的所有复选框转换为单独的选择组。 将创建单独的选择组以保留与AcroForm的绑定。 请勿在自适应表单中合并选择组。 这会导致绑定丢失。 如果合并选择组，请再次转换表单以重新获得丢失的绑定。 </td>
        <td></td>
    </tr>
    <tr >
        <td>某些表的边界在自动生成的记录文档(DoR)中扩展出页面。 </td>
        <td></td>
    </tr>
</table>

## 限制 {#limitations}

* 不支持具有复杂动态布局、具有虚线轮廓或填充字段的PDF forms。
* 未识别图像内的图像和文本。 手动将图像添加到转换后的表单。
* 不支持图稿XDP文档。
* 不支持大于15页的PDF forms。
* 加密的、受密码保护的安全文档不会转换。 在运行转换之前删除加密或密码。
* 不支持诸如无边框表、嵌套表和带有占位符值的表等复杂表。 在转换之后，使用自适应表单编辑器添加或修改复杂表。 仅支持具有空字段、适当标题和清除边界的简单表。
* 此服务仅将英语、法语、德语、西班牙语、意大利语和葡萄牙语表单转换为自适应表单。 您可以使用将转换后的自适应表单翻译为其他语言 [AEM翻译工作流](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html).
* AEM 6.4 Forms不支持自动检测输入表单的多列布局。
* 使用源PDF表单中的颜色编码的信息不会传递到自适应表单中。
* 源PDF表单的颜色不会传递到自适应表单主题中。
* 将彩色PDF forms作为灰度形式处理，并相应地检测场。
