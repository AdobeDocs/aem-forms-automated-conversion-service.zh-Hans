---
title: '自动表单转换服务疑难解答 '
seo-title: '自动表单转换服务(AFCS)疑难解答 '
description: '常见AFCS问题及其解决方案 '
seo-description: 常见AFCS问题及其解决方案
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 3a82102feffa7fc618dc37c9a745c254a46a0700

---


# 自动表单转换服务疑难解答


<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. --> The document  provides basic troubleshooting steps for common errors.

## 常见错误 {#commonerrors}

| 错误 | 示例 |
|--- |--- |
| **错误消息**<br> :访问令牌标题不可用。 <br><br> **原因**<br> 管理员已创建多个IMS配置，或者IMS配置无法在Adobe Cloud上访问AFCS服务。 <br><br>**分辨率&#x200B;**如果有多个配置，请删除所有配置并<br>创建新配置[](configure-service.md#obtainpubliccertificates)。<br>如果有单个配置，请使用“运行状**&#x200B;况检查&#x200B;**”[检查连接](configure-service.md#createintegrationoption)。 | ![访问令牌标题不可用](assets/invalid-ims-configurations.png) |
| **错误消息**<br> ：无法连接到服务。  <br><br>**原因&#x200B;**<br>Automated Forms Conversion Service Cloud服务中提及错误的服务URL或没有服务URL。<br><br>**解析**<br> Automated Forms [](configure-service.md#configure-the-cloud-service) Conversion Service Cloud服务中的正确服务URL。 | ![无法连接到服务。](assets/wrong-service-url-configured.png) |
| **错误消息**<br> ：服务无法转换表单。  <br><br>**原因&#x200B;**<br>：您终端出现网络连接问题，服务因Adobe Cloud的定期维护或中断而关闭。<br><br>**解决**<br> ：解决您最终的网络连接问题，并检查https://status.adobe.com/上服务的状态，以确定计划内或计划外中断。 | ![无法连接到服务。](assets/conversion-failure.png) |
| **错误消息**<br> ，页数大于15。  <br><br>**原因&#x200B;**<br>源表单的长度超过15页。<br><br>**解决方**<br> 案使用Adobe Acrobat拆分表单，页面超过15页。 将表单中的页数调整为少于15页。 | ![无法连接到服务。](assets/number-of-pages.png) |
| **错误消息**<br> ：文件数大于15。  <br><br>**原因&#x200B;**<br>该文件夹包含15个以上的表单。<br><br>**解决方**<br> 案将文件夹中的表单数量设为小于或等于15。 将页面总数置于小于50的文件夹中。 将文件夹大小调整为小于10 MB。 请勿将表单保留在子文件夹中。 将源表单组织成一批8-15个表单。 | ![无法连接到服务。](assets/number-of-pages.png) |
| **错误消息** : <br> 不支持源文件格式。  <br><br>**原因&#x200B;**<br>包含源表单的文件夹包含一些不支持的文件。<br><br>**分辨率**<br> 此服务仅支持。xdp和。pdf文件。 从文件夹中删除具有任何其他扩展名的文件并运行转换。 | ![无法连接到服务。](assets/unsupported-file-formats.png) |
| **不支持错误消息**<br> ：扫描的表单。  <br><br>**原因&#x200B;**<br>PDF表单仅包含表单的扫描图像且不包含内容结构。<br><br>**分辨率**<br> 该服务不支持将扫描的表单或表单的图像转换为自适应的现成功能。 但是，您使用Adobe Acrobat将表单的图像转换为PDF表单。 然后，使用该服务将PDF表单转换为自适应表单。 在Acrobat中始终使用表单的高质量图像进行转换。 它提高了转换质量。 | ![无法连接到服务。](assets/scanned-forms-error.png) |
| **不支持Error** Message <br> Encrypted PDF表单。  <br><br>**原因&#x200B;**<br>文件夹包含加密的PDF表单。<br><br>**分辨率**<br> 此服务不支持将加密的PDF表单转换为自适应表单。 删除加密，上传未加密的表单，然后运行转换。 | ![无法连接到服务。](assets/secured-pdf-form.png) |
| **错误消息**<br> 无法解析元模型JSON模式。  <br><br>**原因&#x200B;**<br>：提供给服务的JSON模式格式不正确，包含无效字符或使用无效语法映射组件。<br><br>**分辨率**<br> 检查JSON文件的格式。 您可以使用任何在线JSON验证程序检查模式的格式和结构。 有关元 [模型语法的信息，请参阅](extending-the-default-meta-model.md) ，扩展默认元模型文章。 | ![无法连接到服务。](assets/invalid-meta-model-schema.png) |

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
<td><strong>Error Message</strong> <br> Unable to connect to the service.  <br><br><strong>Reason</strong> <br> Incorrect service URL or no service URL is mentioned in Automated Forms Conversion Service cloud services. <br><br><strong>Resolution</strong> <br> Correct <a href="configure-service.md#configure-the-cloud-service">Service URL</a> in Automated Forms Conversion Service Cloud services.</td>
<td><img alt="Unable to connect to the service." src="assets/wrong-endpoint-configured.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The service failed to convert the form.  <br><br><strong>Reason</strong> <br> Network connectivity issues at your end, the service is down due to scheduled maintenance, or outage on Adobe Cloud. <br><br><strong>Resolution</strong> <br> Resolve network connectivity issues at your end and check the status of the service on <a href="https://status.adobe.com/">https://status.adobe.com/</a> for a planned or unplanned outage.</td>
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