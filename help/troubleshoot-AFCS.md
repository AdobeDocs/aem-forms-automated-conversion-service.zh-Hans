---
title: '自动表单转换服务疑难解答 '
seo-title: '自动表单转换服务(AFCS)疑难解答 '
description: '常见AFCS问题及其解决方案 '
seo-description: 常见AFCS问题及其解决方案
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 65dd07048b3cc7d9434568a8188dc08a1db66ada

---


# 自动表单转换服务疑难解答


本文提供有关自动表单转换服务生产环境中可能出现的安装、配置和管理问题的信息。 本文档还提供常见错误消息的基本疑难解答步骤和说明。

## 常见错误 {#commonerrors}

| 错误 | 示例 |
|--- |--- |
| **错误消息**<br> :访问令牌标题不可用。 <br><br>**原因&#x200B;**<br>管理员已创建多个IMS配置，或者IMS配置无法在Adobe Cloud上访问AFCS服务。<br><br>**分辨率** 如果有多个配置，请删除所有配置并 <br> 创建新配置 [](configure-service.md#obtainpubliccertificates)。 <br> 如果有单一配置，请使 **[!UICONTROL Health Check]** 用检 [查连接](configure-service.md#createintegrationoption)。 | ![彩色表单](assets/invalid-ims-configuration.png) |
| **错误消息**<br> ：无法连接到服务。  <br><br>**原因&#x200B;**<br>Automated Forms Conversion Service Cloud服务中提及错误的服务URL或没有服务URL。<br><br>**解析**<br> Automated Forms [](configure-service.md#configure-the-cloud-service) Conversion Service Cloud服务中的正确服务URL。 | ![彩色表单](assets/wrong-endpoint-configured.png) |
