---
title: '将PDF forms转换为自适应表单 '
seo-title: Convert PDF forms to adaptive forms
description: 运行Automated forms conversion服务，将PDF forms转换为自适应表单
seo-description: Run the Automated Forms Conversion service to convert PDF forms to adaptive forms
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
exl-id: 415e05b5-5a90-490c-bf7c-d3365ce95e24
source-git-commit: 5f07f5df6369007a491cf0873839f84a61827cb5
workflow-type: tm+mt
source-wordcount: '1631'
ht-degree: 6%

---

# 将PDF forms转换为自适应表单 {#convert-print-forms-to-adaptive-forms}

AEM FormsAutomated forms conversion服务由Adobe Sensei提供支持，可自动将您的PDF forms转换为设备友好且响应迅速的自适应表单。 无论您使用的是非交互式PDF forms、Acro Forms还是基于XFA的PDF forms,Automated forms conversion服务都可以轻松地将这些表单转换为自适应表单。 有关功能、转化工作流和入门信息的信息，请参阅 [automated forms conversion](introduction.md) 服务。

## 先决条件 {#pre-requisites}

* [**配置转换服务**](configure-service.md)

* **准备 [模板](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html) 要应用于已转换的表单：** 通过使用模板，您可以在所有自适应表单中应用一致的品牌策略。 此外，Automated forms conversion服务不提取和使用源PDF文档的页眉和页脚。 您可以使用自适应表单模板来指定页眉和页脚。 在转换期间，模板中指定的页眉和页脚将应用于自适应表单。 为模板创建文件夹时，请选择 **[!UICONTROL Browse configurations]** 选项。

* **准备 [主题](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html) 要应用于已转换的表单：** 通过使用主题，您可以对组织的所有自适应表单应用一致的样式。

* **（可选）** [**将源PDF forms转换为Adobe Sign表单**](frequently-asked-questions.md)

## 启动转化过程 {#start-the-conversion-process}

将AEM实例与AEM Forms转换服务连接后，您可以将PDF forms转换为自适应表单。 按所列顺序执行以下步骤以转换表单：

