---
title: 审阅并修正转换后的表单
seo-title: 审阅并修正转换后的表单
description: 查看并更正由Automated forms conversion服务转换的自适应表单。
seo-description: 查看并更正由Automated forms conversion服务转换的自适应表单
uuid: 5a0a6d24-dff6-4732-b607-24848b07b26d
topic-tags: forms
discoiquuid: f45ab2d7-5234-42d6-aeb6-b2cb1a7ce3c2
exl-id: 64330fa2-aa9d-4ba4-96df-b75deed3e693
source-git-commit: 1a3f79925f25dcc7dbe007f6e634f6e3a742bf72
workflow-type: tm+mt
source-wordcount: '2536'
ht-degree: 0%

---

# 审阅并修正转换后的表单{#review-and-correct-converted-forms}

AEM FormsAutomated forms conversion服务可识别输入PDF文档的字段、内容和布局，并将PDF文档转换为自适应表单。 输出自适应表单可能有一些缺失或转换不正确的字段。 您可以使用审阅和更正编辑器对已识别的字段进行改进，并重新生成自适应表单，以使输出更接近所需体验。 首次转换后，您可以在编辑器中打开输入的PDF文档，以：

* 查看转化过程中标识的所有字段和内容
* 识别转化期间遗漏的字段和内容
* 验证字段的类型并更改其类型（如果需要）
* 验证已识别的表、调整列大小和修改单元格内容
* 删除错误标识的字段

进行所需的更改后，将PDF forms重新发送到转换服务。 成功转换后，更新的资产（包括自适应表单和架构）会下载到您的AEM Forms实例。 您可以重复该过程，直到获得所需的体验。![](assets/stages-of-form-2.gif)

您需要Google Chrome、Mozilla FireFox或Microsoft Edge浏览器才能使用审阅和正确的编辑器。 编辑器不支持Internet Explorer。

## 欢迎使用Review and Crort editor {#welcome-to-review-and-correct-editor}

“审阅和更正”编辑器提供了易于使用的界面。 它具有以下组件：

* 内容浏览器：您可以使用内容浏览器更改元素的位置。 内容浏览器允许您拖放表单对象以更改其位置。 例如，在文本框之前移动表。 它会相应地更改输出自适应表单的制表符顺序。
* 属性浏览器：它显示选定字段的属性。 您还可以修改属性。
* 工具栏：工具栏位于编辑器顶部。 它显示用于添加、修改、分组、取消分组和删除字段的工具。
* 打开属性：点按![](assets/properties.png)图标时，将显示打开属性选项。 您可以单击打开属性以打开表单属性并查看其他选项。
* 过滤器按钮：过滤器按钮![](assets/toggle_eye.png)位于编辑器顶部。 它允许您过滤字段以仅显示文本、字段、选择组、面板或所有组件。
* “保存”按钮：**[!UICONTROL Save]**&#x200B;按钮位于编辑器的右上角。 您还可以使用保存按钮旁边的箭头查看用于发送表单以进行转换的选项。

* PDF表单：编辑器显示源PDF文档，并将其叠加以标识的字段。 您可以使用工具栏中的工具修改字段。
* 页面：源表单可以有多个页面。 编辑器在右上角提供了一个按钮，用于在页面之间导航。

![查看和更正UI](assets/reviewcorrectui.png)

**A.** 内容浏览 **器B.** 属性浏览器 **C.** 工具栏 **D.** 属性按钮 **E.** 过滤器按钮 **F.** 保存按钮 **G.** PDF表单，其中已标识字段被覆盖

首次成功转换后，转换服务将叠加源PDF文档，其中包含已标识的字段和组件。 这些字段或组件的类型如下：文本、字段、面板、选择组和表：

* 文本：源PDF文档中的纯文本。 例如，上面显示的图像中的“贷款应用程序”文本。
* 字段：与值或输入框关联的文本或图标标签的组合。 例如，上图中的“名字”字段名称。 它有文本标签和一个输入框。 字段支持文本、数字、下拉列表、日期、电子邮件、电话号码、签名、货币和密码数据类型。
* 面板：内容和组件的逻辑集合。 例如，上图中“人员1”和“人员2”面板的“个人详细信息”。
* 选择组：与多个选择选项关联的文本组合：复选框和单选按钮。 例如，上图中的“婚姻状态”和“现有客户”。\
   转换服务根据选择组标题及其多选选项，自动将选择组转换为单选单选按钮或多选复选框。 例如，如果存在&#x200B;**选择任意**&#x200B;作为选择组标题或多选选项，则允许您仅选择一个选项&#x200B;**是**&#x200B;或&#x200B;**否**，则转换服务会自动将选择组转换为单选单选按钮。 同样，如果存在&#x200B;**选择所有应用**&#x200B;或&#x200B;**选择多个**&#x200B;作为选择组标题或多选选项允许您选择多个选项，则转换服务会自动将选择组转换为多选复选框。

