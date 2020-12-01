---
title: '将PDF forms转换为自适应表单 '
seo-title: '将PDF forms转换为自适应表单 '
description: 运行Automated forms conversion服务，将PDF forms转换为自适应表单
seo-description: 运行Automated forms conversion服务，将PDF forms转换为自适应表单
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
translation-type: tm+mt
source-git-commit: c4f0d07b38cdb6aa162a0b61abe12fe9d1677a8c
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 6%

---


# 将PDF forms转换为自适应表单{#convert-print-forms-to-adaptive-forms}

AEM FormsAutomated forms conversion服务由Adobe Sensei提供支持，可自动将您的PDF forms转换为适合设备的响应式自适应表单。 无论您是使用非交互式PDF forms、AcroFormsPDF forms还是基于XFA的，Automated forms conversion服务都可以轻松地将这些表单转换为自适应表单。 有关功能、转换工作流和入门信息的信息，请参阅[Automated forms conversion](introduction.md)服务。

## 先决条件{#pre-requisites}

* [**配置转换服务**](configure-service.md)

* **准备要应 [](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html) 用于转换表单的模板：使** 用模板，您可以在所有自适应表单上应用一致的品牌。此外，Automated forms conversion服务不提取和使用源PDF文档的页眉和页脚。 您可以使用自适应表单模板指定页眉和页脚。 在转换过程中，模板中指定的页眉和页脚将应用于自适应表单。 为模板创建文件夹时，请为每个人选择&#x200B;**[!UICONTROL Browse configurations]**&#x200B;选项。

* **准备要应 [](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html) 用于转换表单的主题：** 使用主题，您可以将一致的样式应用于组织的所有自适应表单。

* **（可选）将** [**源PDF forms转换为Adobe Sign表单**](frequently-asked-questions.md)


## 开始转换过程{#start-the-conversion-process}

将AEM实例与AEM Forms转换服务连接后，可以将PDF forms转换为自适应表单。 按列出顺序执行以下步骤以转换表单：

