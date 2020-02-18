---
title: 审阅和更正转换的表单
seo-title: 审阅和更正转换的表单
description: 查看并更正由自动表单转换服务转换的自适应表单。
seo-description: 查看并更正由自动表单转换服务转换的自适应表单
uuid: 5a0a6d24-dff6-4732-b607-24848b07b26d
topic-tags: forms
discoiquuid: f45ab2d7-5234-42d6-aeb6-b2cb1a7ce3c2
translation-type: tm+mt
source-git-commit: 3303c72b7d644dd183c036ba3cc48e629a9a503e

---


# 审阅和更正转换的表单{#review-and-correct-converted-forms}

AEM Forms Automated Forms Conversion服务标识输入PDF文档的字段、内容和布局，并将PDF文档转换为自适应表单。 输出自适应表单可能有一些缺失或未正确转换的字段。 您可以使用“审阅并更正”编辑器对已识别的字段进行改进，然后重新生成自适应表单以使输出更接近所需体验。 第一次转换后，您可以在编辑器中打开输入的PDF文档，以：

* 查看转换过程中标识的所有字段和内容
* 识别转换过程中遗漏的字段和内容
* 根据需要验证字段的类型并更改其类型
* 验证标识的表、调整列大小和修改单元格内容
* 删除错误标识的字段

进行所需的更改后，将PDF表单重新发送到转换服务。 成功转换后，更新的资产（包括自适应表单和架构）将下载到您的AEM Forms实例。 您可以重复该过程，直到获得所需的体验。 ![](assets/stages-of-form-2.gif)

您需要Google Chrome、Mozilla FireFox或Microsoft edge浏览器才能使用审阅和正确的编辑器。 编辑器不支持Internet Explorer。

## 欢迎使用“审阅”和“正确的编辑器” {#welcome-to-review-and-correct-editor}

“审阅”和“正确”编辑器提供了易于使用的界面。 它具有以下组件：

* 内容浏览器：您可以使用内容浏览器更改元素的位置。 内容浏览器允许您拖放表单对象以更改其位置。 例如，在文本框前移动表。 它会相应地更改输出自适应表单的跳位顺序。
* 属性浏览器：它显示选定字段的属性。 您还可以修改属性。
* 工具栏：工具栏位于编辑器的顶部。 它显示用于添加、修改、分组、取消分组和删除字段的工具。
* 打开属性：点击图标时，将显示打开属性 ![](assets/properties.png) 选项。 您可以单击打开属性以打开表单属性并查看其他选项。
* “筛选”按钮：过滤器按 ![](assets/toggle_eye.png) 钮位于编辑器顶部。 它允许您过滤字段以仅显示文本、字段、选择组、面板或所有组件。
* 保存按钮：该 **[!UICONTROL Save]** 按钮位于编辑器的右上角。 您还可以使用“保存”按钮旁边的箭头查看用于发送表单以进行转换的选项。

* PDF表单：编辑器显示源PDF文档，并将其与标识的字段叠加。 您可以使用工具栏中的工具修改字段。
* 页面：源表单可以包含多个页面。 编辑器在右上角提供一个按钮，用于在页面之间导航。

![查看和更正UI](assets/reviewcorrectui.png)

**************答：内容浏**&#x200B;览器B。属性浏览 **器C.** 工具 **栏D。属性按**&#x200B;钮E。过滤器按 **钮F。保存按**&#x200B;钮G。PDF表单已覆盖已识别的字段

第一次成功转换后，转换服务将叠加源PDF文档以及标识的字段和组件。 这些字段或组件的类型为：文本、字段、面板、选择组和表：

