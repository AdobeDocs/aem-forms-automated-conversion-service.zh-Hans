---
title: 自动化表单转换服务 (AFCS) 故障诊断
description: AFCS 常见问题及解决办法
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
contentOwner: khsingh
exl-id: e8406ed9-37f5-4f26-be97-ad042f9ca57c
TQID: https://experienceleague.adobe.com/CYDvLiZX-BqErF-cKQX1SieVDMxkoD1kfP4rLIT9ku0
product_v2:
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: d49d6117-dd89-469c-a774-cc96b7eee433
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: ce44533e-8ec8-4e11-a9e9-78b0fe561832
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 0be767cc3d09331ea7a61c114a11bb0354b5f4ad
workflow-type: tm+mt
source-wordcount: 689
ht-degree: 79%

---

# 自动化表单转换服务 (AFCS) 故障诊断

本文档提供常见错误的基本故障诊断步骤。

<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. -->

## 常见错误 {#commonerrors}

| 错误 | 示例 |
|--- |--- |
| **错误消息** <br>访问令牌标头不可用。<br><br> **原因** <br>管理员创建了多个 IMS 配置，或 IMS 配置无法在 Adobe Cloud 上连接 AFCS 服务。 <br><br>**分辨率** <br>如果有多个配置，请删除所有配置并[创建新的配置](configure-service.md#obtainpubliccertificates)。<br> 如果只有一个配置，请使用&#x200B;**运行状况检查**&#x200B;到[检查连接](configure-service.md#createintegrationoption)。 | ![访问令牌标头不可用](assets/invalid-ims-configurations.png) |
| **错误消息** <br>无法连接到服务。  <br><br>**原因** <br>服务URL不正确或自动表单转换服务(AFCS)云服务中没有提及服务URL。 <br><br>**解决办法** <br>在自动表单转换服务(AFCS)云服务中更正[服务URL](configure-service.md#configure-the-cloud-service)。 | ![无法连接到服务。](assets/wrong-service-url-configured.png) |
| **错误消息** <br>服务无法转换表单。  <br><br>**原因** <br>您的网络连接有问题、服务因定期维护停止或 Adobe Cloud 中断。 <br><br>**解决办法** <br>解决您的网络连接问题，并在 https://status.adobe.com/zh-cn/ 上检查服务状态，确定是否有计划的或意外的中断。 | ![无法连接到服务。](assets/conversion-failure.png) |
| **错误消息** <br>页面超过 15 页。  <br><br>**原因** <br>源表单超过 15 页。  <br><br>**解决办法** <br>使用 Adobe Acrobat 对超过 15 页的表单进行拆分。 将表单缩减到 15 页以下。 | ![无法连接到服务。](assets/number-of-pages.png) |
| **错误消息** <br>文件数超过 15 个。  <br><br>**原因** <br>  本文件夹包含的表单超过 15 个。 <br><br>**解决办法** <br>将文件夹中的表单数量缩减到 15 个或 15 个以下。 将文件夹中的总页数缩减到 50 页以下。 将文件夹的大小缩减到 10 MB 以下。 请勿将表单放在子文件夹中。 以 8 到 15 个表单为一个批次整理表单。 | ![无法连接到服务。](assets/number-of-pages.png) |
| **错误消息** <br>不支持源文件格式。  <br><br>**原因** <br>源表格所在的文件夹中存在一些不支持的文件。 <br><br>**解决办法** <br>本服务仅支持 .xdp 和 .pdf 文件。 从文件夹中删除任何其他扩展名的文件，然后运行转换。 | ![无法连接到服务。](assets/unsupported-file-formats.png) |
| **错误消息** <br>扫描的表单不受支持。  <br><br>**原因** <br>PDF 表单仅包含表单的扫描图像，不包含内容结构。 <br><br>**解决办法** <br>本服务不支持直接将扫描的表单或表单图像转换为自适应表单。 但您可以使用 Adobe Acrobat 将表单图像转换为 PDF 表单。 然后再使用本服务将 PDF 表单转换为自适应表单。 对于 Acrobat，请务必使用高质量的表单图像进行转换。 这样可以提高转换质量。 | ![无法连接到服务。](assets/scanned-forms-error.png) |
| **错误消息** <br>加密的 PDF 表单不受支持。  <br><br>**原因** <br>文件夹包含加密的 PDF 表单。 <br><br>**解决办法** <br>本服务不支持将加密的 PDF 表单转换为自适应表单。 删除加密，上传未加密表单，然后运行转换。 | ![无法连接到服务。](assets/secured-pdf-form.png) |
| **错误消息** <br>无法解析元模型 JSON 架构。  <br><br>**原因** <br>提供给本服务的 JSON 架构格式不正确，其中包含无效字符或用于映射组件的语法无效。  <br><br>**解决办法** <br>检查 JSON 文件格式。 可使用任何在线 JSON 验证器来检查架构格式和结构。 请参阅[“扩展默认的元模型”](extending-the-default-meta-model.md)一文，了解有关元模型语法的信息。 | ![无法连接到服务。](assets/invalid-meta-model-schema.png) |
| **错误（仅限内部部署环境）** <br> **[!UICONTROL Source Language]**&#x200B;选项未列出自适应表单的正确语言。 <br><br>**原因** <br>自适应表单的jcr:language属性设置不正确。  <br><br>**分辨率** <br>打开CRX-DE LITE，导航到`/content/forms/af/`，打开`jcr:content`节点，并将节点的值设置为正确的语言。 有关支持的语言的列表，请参阅[添加对不受支持的区域设置的本地化支持](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/supporting-new-language-localization.html?lang=zh-Hans#add-localization-support-for-non-supported-locales)。 | ![无法连接到服务。](assets/aem-forms-translation-project-language-unavailable.png) |

<!--

<table>
<thead>
<tr>
<th>Error</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Error Message</strong> <p> The access token header is not available. </p><br><strong>Reason</strong> <br> An administrator has created multiple IMS configurations or IMS configuration is not able to reach AFCS service on Adobe Cloud. <br><br><strong>Resolution</strong> <br> If there are multiple configurations, delete all the configurations and <a href="configure-service.md#obtainpubliccertificates">create a new configuration</a>. <br> If there is a single configuration, use <strong> Health Check </strong> to <a href="configure-service.md#createintegrationoption">check connectivity</a>.</td>
<td><img alt="The access token header is not available" src="assets/invalid-ims-configuration.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Unable to connect to the service.  <br><br><strong>Reason</strong> <br> Incorrect service URL or no service URL is mentioned in Automated Forms Conversion Service (AFCS) cloud services. <br><br><strong>Resolution</strong> <br> Correct <a href="configure-service.md#configure-the-cloud-service">Service URL</a> in Automated Forms Conversion Service (AFCS) Cloud services.</td>
<td><img alt="Unable to connect to the service." src="assets/wrong-endpoint-configured.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The service failed to convert the form.  <br><br><strong>Reason</strong> <br> Network connectivity issues at your end, the service is down due to scheduled maintenance, or outage on Adobe Cloud. <br><br><strong>Resolution</strong> <br> Resolve network connectivity issues at your end and check the status of the service on <a href="https://status.adobe.com/zh-cn/">https://status.adobe.com/zh-cn/</a> for a planned or unplanned outage.</td>
<td><img alt="The service failed to convert the form." src="assets/service-failure.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The number of pages is more than 15.  <br><br><strong>Reason</strong> <br> The source form is more than 15 pages long.  <br><br><strong>Resolution</strong> <br> Use Adobe Acrobat to split forms with more than 15 pages. Bring the number of pages in a form to less than 15.</td>
<td><img alt="The number of pages is more than 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The number of files is more than 15.  <br><br><strong>Reason</strong> <br>  The folder contains more than 15 forms. <br><br><strong>Resolution</strong> <br> Bring the number of forms in a folder to less than or equal to 15. Bring the total number of pages in a folder less than 50. Bring the size of the folder to less than 10 MB. Do not keep forms in a sub-folder. Organize source forms into a batch of 8-15 forms.</td>
<td><img alt="The number of files is more than 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The source file format is not supported.  <br><br><strong>Reason</strong> <br> The folder containing source forms have some unsupported files. <br><br><strong>Resolution</strong> <br> The service supports only .xdp and .pdf files. Remove files with any other extension from the folder and run the conversion.</td>
<td><img alt="The source file format is not supported." src="assets/unsupported-file-formats.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Scanned forms are not supported.  <br><br><strong>Reason</strong> <br> The PDF form contains only scanned images of the form and contains no content structure. <br><br><strong>Resolution</strong> <br> The service does not support converting scanned forms or an image of a form to an adaptive out-of-the-box. However, you use Adobe Acrobat to convert the image of a form to a PDF Form. Then, use the service to convert the PDF Form to an adaptive form. Always use a high-quality image of the form for conversion in Acrobat. It improves the quality of the conversion.</td>
<td><img alt="Scanned forms are not supported." src="assets/scanned-forms-error.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Encrypted PDF form is not supported.  <br><br><strong>Reason</strong> <br> The folder contains encrypted PDF forms. <br><br><strong>Resolution</strong> <br> The service does not support converting an encrypted PDF form to an adaptive form. Remove the encryption, upload the non-encrypted form, and run the conversion.</td>
<td><img alt="Encrypted PDF form is not supported." src="assets/secured-pdf-form.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Unable to parse meta-model JSON schema.  <br><br><strong>Reason</strong> <br> The JSON schema supplied to the service is not properly formatted, contains invalid characters, or uses invalid syntax to map components.  <br><br><strong>Resolution</strong> <br> Check the formatting of the JSON file. You can use any online JSON validator to check the formatting and structure of the schema. See, <a href="extending-the-default-meta-model.md">Extend the default meta-model</a> article for information on meta-model syntax.</td>
<td><img alt="Unable to parse meta-model JSON schema" src="assets/invalid-meta-model-schema.png" /></td>
</tr>
</tbody>
</table>
-->
