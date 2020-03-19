---
title: 常见问题
seo-title: 常见问题
description: 常见问题或常见问题解答
seo-description: 自动化表单转换服务的常见问题解答
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
translation-type: tm+mt
source-git-commit: 022b86b77c4a524f320cbcbcd6bad4403ddf57d8

---


# 常见问题{#frequently-asked-questions}

1. **Automated Forms Conversion服务支持哪个版本的AEM Forms?**
   <p>自动表单转换服务支持AEM 6.4表单和AEM 6.5表单。 它适用于OSGi上的AEM Forms和JEE上的AEM表单。 您需要AEM作者实例顶部的最新AEM Forms加载项包才能使用该服务。 有关详细说明，请参 <a href="configure-service.md">阅配置自动表单转换服务</a> 。</p> 
    <br>

1. **该服务是否可以预先安装？**
   <p>Adobe定期培训自动表单转换服务的AI和ML算法，使用新的数据集提高转换准确性。 更新的算法会定期部署到Adobe Cloud上运行的转换服务。 服务的所有客户都从更新的算法中受益。 因此，云托管的中央部署最适合自动化表单转换服务，以持续学习和改进所有客户。</p> 
    <p>该服务将空白表单转换为自适应表单。 该服务不支持已填写表单以及从已填写表单提取数据。 从已填写的表单中删除数据，在将表单发送到服务进行转换之前从表单中删除或列出专有信息</p> <br>

