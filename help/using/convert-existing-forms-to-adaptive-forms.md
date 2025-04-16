---
title: 将PDF forms转换为自适应表单
description: 运行自动表单转换服务(AFCS)，将PDF forms转换为自适应表单
feature: Adaptive Forms, Foundation Components
role: Admin, Developer
level: Beginner, Intermediate
source-git-commit: 02e808d6d777078d148f073835e24fd20712eade
workflow-type: tm+mt
source-wordcount: '1783'
ht-degree: 8%

---

# 将PDF forms转换为自适应表单 {#convert-print-forms-to-adaptive-forms}

AEM Forms自动表单转换服务(AFCS)由Adobe Sensei提供支持，可自动将PDF forms转换为设备友好型且响应迅速的自适应表单<!--foundation and [core components](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction)-->。 无论您使用的是非交互式PDF forms、Acro Forms还是基于XFA的PDF forms，自动表单转换服务(AFCS)都可以轻松将这些表单转换为自适应表单。 有关功能、转换工作流和登录信息的信息，请参阅[自动表单转换](introduction.md)服务。

## 先决条件 {#pre-requisites}

* [**配置转换服务**](configure-service.md)

* **准备要应用于转换表单的[模板](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html)：**&#x200B;使用模板可以跨所有自适应表单应用一致的品牌。 此外，自动表单转换服务(AFCS)不提取和使用源PDF文档的页眉和页脚。 您可以使用自适应表单模板指定页眉和页脚。 在转换期间，模板中指定的页眉和页脚将应用于自适应表单。 在为模板创建文件夹时，请为所有人选择&#x200B;**[!UICONTROL Browse configurations]**&#x200B;选项。

* **准备要应用于转换表单的[主题](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html)：**&#x200B;使用主题可让您将一致的样式应用于组织的所有自适应表单。

* **（可选）** [**将源PDF forms转换为Adobe Sign表单**](frequently-asked-questions.md)

## 开始转换过程 {#start-the-conversion-process}

将AEM实例与AEM Forms转换服务连接后，可将PDF forms转换为自适应表单。 按照列出的顺序执行以下步骤以转换表单：

