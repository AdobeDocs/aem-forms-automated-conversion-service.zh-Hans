---
title: 常见问题
seo-title: 常见问题
description: 常见查询或常见问题
seo-description: automated forms conversion服务常见问题
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
translation-type: tm+mt
source-git-commit: 92cd241915ef5818fb004a8982674b4f6753c171
workflow-type: tm+mt
source-wordcount: '1825'
ht-degree: 4%

---


# 常见问题{#frequently-asked-questions}

1. **automated forms conversion服务支持哪个版本的AEM Forms?**

   <p>automated forms conversion服务支持AEM 6.4Forms和AEM 6.5Forms。 它在OSGi和AEM JEE表单上都与AEM Forms协作。 您需要AEM作者实例顶部最新的AEM Forms加载项包才能使用服务。 有关详细说明，请参阅<a href="configure-service.md">配置Automated forms conversion</a>服务。</p> 
    <br>

1. **该服务是否可以预先安装？**

   <p>Adobe定期训练Automated forms conversion服务的AI和ML算法，使用新的数据集来提高转换精度。 更新的算法会定期部署到在Adobe云上运行的转换服务。 该服务的所有客户都从更新的算法中受益。 因此，云托管的中央部署最适合Automated forms conversion服务，以持续学习和改进所有客户。</p> 
    <p>该服务将空白表单转换为自适应表单。 该服务不支持已填写表单以及从已填写表单提取数据。 从已填写的表单中删除数据，允许列表在将表单发送到服务进行转换之前从表单中删除或专有信息</p> <br>

