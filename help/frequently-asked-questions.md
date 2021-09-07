---
title: 常见问题
seo-title: Frequently asked questions
description: 常见查询或常见问题解答
seo-description: frequently asked questions for Automated Forms Conversion Service
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
exl-id: 3a29f8d4-8ea0-49eb-bfe0-0eab5f0c52c7
source-git-commit: 47261710e6616c27c210ac53bffcc2387a06ea7a
workflow-type: tm+mt
source-wordcount: '1821'
ht-degree: 3%

---

# 常见问题{#frequently-asked-questions}

1. **automated forms conversion服务支持哪个版本的AEM Forms?**

   <p>automated forms conversion服务支持AEM 6.4 Forms和AEM 6.5 Forms。 它适用于OSGi上的AEM Forms和JEE上的AEM表单。 您需要AEM创作实例上最新的AEM Forms附加组件包才能使用该服务。 有关详细说明，请参阅<a href="configure-service.md">配置Automated forms conversion</a>服务。</p> 
    <br>

1. **该服务是否可以在内部部署中安装？**

   <p>Adobe定期训练Automated forms conversion服务的AI和ML算法，并使用新的数据集来提高转换准确性。 更新的算法会定期部署到在Adobe云上运行的转化服务。 该服务的所有客户都从更新的算法中受益。 因此，云托管的中央部署最适合于Automated forms conversion服务，以便持续学习并向所有客户交付改进。</p> 
    <p>该服务将空白表单转换为自适应表单。 该服务不支持已填写表单以及从已填写表单中提取数据。 从已填写的表单中删除数据，在将表允许列表单发送到服务进行转换之前，从表单中删除或专有信息</p> <br>

