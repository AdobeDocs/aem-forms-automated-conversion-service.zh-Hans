---
title: 常见问题
seo-title: Frequently asked questions
description: 常见问题或常见问题
seo-description: frequently asked questions for Automated Forms Conversion Service
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
exl-id: 3a29f8d4-8ea0-49eb-bfe0-0eab5f0c52c7
source-git-commit: 298d6c0641d7b416edb5b2bcd5fec0232f01f4c7
workflow-type: tm+mt
source-wordcount: '1799'
ht-degree: 3%

---

# 常见问题{#frequently-asked-questions}

1. **automated forms conversion服务支持哪个AEM Forms版本？**
   <p>automated forms conversion服务支持AEM 6.4 Forms和AEM 6.5 Forms。 它可与OSGi上的AEM Forms以及JEE上的AEM Forms配合使用。 您需要在AEM创作实例之上添加最新的AEM Forms附加组件包才能使用该服务。 有关详细说明，请参阅 <a href="configure-service.md">配置Automated forms conversion</a> 服务。</p> 
    <br>

1. **是否可以在内部部署安装服务？**
   <p>Adobe使用新数据集定期训练Automated forms conversion服务的AI和ML算法，以提高转换准确性。 更新后的算法会定期部署到Adobe云上运行的转换服务。 该服务的所有客户都从更新的算法中受益。 因此，云托管式集中部署最适合Automated forms conversion服务不断学习并为所有客户提供改进。</p> 
    <p>该服务将空白表单转换为自适应表单。 该服务不支持已填写的表单以及从已填写的表单中提取数据。 将表单发送到服务进行转换之前，从填写的表单中删除数据，并从表单中删除或允许列表专有信息</p> <br>

