---
title: '自动表单转换服务疑难解答 '
seo-title: '自动表单转换服务(AFCS)疑难解答 '
description: '常见AFCS问题及其解决方案 '
seo-description: 常见AFCS问题及其解决方案
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 4b9f3f4fe3b3901cb99c9374ff40e8f49855237f

---


# 自动表单转换服务疑难解答


本文提供有关自动表单转换服务生产环境中可能出现的安装、配置和管理问题的信息。 本文档还提供常见错误消息的基本疑难解答步骤和说明。

## 常见错误 {#commonerrors}

| 错误 | 示例 |
|--- |--- |
| **错误消息**<br> :访问令牌标题不可用。 <br><br>**原因&#x200B;**<br>管理员已创建多个IMS配置，或者IMS配置无法在Adobe Cloud上访问AFCS服务。<br><br>**分辨率** 如果有多个配置，请删除所有配置并 <br> 创建新配置 [](configure-service.md#obtainpubliccertificates)。 <br> 如果有单一配置，请使 **[!UICONTROL Health Check]** 用检 [查连接](configure-service.md#createintegrationoption)。 | ![访问令牌标题不可用](assets/invalid-ims-configuration.png) |
| **错误消息**<br> ：无法连接到服务。  <br><br>**原因&#x200B;**<br>Automated Forms Conversion Service Cloud服务中提及错误的服务URL或没有服务URL。<br><br>**解析**<br> Automated Forms [](configure-service.md#configure-the-cloud-service) Conversion Service Cloud服务中的正确服务URL。 | ![无法连接到服务。](assets/wrong-endpoint-configured.png) |
| **错误消息**<br> ：服务无法转换表单。  <br><br>**原因&#x200B;**<br>：由于Adobe Cloud上的定期维护或中断，您的终端或服务中断时出现网络连接问题。<br><br>**解决**<br> ：解决您最终的网络连接问题，并检查https://status.adobe.com/上服务的状态，以确定计划内或计划外停机。 | ![无法连接到服务。](assets/service-failure.png) |
| **错误消息**<br> ，页数大于15。  <br><br>**原因&#x200B;**<br>包含源XDP和PDF表单的文件夹包含15个以上的文件。<br><br>**解决方**<br> 案将文件夹中的表单数量设为小于或等于15。 将页面总数置于小于50的文件夹中。 将文件夹大小调整为小于10 MB。 请勿将表单保留在子文件夹中。 将源文档组织到一组8-15文档中。 | ![无法连接到服务。](assets/number-of-pages.png) |
| **错误消息** : <br> 不支持源文件格式。  <br><br>**原因&#x200B;**<br>包含源表单的文件夹包含一些不支持的文件。<br><br>**分辨率**<br> 此服务仅支持。xdp和。pdf文件。 从文件夹中删除具有任何其他扩展名的文件并运行转换。 | ![无法连接到服务。](assets/unsupported-file-formats.png) |
| **不支持错误消息**<br> ：扫描的表单。  <br><br>**原因&#x200B;**<br>PDF表单仅包含表单的扫描图像且不包含内容结构。<br><br>**分辨率**<br> 该服务不支持将扫描的表单或表单的图像转换为自适应的现成功能。 但是，您使用Adobe Acrobat将表单的图像转换为PDF表单。 然后，使用该服务将PDF表单转换为自适应表单。 在Acrobat中始终使用表单的高质量图像进行转换。 它提高了转换质量。 | ![无法连接到服务。](assets/scanned-forms-error.png) |