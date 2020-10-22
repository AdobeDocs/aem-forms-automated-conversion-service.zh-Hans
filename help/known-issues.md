---
title: 已知问题
seo-title: 已知问题
description: forms自动化转化服务的已知问题和限制
seo-description: 在开始使用AEM FormsForms自动转化服务之前，请了解该服务的已知问题和限制
uuid: b1dc661b-ccd3-457f-acbb-4bd25db86e1e
topic-tags: introduction
discoiquuid: 9cd2363c-47a0-46e9-98cd-1fe088b9cd6e
translation-type: tm+mt
source-git-commit: 589eacfd6200f4336b7a4a7708e10f3dfe08406d
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 1%

---

# 已知问题和限制 {#known-issues-limitations}

在开始使用AEM FormsForms自动转化服务之前，请查看以下已知问题和限制：

## 已知问题 {#known-issues}

* 包含要转换的表单的文件夹总共不应超过15个表单和50页。 源文件夹的大小不应超过10 MB。 请勿在源文件夹中创建子文件夹。
* 某些表单对象在人眼中很容易看到，但 [难以识别服务对象](styles-and-pattern-considerations-and-best-practices.md)。 使用 [审阅和正确的编辑器](review-correct-ui-edited.md) ，识别和转换此类表单对象。
* 审阅和正确编辑器：

   * 没有撤消操作。 “保存”按钮将永久保存更改。
   * 不支持基于XFA的表单的可重复面板。
   * 如果使用“审阅并更正”编辑器修改表中的列表，则行宽不会自动调整，文本可能会溢出到表的下一行。
   * 该功 **[!UICONTROL Auto-detect multi-column layout from input forms]** 能不适用于“审阅”和“更正”编辑器和表单片段。
   * 使用“审阅”和“正确”编辑器创建的涂写签名无法加载已发布的自适应表单。


* 对于基于XFA的表单：
   * 不支持从基于XFA的表单提取片段。
   * 不支持XFA脚本。 例如，用于为下拉组件自动生成值的脚本。
   * 元模型不适用于选择组
   * 单个字符的选择组选项未标识
   * 当源文档是动态XFA(.XDP)，并且它以自 [适应形式定义XFA属性的行为](https://helpx.adobe.com/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr)，则源文档的存在属性将不被接受。 例如，源文档中的字段被标记为隐藏，脚本使字段可见，然后该字段在输出自适应表单中保持可见。

* 在使用“将输 **入的AcroForm用作生成的自适应表单的记录文档(DoR)** ”选项时，请考虑以下事项：

<table>
    <tr>
        <td>复合文本字段的绑定和数据丢失。 复合文本字段有多个文本框彼此对齐。 例如，在AcroForm中，信用卡号被拆分为多个文本框，每个文本框都有单独的绑定。 当AcroForm转换为自适应表单时，转换的自适应表单对于所有文本框都具有单个绑定。 作为一种解决方法，在将AcroForm转换为自适应表单之前，请修改AcroForm以使用单个文本框来接受信用卡号。</td>
        <td><img  src="assets/creditCard_Composite.png"/>                                                            </td>
    </tr>
    <tr>
        <td>组合日期字段的绑定和数据丢失。 组合日期字段由三个不同的字段组成。 例如，AcroForm中的出生日期字段被拆分为三个单独的字段。 自适应表单提供现成的日期选取器组件。 要在保留AcroForm绑定的同时使用自适应表单的日期选取器组件，请在将AcroForm转换为自适应表单之前，将AcroForm修改为使用单个日期字段。</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>如果复选框的大小大于随附的文本，则不会检测到复选框，并丢失AcroForm中的绑定。 修改AcroForm，使复选框的大小小于随附文本。</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>如果输入字段与相应的文本字段不对齐，则不检测输入字段。  </td>
        <td><img  src="assets/non-alingned-fields.png"/></td>
    </tr>
    <tr >
        <td>该服务将AcroForm的所有复选框转换为单独的选择组。 将创建单独的选择组以保留与AcroForm的绑定。 不要在自适应表单中合并选择组。 这将导致绑定丢失。 如果合并选择组，请再次转换表单以重新获得丢失的绑定。 </td>
        <td></td>
    </tr>
    <tr >
        <td>某些表的边框在自动生成的记录文档(DoR)中从页面扩展出来。 </td>
        <td></td>
    </tr>
</table>

## 限制 {#limitations}

* 不支持具有复杂动态布局的PDF forms、带虚线轮廓的字段或已填充字段。
* 图像中的图像和文本未被识别。 手动向转换的表单添加图像。
* 不支持图稿XDP文档。
* 不支持大于15页的PDF forms。
* 加密的、受密码保护的和受保护的文档不会进行转换。 运行转换前，请删除加密或密码。
* 不支持复杂表，如无边框表、嵌套表和具有占位符值的表。 转换后，使用自适应表单编辑器添加或修改复杂表。 仅支持带空字段、正确标题和清晰边界的简单表。
* 该服务仅将英语表单转换为自适应表单。 You can translate converted adaptive forms to another language using [AEM translation workflow](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html).
* AEM 6.4Forms不支持多列输入表单布局自动检测。
* 使用源PDF表单中的颜色编码的信息不会应用到自适应表单。
* 源PDF表单的颜色将转移到自适应表单主题。
* 彩色PDF forms被视为灰度表单，并相应地检测场。