* 表：一个二维表，其中包含以列和行表示的信息。 可以向表中添加或删除行或列。

## 开始审核转化{#start-reviewing-a-conversion}

首次成功转换后，转换服务将叠加源PDF文档，其中包含已标识的字段和组件。 您可以对已识别的字段进行改进并重新生成自适应表单，以获得更接近所需体验的输出。 只有在首次成功转化后，才能开始查看转化。

### 开始之前{#before-you-start}

* 审阅和更正编辑器不支持片段。 请勿使用编辑器来查看在转化期间启用了&#x200B;**提取片段**&#x200B;选项的转化。 您可以使用[自适应表单编辑器](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)进行此类转换。

* “审阅”和“更正”编辑器没有撤消操作。 仅使用保存按钮永久保存更改。

### 开始审阅{#start-the-review}

要开始审核转化，请选择用于转化的源PDF文档，然后选择并点按&#x200B;**审核转化**。 在新选项卡中打开“审阅和更正”编辑器。 您可以开始审核转化。 在开始修复任何其他问题之前，请执行以下基本检查：

![](assets/usingreviewandcorrecteditor.png)

1. **检查所有字段的类型**:转换服务可能会为字段分配错误类型。例如，在移动电话字段中会分配类型文本，而不是类型电话。 您可以将鼠标悬停在字段上以查找字段类型。

   要更改字段类型，请选择字段，打开属性浏览器，从&#x200B;**[!UICONTROL Type]**&#x200B;下拉列表中选择值，然后点按&#x200B;**[!UICONTROL Save]**。 类型已更改。

   ![](assets/check-typex75.gif)

1. **删除其他面板**:转换服务可以生成额外的面板。例如，父面板中包含额外的子面板，空白空间转换为面板，复选框转换为面板。 查看所有面板的边界并移除额外的面板。 可以使用过滤器![](assets/toggle_eye.png)按钮或内容浏览器查看所有面板。

   您可以删除或取消组合面板以将其删除。 使用删除选项时，面板的子字段或组件也会被删除：

   * 要删除面板，请选择该面板，然后点按工具栏中的删除![](assets/delete-icon.png)图标。 在确认对话框中，点按&#x200B;**[!UICONTROL Confirm]**。 点按&#x200B;**[!UICONTROL Save]**&#x200B;以保存更改。

   * 要取消面板的组合，请选择面板，然后点按工具栏中的取消组合图标。 该面板是未分组的，未分组面板的子字段将调整为父字段。 点按**[!UICONTROL Save]**以保存更改。

1. **创建文本的逻辑组**:验证已识别的文本是否完整和正确。此外，在逻辑上，文本会放置在正确的面板或组中。 例如，在多列布局中，一个逻辑组的文本放置在另一个组中。

   * 要查看文本的完整性和正确性，请使用过滤器![](assets/toggle_eye.png)按钮仅查看文本，单击每个文本，然后进行验证。 修复拼写、拼写错误或语法问题（如果有）。

   * 要向表单中添加文本，请点按+按钮，然后点按&#x200B;**[!UICONTROL Text]**。 绘制框，打开属性浏览器，然后键入要添加到“内容”框的文本。

1. **查看表：** 确保标识表的所有边框。另外，还要确保正确识别单元格的内容。

   * 要识别缺少的边框，请使用&#x200B;**[!UICONTROL Add Column]**&#x200B;或&#x200B;**[!UICONTROL Add Row]**&#x200B;选项。

   * 要删除额外的边框，请使用&#x200B;**[!UICONTROL Delete Column]**&#x200B;或&#x200B;**[!UICONTROL Delete Row]**&#x200B;选项。

进行所需的更改后，点按&#x200B;**[!UICONTROL Save & Convert]**&#x200B;按钮以将PDF forms重新发送到转换服务。 每个字段都将转换为相应的自适应字段组件。 转换后，更新的资产（包括自适应表单和架构）会下载到您的AEM Forms实例。 根据表单的复杂性，服务可能需要一些时间才能完成转换。

