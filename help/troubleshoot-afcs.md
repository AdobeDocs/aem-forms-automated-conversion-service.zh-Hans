---
title: '自动表单转换服务疑难解答 '
seo-title: '自动表单转换服务(AFCS)疑难解答 '
description: '常见AFCS问题及其解决方案 '
seo-description: 常见AFCS问题及其解决方案
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 0af626e21a0c3d6a7d3c339c0b87179b048092d3

---


# 自动表单转换服务疑难解答


<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. --> The document  provides basic troubleshooting steps for common errors.

## 常见错误 {#commonerrors}

<table>
<thead>
<tr>
<th>错误</th>
<th>示例</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>错误消息</strong><br> :访问令牌标题不可用。 <br><br><strong>原因</strong><br> 管理员已创建多个IMS配置，或者IMS配置无法在Adobe Cloud上访问AFCS服务。 <br><br><strong>分辨率</strong> 如果有多个配置，请删除所有配置并 <br> 创建新配置 <a href="configure-service.md#obtainpubliccertificates"></a>。 <br> 如果有单个配置，请使用“运行状 <strong> 况检查” </strong> 检查 <a href="configure-service.md#createintegrationoption">连接性</a>。</td>
<td><img alt="访问令牌标题不可用" src="assets/invalid-ims-configuration.png" /></td>
</tr>
<tr>
<td><strong>错误消息</strong><br> ：无法连接到服务。  <br><br><strong>原因</strong><br> Automated Forms Conversion Service Cloud服务中提及错误的服务URL或没有服务URL。 <br><br><strong>解析</strong><br> Automated Forms <a href="configure-service.md#configure-the-cloud-service"></a> Conversion Service Cloud服务中的正确服务URL。</td>
<td><img alt="无法连接到服务。" src="assets/wrong-endpoint-configured.png" /></td>
</tr>
<tr>
<td><strong>错误消息</strong><br> ：服务无法转换表单。  <br><br><strong>原因</strong><br> ：您终端出现网络连接问题，服务因Adobe Cloud的定期维护或中断而关闭。 <br><br><strong>解决</strong> ：在您的终端解决网络连接问题，并检查https://status.adobe.com/上服务的状 <br> 态 <a href="https://status.adobe.com/"></a> ，以确定计划内或计划外中断。</td>
<td><img alt="服务无法转换表单。" src="assets/service-failure.png" /></td>
</tr>
<tr>
<td><strong>错误消息</strong><br> ，页数大于15。  <br><br><strong>原因</strong><br> 源表单的长度超过15页。  <br><br><strong>解决方</strong><br> 案使用Adobe Acrobat拆分表单，页面超过15页。 将表单中的页数调整为少于15页。</td>
<td><img alt="页数超过15页。" src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>错误消息</strong><br> ：文件数大于15。  <br><br><strong>原因</strong><br> 该文件夹包含15个以上的表单。 <br><br><strong>解决方</strong><br> 案将文件夹中的表单数量设为小于或等于15。 将页面总数置于小于50的文件夹中。 将文件夹大小调整为小于10 MB。 请勿将表单保留在子文件夹中。 将源表单组织成一批8-15个表单。</td>
<td><img alt="文件数超过15个。" src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>错误消息</strong> : <br> 不支持源文件格式。  <br><br><strong>原因</strong><br> 包含源表单的文件夹包含一些不支持的文件。 <br><br><strong>分辨率</strong><br> 此服务仅支持。xdp和。pdf文件。 从文件夹中删除具有任何其他扩展名的文件并运行转换。</td>
<td><img alt="不支持源文件格式。" src="assets/unsupported-file-formats.png" /></td>
</tr>
<tr>
<td><strong>不支持错误消息</strong><br> ：扫描的表单。  <br><br><strong>原因</strong><br> PDF表单仅包含表单的扫描图像且不包含内容结构。 <br><br><strong>分辨率</strong><br> 该服务不支持将扫描的表单或表单的图像转换为自适应的现成功能。 但是，您使用Adobe Acrobat将表单的图像转换为PDF表单。 然后，使用该服务将PDF表单转换为自适应表单。 在Acrobat中始终使用表单的高质量图像进行转换。 它提高了转换质量。</td>
<td><img alt="不支持扫描的表单。" src="assets/scanned-forms-error.png" /></td>
</tr>
<tr>
<td><strong>不支持Error</strong> Message <br> Encrypted PDF表单。  <br><br><strong>原因</strong><br> 文件夹包含加密的PDF表单。 <br><br><strong>分辨率</strong><br> 此服务不支持将加密的PDF表单转换为自适应表单。 删除加密，上传未加密的表单，然后运行转换。</td>
<td><img alt="不支持加密的PDF表单。" src="assets/secured-pdf-form.png" /></td>
</tr>
<tr>
<td><strong>错误消息</strong><br> 无法解析元模型JSON模式。  <br><br><strong>原因</strong><br> ：提供给服务的JSON模式格式不正确，包含无效字符或使用无效语法映射组件。  <br><br><strong>分辨率</strong><br> 检查JSON文件的格式。 您可以使用任何在线JSON验证程序检查模式的格式和结构。 有关元 <a href="extending-the-default-meta-model.md">模型语法的信息，请参阅</a> ，扩展默认元模型文章。</td>
<td><img alt="无法解析元模型JSON模式" src="assets/invalid-meta-model-schema.png" /></td>
</tr>
</tbody>
</table>
