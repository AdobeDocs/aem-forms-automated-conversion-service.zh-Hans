---
title: 简介
description: 加速打印表单向自适应表单的转换
exl-id: edabeac8-cd66-48ca-a99f-9643a1c184cf
source-git-commit: 47261710e6616c27c210ac53bffcc2387a06ea7a
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 70%

---

# 简介 {#introduction-to-automated-forms-conversion-service}

自动化表单转换服务可将 PDF 表单自动转换为自适应表单，帮助加速数据捕获体验的数字化和现代化进程。 此服务由 Adobe Sensei 提供支持，可将您的 PDF 表单自动转换为设备友好、响应迅速且基于 HTML5 的自适应表单。 它可以充分利用现有 PDF 表单和 XFA 表单的投资，并可在表单转换期间将适当的验证、样式和布局应用于自适应表单的相应字段。 此服务有助于：

* 省去采用人工方式将打印表单转换为自适应表单时的繁琐过程
* 在转换期间自动应用相应模式和适当验证
* 在转换期间生成记录文件
* 將常見欄位分組為可重複使用的表單片段
* 在转换期间启用 Adobe Analytics

![操作很简单。 您提供來源表單，其餘一切交給我們。 我們為您提供美觀的最適化表單。 您可以隨時修改成果以致完美。 ](assets/pdf-to-adaptive-form-gitx50.gif)

## 入门培训 {#onboarding}

AEM 6.4 Forms和AEM 6.5 Forms內部部署定期客戶和Adobe管理服務企業客戶可免費使用該服務。 欲访问服务，请联系 Adobe 销售团队或 Adobe 代表。AEM Formsas a Cloud Service客戶也可以免費使用此服務並預先啟用該服務。

Adobe 可为贵企业开启访问通道，并为您指定的管理员提供各种所需权限。 管理员可以向贵企业的 AEM Forms 开发人员（用户）授予权限并连接到该服务。 有关详细信息，请参见[“配置自动化表单转换服务”](configure-service.md)。

## 支援的PDF forms和語言 {#supported-languages-and-pdf-forms}

此服务支持非交互式 PDF 表单、由 Adobe Acrobat 创建的 AcroForms 表单、以及由 AEM Forms 或 Adobe LiveCycle 创建的 XFA 表单。

此服務也支援啟用Adobe Sign的PDF forms。 如果源 PDF 表单具有 Adobe Sign 文本标记，则该服务将在转换期间保留所有与 Adobe Sign 相关的信息，并将源 PDF 中的签名者信息与相应的自适应表单字段相关联。 该功能仅适用于 AcroForms。

此服務可將英文、法文、德文、西班牙文、義大利文和葡萄牙文的表單轉換為最適化表單。 您也可以使用將產生的調適型表單翻譯成其他語言 [AEM翻譯工作流程](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html).

## 转换工作流  {#conversion-workflow}

自动化表单转换服务在 Adobe Cloud 上运行。 您需要将 AEM 实例连接到服务，将表单上传到 AEM 实例，然后开始转换。 整个转换过程如下所示：

![工作流](assets/conversion-workflow.png)

### 1. 搭建环境 {#set-up-the-environment}

自动化表单转换服务在 Adobe Cloud 上运行。 [配置贵企业的 Adobe I/O 帐户，然后将本地 AEM 实例](configure-service.md)连接到 Adobe Cloud 上运行的转换服务。

### 2. 将 PDF 表单转换为自适应表单 {#use-the-conversion-service}

配置好 AEM 表单环境后，若要将 PDF 表单转换为自适应表单，先[将 PDF 表单](convert-existing-forms-to-adaptive-forms.md)上传到 AEM 实例，然后[开始转换](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)。 上传表单之前，请注意以下几点：

* 请勿上传受保护的表单。 该服务无法转换受密码保护和加密的表单。
* 請勿上傳英文、法文、德文、西班牙文、義大利文和葡萄牙文以外任何語言的掃描、彩色、填寫的表單和表單。 此类表单不受支持。
* 请勿上传文件名中带空格的 PDF 表单。
* 请勿上传 [PDF 产品组合](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)。 此服務無法將PDFPortfolio轉換為最適化表單。
* 对 PDF 表单进行修改，详情参见[“最佳实践和注意事项”](styles-and-pattern-considerations-and-best-practices.md)文章。
* 阅读[“已知问题”](known-issues.md)避免出现意外故障。

### 3. 查看转换后的表单 {#review-converted-forms}

現實世界的表單在欄位配置、命名或隱含建議方面可能具有複雜的資料擷取需求，而基於AI/ML的檢測邏輯可能無法準確擷取這些表單。 自动化转换完成后，您可使用[审阅和修正编辑器](review-correct-ui-edited.md)对转换后的表单进行审核并作必要更新，生成更符合要求的输出效果。 完成必要更改后，再次发送表单进行转换。

自動轉換所需的時間取決於多種因素，例如輸入表單的大小、表單的複雜性，以及服務的處理佇列上所缺的時間。 文件夹/文件上的状态指示器会定期向用户发送转换进度通知。 转换完成后，系统还会向配置的电子邮件地址发送通知。