1. **该服务是否支持所有格式的PDF forms？ 支持哪些所有语言？**
   <p>该服务可以将非交互式PDF forms、基于XFA的XDP和PDF forms以及AcroForms转换为自适应表单。 该服务不支持扫描或填写的表单。 有关其他限制，请参阅 <a href="known-issues.md">已知问题</a> 文章。<br /> </p> 
    <p>我们定期添加对其他源类型的支持。 保留 <a href="introduction.md">支持的PDF表单</a> 部分，以定期更新新添加的特性和功能。</p>

   该服务只能将英语、法语、德语、西班牙语、意大利语和葡萄牙语表单转换为自适应表单。 您可以使用将生成的自适应表单翻译成其他语言 [AEM翻译工作流。](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **该服务能否生成XDP而不是自适应表单？**
   <p>该服务未生成XDP输出。 我们定期向服务中添加功能和内容。 保留 <a href="introduction.md">支持的语言和PDF forms</a> 部分，以定期更新新添加的特性和功能。</p> <br>

1. **生成的架构的类型是什么？**
   <p>您可以使用该服务生成： </p>

   * 绑定到JSON架构的自适应表单和
   * 自适应表单未绑定到任何架构 <br><br>

1. **该服务能否将Microsoft Word表单转换为自适应表单？**
   <p>否，该服务不会将Microsoft Word表单转换为自适应表单。 您可以将Microsoft Word表单保存为PDF表单，并将PDF表单转换为自适应表单。 整个过程是 </p> <br>

   1. 使用Adobe Acrobat可以 [将Word文档转换为非交互式PDF](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html).
   1. 使用Adobe Acrobat可以 [将生成的PDF forms转换为可填写的PDF表单](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html).
   1. 使用Adobe Acrobat手动更新和修复表单字段。
   1. 保存PDF表单。 现在，您可以将该表单与转换服务结合使用来生成自适应表单。 您还可以将表单用作记录文档模板。


1. **该服务是否可以将扫描的纸质表单和彩色表单转换为自适应表单？**
   <p>该服务可将彩色PDF forms转换为自适应表单。 该服务不支持扫描或填写的表单。 有关其他限制，请参阅 <a href="known-issues.md">已知问题</a> 文章。</p> <br>

1. **该服务是否可以将扫描的表单或仅表单的图像转换为自适应表单？**
   <p>此服务不支持直接将扫描的表单或表单图像转换为自适应表单。 但您可以使用 Adobe Acrobat 将表单图像转换为 PDF 表单。 然后再使用本服务将 PDF 表单转换为自适应表单。 对于 Acrobat，请务必使用高质量的表单图像进行转换。 这样可以提高转换质量。</p> <br>

1. **某些基于XDP的表单使用表单片段，这些表单片段应该上传到何处？**
   <p class="MsoNormal">将表单片段上传到转换文件夹并保留原始文件夹结构。 它有助于保留在基于XDP的表单和表单片段中使用的相对路径。</p> <br>

1. **该服务是否支持架构绑定的XDP表单？ 如果我将XDP绑定到架构，是否需要将架构嵌入到XDP？**
   <p>是，该服务支持绑定架构的XDP表单，并要求将架构嵌入到源XDP表单中。 转换绑定架构的XDP表单时，服务会生成JSON架构。 JSON架构在结构上与源XDP表单的XSD架构类似。</p> <br>

1. **该服务无法转换表单。 问题的原因以及如何解决？**
转换失败的最常见原因是：</p>
   * 转换提供有抵押PDF forms。 请勿使用受密码保护或安全的PDF forms进行转换。
   * Internet连接中断。 确保在转换期间已连接到Internet。
   * 源PDF具有表单的图像，而不是实际的表单。
   * 服务配置不正确、未提供服务URL或提供的服务URL不正确。 查看 [服务配置](configure-service.md#configure-the-cloud-service) 在 **[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**.
   * IMS配置未正确配置。 对IMS配置执行运行状况检查以确保其正常工作。 要检查IMS配置是否正确，请执行以下操作：
      1. 转到 `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. 选择配置。 单击 **[!UICONTROL Check Health]** （从标题中）并单击 **[!UICONTROL Check]**. 如果成功，您将获得 **[!UICONTROL Token retrieved successfully!]** 消息。 <br> <br>

1. **使用自定义字体是否会影响转化？**
   <p>当非交互式PDF表单转换为自适应表单时，为了提高转换质量，字体将嵌入到PDF表单中。 对嵌入字体的支持仅限于非交互式PDF forms。 为了优化AcroForm和基于XFA的PDF forms的转换，使用后备字体。</p> 
    <p>仅自定义字体目录中列出的表单可用 <strong>Customer fonts目录</strong> 字段 <strong> CQ-DAM-Handler-Gibson Font Manager服务</strong> 在非交互式PDF表单中嵌入配置。</p> 
    <p> </p> <br>

1. **该服务是否识别并在输出的自适应表单中使用源PDF的字体？**
   <p>响应HTML表单的样式和布局通常与PDF表单或基于纸张的表单不同。 为了支持组织内一致的布局和样式，自适应表单使用 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">用于设置表单样式的主题</a>. 转换服务使用转换期间应用的主题中指定的字体和字体样式。 您可以更改主题的字体和字体样式，为自适应表单的组件提供独特的外观。</p> <br>

1. **该服务是否自动从基于XDP的表单中提取JavaScript并将其应用于相应的自适应表单？**
   <p>该服务不会自动将基于XFA的表单或Acro Forms的脚本转换为相应的自适应表单规则。 您（表单作者）可以使用 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">规则编辑器</a> 向自适应表单添加交互性。</p> <br>

1. **某些表单对象未正确转换为自适应表单组件。 如何解决此问题？**
   <p>automated forms conversion服务需要通过大量表单进行培训。 但基于AI/ML的应用程序受限于其训练数据和模式。 可能存在多种字段类型、布局、模式和上下文，人类感知可以识别这些字段，但难以进行自动识别。 该服务可能无法识别此类对象，或者可能无法正确识别它们。 您可以使用 <a href="review-correct-ui-edited.md" target="_blank">查看并更正</a> 编辑者，在熟悉的基于纸质表单的版面输入表单中进行必要的修改。</p> <br/>

1. **某些更正在表单之间重复。 该服务能否在未来的转换中识别并修复所有此类实例？**

   该服务始终针对您的表单和模式进行培训。 它每天学习新模式。 它尚未开始自动应用跨表单重复的校正。 留意预发行表单，了解此类功能的可用性。 <br/><br/>

   您可以使用元模型将表单对象映射到您选择的自适应表单组件，并为组件预配置验证、规则、数据模式、帮助文本和可访问性属性。 所有指定的属性将在转换期间应用。 可以使用元模型将通用属性应用于字段。 它可以帮助您减少表单中的一些重复问题。<br/><br/>

1. **对于包含敏感数据(如个人身份信息(PII)信息)的表单，有哪些选项？**
该服务仅支持空白或未填写的表单。 请勿上传包含个人身份信息(PII)的已填写表单或表单。 此外，删除源表单中预填的数据、个人身份信息(PII)、机密和专有信息。 <br/>

1. **页眉和页脚应放置在何处？**
   <p>将页眉和页脚放置在自适应表单模板中。 如果源PDF表单具有页眉和页脚，该服务将在转换期间检测检测到的页眉和页脚，并将其替换为自适应表单模板中可用的页眉和页脚。 如果自适应表单中包含任何额外的页眉或页脚，您可以使用 <a href="review-correct-ui-edited.md">查看并更正</a> 编辑器以修复或删除此类页眉或页脚。</p> <br />

1. **与手动规划、创建资产（主题、模板）、创建和发布自适应表单的过程相比，该服务节省了多少时间？**
   <p>时间长短取决于输入表单的大小和复杂性以及请求数量。 与手动表单转换过程相比，该服务旨在以更快的速度将PDF forms转换为自适应表单，从而显着缩短实现价值的时间。 </p> <br />

1. **如果我遇到与RSA库相关的错误，该怎么办？ 错误消息类似于下面提到的消息：** <br/>
   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
当没有为RSA/BouncyCastle库配置引导委派时，会发生上述错误。 执行以下步骤以解决问题：
   <p> </p>

   1. 停止AEM实例。 导航到 `[AEM installation directory]\crx-quickstart\conf\` 文件夹。 打开sling.properties文件进行编辑。 如果您使用 `[AEM installation directory]\crx-quickstart\bin\start.bat` 要启动AEM实例，请编辑位于的sling.properties `[AEM_root]\crx-quickstart\`.
   1. 将以下属性添加到sling.properties文件：<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. 保存并关闭文件。 <br/>
   1. 启动 AEM 实例。<br/>
   <br/>

1. **如何自动更改自适应表单文本的大小写？**
   <p>您可以使用主题或样式编辑器中的自适应来更改自适应表单字段的大小写。 例如，您可以打开主题编辑器，并将表单的所有文本的Case属性值设置为大写、小写或驼峰式大小写。 您还可以使用主题编辑器中的“CSS覆盖”选项创建不同类型的样式。</p>

1. **能否在Automated forms conversion服务中使用Adobe Sign文本标记？**
   <p> 当您使用Automated forms conversion服务将PDF表单转换为自适应表单，并且PDF表单具有Adobe Sign文本标记时，这些标记将转换为相应的自适应表单字段，并且签名者详细信息将自动填充。  该功能仅适用于Acro Forms，并且自适应表单支持有限数量的Adobe Sign字段。</p>  </br>

1. **如何创建启用Adobe Sign的PDF表单？**
   </p>要创建启用Adobe Sign的PDF表单，请执行以下操作：</p>

   添加 [Adobe Sign文本标记](https://helpx.adobe.com/sign/using/text-tag.html) 到字段名称或使用 [转换为Adobe Sign表单](https://helpx.adobe.com/sign/using/create-forms-with-acrobat.html) 选项。
