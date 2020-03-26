---
title: '将PDF表单转换为自适应表单 '
seo-title: '将PDF表单转换为自适应表单 '
description: 运行Automated Forms Conversion服务，将PDF表单转换为自适应表单
seo-description: 运行Automated Forms Conversion服务，将PDF表单转换为自适应表单
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
translation-type: tm+mt
source-git-commit: bcd55fa59f37b71b95b7cbfd80fcda368eaba408

---


# Convert PDF forms to adaptive forms {#convert-print-forms-to-adaptive-forms}

AEM Forms Automated Forms Conversion服务（由Adobe Sensei提供支持）可自动将PDF表单转换为适合设备的响应式自适应表单。 无论您是使用非交互式PDF表单、Acro Forms还是基于XFA的PDF表单，“自动表单转换”服务都可以轻松将这些表单转换为自适应表单。 有关功能、转换工作流程和入门信息的信息，请参 [阅自动表单转换服务](introduction.md) 。

## Pre-requisites {#pre-requisites}

* [**配置转换服务&#x200B;**](configure-service.md)

* **准备要应[用于转换](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html)的表单的模板：** 使用模板，您可以在所有自适应表单中应用一致的品牌。 此外，自动表单转换服务不提取和使用源PDF文档的页眉和页脚。 您可以使用自适应表单模板指定页眉和页脚。 在转换过程中，模板中指定的页眉和页脚将应用于自适应表单。

* **准备要应[用于转换](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html)的表单的主题:** 通过使用主题，您可以将一致的样式应用于组织的所有自适应表单。

## 开始转化过程 {#start-the-conversion-process}

在将AEM实例与AEM Forms Conversion Service连接后，您可以将PDF表单转换为自适应表单。 按列出的顺序执行以下步骤以转换表单：

* [将PDF表单上传到AEM Forms服务器](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [运行转换](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [查看并更正转换的表单](review-correct-ui-edited.md)

### 将PDF表单上传到AEM Forms服务器 {#upload-pdf-forms-to-your-aem-forms-server}

转换服务将AEM Forms实例中可用的PDF表单转换为自适应表单。 您可以根据需要一次性或分阶段上传所有PDF表单。 上传表单之前，请注意以下几点：

* 将表单数保留在小于15的文件夹中，将总页数保留在小于50的文件夹中。
* 将文件夹大小保持在10 MB以下。 请勿将表单保留在子文件夹中。
* 使表单中的页数保持在15以下。
* 请勿上传受保护的表单。 该服务不转换受口令保护和受保护的表单。
* 请勿上传文件名中包含空格的源表单。 在上传表单之前，从文件名中删除空格。
* 请勿上传 [PDF 产品组合](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)。 该服务无法将 PDF 产品组合转换为自适应表单。
* 阅读“已 [知问题](known-issues.md) ”和“最 [佳实践和注意事项](styles-and-pattern-considerations-and-best-practices.md) ”部分，并对表单进行建议的更改。

执行以下步骤，将要转换的表单上传到AEM Forms实例上的文件夹：

1. 登录到AEM Forms实例。

1. Tap **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. 点按 **[!UICONTROL Create]**> **[!UICONTROL Folder]**. 指 **定文件夹的** 标题 **** 和名称。 点按 **[!UICONTROL Create]**. 将创建文件夹。
1. 点按以打开新创建的文件夹。
1. 点按 **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. 选择要上传的表单，单 **[!UICONTROL Open]**&#x200B;击，然后单击 **[!UICONTROL Upload]**。 将上传表单。

### 运行转换 {#run-the-conversion}

上传表单并配置服务后，请执行以下步骤以开始转换：

1. 在AEM Forms实例中，点按转 **[!UICONTROL Adobe Experience Manager]** 换设 ![置对话框](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]**![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**。
1. 选择包含PDF表单（要转换的表单）的表单或文件夹，然后点按 **[!UICONTROL Start Automated Conversion]**。 将出 **[!UICONTROL Conversion Settings]** 现对话框。

   ![指定配置](assets/conversion-settings-dialog.png)

1. 在“转 **[!UICONTROL Basic]** 换设置”对话框的选项卡中：

   * **[!UICONTROL Select a cloud configuration]**. 选择配置时，已指定默认模板和主题。 您可以根据需要指定其他模板或主题。
   * 指定保存生成的自适应表单和相应模式的位置。 您可以使用默认路径或指定自定义路径。
   * 使用 **生成不带数据模型绑定的自适应表单** ，以选择是否要生成带有或不带数据模型绑定的自适应表单。
如果不选择此选项，转换服务会自动将自适应表单与JSON模式关联，并在自适应表单和JSON模式中可用的字段之间创建数据绑定。 该字 **[!UICONTROL Save generated data model schema at]** 段显示保存生成的JSON模式的默认位置。 您还可以自定义位置以保存生成的模式。
如果选择此选项，转换服务将生成一个没有数据模型绑定的自适应表单。 成功转换后，您可以将自适应表单与表单数据模型、XML模式或JSON模式关联。 有关详细信息，请参 [阅创建自适应表单](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html)。
   <!--
   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. 在“转换 **[!UICONTROL Additional]** 设置”对话框的选项卡中，
   * 选择该 **[!UICONTROL Extract fragment from adaptive forms]** 选项可让转换服务识别、提取和下载转换表单的表单片段。 当您选择该选 **[!UICONTROL Extract fragment from adaptive forms]** 项时，将启用指定用于保存提取的表单片段和相应表单片段模式的路径的选项。
   * 指定位置(如果您有 **[!UICONTROL existing adaptive form fragments]**&#x200B;一些基于JSON模式且模式的自适应表单片段较少)，并且您计划在自动生成的自适应表单中使用这些片段。 转换服务将可用的基于JSON模式的表单与输入PDF表单（仅限非交互式PDF表单）匹配，并且模式不太自适应的表单片段（如果有匹配项），则匹配的自适应表单片段将用于相应的自适应表单。
   >[!NOTE]
   >
   >
   > * 一次只能使 **[!UICONTROL  Extract Fragment]** 用 **[!UICONTROL Use existing adaptive form fragments]** 或选项。 不能同时使用这两个选项。
   > * 您只能对非 **[!UICONTROL Use existing adaptive form fragments]** 交互式PDF表单使用此选项。 尚不支持其他表单类型。
   > * 您只能使用绑定到JSON模式的未绑定片段或片段以及自动转换服务。 请勿使用XFA片段。 不支持XFA片段。


   * 选择该 **[!UICONTROL Auto-detect multi-column layout of input forms]** 选项可保留用于台式机和笔记本电脑等大屏幕的源表单的布局。 此选项在保留源表单的多列布局时很有帮助。 例如，当源PDF具有两列布局时，服务将生成一个输出自适应表单，该表单具有用于大屏幕显示的两列布局和用于诸如移动电话的小屏幕设备的单列布局。 该功能在数据源模式结构方面存在一些已知问题。 有关详细信息，请参 [阅已知问题文章](known-issues.md) 。
   * 默认情况下，服务为PDF表单的每页创建单独的顶级面板。 现在，您可以使用该选 **[!UICONTROL Auto-detect logical sections]** 项拖放页面级面板（基于页码的面板）并仅创建逻辑面板。 它还会将不属于任何部分的字段归为俱乐部，前面有逻辑部分，而后面有跨两个相邻页面的逻辑部分的字段则归入单个逻辑部分。 例如，如果某个逻辑部分的某些字段位于第1页的末尾，而某些字段位于第2页的开头，则所有此类字段都会汇集到一个逻辑部分中。

      >[!NOTE]
      > 您需要连接器包1.1.38或更高版本才能使用该 **[!UICONTROL Auto-detect logical sections]** 功能。



1. 点按 **[!UICONTROL Start Conversion]**. 转换即会启动。 转换进度显示在文件夹或表单上，直到转换进行。 转换完成后，消息将替换另一条状态消息（已转换、部分转换或转换失败）。 在转换完成时，还会在配置的电子邮件地址上发送状态电子邮件：

   * 成功转换后，转换后的自适应表单和相关模式将下载到转换对话框的选项卡 **[!UICONTROL Basic]** 中指定的路径。 仅当在开始转换之前选择了“提取片段”选项时，才下载表单片段和相应的模式。
   * 在转换失败时，如果所有输入表 **[!UICONTROL Conversion Failed]** 单都无法转换，或当所有输入表单中只有几个无法转换时 **[!UICONTROL Partially Failed]** ，显示消息，则显示消息。 将在配置的电子邮件地址上发 [送状态电子邮件](configure-service.md#configureemailnotification) ，并将错误记录到error.log文件。
   如果要将基于XFA的PDF表单转换为自适应表单，转换服务会将PDF表单自动关联到转换后的自适应表单，作为记录模板的文档。 转换后，您可以打开自适应表单属性以视图选项卡部分中记录模板 **[!UICONTROL Document of Record Template Configuration]** 的文档 **[!UICONTROL Form Model]** 情况。 </br>

   仅当您启用> **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** 选项时，转换服务才会将PDF表单自动上传到转换后的自适应表单作为“记录”模板的文档 **[!UICONTROL Generate Document of Record]** 。

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
   >如果转换过程需要60分钟以上，而PDF表单仍未转换为自适应表单，请在AEM Forms实例上创建新文件夹，将PDF表单上传到新创建的文件夹，然后重新开始转换。

## Review and correct the converted forms {#review-and-correct-the-converted-forms}

现实世界的表单具有复杂的数据捕获要求。 自动转换完成后，客户可以查看表单的转换质量并对表单进行必要的更新。 AEM Forms提供了一个审 [阅和正确的编辑器](review-correct-ui-edited.md) ，用于进行所需的更改。 它允许您改进表单字段的自动识别，并将已识别的字段从一种类型转换为另一种类型。 例如，您可以帮助识别表单的两列布局，并将自动标识为单选按钮的字段更改为多个选择字段。