* 文本：源PDF文档中的纯文本。 例如，上面显示的图像中的贷款申请文本。
* 字段：与值或输入框关联的文本或图标标签的组合。 例如，上图中的第一个字段名称。 它具有文本标签和输入框。 字段支持文本、数字、下拉列表、日期、电子邮件、电话号码、签名、货币和密码数据类型。
* 面板：内容和组件的逻辑集合。 例如，上图中“人员1”和“人员2”面板的“个人详细信息”。
* 选择组：与多种选择选项关联的文本组合：按钮。 例如，上图中的“婚姻状态”和“现有客户”。\
   转换服务基于选择组标题及其多选选项，将选择组自动转换为单选单选按钮或多选复选框。 例如，如果存在“选择任意一个 **”作为选择组标题，或者“多选”选项允许您仅选择一个选项(** Yes **or** No ****)，则转换服务会自动将选择的组转换为单选单选按钮。 同样，如果存在“选择全部应用 **”或“选择多个****** ”作为选择组标题，或者“多选”选项允许您选择多个选项，则转换服务会自动将选择组转换为多选复选框。

* 表：包含以列和行表示的信息的2-d表。 可以向表中添加或删除行或列。

## 开始查看转化 {#start-reviewing-a-conversion}

第一次成功转换后，转换服务将叠加源PDF文档以及标识的字段和组件。 您可以对已识别的字段进行改进，并重新生成自适应表单，使输出更接近所需体验。 只有在第一次成功转化后，才可以开始查看转化。

### Before you start {#before-you-start}

* “审阅”和“更正”编辑器不支持片段。 请勿使用编辑器来查看在转换过程中启用了“提取 **片段** ”选项的转换。 您可以使用自适 [应表单编辑器进行](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html) 此类转换。

* “审阅并更正”编辑器没有撤消操作。 仅使用“保存”按钮永久保存更改。

### 开始审阅 {#start-the-review}

要开始审核转换，请选择用于转换的源PDF文档，然后选择并点按审核转 **换**。 “审阅并更正”编辑器将在新选项卡中打开。 您可以开始查看转化率。 在开始修复任何其他问题之前，请执行以下基本检查：

![](assets/usingreviewandcorrecteditor.png)

1. **检查所有字段的类型**:转换服务可能为字段指定错误类型。 例如，为手机字段分配文本类型，而不是键入电话。 您可以将鼠标悬停在字段上以查找字段的类型。

   要更改字段的类型，请选择字段，打开属性浏览器，从下拉菜单中选择 **[!UICONTROL Type]** 一个值，然后点按 **[!UICONTROL Save]**。 类型已更改。

   ![](assets/check-typex75.gif)

1. **删除其他面板**:转换服务可以生成额外的面板。 例如，父面板中包含额外的子面板，空白空间转换为面板，复选框转换为面板。 查看所有面板的边界并删除其他面板。 您可以使用过滤器按 ![](assets/toggle_eye.png) 钮或内容浏览器查看所有面板。

   您可以删除或取消组合面板以将其删除。 使用删除选项时，面板的子字段或组件也会被删除：

   * 要删除面板，请选择该面板，然后点按工具栏 ![](assets/delete-icon.png) 中的删除图标。 在确认对话框中，点按 **[!UICONTROL Confirm]**。 点按 **[!UICONTROL Save]** 以保存更改。

   * 要取消组合面板，请选择面板，然后点按工具栏中的取消组合图标。 该面板将取消分组，取消分组面板的子字段将调整为父字段。 点按**[!UICONTROL Save]**以保存更改。

1. **创建文本的逻辑组**:验证所识别的文本是否完整和正确。 同时，文本逻辑上放在正确的面板或组中。 例如，在多列布局中，一个逻辑组的文本被放置到另一个组中。

   * 要查看文本的完整性和正确性，请使用筛选器按 ![](assets/toggle_eye.png) 钮仅查看文本，单击每个文本，并进行验证。 修复拼写、打字错误或语法问题（如果有）。

   * 要向表单中添加文本，请点按+按钮，点按 **[!UICONTROL Text]**。 绘制该框，打开属性浏览器，然后键入要添加到“内容”框的文本。

1. **** 查看表：确保标识表的所有边框。 同时，确保正确识别单元格的内容。

   * 要识别错过的边框，请使用 **[!UICONTROL Add Column]** 或选 **[!UICONTROL Add Row]** 项。

   * 要删除额外的边框，请使 **[!UICONTROL Delete Column]** 用或 **[!UICONTROL Delete Row]** 选项。

