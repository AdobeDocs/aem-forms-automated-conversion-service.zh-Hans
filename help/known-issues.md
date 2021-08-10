---
title: 已知问题
seo-title: 已知问题
description: automated forms conversion服务的已知问题和限制
seo-description: 在开始使用AEM FormsAutomated forms conversion服务之前，请了解该服务的已知问题和限制
uuid: b1dc661b-ccd3-457f-acbb-4bd25db86e1e
topic-tags: introduction
discoiquuid: 9cd2363c-47a0-46e9-98cd-1fe088b9cd6e
exl-id: 35f59e02-e38e-473a-94c8-123e0a85ac8e
source-git-commit: af05922f9eb76b7b0a30601824c6006fe555ea80
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 1%

---

# 已知问题和限制 {#known-issues-limitations}

在开始使用AEM FormsAutomated forms conversion服务之前，请查看以下已知问题和限制：

## 已知问题 {#known-issues}

* 包含表单进行转换的文件夹，其表单总数不应超过15个，页面应不超过50个。 源文件夹的大小不应超过10 MB。 请勿在源文件夹中创建子文件夹。
* 某些形式的对象在人眼中很容易看到，但是[难以识别服务](styles-and-pattern-considerations-and-best-practices.md)。 使用[Review and recort editor](review-correct-ui-edited.md)标识和转换此类表单对象。
* 审阅和更正编辑器：

   * 没有撤消操作。 保存按钮可永久保存更改。
   * 不支持基于XFA的表单的可重复面板。
   * 如果使用“审阅并修正”编辑器修改表中的列表，则行宽不会自动调整，文本可能会溢出到表的下一行。
   * **[!UICONTROL Auto-detect multi-column layout from input forms]**&#x200B;功能不适用于审阅和更正编辑器及表单片段。
   * 为已发布的自适应表单加载使用审阅和更正编辑器创建的涂写签名失败。


* 对于基于XFA的表单：
   * 不支持从基于XFA的表单中提取片段。
   * 不支持XFA脚本。 例如，用于为下拉组件自动生成值的脚本。
   * 元模型不适用于选择组
   * 单个字符的“选择组”选项未被识别
   * 如果源文档是动态XFA(.XDP)，并且[定义自适应表单](https://helpx.adobe.com/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr)中XFA属性的行为，则源文档的存在属性将不受支持。 例如，源文档中的字段被标记为隐藏，并且脚本使该字段可见，然后该字段在输出自适应表单中保持可见。

* 对生成的自适应表单&#x200B;**使用**&#x200B;使用输入AcroForm作为记录文档(DoR)选项时，请考虑以下事项：

<table>
    <tr>
        <td>复合文本字段的绑定和数据将丢失。 复合文本字段具有多个彼此对齐的文本框。 例如，在AcroForm中，信用卡号被拆分为多个文本框，每个文本框都有单独的绑定。 当AcroForm转换为自适应表单时，转换后的自适应表单对所有文本框都有一个绑定。 作为解决方法，在将AcroForm转换为自适应表单之前，请修改AcroForm以使用单个文本框来接受信用卡号。</td>
        <td><img  src="assets/creditCard_Composite.png"/>                                                            </td>
    </tr>
    <tr>
        <td>复合日期字段的绑定和数据将丢失。 复合日期字段由三个不同的字段组成。 例如，AcroForm中的出生日期字段被拆分为三个单独的字段。 自适应表单提供了一个现成的日期选取器组件。 要在保留AcroForm绑定的同时使用自适应表单的日期选取器组件，请在将AcroForm转换为自适应表单之前，修改AcroForm以使用单个日期字段。</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>如果复选框的大小大于随附文本，则不会检测到复选框，并且AcroForm中的绑定将丢失。 修改AcroForm以使复选框的大小小于随附文本。</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>如果输入字段与相应的文本字段不对齐，则不会检测输入字段。  </td>
        <td><img  src="assets/non-alingned-fields.png"/></td>
    </tr>
    <tr >
        <td>该服务将AcroForm的所有复选框转换为单独的选择组。 将创建单独的选择组以保留与AcroForm的绑定。 请勿在自适应表单中合并选择组。 这会导致绑定丢失。 如果合并选择组，请再次转换表单以重新获得丢失的绑定。 </td>
        <td></td>
    </tr>
    <tr >
        <td>某些表格的边界在自动生成的记录文档(DoR)中从页面外扩展。 </td>
        <td></td>
    </tr>
</table>

## 限制 {#limitations}

* 不支持具有复杂动态布局的PDF forms、具有虚线轮廓的字段或已填充的字段。
* 图像内的图像和文本未被识别。 手动将图像添加到已转换的表单。
* 不支持图稿XDP文档。
* 不支持大于15页的PDF forms。
* 加密的、受密码保护的和安全的文档不会进行转换。 在运行转换之前，请删除加密或密码。
* 不支持诸如无边距表、嵌套表和具有占位符值的表之类的复杂表。 转换后，使用自适应表单编辑器添加或修改复杂表。 仅支持具有空字段、正确标题和清除边界的简单表。
* 该服务仅将英语、法语、德语和西班牙语表单转换为自适应表单。 您可以使用[AEM翻译工作流](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)将转换后的自适应表单翻译成其他语言。
* AEM 6.4 Forms不支持自动检测输入表单的多列布局。
* 使用源PDF表单中的颜色编码的信息不会传递到自适应表单。
* 源PDF表单的颜色不会传递到自适应表单主题。
* 彩色PDF forms被视为灰度形式，并相应地检测字段。
