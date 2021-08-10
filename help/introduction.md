---
title: 简介
description: 加速打印表单向自适应表单的转换
exl-id: edabeac8-cd66-48ca-a99f-9643a1c184cf
source-git-commit: af05922f9eb76b7b0a30601824c6006fe555ea80
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 70%

---

# 简介 {#introduction-to-automated-forms-conversion-service}

自动化表单转换服务可将 PDF 表单自动转换为自适应表单，帮助加速数据捕获体验的数字化和现代化进程。 此服务由 Adobe Sensei 提供支持，可将您的 PDF 表单自动转换为设备友好、响应迅速且基于 HTML5 的自适应表单。 它可以充分利用现有 PDF 表单和 XFA 表单的投资，并可在表单转换期间将适当的验证、样式和布局应用于自适应表单的相应字段。 此服务有助于：

* 省去采用人工方式将打印表单转换为自适应表单时的繁琐过程
* 在转换期间自动应用相应模式和适当验证
* 在转换期间生成记录文件
* 将常见字段分组为可重用表单片段
* 在转换期间启用 Adobe Analytics

![操作很简单。 您为我们提供源表单，并将所有内容留给我们。 我们为您提供漂亮的自适应表单。 您始终可以对输出内容进行修改，直至满意为止。](assets/pdf-to-adaptive-form-gitx50.gif)

## 入门 {#onboarding}

AEM 6.4 Forms和AEM 6.5 Forms内部部署客户和Adobe管理服务企业客户可免费使用此服务。 欲访问服务，请联系 Adobe 销售团队或 Adobe 代表。此外，AEM Forms作为Cloud Service客户，还可免费使用并预启用该服务。

Adobe 可为贵企业开启访问通道，并为您指定的管理员提供各种所需权限。 管理员可以向贵企业的 AEM Forms 开发人员（用户）授予权限并连接到该服务。 有关详细信息，请参见[“配置自动化表单转换服务”](configure-service.md)。

## 支持的PDF forms和语言 {#supported-languages-and-pdf-forms}

此服务支持非交互式 PDF 表单、由 Adobe Acrobat 创建的 AcroForms 表单、以及由 AEM Forms 或 Adobe LiveCycle 创建的 XFA 表单。

该服务还支持启用Adobe Sign的PDF forms。 如果源 PDF 表单具有 Adobe Sign 文本标记，则该服务将在转换期间保留所有与 Adobe Sign 相关的信息，并将源 PDF 中的签名者信息与相应的自适应表单字段相关联。 该功能仅适用于 AcroForms。

该服务可将英语、法语、德语和西班牙语表单转换为自适应表单。 您还可以使用[AEM翻译工作流](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)将生成的自适应表单翻译成其他语言。

## 转换工作流  {#conversion-workflow}

自动化表单转换服务在 Adobe Cloud 上运行。 您需要将 AEM 实例连接到服务，将表单上传到 AEM 实例，然后开始转换。 整个转换过程如下所示：

![工作流](assets/conversion-workflow.png)

### 1. 搭建环境 {#set-up-the-environment}

自动化表单转换服务在 Adobe Cloud 上运行。 [配置贵企业的 Adobe I/O 帐户，然后将本地 AEM 实例](configure-service.md)连接到 Adobe Cloud 上运行的转换服务。

### 2. 将 PDF 表单转换为自适应表单 {#use-the-conversion-service}

配置好 AEM 表单环境后，若要将 PDF 表单转换为自适应表单，先[将 PDF 表单](convert-existing-forms-to-adaptive-forms.md)上传到 AEM 实例，然后[开始转换](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)。 上传表单之前，请注意以下几点：

* 请勿上传受保护的表单。 该服务无法转换受密码保护和加密的表单。
* 请勿以英语、法语、德语和西班牙语以外的任何语言上传扫描的、彩色的、已填充的表单和表单。 此类表单不受支持。
* 请勿上传文件名中带空格的 PDF 表单。
* 请勿上传 [PDF 产品组合](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)。 该服务无法将PDFPortfolio转换为自适应表单。
* 对 PDF 表单进行修改，详情参见[“最佳实践和注意事项”](styles-and-pattern-considerations-and-best-practices.md)文章。
* 阅读[“已知问题”](known-issues.md)避免出现意外故障。

### 3. 查看转换后的表单 {#review-converted-forms}

真实世界表单在字段布局、命名或隐式建议方面可能具有复杂的数据捕获要求，而基于AI/ML的检测逻辑可能无法准确捕获这些要求。 自动化转换完成后，您可使用[审阅和修正编辑器](review-correct-ui-edited.md)对转换后的表单进行审核并作必要更新，生成更符合要求的输出效果。 完成必要更改后，再次发送表单进行转换。

自动转换所花费的时间取决于各种因素，如输入表单的大小、表单的复杂性、服务处理队列的借出。 文件夹/文件上的状态指示器会定期向用户发送转换进度通知。 转换完成后，系统还会向配置的电子邮件地址发送通知。