进行所需的更改后，点按 **[!UICONTROL Save & Convert]** 按钮以将PDF表单重新发送到转换服务。 每个字段被转换为相应的自适应字段组件。 转换后，更新的资产（包括自适应表单和架构）将下载到您的AEM Forms实例。 根据表单的复杂性，服务可能需要一些时间才能完成转换。

![保存和转换](assets/save-and-convert.png)

执行基本检查后，您可以查看表单以修复特定于您的组织的问题。 这些问题可能与添加缺失字段等相关。 您可以查看“使 [用审阅和更正编辑器工具](review-correct-ui-edited.md#use-the-review-and-correct-editor-tools) ”部分，了解编辑器为修复此类问题提供的所有工具。

您还可以确认几乎所有表单中出现的相同问题，并向Adobe报告此类模式。 使用“审阅并更正”编辑器，直到获得所需的体验。

## 使用“审阅”和“更正”编辑器工具 {#use-the-review-and-correct-editor-tools}

使用“审阅”和“正确”编辑器，您可以：

* [将组件添加到表单](review-correct-ui-edited.md#add-a-component-to-the-form)
* [添加或编辑表](review-correct-ui-edited.md)
* [更改组件类型](review-correct-ui-edited.md#change-type-a-component)

* [创建或删除面板](review-correct-ui-edited.md#create-or-remove-a-panel)
* [删除面板或组件](review-correct-ui-edited.md#delete-a-panel-or-component)
* [设置组件的属性](review-correct-ui-edited.md#set-properties-of-a-component)
* [发送表单以进行转换](review-correct-ui-edited.md#send-a-form-for-conversion)

### 将组件添加到表单 {#add-a-component-to-the-form}

转换服务可能无法识别打印表单的某些组件。 例如，在转换 **过程中，表单的** “出生日期”组件中未标识。 您可以使用 **+工具** 来帮助识别此类组件。 该工具允许您添加文本、字段、选择组、表和面板组件。

![](assets/add-component.gif)

要向表单中添加组件，请点按 **[!UICONTROL +]** 和点按 **[!UICONTROL Field]**。 绘制字段的框覆盖标签和输入框。 例如，上面的示例图像使用字段组件将“出生日期”标签和 **其下方的“值** ”框添加到表单中。 绘制框时，转换服务会标识字段的类型。 您可以根据需要从属性浏览器更改字段的类型。 创建组件后，打开属性浏览器，然后设置组件的属性。

点按 **[!UICONTROL Save]** 按钮以保存修改，或使用按 **[!UICONTROL Save & Convert]** 钮将PDF表单重新发送到转换服务。

### 添加或编辑表 {#addedittable}

转换可使表单元格的几个单元格、边界或内容不可见。 例如，表的行不被标识。 您可以使用“审阅并更正”编辑器来标识此类项目。 可以对表执行以下操作：

* 要选择表，请单击表的任意单元格。
* 要修改单元格的属性，如名称、标题或类型，请双击单元格。 您还可以双击单元格以修改内容，标记必填字段，然后选择其他属性。
* 要向表单添加／标识完全未识别的或新表，请使用该工 **[!UICONTROL +]** 具。
* 要调整表的单元格或行的大小，请单击表的空白区域，将指针悬停在行或列边界上，当光标指针发生变化时，选择并移动该边界。 调整大小后，单 **[!UICONTROL Done]** 击以提交更改。 可以按键放 **[!UICONTROL ESC]** 弃调整大小。

* 要添加或删除行或列，请选择表行中的单元格，然后从菜单中 **[!UICONTROL Add Row]**&#x200B;选择 **[!UICONTROL Add Column]**、 **[!UICONTROL Delete Row]**&#x200B;或 **[!UICONTROL Delete Column]** 选项 ![](assets/table_18x18.png) 。

* 要拆分表格的单元格，请从菜单 **[!UICONTROL Spilt Vertical]** 中选 **[!UICONTROL Split Horizontal]** 择或选 ![](assets/table_18x18.png) 项。

* 要合并表的单元格，请选择要合并的单元格，然后从表菜 **[!UICONTROL Merge Cells]** 单中选 ![](assets/table_18x18.png) 择选项。

### 更改组件类型 {#change-type-a-component}

转换服务可能会创建一些类型不正确的字段。 例如，在下图中，“性别 **”字段被错误地标识为“文** 本”字段 **** 。 此外，标签的内容不正确。 字段应为选择字段类型，标签应为“性别”。 要更改组件类型并更正其标签：

选择要转换、点按和点 ![](assets/smock_shuffle_18_n.svg) 按字段类型的字段。 该字段将转换为选定的字段类型。 字段只能转换为下表中列出的类型。 面板组件只能取消分组，而不能转换。

| **组件** | **转换为** |
|---|---|
| 文本 | 字段或选择组 |
| 字段 | 文本或选择组 |
| 选择组 | 文本或面板 |

转换后，打开属性浏览器，指定标签，并指定其他必需的属性。 点按 **[!UICONTROL Save]** 按钮以保存修改，或使用“保存并转换”按钮将PDF表单重新发送到转换服务。

### 创建或删除面板 {#create-or-remove-a-panel}

转换服务将打印表单的相关组件和内容聚合到面板。 例如，表单可以有一个地址面板，其中包含字段，如名称、出图号、区域、城市、州／省、邮政编码和国家／地区。 这些字段将分组在一个面板中。 表单可以包含多个面板。

转换服务可以创建具有与其他组件无关的组件的面板，或将相对组件留出面板。 您可以使用分组或取消分组工具修复这些面板：

* 要删除面板，请选择该面板，然后点按取消分组 ![取消分组](assets/ungroupX18.png)。 该面板会被删除，面板的子组件会移到父组件。 您还可以使用删 [除组件选项](review-correct-ui-edited.md#delete-a-panel-or-component) ，删除面板及其子项。

* 要创建面板，请使用Ctrl键（在Windows或Linux上）或Control键（在Mac上）选择相关组件，然后点按 ![组](assets/group.jpg) 以创建面板。 打开属性浏览器以指定面板的属性。

点按 **[!UICONTROL Save]** 按钮以保存修改，或使用按 **[!UICONTROL Save & Convert]** 钮将PDF表单重新发送到转换服务。

### 删除面板或组件 {#delete-a-panel-or-component}

转换服务可以识别某些不正确的面板或组件。 这些面板中的大多数组件都与之无关。 您可以删除此类面板或组件。

要删除面板或组件，请选择面板或组件，然后点按删除图 ![](assets/delete-icon.png) 标。 在确认对话框中，点按 **[!UICONTROL Confirm]**。 将删除选定的面板或组件。 删除面板时，面板的所有子项也会被删除。 可以使用Ctrl键（在Windows或Linux上）或Control键（在Mac上）选择多个组件或面板。

### 设置组件的属性 {#set-properties-of-a-component}

表单的每个组件都有一组属性，如名称、标题、类型。 要设置组件的属性，请选择组件，然后点按属性浏览器。 此时将显示所选组件的属性。 更改或设置属性。

点按 **[!UICONTROL Save]** 按钮以保存修改，或使用按 **[!UICONTROL Save & Convert]** 钮将PDF表单重新发送到转换服务。

### 发送表单以进行转换 {#send-a-form-for-conversion}

在“审阅”和“更正”编辑器中进行所有所需的更改后，可以重新发送表单以进行转换。 要发送表单以进行转换，请点按 **[!UICONTROL Save & Convert]**。 该文 **[!UICONTROL Sent for conversion label]** 件夹将应用于包含源文档的文件夹，并且更新的源表单将上传到Adobe I/O上运行的转换服务。

根据表单的复杂性，转换服务可能需要一些时间才能转换表单。 转换完成后，转换后的自适应表单和相关资产会下载到您的计算机。 转换完成后，您可以在编辑器中查看表单，并根据需要在自适应表单编辑器中打开自适应表单 [](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html) ，以进行最终的修复。

如果在自适应表单编辑器中更新表单后重新发送表单以进行转换，则自适应表单中所做的所有更改都将丢失。 只有在成功转换后，才能在审阅中打开表单并更正编辑器。

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
