---
title: automated forms conversion服务(AFCS)简介
description: 加速打印表单向自适应表单的转换
solution: Experience Manager Forms
feature: Adaptive Forms, Foundation Components
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
exl-id: edabeac8-cd66-48ca-a99f-9643a1c184cf
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 58%

---

# automated forms conversion服务(AFCS) {#introduction-to-automated-forms-conversion-service}

automated forms conversion服务(AFCS)通过将PDF forms自动转换为自适应表单，帮助加快数据捕获体验的数字化和现代化进程。 此服务由 Adobe Sensei 提供支持，可将您的 PDF 表单自动转换为设备友好、响应迅速且基于 HTML5 的自适应表单。 它可以充分利用现有 PDF 表单和 XFA 表单的投资，并可在表单转换期间将适当的验证、样式和布局应用于自适应表单的相应字段。 此服务有助于：

* 省去采用人工方式将打印表单转换为自适应表单时的繁琐过程
* 在转换期间自动应用相应模式和适当验证
* 在转换期间生成记录文件
* 将常见字段分组为可重用的表单片段
* 在转换期间启用 Adobe Analytics

![操作很简单。 您向我们提供源表单，其余一切交给我们。 我们为您提供美观的自适应表单。 您可以随时对输出内容进行修改，直至满意为止。](assets/pdf-to-adaptive-form-gitx50.gif)

## 入门培训 {#onboarding}

AEM 6.4 Forms和AEM 6.5 Forms本地部署客户和Adobe托管服务企业客户可免费使用此服务。 您可以联系Adobe销售团队或您的Adobe代表，请求访问服务。 AEM Formsas a Cloud Service客户还可以免费使用并预启用该服务。

Adobe 可为贵企业开启访问通道，并为您指定的管理员提供各种所需权限。 管理员可以向贵企业的 AEM Forms 开发人员（用户）授予权限并连接到该服务。 有关详细信息，请参见[“配置自动化表单转换服务”](configure-service.md)。

## 支持的PDF forms和语言 {#supported-languages-and-pdf-forms}

此服务支持非交互式 PDF 表单、由 Adobe Acrobat 创建的 AcroForms 表单、以及由 AEM Forms 或 Adobe LiveCycle 创建的 XFA 表单。

该服务还支持已启用Adobe Sign的PDF forms。 如果源 PDF 表单具有 Adobe Sign 文本标记，则该服务将在转换期间保留所有与 Adobe Sign 相关的信息，并将源 PDF 中的签名者信息与相应的自适应表单字段相关联。 该功能仅适用于 AcroForms。

该服务可将英语、法语、德语、西班牙语、意大利语和葡萄牙语表单转换为自适应表单。 您还可以使用[AEM翻译工作流](https://helpx.adobe.com/cn/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)将生成的自适应表单翻译成其他语言。

## 转化工作流  {#conversion-workflow}

automated forms conversion服务(AFCS)在Adobe云上运行。 您需要将 AEM 实例连接到服务，将表单上传到 AEM 实例，然后开始转换。 整个转换过程如下所示：

![工作流](assets/conversion-workflow.png)

### 1.设置环境 {#set-up-the-environment}

automated forms conversion服务(AFCS)在Adobe云上运行。 [配置贵企业的 Adobe I/O 帐户，然后将本地 AEM 实例](configure-service.md)连接到 Adobe Cloud 上运行的转换服务。

### 2.将PDF forms转换为自适应表单 {#use-the-conversion-service}

配置好 AEM 表单环境后，若要将 PDF 表单转换为自适应表单，先[将 PDF 表单](convert-existing-forms-to-adaptive-forms.md)上传到 AEM 实例，然后[开始转换](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)。 上传表单之前，请注意以下几点：

* 请勿上传受保护的表单。 该服务无法转换受密码保护和加密的表单。
* 除英语、法语、德语、西班牙语、意大利语和葡萄牙语外，请勿上传任何语言的扫描、彩色、已填充表单和表单。 此类表单不受支持。
* 请勿上传文件名中带空格的 PDF 表单。
* 请勿上传 [PDF 产品组合](https://helpx.adobe.com/cn/acrobat/using/overview-pdf-portfolios.html)。 该服务无法将PDFPortfolio转换为自适应表单。
* 对 PDF 表单进行修改，详情参见[“最佳实践和注意事项”](styles-and-pattern-considerations-and-best-practices.md)文章。
* 阅读[“已知问题”](known-issues.md)避免出现意外故障。

### 3.查看转换后的表单 {#review-converted-forms}

现实世界的表单可能在字段布局、命名或隐式建议方面有复杂的数据捕获要求，而基于AI/ML的检测逻辑可能无法准确捕获这些表单。 自动化转换完成后，您可使用[审阅和修正编辑器](review-correct-ui-edited.md)对转换后的表单进行审核并作必要更新，生成更符合要求的输出效果。 完成必要更改后，再次发送表单进行转换。

自动转换所花费的时间取决于多种因素，例如输入表单的大小、表单的复杂性、处理队列上的负荷等。 文件夹/文件上的状态指示器会定期向用户发送转换进度通知。 转换完成后，系统还会向配置的电子邮件地址发送通知。