* [将PDF forms上传到AEM Forms服务器](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [运行转换](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [查看并更正转换后的表单](review-correct-ui-edited.md)

### 将PDF forms上传到AEM Forms服务器 {#upload-pdf-forms-to-your-aem-forms-server}

转换服务将AEM Forms实例上可用的PDF forms转换为自适应表单。 您可以根据需要一次性或分阶段上传所有PDF forms。 上传表单之前，请注意以下几点：

* 将文件夹中的表单数保持在15个以下，将文件夹中的总页数保持在50个以下。
* 将文件夹大小保持在10 MB以下。 不要将表单保留在子文件夹中。
* 将表单中的页数保持在15页以下。
* 请勿上传受保护的表单。 该服务无法转换受密码保护和受保护的表单。
* 请勿上载文件名中带有空格的源表单。 在上传表单之前，从文件名称中删除空格。
* 请勿上传 [PDF 产品组合](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)。 该服务无法将PDF Portfolio转换为自适应表单。
* 阅读[已知问题](known-issues.md)和[最佳实践和注意事项](styles-and-pattern-considerations-and-best-practices.md)部分，并对表单进行建议的更改。

执行以下步骤，上传要转换为AEM Forms实例上的文件夹的表单：

1. 登录到AEM Forms实例。
1. 点按&#x200B;**[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**。
1. 点按&#x200B;**[!UICONTROL Create]**> **[!UICONTROL Folder]**。 指定文件夹的&#x200B;**标题**&#x200B;和&#x200B;**名称**。 点击&#x200B;**[!UICONTROL Create]**。将创建一个文件夹。
1. 点按以打开新创建的文件夹。
1. 点按&#x200B;**[!UICONTROL Create]**> **[!UICONTROL File Upload]**。 选择要上载的表单，单击&#x200B;**[!UICONTROL Open]**，然后单击&#x200B;**[!UICONTROL Upload]**。 表单已上传。

### 运行转换 {#run-the-conversion}

上传表单并配置服务后，请执行以下步骤，以开始转换：

1. 在您的AEM Forms实例上，点按&#x200B;**[!UICONTROL Adobe Experience Manager]** ![转化设置对话框](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**。
1. 选择一个表单或包含PDF forms（要转换的表单）的文件夹，然后点按&#x200B;**[!UICONTROL Start Automated Conversion]**。 出现&#x200B;**[!UICONTROL Conversion Settings]**&#x200B;对话框。

   ![指定配置](assets/conversion-settings-dialog.png)

   **将PDF转换为自适应表单核心组件**

   <span class="preview"> 此功能属于 Early Adopter 计划。您可以使用官方电子邮件 ID 写信给 aem-forms-ea@adobe.com，加入早期采用者计划并申请使用该功能。</span>

   要将PDF forms转换为基于基础的表单，需要上述转换设置。 要将PDF表单转换为基于核心组件的自适应表单，请执行以下操作：

   1. 请确保已在您的AEM Forms实例上启用[核心组件](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction)。 如果未启用，您可以[在AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/adaptive-forms-core-components/enable-adaptive-forms-core-components)或[Cloud Service环境](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/enable-adaptive-forms-core-components)上启用核心组件。
   1. 选择基于[核心组件的自适应表单模板和主题](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components)，如下图所示：
      ![选择自适应表单模板](assets/select-af-template-1.png)。
   1. 点按&#x200B;**[!UICONTROL Start Conversion]**&#x200B;以将PDF转换为基于核心组件的表单。
   >[!NOTE]
   > * 数据绑定或数据模型架构等属性不适用于基于核心组件的自适应表单，但同样适用于基础组件。
   > * [对于基于核心组件的表单，无法查看并更正转换后的表单](#review-and-correct-the-converted-forms)。


1. 在“转换设置”对话框的&#x200B;**[!UICONTROL Basic]**&#x200B;选项卡中：

   * **[!UICONTROL Select a cloud configuration]**。选择配置时，已指定默认模板和主题。 如果需要，您可以指定其他模板或主题。
   * 指定用于保存生成的自适应表单和相应架构的位置。 您可以使用默认路径或指定自定义路径。
   * 使用&#x200B;**生成没有数据模型绑定的自适应表单**选项选择是否要生成具有或不具有数据模型绑定的自适应表单。
如果不选择此选项，转换服务会自动将自适应表单与JSON架构相关联，并在自适应表单中可用的字段与JSON架构之间创建数据绑定。 **[!UICONTROL Save generated data model schema at]**字段显示保存生成的JSON架构的默认位置。 您还可以自定义保存生成的架构的位置。
如果选择此选项，则转换服务会生成一个没有数据模型绑定的自适应表单。 成功转换后，您可以将自适应表单与表单数据模型、XML架构或JSON架构相关联。 有关详细信息，请参阅[创建自适应表单](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html)。

   <!--

   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. 在“转换设置”对话框的&#x200B;**[!UICONTROL Additional]**&#x200B;选项卡中，
   * 选择&#x200B;**[!UICONTROL Extract fragment from adaptive forms]**&#x200B;选项，以允许转换服务识别、提取和下载已转换表单的表单片段。 选择&#x200B;**[!UICONTROL Extract fragment from adaptive forms]**&#x200B;选项时，已启用用于指定保存提取的表单片段和相应表单片段架构的路径的选项。
   * 如果您有一些现有的基于JSON架构且架构较少的自适应表单片段，并且计划在自动生成的自适应表单中使用这些片段，请指定&#x200B;**[!UICONTROL existing adaptive form fragments]**&#x200B;的位置。 转换服务将基于JSON架构的可用和架构较少的自适应表单片段与输入PDF forms(仅限非交互式PDF forms)匹配，如果存在匹配，则匹配的自适应表单片段将在相应的自适应表单中使用。

   >[!NOTE]
   >
   >
   > * 您一次只能使用&#x200B;**[!UICONTROL  Extract Fragment]**&#x200B;或&#x200B;**[!UICONTROL Use existing adaptive form fragments]**&#x200B;选项。 不能同时使用这两个选项。
   > * 只能在非交互式PDF forms中使用&#x200B;**[!UICONTROL Use existing adaptive form fragments]**&#x200B;选项。 尚不支持其他表单类型。
   > * 您只能使用未绑定的片段或通过Automated Conversion Service绑定到JSON架构的片段。 请勿使用XFA片段。 不支持XFA片段。
   >

   * 选择&#x200B;**[!UICONTROL Auto-detect multi-column layout of input forms]**&#x200B;选项以保留桌面和笔记本电脑等大型屏幕的源表单布局。 选项有助于保留源表单的多列布局。 例如，当源PDF具有两列布局时，该服务将生成一个输出自适应表单，该表单具有适用于大屏幕显示器的两列布局和适用于手机等小屏幕设备的单列布局。 该功能在数据源架构结构中存在一些已知问题。 有关详细信息，请参阅[已知问题](known-issues.md)文章。
   * 默认情况下，该服务会为 PDF 表单每个页面单独创建顶层面板。 现在，您可以使用&#x200B;**[!UICONTROL Auto-detect logical sections]**&#x200B;选项不创建页面级别面板（基于页码的面板），而仅创建逻辑面板。 它还会将不属于任何之前逻辑部分的字段和跨页面逻辑部分的字段合并到一个逻辑部分中。 例如，如果某个逻辑部分的一部分字段位于第 1 页结尾而另一部分位于第 2 页开头，则所有此类字段会被合并到一个逻辑部分中。

     >[!NOTE]
     > 要使用&#x200B;**[!UICONTROL Auto-detect logical sections]**&#x200B;功能，需要安装连接器软件包1.1.38或更高版本。

* (仅限AEM Forms as a Cloud Service)[自动将部分转换为片段]选项适用于超过15页的PDF forms。 它将检测到的顶级部分转换为片段。 它还支持对所有创建的片段进行延迟加载。 它有助于提高转换表单的呈现速度，并使在自适应表单编辑器中加载大型表单变得更容易。

  >[!NOTE]
  > 在使用“自动将部分转换为片段”选项时，请勿使用响应式布局模板。
  > 使用审阅和修正编辑器将小面板合并到大面板。 它有助于减少转换后的自适应表单中的片段数。
  > 如果您遇到“调用次数过多”的例外情况，
  >
  > * 重新构建表单以创建简化的层次结构
  > * [将sling.max.calls参数]的值增加到足够高的数值，直到异常消失。
  > * [增加缓存的大小](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/configure-aem-forms/configure-adaptive-forms-cache.html)。 如果表单过于复杂，具有大量表格和多级别层次结构，则会发生该错误。

1. 点击&#x200B;**[!UICONTROL Start Conversion]**。转换已启动。 转换进度会显示在文件夹或表单上，直到转换正在进行为止。 转换完成后，该消息会被替换成其他状态消息（“已转换”、“已部分转换”或“转换失败”）。 转换完成后，还会向配置的电子邮件地址发送状态电子邮件：

   * 成功转换后，已转换的自适应表单和相关架构将下载到转换对话框的&#x200B;**[!UICONTROL Basic]**&#x200B;选项卡中指定的路径。 只有在开始转换之前选择了“提取片段”选项时，才会下载表单片段和相应的架构。
   * 在转换失败时，如果所有输入表单均无法转换，则显示&#x200B;**[!UICONTROL Conversion Failed]**&#x200B;消息；如果所有输入表单中只有少数表单无法转换，则显示&#x200B;**[!UICONTROL Partially Failed]**&#x200B;消息。 在[配置的电子邮件地址](configure-service.md#configureemailnotification)上发送状态电子邮件，并在error.log文件中记录错误。

   如果您将基于XFA的PDF表单转换为自适应表单，转换服务会自动将PDF表单与作为记录文档模板的已转换自适应表单相关联。 转换后，可打开自适应表单属性以在&#x200B;**[!UICONTROL Form Model]**&#x200B;选项卡的&#x200B;**[!UICONTROL Document of Record Template Configuration]**&#x200B;部分中查看记录文档模板。</br>

   仅当您启用&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]**&#x200B;选项时，转换服务才会将PDF表单自动上传到已转换的自适应表单作为记录文档模板。

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
   >如果转换过程需要60分钟以上的时间，并且PDF表单仍未转换为自适应表单，请在AEM Forms实例上创建文件夹，将PDF表单上传到新创建的文件夹，然后重新启动转换。

## 查看并更正转换后的表单 {#review-and-correct-the-converted-forms}

现实世界的表单具有复杂的数据捕获要求。 自动转换完成后，客户可以检查表单的转换质量，并对表单进行必要的更新。 AEM Forms提供了[审核和更正](review-correct-ui-edited.md)编辑器以进行所需更改。 它允许您改进表单字段的自动识别，并将识别的字段从一种类型转换为另一种类型。 例如，您可以帮助标识表单的双列布局，并将自动标识为单选按钮的字段更改为多个选择字段。