![保存和转换](assets/save-and-convert.png)

执行基本检查后，您可以查看表单以修复特定于贵组织的问题。 这些问题可能与添加缺失字段等相关。 您可以查看[使用审阅和更正编辑器工具](review-correct-ui-edited.md#use-the-review-and-correct-editor-tools)部分，了解编辑器为解决此类问题提供的所有工具。

您还可以努力识别几乎所有表单中出现的相同问题，并将此类模式报告给Adobe。 在获得所需体验之前，请使用审阅和更正编辑器。

## 使用“审阅并更正”编辑器工具{#use-the-review-and-correct-editor-tools}

使用审阅和正确的编辑器，您可以：

* [将组件添加到表单](review-correct-ui-edited.md#add-a-component-to-the-form)
* [添加或编辑表](review-correct-ui-edited.md)
* [更改组件类型](review-correct-ui-edited.md#change-type-a-component)

* [创建或删除面板](review-correct-ui-edited.md#create-or-remove-a-panel)
* [删除面板或组件](review-correct-ui-edited.md#delete-a-panel-or-component)
* [设置组件的属性](review-correct-ui-edited.md#set-properties-of-a-component)
* [发送表单以进行转换](review-correct-ui-edited.md#send-a-form-for-conversion)

### 将组件添加到表单{#add-a-component-to-the-form}

转换服务可能无法识别打印表单的某些组件。 例如，在表单的&#x200B;**出生日期**&#x200B;组件中，转换期间未识别该组件。 您可以使用&#x200B;**+**&#x200B;工具帮助识别此类组件。 该工具允许您添加文本、字段、选择组、表和面板组件。

![](assets/add-component.gif)

要向表单中添加组件，请点按&#x200B;**[!UICONTROL +]** ，然后点按&#x200B;**[!UICONTROL Field]**。 绘制一个包含字段标签和输入框的框。 例如，上述示例图像使用字段组件将&#x200B;**出生日期**&#x200B;标签和值框添加到表单中。 绘制框时，转换服务会标识字段的类型。 您可以根据需要从属性浏览器中更改字段类型。 创建组件后，打开属性浏览器，然后设置组件的属性。

点按&#x200B;**[!UICONTROL Save]**&#x200B;按钮以保存修改或使用&#x200B;**[!UICONTROL Save & Convert]**&#x200B;按钮将PDF forms重新发送到转换服务。

### 添加或编辑表 {#addedittable}

转化可能会使表单元格的一些单元格、边界或内容未识别。 例如，表的行未被标识。 您可以使用“审阅并更正”编辑器来标识此类项目。 您可以对表执行以下操作：

* 要选择表，请单击表的任何单元格。
* 要修改单元格的属性（如名称、标题或类型），请双击单元格。 您还可以双击单元格以修改内容，标记必填字段，然后选择其他属性。
* 要在表单中添加/标识完全未识别或新表，请使用&#x200B;**[!UICONTROL +]**&#x200B;工具。
* 要调整单元格或表行的大小，请单击表的空区域，将鼠标悬停在行或列边界上，当光标指针发生更改时，选择并移动该边界。 调整大小后，单击&#x200B;**[!UICONTROL Done]**&#x200B;以提交更改。 可以按&#x200B;**[!UICONTROL ESC]**&#x200B;键放弃调整大小。

* 要添加或删除行或列，请选择表行中的单元格，然后从![](assets/table_18x18.png)菜单中选择&#x200B;**[!UICONTROL Add Row]**、**[!UICONTROL Add Column]**、**[!UICONTROL Delete Row]**&#x200B;或&#x200B;**[!UICONTROL Delete Column]**&#x200B;选项。

* 要在表中拆分单元格，请从![](assets/table_18x18.png)菜单中选择&#x200B;**[!UICONTROL Spilt Vertical]**&#x200B;或&#x200B;**[!UICONTROL Split Horizontal]**&#x200B;选项。

* 要合并表的单元格，请选择要合并的单元格，然后从![](assets/table_18x18.png)表菜单中选择&#x200B;**[!UICONTROL Merge Cells]**&#x200B;选项。

### 更改组件{#change-type-a-component}的类型

转换服务可能会创建某些类型不正确的字段。 例如，在下图中，**Gender**&#x200B;字段被错误地标识为&#x200B;**Text**&#x200B;字段。 此外，标签的内容不正确。 字段应为选择的字段类型，标签应为“性别”。 要更改组件类型并更正其标签，请执行以下操作：

选择要转换的字段，点按![](assets/smock_shuffle_18_n.svg) ，然后点按字段类型。 字段将转换为选定的字段类型。 字段只能转换为下表中列出的类型。 只能对面板组件进行分组，而不能进行转换。

| **组件** | **转换为** |
|---|---|
| 文本 | 字段或选择组 |
| 字段 | 文本或选择组 |
| 选择组 | 文本或面板 |

转换后，打开属性浏览器，指定标签，并指定其他必需的属性。 点按&#x200B;**[!UICONTROL Save]**&#x200B;按钮以保存修改或使用保存并转换按钮将PDF forms重新发送到转换服务。

### 创建或删除面板{#create-or-remove-a-panel}

转换服务将打印表单的相关组件和内容聚合到面板。 例如，表单可以有一个地址面板，其中包含以下字段：名称、出图号、区域、城市、州、邮政编码和国家/地区。 这些字段将分组到一个面板中。 一个表单可以包含多个面板。

转换服务可以创建具有与其他组件无关的组件的面板，或将相对组件留出面板。 您可以使用组或取消组工具来修复此类面板：

* 要删除面板，请选择该面板，然后点按取消组![取消组](assets/ungroupX18.png)。 该面板会被删除，并且面板的子组件会移动到父组件。 您还可以使用[delete component](review-correct-ui-edited.md#delete-a-panel-or-component)选项删除面板及其子项。

* 要创建面板，请使用Ctrl键（在Windows或Linux上）或Control键（在Mac上）选择相关组件，然后点按![组](assets/group.jpg)以创建面板。 打开属性浏览器以指定面板的属性。

点按&#x200B;**[!UICONTROL Save]**&#x200B;按钮以保存修改或使用&#x200B;**[!UICONTROL Save & Convert]**&#x200B;按钮将PDF forms重新发送到转换服务。

### 删除面板或组件{#delete-a-panel-or-component}

转换服务可以识别一些不正确的面板或组件。 这些面板的大多数组件都与它们无关。 您可以删除此类面板或组件。

要删除面板或组件，请选择面板或组件，然后点按删除![](assets/delete-icon.png)图标。 在确认对话框中，点按&#x200B;**[!UICONTROL Confirm]**。 将删除选定的面板或组件。 删除面板时，该面板的所有子项也会被删除。 您可以使用Ctrl键（在Windows或Linux上）或Control键（在Mac上）选择多个组件或面板。

### 设置组件{#set-properties-of-a-component}的属性

表单的每个组件都有一组属性，如名称、标题、类型。 要设置组件的属性，请选择组件，然后点按属性浏览器。 此时会显示所选组件的属性。 更改或设置属性。

点按&#x200B;**[!UICONTROL Save]**&#x200B;按钮以保存修改或使用&#x200B;**[!UICONTROL Save & Convert]**&#x200B;按钮将PDF forms重新发送到转换服务。

### 发送表单进行转换{#send-a-form-for-conversion}

在审阅和更正编辑器中进行所有必需的更改后，您可以重新发送表单以进行转换。 要发送表单以进行转换，请点按&#x200B;**[!UICONTROL Save & Convert]**。 **[!UICONTROL Sent for conversion label]**&#x200B;将应用于包含源文档的文件夹，并且更新的源表单会上传到运行Adobe I/O的转换服务。

转换服务可能需要一些时间才能转换表单，具体取决于表单的复杂性。 转换完成后，转换后的自适应表单和相关资产会下载到您的计算机。 转换完成后，您可以在编辑器中查看表单，并根据需要在[自适应表单编辑器](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)中打开自适应表单以获取最终的修复集。

如果在自适应表单编辑器中更新表单后重新发送表单以进行转换，则在自适应表单中所做的所有更改都将丢失。 只有在成功转换后，才能在审阅中打开表单并更正编辑器。

<!--
Comment Type: draft

<h3>Open adaptive forms editor</h3>
-->

<!--
Comment Type: draft

<p>There can be instances where you require adaptive forms editor to make the changes like, applying a different theme to the form or fixing tables. Once you have made all the required changes in Review and Correct editor and converted the form, you can open your form in adaptive forms editor to make the final set of changes.</p>
<p>To open the form with adaptive forms editor, tap the <img src="assets/properties.png" /> icon, and tap <strong>Open Adaptive Form Editor</strong>. The form opens in adaptive form editor. </p>


## Previous {#previous}

[Use Automated Forms Conversion service](convert-existing-forms-to-adaptive-forms.md)
-->