1. **该服务是否支持所有格式的PDF表单？ 支持哪些语言？**
   <p>该服务可以将非交互式PDF表单、基于XFA的XDP和PDF表单以及AcroForms转换为自适应表单。 服务不支持扫描或填写的表单。 有关其他限制，请参阅已 <a href="known-issues.md">知问题文章</a> 。<br /> </p> 
    <p>我们定期添加对其他源类型的支持。 将支持的 <a href="introduction.md">PDF表单部分保留在观察列表中</a> ，以定期更新新添加的功能和特性。</p>

   此服务仅限于将英语表单转换为自适应表单。 You can translate the generated adaptive forms to another language using [AEM translation workflow.](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **该服务能否生成XDP而不是自适应表单？**
   <p>服务不生成XDP输出。 我们会定期为服务添加功能。 将支持 <a href="introduction.md">的语言和PDF表单部分保留在观察列表中</a> ，以定期更新新添加的功能和特性。</p> <br>

1. **生成的架构的类型是什么？**
   <p>您可以使用服务生成： </p>

   * 绑定到JSON架构和
   * 未绑定到任何架构的自适应表单 <br><br>

1. **该服务是否可以将Microsoft Word表单转换为自适应表单？**
   <p>否，该服务不会将Microsoft Word表单转换为自适应表单。 您可以将Microsoft Word表单保存为PDF表单，并将PDF表单转换为自适应表单。 整个过程是 </p> <br>

   1. 使用Adobe Acrobat将 [Word文档转换为非交互式PDF](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html)。
   1. 使用Adobe Acrobat将生 [成的PDF表单转换为可填写的PDF表单](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html)。
   1. 使用Adobe Acrobat手动更新和修复表单字段。
   1. 保存PDF表单。 现在，您可以将表单与转换服务一起使用以生成自适应表单。 您还可以将表单用作记录文档模板。


1. **该服务是否可以将扫描的纸质表单和彩色表单转换为自适应表单？**
   <p>该服务可以将PDF表单转换为自适应表单。 服务不支持扫描或填写的表单。 有关其他限制，请参阅已 <a href="known-issues.md">知问题文章</a> 。</p> <br>

1. **该服务是否可以将扫描的表单或仅表单的图像转换为自适应表单？**
   <p>该服务不支持将扫描的表单或表单的图像转换为自适应的现成功能。 但是，您使用Adobe Acrobat将表单的图像转换为PDF表单。 然后，使用该服务将PDF表单转换为自适应表单。 在Acrobat中始终使用表单的高质量图像进行转换。 它提高了转换质量。</p> <br>

1. **某些基于XDP的表单使用表单片段，这些表单片段应在何处上传？**
   <p class="MsoNormal">将表单片段上传到转换文件夹并保留原始文件夹结构。 它有助于保留在基于XDP的表单和表单片段中使用的相对路径。</p> <br>

1. **服务是否支持架构绑定的XDP表单？ 如果我的XDP绑定到架构，是否需要将架构嵌入到XDP?**
   <p>是的，该服务支持架构绑定的XDP表单，并要求将架构嵌入到源XDP表单。 转换架构绑定的XDP表单时，服务将生成JSON架构。 JSON架构的结构与源XDP表单的XSD架构类似。</p> <br>

1. **服务无法转换表单。 原因何在，如何解决？**
转化为失败的最常见原因是：</p>
   * 为转换提供了安全的PDF表单。 请勿使用受口令保护或受保护的PDF表单进行转换。
   * Internet连接中断。 确保在转换过程中已连接到Internet。
   * 源PDF包含表单的图像，而不是实际的表单。
   * 服务配置不正确、未提供服务URL或提供的服务URL不正确。 请在 [> >](configure-service.md#configure-the-cloud-service) **[!UICONTROL AEM]****[!UICONTROL Tools]** >查看服务配置 **[!UICONTROL Cloud Services]****[!UICONTROL Automated Forms Conversion configuration]**。
   * IMS配置未正确配置。 对IMS配置执行运行状况检查以确保其正常工作。 检查IMS配置是否正确：
      1. 转到 `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. 选择配置。 单击标 **[!UICONTROL Check Health]** 题中的，然后单击 **[!UICONTROL Check]**。 如果成功，您会收到 **[!UICONTROL Token retrieved successfully!]** 消息。 <br> <br>

1. **使用自定义字体是否会影响转换？**
   <p>当非交互式PDF表单转换为自适应表单以提高转换质量时，字体将嵌入到PDF表单中。 嵌入字体的支持仅限于非交互式PDF表单。 要优化AcroForm和基于XFA的PDF表单的转换，请使用回退字体。</p> 
    <p>只有在 <strong></strong><strong></strong> CQ-DAM-Handler-Gibson字体管理器服务配置的“客户字体”目录字段中列出的自定义字体目录中可用的表单才嵌入到非交互式PDF表单中。</p> 
    <p> </p> <br>

1. **该服务是否在输出自适应表单中识别和使用源PDF的字体？**
   <p>响应式HTML表单的样式和布局通常与PDF或基于纸张的表单不同。 为了在组织内支持一致的布局和样式，自适应表单使 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">用主题来设计表单样式</a>。 转换服务使用在转换过程中应用的主题中指定的字体和字体样式。 您可以更改主题的字体和字体样式，为自适应表单的组件提供独特的外观。</p> <br>

1. **该服务是否会从基于XDP的表单中自动提取JavaScript并将其应用于相应的自适应表单？**
   <p>该服务不会自动将基于XFA的表单或Acro表单的脚本转换为相应的自适应表单规则。 您（表单作者）可以使用规则编 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">辑器</a> ，将交互性添加到自适应表单。</p> <br>

1. **某些表单对象无法正确转换为自适应表单组件。 如何解决此问题？**
   <p>自动表单转换服务是针对大量表单进行培训的。 但基于AI/ML的应用程序受其培训数据和模式的限制。 可能有多种字段类型、布局、模式和上下文，这些类型对人类的感知可以辨别，但是难以自动识别。 服务可能无法识别这些对象或可能识别错误。 您可以使用“ <a href="review-correct-ui-edited.md" target="_blank">审阅”和“正确编辑器</a> ”，在输入表单的纸质布局中进行必要的修改。</p> <br/>

1. **某些更正会跨表单重复。 该服务能否识别并修复所有此类实例，以便将来进行转换？**

   该服务可以持续地培训您的表单和模式。 它每天学习新模式。 尚未开始自动应用跨表单重复的校正。 请注意预发行表单，以便获得此类功能。 <br/><br/>

   您可以使用元模型将表单对象映射到您选择的自适应表单组件，并为这些组件预配置验证、规则、数据模式、帮助文本和辅助功能属性。 转换过程中将应用所有指定的属性。 您可以使用元模型将通用属性应用于字段。 它可以帮助您减少表单中的一些重复问题。<br/><br/>

1. **对于包含敏感数据(如个人识别信息(PII)信息)的表单，有哪些选项？**
该服务仅支持空白或未填写的表单。 请勿上传已填写的表单或包含个人识别信息(PII)的表单。 此外，删除源表单中预填的数据和白标PII、机密和专有信息。 <br/>

1. **页眉和页脚应放在何处？**
   <p>将页眉和页脚放在自适应表单模板中。 如果源PDF表单有页眉和页脚，则服务会在转换过程中检测检测到的页眉和页脚，并将其替换为自适应表单模板中可用的页眉和页脚。 如果自适应表单中包含任何额外的页眉或页脚，则可以使用“审阅”和“更正”编辑器来修复或删除此类页眉或页脚。 <a href="review-correct-ui-edited.md"></a></p> <br />

1. **与手动规划、创建资产（主题、模板）、创建和发布自适应表单相比，该服务可节省多少时间？**
   <p>时间长度取决于输入表单的大小和复杂性以及请求的数量。 与手动转换表单的过程相比，该服务打算以更快的速度将PDF表单转换为自适应表单，从而显着缩短实现价值的时间。 </p> <br />

1. **如果遇到与RSA库相关的错误，该怎么办？ 错误消息与下面提到的消息类似：** <br/>
   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` 未 <br>为RSA/BouncyCastle库配置引导委托时，会出现上述错误。 请执行以下步骤以解决问题：
   <p> </p>

   1. 停止AEM实例。 导览至文 `[AEM installation directory]\crx-quickstart\conf\` 件夹。 打开sling.properties文件进行编辑。 如果您使 `[AEM installation directory]\crx-quickstart\bin\start.bat` 用启动AEM实例，请编辑位于的sling.properties `[AEM_root]\crx-quickstart\`。
   1. 将以下属性添加到sling.properties文件：<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. 保存并关闭文件。 <br/>
   1. 启动AEM实例。<br/>
   <br/>

1. **如何自动更改自适应表单文本的大小写？**
   <p>您可以使用主题或样式编辑器中的自适应更改自适应表单字段的大小写。 例如，您可以打开主题编辑器并将表单中所有文本的大小写属性的值设置为大写、小写或camelCase。 您还可以使用主题编辑器中的“CSS覆盖”选项来创建不同类型的样式。</p>