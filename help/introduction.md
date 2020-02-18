---
title: 简介
description: '加快将打印表单转换为自适应表单的速度 '
translation-type: tm+mt
source-git-commit: ef5789dabccc65dcf988b9424b435aa036017691

---


# 简介 {#introduction-to-automated-forms-conversion-service}

自动表单转换服务通过将PDF表单自动转换为自适应表单，帮助加快数据捕获体验的数字化和现代化。 此服务由Adobe Sensei提供支持，可自动将您的PDF表单转换为设备友好型、响应式和基于HTML5的自适应表单。 在利用PDF表单和XFA中的现有投资的同时，该服务在转换过程中还将适当的验证、样式和布局应用于自适应表单字段。 该服务有助于：

* 节省将打印表单转换为自适应表单所需的手动工作
* 在转换过程中应用模式和适当的验证
* 在转换过程中生成记录文档
* 将经常出现的字段分组到可重用的表单片段中
* 在转化过程中启用Adobe Analytics

![这很简单。 您只需提供源表单，并将所有内容留给我们。 我们将为您提供美观的自适应表单。 当然，你会对产出感到满意。 ](assets/pdf-to-adaptive-form-gitx50.gif)

## 入职 {#onboarding}

AEM 6.5 Forms内部部署定期客户和Adobe Managed service企业客户可免费使用该服务。 您可以联系Adobe销售团队或Adobe代表以请求访问该服务。

Adobe为您的组织启用了访问权限，并为您组织中指定为管理员的人员提供所需的权限。 管理员可以授予您单位的AEM Forms开发人员（用户）连接服务的访问权限。 有关详 [细信息，请参阅配置自动表单转换服务](configure-service.md) 。

## 支持的PDF表单和语言 {#supported-languages-and-pdf-forms}

该服务支持非交互式PDF表单、使用Adobe Acrobat创建的称为AcroForms的表单以及使用AEM Forms或Adobe LiveCycle创建的基于XFA的表单。

该服务只能将英语表单转换为自适应表单。 您可以使用 [AEM翻译工作流将生成的自适应表单翻译为其他语言](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)。

## 转换工作流 {#conversion-workflow}

自动表单转换服务在Adobe cloud上运行。 您将AEM实例连接到服务，将表单上传到AEM实例，然后开始转换。 完整的转化过程如下：

![工作流](assets/conversion-workflow.png)

### 1.设置环境 {#set-up-the-environment}

自动表单转换服务在Adobe cloud上运行。 [配置单位的Adobe I/O帐户，并将本地AEM实例连接到Adobe cloud上运行的转换服务](configure-service.md) 。

### 2.将PDF表单转换为自适应表单 {#use-the-conversion-service}

在配置AEM表单环境后，要将PDF表单转换为自适应表单，请将 [PDF表单上传到AEM实例](convert-existing-forms-to-adaptive-forms.md) ，然后 [开始转换](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)。 在上传表单之前，请考虑以下事项：

* 请勿上传受保护的表单。 该服务不会转换受密码保护和加密的表单。
* 请勿上传扫描的、彩色的、非英语的表单和填写的表单。 不支持此类表单。
* 请勿上传文件名中包含空格的PDF表单。
* 请勿上传 [PDF包](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)。 该服务不会将PDF包转换为自适应表单。
* 对PDF表单进行建议的更改，这些更改在最佳实践和 [注意事项文章中介绍](styles-and-pattern-considerations-and-best-practices.md) 。
* 阅读已知 [问题文章](known-issues.md) ，以避免陷入陷阱。

### 3.查看转换的表单 {#review-converted-forms}

真实表单在字段布局、命名或隐式建议方面可能具有复杂的数据捕获要求，而基于AI/ML的检测逻辑可能无法准确捕获这些要求。 自动转换完成后，您可以使用“ [Review and Correct”（审阅和更正）编辑器来审阅转换的表单](review-correct-ui-edited.md) ，并进行必要的更新并生成更接近所需体验的增强输出。 进行必要的更改后，再次发送表单以进行转换。

自动转换所花费的时间取决于各种因素，如输入表单的大小、表单的复杂性、对服务处理队列的贷款等。 通过文件夹／文件上的状态指示器定期向用户通知进度。 转换完成后，还会向配置的电子邮件地址发送电子邮件通知。