* [将PDF forms上传到您的AEM Forms服务器](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [运行转换](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [检查并更正转换的表单](review-correct-ui-edited.md)

### 将PDF forms上传到您的AEM Forms服务器{#upload-pdf-forms-to-your-aem-forms-server}

转换服务将AEM Forms实例上的可用PDF forms转换为自适应表单。 您可以根据需要一次性或分阶段上传所有PDF forms。 上传表单之前，请注意以下几点：

* 将文件夹中的表单数保留在15以下，将文件夹中的页面总数保留在50以下。
* 将文件夹大小保持在10 MB以下。 请勿将表单保留在子文件夹中。
* 以少于15的形式保留页数。
* 请勿上传受保护的表单。 服务不会转换受密码保护和受保护的表单。
* 请勿上传文件名中包含空格的源表单。 在上传表单之前，从文件名中删除空格。
* 请勿上传 [PDF 产品组合](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)。 服务不会将PDFPortfolio转换为自适应表单。
* 阅读[已知问题](known-issues.md)和[最佳实践和注意事项](styles-and-pattern-considerations-and-best-practices.md)部分，并对表单进行建议的更改。

请执行以下步骤，将要转换的表单上传到您的AEM Forms实例上的文件夹：

1. 登录AEM Forms实例。

1. 点按&#x200B;**[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**。
1. 点按 **[!UICONTROL Create]**> **[!UICONTROL Folder]**. 指定文件夹的&#x200B;**标题**&#x200B;和&#x200B;**名称**。 点按 **[!UICONTROL Create]**. 将创建文件夹。
1. 点按以打开新创建的文件夹。
1. 点按 **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. 选择要上传的表单，单击&#x200B;**[!UICONTROL Open]**，然后单击&#x200B;**[!UICONTROL Upload]**。 将上传表单。

### 运行转换{#run-the-conversion}

上传表单并配置服务后，请执行以下步骤来开始转换：

1. 在您的AEM Forms实例上，点按&#x200B;**[!UICONTROL Adobe Experience Manager]** ![转换设置对话框](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**。
1. 选择包含PDF forms（要转换的表单）的表单或文件夹，然后点按&#x200B;**[!UICONTROL Start Automated Conversion]**。 出现&#x200B;**[!UICONTROL Conversion Settings]**&#x200B;对话框。

   ![指定配置](assets/conversion-settings-dialog.png)

1. 在“转换设置”对话框的&#x200B;**[!UICONTROL Basic]**&#x200B;选项卡中：

   * **[!UICONTROL Select a cloud configuration]**. 选择配置时，已指定默认模板和主题。 您可以根据需要指定其他模板或主题。
   * 指定保存生成的自适应表单和相应模式的位置。 可以使用默认路径或指定自定义路径。
   * 使用&#x200B;**生成不带数据模型绑定的自适应表单**选项，选择是否要生成带有或不带数据模型绑定的自适应表单。
如果不选择此选项，转换服务将自动将自适应表单与JSON模式关联，并在自适应表单和JSON模式中可用的字段之间创建数据绑定。 **[!UICONTROL Save generated data model schema at]**字段显示保存生成的JSON模式的默认位置。 您还可以自定义位置以保存生成的模式。
如果选择此选项，转换服务将生成一个没有数据模型绑定的自适应表单。 成功转换后，您可以将自适应表单与表单数据模型、XML模式或JSON模式关联。 有关详细信息，请参阅[创建自适应表单](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html)。

   <!--
   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. 在“转换设置”对话框的&#x200B;**[!UICONTROL Additional]**&#x200B;选项卡中，
   * 选择&#x200B;**[!UICONTROL Extract fragment from adaptive forms]**&#x200B;选项，使转换服务能够识别、提取和下载转换表单的表单片段。 选择&#x200B;**[!UICONTROL Extract fragment from adaptive forms]**&#x200B;选项时，将启用用于指定保存提取的表单片段和相应表单片段模式的路径的选项。
   * 如果您有一些现有的基于JSON模式且模式的自适应表单片段，并且计划在自动生成的自适应表单中使用这些片段，请指定&#x200B;**[!UICONTROL existing adaptive form fragments]**&#x200B;的位置。 转换服务将可用的基于JSON模式的和模式较少的自适应表单片段与输入PDF forms(仅非交互式PDF forms)匹配，如果存在匹配，则匹配的自适应表单片段将用于相应的自适应表单。

   >[!NOTE]
   >
   >
   > * 一次只能使用&#x200B;**[!UICONTROL  Extract Fragment]**&#x200B;或&#x200B;**[!UICONTROL Use existing adaptive form fragments]**&#x200B;选项。 不能同时使用这两个选项。
   > * 只能对非交互式PDF forms使用&#x200B;**[!UICONTROL Use existing adaptive form fragments]**&#x200B;选项。 尚不支持其他表单类型。
   > * 您只能使用绑定到自动转换服务的JSON模式的未绑定片段或片段。 请勿使用XFA片段。 不支持XFA片段。


   * 选择&#x200B;**[!UICONTROL Auto-detect multi-column layout of input forms]**&#x200B;选项可保留源表单在台式机和笔记本电脑等大屏幕中的布局。 此选项在保留源表单的多列布局时很有帮助。 例如，当源PDF具有两列布局时，服务将为大屏幕显示生成具有两列布局的输出自适应表单，为手机等小屏幕设备生成单列布局。 该功能在数据源模式结构方面存在一些已知问题。 有关详细信息，请参阅[known-issues](known-issues.md)文章。
   * 默认情况下，该服务会为 PDF 表单每个页面单独创建顶层面板。 现在，您可以使用&#x200B;**[!UICONTROL Auto-detect logical sections]**&#x200B;选项不创建页面级面板（基于页码的面板），而只创建逻辑面板。 它还会将不属于任何之前逻辑部分的字段和跨页面逻辑部分的字段合并到一个逻辑部分中。 例如，如果某个逻辑部分的一部分字段位于第 1 页结尾而另一部分位于第 2 页开头，则所有此类字段会被合并到一个逻辑部分中。

      >[!NOTE]
      > 您需要连接器软件包1.1.38或更高版本才能使用&#x200B;**[!UICONTROL Auto-detect logical sections]**&#x200B;功能。



1. 点按 **[!UICONTROL Start Conversion]**. 转换即会启动。 在转换进行之前，转换进度会显示在文件夹或表单上。 转换完成后，该消息将替换另一个状态消息（已转换、部分转换或转换失败）。 转换完成后，还会在配置的电子邮件地址上发送状态电子邮件：

   * 成功转换后，转换后的自适应表单和相关模式将下载到转换对话框的&#x200B;**[!UICONTROL Basic]**&#x200B;选项卡中指定的路径。 只有在开始转换之前选择了“提取片段”选项，才会下载表单片段和相应的模式。
   * 在转换失败时，如果所有输入表单都无法转换，则显示&#x200B;**[!UICONTROL Conversion Failed]**&#x200B;消息；如果只有少数几个输入表单无法转换，则显示&#x200B;**[!UICONTROL Partially Failed]**&#x200B;消息。 在[配置的电子邮件地址](configure-service.md#configureemailnotification)上发送状态电子邮件，并将错误记录到error.log文件。

   如果您要将基于XFA的PDF表单转换为自适应表单，转换服务会自动将PDF表单与转换的自适应表单关联为记录模板的文档。 转换后，您可以打开自适应表单属性，以视图&#x200B;**[!UICONTROL Form Model]**&#x200B;选项卡&#x200B;**[!UICONTROL Document of Record Template Configuration]**&#x200B;部分中记录模板的文档。</br>

   仅当启用&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]**&#x200B;选项时，转换服务才会将PDF表单作为记录模板的文档自动上传到转换后的自适应表单。

   <!--
   Comment Type: draft

   <note type="note">
   <p>By default, the adaptive form produces a JSON schema instead of XML schema on submission. JSON schema of a converted adaptive form is complaint with XML schema of an XFA-based form. You can use the <a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString">org.apache.sling.commons.json.xml API</a> to convert a JSON schema to XML schema. You can also use the following sample code for conversion:</p>
   <p><code class="code">import org.apache.sling.commons.json.JSONException;
   <discoiqbr /> import org.apache.sling.commons.json.JSONObject;
   <discoiqbr /> import org.apache.sling.commons.json.xml.XML;
   <discoiqbr />
   <discoiqbr /> public class ConversionUtils {
   <discoiqbr />
   <discoiqbr /> public static String jsonToXML(String jsonString) throws JSONException {
   <discoiqbr /> //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
   <discoiqbr /> //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
   <discoiqbr /> //Note: Need to extract boundData part before converting to XML
   <discoiqbr /> return XML.toString(new JSONObject(jsonString));
   <discoiqbr /> }
   <discoiqbr /> }</code><br /> </p>
   </note>
   -->

   >[!NOTE]
   >
   >如果转换过程需要60分钟以上，而PDF表单仍未转换为自适应表单，请在AEM Forms实例上创建一个文件夹，将PDF表单上传到新创建的文件夹，然后重新开始转换。

## 查看并更正转换后的表单{#review-and-correct-the-converted-forms}

现实世界的表单具有复杂的数据捕获要求。 自动转换完成后，客户可以检查表单的转换质量并对表单进行必要的更新。 AEM Forms提供[评论和正确的](review-correct-ui-edited.md)编辑器以进行所需的更改。 它允许您改进表单字段的自动识别，并将已识别的字段从一种类型转换为另一种类型。 例如，您可以帮助识别表单的两列布局，并将自动标识为单选按钮的字段更改为多个选择字段。