1. **该服务是否支持所有格式的PDF forms?支持哪些所有语言？**

   <p>该服务可以将非交互式PDF forms、基于XFA的XDP和PDF forms以及AcroForms转换为自适应表单。 服务不支持扫描或填写的表单。 有关其他限制，请参阅<a href="known-issues.md">已知问题</a>文章。<br /> </p> 
    <p>我们定期添加对其他源类型的支持。 将<a href="introduction.md">supportedPDF forms</a>部分保留在监视列表中，以定期更新新添加的功能和特性。</p>

   此服务仅限于将英语表单转换为自适应表单。 您可以使用[AEM转换工作流将生成的自适应表单翻译为其他语言。](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **该服务能否生成XDP而不是自适应表单？**

   <p>服务不生成XDP输出。 我们会定期为服务添加功能。 将<a href="introduction.md">支持的语言和PDF forms</a>部分保留在观察列表中，以定期更新新添加的功能和特性。</p> <br>

1. **生成的模式类型是什么？**

   <p>您可以使用服务生成： </p>

   * 绑定到JSON模式和
   * 未绑定到任何模式<br><br>的自适应表单

1. **该服务是否可以将Microsoft Word表单转换为自适应表单？**

   <p>否，服务不会将Microsoft Word表单转换为自适应表单。 您可以将Microsoft Word表单保存为PDF表单，并将PDF表单转换为自适应表单。 整个过程是 </p> <br>

   1. 使用Adobe Acrobat将Word文档转换为非交互式PDF[。](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html)
   1. 使用Adobe Acrobat将生成的PDF forms转换为可填写的PDF表单[。](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html)
   1. 使用Adobe Acrobat手动更新和修复表单字段。
   1. 保存PDF表单。 现在，您可以将表单与转换服务结合使用以生成自适应表单。 您还可以将表单用作记录模板的文档。


1. **该服务是否可以将扫描的纸质表单和彩色表单转换为自适应表单？**

   <p>该服务可以将颜色PDF forms转换为自适应表单。 服务不支持扫描或填写的表单。 有关其他限制，请参阅<a href="known-issues.md">已知问题</a>文章。</p> <br>

1. **该服务是否可以将扫描的表单或仅将表单的图像转换为自适应表单？**

   <p>该服务不支持将扫描的表单或表单的图像转换为自适应的现成表单。 但您可以使用 Adobe Acrobat 将表单图像转换为 PDF 表单。 然后再使用本服务将 PDF 表单转换为自适应表单。 对于 Acrobat，请务必使用高质量的表单图像进行转换。 这样可以提高转换质量。</p> <br>

1. **某些基于XDP的表单使用表单片段，这些表单片段应从何处上传？**

   <p class="MsoNormal">将表单片段上传到转换文件夹并保留原始文件夹结构。 它有助于保留在基于XDP的表单和表单片段中使用的相对路径。</p> <br>

1. **服务是否支持模式绑定的XDP表单？如果XDP绑定到模式，是否需要将模式嵌入到XDP?**

   <p>是，该服务支持模式绑定的XDP表单，并需要将模式嵌入到源XDP表单中。 转换模式绑定XDP表单时，服务将生成JSON模式。 JSON模式的结构与源XDP表单的XSD模式类似。</p> <br>

1. **服务无法转换表单。原因何在，如何解决？**
转换失败的最常见原因是：
</p>
   * 为转换提供有担保PDF forms。 切勿使用受密码保护的PDF forms或受保护的数据进行转换。
   * Internet连接中断。 确保在转换过程中连接到Internet。
   * 源PDF包含表单的图像，而不是实际的表单。
   * 服务配置不正确、未提供服务URL或提供的服务URL不正确。 检查&#x200B;**[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**&#x200B;的[服务配置](configure-service.md#configure-the-cloud-service)。
   * 未正确配置IMS配置。 对IMS配置执行运行状况检查以确保其正常工作。 检查IMS配置是否正确：
      1. 转到 `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. 选择配置。 单击标题中的&#x200B;**[!UICONTROL Check Health]**，然后单击&#x200B;**[!UICONTROL Check]**。 如果成功，您会收到&#x200B;**[!UICONTROL Token retrieved successfully!]**&#x200B;消息。<br> <br>

1. **使用自定义字体是否会影响转换？**

   <p>将非交互式PDF表单转换为自适应表单以提高转换质量时，字体将嵌入到PDF表单中。 嵌入字体的支持仅限于非交互式PDF forms。 要优化AcroForm和基于XFA的PDF forms的转换，请使用回退字体。</p> 
    <p>只有<strong> CQ-DAM-Handler-Gibson字体管理器服务</strong>配置的<strong>客户字体目录</strong>字段中列出的自定义字体目录中可用的表单才嵌入非交互式PDF表单中。</p> 
    <p> </p> <br>

1. **该服务是否在输出自适应表单中识别和使用源PDF的字体？**

   <p>响应式HTML表单的样式和布局通常与PDF或基于纸张的表单不同。 为了在整个组织中支持一致的布局和样式，自适应表单使用<a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">主题设置表单的样式。 </a>转换服务使用转换过程中应用的主题中指定的字体和字体样式。 您可以更改主题的字体和字体样式，为自适应表单的组件提供独特的外观。</p> <br>

1. **该服务是否会从基于XDP的表单自动提取JavaScript并将其应用到相应的自适应表单？**

   <p>该服务不会自动将基于XFA的表单或AcroForms的脚本转换为相应的自适应表单规则。 您（表单作者）可以使用<a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">规则编辑器</a>向自适应表单添加交互性。</p> <br>

1. **某些表单对象无法正确转换为自适应表单组件。如何解决此问题？**

   <p>automated forms conversion服务是在大量表单上进行培训的。 但基于AI/ML的应用程序受其培训数据和模式的限制。 可能有多种字段类型、布局、模式和上下文可以辨别为人类感知，但难以自动识别。 服务可能无法识别此类对象，或可能识别错误。 您可以使用<a href="review-correct-ui-edited.md" target="_blank">Review and Correct</a>编辑器在熟悉的纸张表单输入表单布局中进行必要的修改。</p> <br/>

1. **某些更正会跨表单重复。该服务能否在将来的转换中识别并修复所有此类实例？**

   该服务对您的表单和模式进行了一致的培训。 它每天学习新的模式。 它尚未开始跨表单重复的自动应用校正。 请注意预发行表单，以获得此类功能。<br/><br/>

   您可以使用元模型将表单对象映射到您选择的自适应表单组件，并为这些组件预配置验证、规则、数据模式、帮助文本和辅助功能属性。 转换过程中将应用所有指定的属性。 您可以使用元模型将通用属性应用到字段。 它可以帮助您减少表单之间重复出现的问题。<br/><br/>

1. **具有敏感数据(如个人身份信息(PII)信息)的表单有哪些选项？**
该服务仅支持空或未填写的表单。请勿上传已填写的表单或包含个人身份信息(PII)的表单。 此外，删除源表单中预填数据、个人身份信息(PII)、机密和专有信息。 
<br/>

1. **页眉和页脚应放在何处？**

   <p>将页眉和页脚放在自适应表单模板中。 如果源PDF表单具有页眉和页脚，则服务会在转换过程中检测检测到的页眉和页脚，并将其替换为自适应表单模板中提供的页眉和页脚。 如果自适应表单中包含任何额外的页眉或页脚，则可以使用<a href="review-correct-ui-edited.md">审阅和更正</a>编辑器来修复或删除此类页眉或页脚。</p> <br />

1. **与手动规划、创建资产(主题、模板)、创建和发布自适应表单相比，该服务可节省多少时间？**

   <p>时间长短取决于输入表单的大小和复杂性以及请求数。 与手动转换表单的过程相比，该服务打算以更快的速度将PDF forms转换为自适应表单，从而显着缩短实现价值的时间。 </p> <br />

1. **如果遇到与RSA库相关的错误，该怎么办？错误消息与下面提到的消息类似：** <br/>

未为RSA/BouncyCastle库配置引导委派时，会发生上述错误。 请执行以下步骤以解决问题：   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
未为RSA/BouncyCastle库配置引导委派时，会发生上述错误。请执行以下步骤以解决问题：
   <p> </p>

   1. 停止AEM实例。 导航到`[AEM installation directory]\crx-quickstart\conf\`文件夹。 打开sling.properties文件进行编辑。 如果使用`[AEM installation directory]\crx-quickstart\bin\start.bat`开始AEM实例，请编辑位于`[AEM_root]\crx-quickstart\`的sling.properties。
   1. 将以下属性添加到sling.properties文件：<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. 保存并关闭文件。<br/>
   1. 开始AEM实例。<br/>

   <br/>

1. **如何自动更改自适应表单文本的大小写？**

   <p>您可以使用自适应主题或样式编辑器更改自适应表单字段的大小写。 例如，您可以打开主题编辑器并将表单所有文本的大小写属性值设置为大写、小写或驼峰大小写。 您还可以使用主题编辑器中的“CSS覆盖”选项创建不同类型的样式。</p>

1. **我是否可以将Adobe Sign文本标记与Automated forms conversion服务一起使用？**

   <p> 当您使用Automated forms conversion服务将PDF表单转换为自适应表单且PDF表单包含Adobe Sign文本标签时，这些标签将转换为相应的自适应表单字段并自动填充签署方详细信息。  该功能仅适用于AcroForms，自适应表单支持有限数量的Adobe Sign字段。</p>  </br>

1. **如何创建支持Adobe Sign的PDF表单？**

   </p>要创建启用Adobe Sign的PDF表单，请执行以下操作：</p>

   将[Adobe Sign文本标记](https://helpx.adobe.com/sign/using/text-tag.html)添加到字段名称或使用[转换为Adobe Sign表单](https://helpx.adobe.com/sign/using/create-forms-with-acrobat.html)选项。