* [将PDF forms上传到AEM Forms服务器](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [运行转化](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [查看并更正转换后的表单](review-correct-ui-edited.md)

### 将PDF forms上传到AEM Forms服务器 {#upload-pdf-forms-to-your-aem-forms-server}

转换服务可将AEM Forms实例上可用的PDF forms转换为自适应表单。 您可以根据需要一次或分阶段上传所有PDF forms。 上传表单之前，请注意以下几点：

* 将文件夹中的表单数量保留在15个以下，将文件夹中的总页数保留在50个以下。
* 将文件夹的大小保持在10 MB以下。 请勿将表单保留在子文件夹中。
* 使表单中的页数少于15页。
* 请勿上载受保护的表单。 该服务无法转换受密码保护和受保护的表单。
* 请勿上载文件名中带空格的源表单。 在上传表单之前，从文件名中删除空格。
* 请勿上传 [PDF 产品组合](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)。 服务不会将PDFPortfolio转换为自适应表单。
* 阅读 [已知问题](known-issues.md) 和 [最佳实践和注意事项](styles-and-pattern-considerations-and-best-practices.md) ，并对表单进行建议的更改。

执行以下步骤，将要转换的表单上传到AEM Forms实例上的文件夹：

1. 登录到AEM Forms实例。

1. 点按 **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. 点按 **[!UICONTROL Create]**> **[!UICONTROL Folder]**. 指定 **标题** 和 **名称** 的子菜单。 点击&#x200B;**[!UICONTROL Create]**。随即会创建文件夹。
1. 点按以打开新创建的文件夹。
1. 点按 **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. 选择要上传的表单，单击 **[!UICONTROL Open]**，然后单击 **[!UICONTROL Upload]**. 表单已上传。

### 运行转化 {#run-the-conversion}

上传表单并配置服务后，请执行以下步骤以开始转换：

1. 在您的AEM Forms实例上，点按 **[!UICONTROL Adobe Experience Manager]** ![“转化设置”对话框](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. 选择包含PDF forms（要转换的表单）的表单或文件夹，然后点按 **[!UICONTROL Start Automated Conversion]**. 的 **[!UICONTROL Conversion Settings]** 对话框。

   ![指定配置](assets/conversion-settings-dialog.png)

1. 在 **[!UICONTROL Basic]** 选项卡：

   * **[!UICONTROL Select a cloud configuration]**. 选择配置时，已指定默认模板和主题。 您可以根据需要指定其他模板或主题。
   * 指定保存生成的自适应表单和相应架构的位置。 您可以使用默认路径或指定自定义路径。
   * 使用 **生成不带数据模型绑定的自适应表单** 选项，以选择是否要生成具有或不具有数据模型绑定的自适应表单。
如果未选择此选项，则转换服务会自动将自适应表单与JSON架构关联，并在自适应表单和JSON架构中可用的字段之间创建数据绑定。 的 **[!UICONTROL Save generated data model schema at]** 字段中显示保存生成的JSON架构的默认位置。 您还可以自定义保存生成架构的位置。
如果选择此选项，转换服务将生成一个没有数据模型绑定的自适应表单。 成功转换后，您可以将自适应表单与表单数据模型、XML架构或JSON架构相关联。 有关更多信息，请参阅 [创建自适应表单](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html).

   <!--

   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. 在 **[!UICONTROL Additional]** 选项卡，
   * 选择 **[!UICONTROL Extract fragment from adaptive forms]** 选项，以便转换服务识别、提取和下载已转换表单的表单片段。 当您选择 **[!UICONTROL Extract fragment from adaptive forms]** 选项，则会启用用于指定路径以保存提取的表单片段和相应的表单片段架构的选项。
   * 指定的位置 **[!UICONTROL existing adaptive form fragments]**，但前提是您现有一些基于JSON架构的表单片段和架构较不自适应的表单片段，并且您计划在自动生成的自适应表单中使用这些片段。 转换服务将可用的基于JSON架构的表单片段和模式较不自适应表单片段与输入PDF forms(仅限非交互式PDF forms)进行匹配，如果存在匹配项，则匹配的自适应表单片段将在相应的自适应表单中使用。

   >[!NOTE]
   >
   >
   > * 您只能使用 **[!UICONTROL  Extract Fragment]** 或 **[!UICONTROL Use existing adaptive form fragments]** 中。 不能同时使用这两个选项。
   > * 您可以使用 **[!UICONTROL Use existing adaptive form fragments]** 选项。 尚不支持其他表单类型。
   > * 您只能使用通过自动转换服务绑定到JSON架构的未绑定片段或片段。 请勿使用XFA片段。 不支持XFA片段。


   * 选择 **[!UICONTROL Auto-detect multi-column layout of input forms]** 用于为台式机和笔记本电脑等大屏幕保留源表单布局的选项。 此选项有助于保留源表单的多列布局。 例如，当源PDF具有两列布局时，该服务将生成一个输出自适应表单，该表单具有用于大屏幕显示的两列布局和用于诸如移动电话之类的小屏幕设备的单列布局。 该功能在数据源模式结构中存在一些已知问题。 有关详细信息，请参阅 [已知问题](known-issues.md) 文章。
   * 默认情况下，该服务会为 PDF 表单每个页面单独创建顶层面板。 现在，您可以使用 **[!UICONTROL Auto-detect logical sections]** 不创建页面级面板（基于页码的面板）和仅创建逻辑面板的选项。 它还会将不属于任何之前逻辑部分的字段和跨页面逻辑部分的字段合并到一个逻辑部分中。 例如，如果某个逻辑部分的一部分字段位于第 1 页结尾而另一部分位于第 2 页开头，则所有此类字段会被合并到一个逻辑部分中。

      >[!NOTE]
      > 您需要连接器软件包1.1.38或更高版本才能使用  **[!UICONTROL Auto-detect logical sections]** 功能。


* (仅AEM Formsas a Cloud Service) [自动将区域转换为片段] 选项适用于页面数超过15的PDF forms。 它将检测到的顶级部分转换为片段。 它还为所有创建的片段启用延迟加载。 它有助于提高已转换表单的渲染速度，并且更便于在自适应表单编辑器中加载大型表单。

   >[!NOTE]
   > 使用自动将区域转换为片段选项时，请勿使用响应式布局模板。
   > 使用审阅和正确的编辑器将小面板合并为大面板。 这有助于减少转换后的自适应表单中的片段数。
   > 如果您遇到“调用过多”例外，
   >
   > * 重构表单以创建简化的层次结构
   > * [增加sling.max.calls参数的值]到足够高的数字，直到异常消失。
   > * [增加缓存大小](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/configure-aem-forms/configure-adaptive-forms-cache.html). 如果表单过于复杂、表数量大、层次结构多，则会出错。


1. 点击&#x200B;**[!UICONTROL Start Conversion]**。转换即会开始。 在转换进行之前，文件夹或表单上会显示转换进度。 转换完成后，该消息将被替换另一个状态消息（已转换、已部分转换或转换失败）。 在完成转换后，还会在配置的电子邮件地址上发送状态电子邮件：

   * 成功转换后，转换后的自适应表单和相关架构将下载到 **[!UICONTROL Basic]** 选项卡。 仅当在开始转换之前选择了提取片段选项时，才会下载表单片段和相应的架构。
   * 在转换失败时， **[!UICONTROL Conversion Failed]** 如果所有输入表单无法转换或 **[!UICONTROL Partially Failed]** 当只有少数输入表单无法转换时，会显示消息。 系统会在 [已配置的电子邮件地址](configure-service.md#configureemailnotification) 错误记录到error.log文件。

   如果您要将基于XFA的PDF表单转换为自适应表单，则转换服务会自动将PDF表单与转换后的自适应表单关联为记录文档模板。 转换后，您可以打开自适应表单属性，以在 **[!UICONTROL Document of Record Template Configuration]** 部分 **[!UICONTROL Form Model]** 选项卡。 </br>

   仅当您启用了 **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** 选项。

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
   >如果转换过程需要超过60分钟，且PDF表单仍未转换为自适应表单，请在AEM Forms实例上创建文件夹，将PDF表单上传到新创建的文件夹，然后重新启动转换。

## 查看并更正转换后的表单 {#review-and-correct-the-converted-forms}

现实世界的表单具有复杂的数据捕获要求。 自动化转换完成后，客户可以查看表单的转换质量并对表单进行必要的更新。 AEM Forms提供 [审阅和更正](review-correct-ui-edited.md) 编辑器进行所需的更改。 利用该功能，可改进表单字段的自动识别功能，并将已识别的字段从一种类型转换为另一种类型。 例如，您可以帮助识别表单的两列布局，并将自动标识为单选按钮的字段更改为多个选项字段。