1. **该服务是否支持所有格式的PDF forms?支持哪些语言？**

   <p>该服务可以将非交互式PDF forms、基于XFA的XDP和PDF forms以及AcroForms转换为自适应表单。 该服务不支持扫描或填写的表单。 有关其他限制，请参阅<a href="known-issues.md">已知问题</a>一文。<br /> </p> 
    <p>我们将定期添加对其他源类型的支持。 将<a href="introduction.md">受支持的PDF表单</a>部分保留在您的观看列表中，以定期更新新添加的特性和功能。</p>

   该服务只能将英语、法语、德语、西班牙语、意大利语和葡萄牙语表单转换为自适应表单。 您可以使用[AEM翻译工作流将生成的自适应表单翻译成其他语言。](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **该服务能否生成XDP而不是自适应表单？**

   <p>服务不会生成XDP输出。 我们将定期向服务添加功能和功能。 将<a href="introduction.md">支持的语言和PDF forms</a>部分保留在监视列表中，以定期更新新添加的特性和功能。</p> <br>

1. **生成的架构的类型是什么？**

   <p>您可以使用服务生成： </p>

   * 绑定到JSON架构的自适应表单，以及
   * 未绑定到任何架构<br><br>的自适应表单

1. **该服务能否将Microsoft Word表单转换为自适应表单？**

   <p>不能，该服务无法将Microsoft Word表单转换为自适应表单。 您可以将Microsoft Word表单保存为PDF表单，并将PDF表单转换为自适应表单。 整个过程是 </p> <br>

   1. 使用Adobe Acrobat将Word文档转换为非交互式PDF](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html)。[
   1. 使用Adobe Acrobat将生成的PDF forms转换为可填写的PDF表单](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html)。[
   1. 使用Adobe Acrobat手动更新和修复表单字段。
   1. 保存PDF表单。 现在，您可以将表单与转换服务结合使用以生成自适应表单。 您还可以将表单用作记录文档模板。


1. **该服务是否可以将扫描的纸质表单和彩色表单转换为自适应表单？**

   <p>该服务可以将颜色PDF forms转换为自适应表单。 该服务不支持扫描或填写的表单。 有关其他限制，请参阅<a href="known-issues.md">已知问题</a>一文。</p> <br>

1. **该服务是否可以将扫描的表单或表单的仅图像转换为自适应表单？**

   <p>该服务不支持直接将扫描的表单或表单图像转换为自适应表单。 但您可以使用 Adobe Acrobat 将表单图像转换为 PDF 表单。 然后再使用本服务将 PDF 表单转换为自适应表单。 对于 Acrobat，请务必使用高质量的表单图像进行转换。 这样可以提高转换质量。</p> <br>

1. **某些基于XDP的表单使用表单片段，应将这些表单片段上传到何处？**

   <p class="MsoNormal">将表单片段上传到转换文件夹并保留原始文件夹结构。 它有助于保留基于XDP的表单和表单片段中使用的相对路径。</p> <br>

1. **服务是否支持绑定到架构的XDP表单？如果我已将XDP绑定到架构，是否需要将架构嵌入到XDP?**

   <p>是，该服务支持绑定到架构的XDP表单，并要求将架构嵌入到源XDP表单中。 在转换绑定到架构的XDP表单时，服务会生成JSON架构。 JSON架构的结构与源XDP表单的XSD架构类似。</p> <br>

1. **服务无法转换表单。原因和如何解决该问题的方法是什么？**
转化失败的最常见原因包括：
</p>
   * 为转换提供安全PDF forms。 请勿使用受密码保护或安全PDF forms进行转换。
   * Internet连接中断。 确保在转换过程中已连接到Internet。
   * 源PDF包含表单的图像，而不是实际的表单。
   * 服务配置不正确、未提供服务URL或提供的服务URL不正确。 在&#x200B;**[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**&#x200B;中检查[服务配置](configure-service.md#configure-the-cloud-service)。
   * 未正确配置IMS配置。 对IMS配置执行运行状况检查，以确保其正常运行。 要检查IMS配置是否正确，请执行以下操作：
      1. 转到 `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. 选择配置。 单击标题中的&#x200B;**[!UICONTROL Check Health]**，然后单击&#x200B;**[!UICONTROL Check]**。 如果成功，您会收到&#x200B;**[!UICONTROL Token retrieved successfully!]**&#x200B;消息。<br> <br>

1. **使用自定义字体是否会影响转换？**

   <p>将非交互式PDF表单转换为自适应表单后，为了提高转换质量，字体会嵌入到PDF表单中。 对嵌入字体的支持仅限于非交互式PDF forms。 为了优化AcroForm和基于XFA的PDF forms的转换，会使用回退字体。</p> 
    <p>只有<strong>Customer fonts directory</strong>字段中列出的<strong> CQ-DAM-Handler-Gibson字体管理器服务</strong>配置的自定义字体目录中可用的表单会嵌入非交互式PDF表单。</p> 
    <p> </p> <br>

1. **该服务是否识别并使用输出自适应表单中源PDF的字体？**

   <p>响应式HTML表单的样式和布局通常与PDF或基于纸张的表单不同。 为了支持组织内一致的布局和样式，自适应表单使用<a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">主题来设置表单的样式</a>。 转换服务使用在转换期间应用的主题中指定的字体和字体样式。 您可以更改主题的字体和字体样式，以便为自适应表单的组件提供不同的外观。</p> <br>

1. **该服务是否会自动从基于XDP的表单中提取JavaScript并将其应用于相应的自适应表单？**

   <p>该服务不会自动将基于XFA的表单或Acro Forms的脚本转换为相应的自适应表单规则。 您（表单作者）可以使用<a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">规则编辑器</a>向自适应表单添加交互性。</p> <br>

1. **某些表单对象无法正确转换为自适应表单组件。如何解决该问题？**

   <p>automated forms conversion服务是在大量表单上进行培训的。 但基于AI/ML的应用程序受其培训数据和模式的限制。 可能有多种字段类型、布局、模式和上下文可辨认为人类感知，但很难进行自动识别。 服务可能无法识别此类对象或可能无法正确识别它们。 您可以使用<a href="review-correct-ui-edited.md" target="_blank">Review and Correct</a>编辑器，对熟悉的基于纸张表单的输入表单布局进行必要的修改。</p> <br/>

1. **某些更正会在表单中重复。该服务能否识别并修复所有此类实例，以便将来进行转化？**

   该服务可持续地培训您的表单和模式。 它每天学习新的模式。 尚未开始自动应用在表单中重复的更正。 请留意预发行表单，以了解此类功能的可用性。<br/><br/>

   您可以使用元模型将表单对象映射到您选择的自适应表单组件，并为组件预配置验证、规则、数据模式、帮助文本和辅助功能属性。 所有指定的属性都将在转换期间应用。 可以使用元模型将通用属性应用到字段。 它可以帮助您减少表单中重复出现的一些问题。<br/><br/>

1. **具有敏感数据(如个人身份信息(PII)信息)的表单有哪些选项？**
服务仅支持空白或未填充的表单。请勿上传包含个人身份信息(PII)的已填写表单或表单。 此外，还可以删除源表单中预填充的数据、个人身份信息(PII)、机密信息和专有信息。 
<br/>

1. **页眉和页脚应放在何处？**

   <p>在自适应表单模板中放置页眉和页脚。 如果源PDF表单具有页眉和页脚，则该服务会在转换期间检测并替换检测到的页眉和页脚，使用自适应表单模板中提供的页眉和页脚。 如果自适应表单中包含任何额外的页眉或页脚，则可以使用<a href="review-correct-ui-edited.md">Review and Crorect</a>编辑器来修复或删除此类页眉或页脚。</p> <br />

1. **与手动规划、创建资产（主题、模板）、创建和发布自适应表单过程相比，该服务可节省多少时间？**

   <p>时间长短取决于输入表单的大小和复杂程度以及请求数。 与手动转换表单的过程相比，该服务打算以更快的速度将PDF forms转换为自适应表单，从而显着缩短实现价值的时间。 </p> <br />

1. **如果遇到与RSA库相关的错误，该怎么办？错误消息与下面提到的消息类似：** <br/>

未为RSA/BouncyCastle库配置引导委派时，会出现上述错误。 执行以下步骤以解决问题：   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
未为RSA/BouncyCastle库配置引导委派时，会出现上述错误。执行以下步骤以解决问题：
   <p> </p>

   1. 停止AEM实例。 导航到`[AEM installation directory]\crx-quickstart\conf\`文件夹。 打开sling.properties文件进行编辑。 如果您使用`[AEM installation directory]\crx-quickstart\bin\start.bat`启动AEM实例，请编辑位于`[AEM_root]\crx-quickstart\`的sling.properties。
   1. 将以下属性添加到sling.properties文件：<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. 保存并关闭文件。<br/>
   1. 启动 AEM 实例。<br/>

   <br/>

1. **如何自动更改自适应表单文本的大小写？**

   <p>您可以使用主题或样式编辑器中的自适应更改自适应表单字段的大小写。 例如，您可以打开主题编辑器，并将表单所有文本的Case属性的值设置为大写、小写或camelCase。 您还可以使用主题编辑器中的“CSS覆盖”选项创建不同类型的样式。</p>

1. **我能否将Adobe Sign文本标记与Automated forms conversion服务结合使用？**

   <p> 当您使用Automated forms conversion服务将PDF表单转换为自适应表单，并且PDF表单具有Adobe Sign文本标签时，这些标签将转换为相应的自适应表单字段，并自动填充签名者详细信息。  该功能仅适用于Acro Forms，自适应表单支持有限数量的Adobe Sign字段。</p>  </br>

1. **如何创建启用Adobe Sign的PDF表单？**

   </p>要创建启用Adobe Sign的PDF表单，请执行以下操作：</p>

   将[Adobe Sign文本标记](https://helpx.adobe.com/sign/using/text-tag.html)添加到字段名称，或使用[转换到Adobe Sign表单](https://helpx.adobe.com/sign/using/create-forms-with-acrobat.html)选项。
