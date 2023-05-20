---
title: 基于数据源的预填充和提交工作流建议（用于生成自适应表单）
seo-title: Prefill and submit options for adaptive forms
description: 針對使用Automated forms conversion服務產生的最適化表單，以資料來源為基礎的預填和提交工作流程。
seo-description: Data-source based prefill and submit workflows for adaptive forms generated using Automated Forms Conversion Service.
uuid: 91409a82-141c-4233-82b1-1539a0b250f8
contentOwner: khsingh
topic-tags: forms
discoiquuid: cad34fff-7f9f-4a27-8b5c-d0a523903eec
privatebeta: true
exl-id: 5deef8f5-5098-47c1-b696-b2db59e92931
source-git-commit: 1a3f79925f25dcc7dbe007f6e634f6e3a742bf72
workflow-type: tm+mt
source-wordcount: '2437'
ht-degree: 2%

---

# 基于数据源的预填充和提交工作流建议（用于生成自适应表单） {#recommended-data-source-btased-prefill-and-submit-workflows-for-adaptive-forms}

您可以透過Automated forms conversion服務轉換的最適化表單來使用下列任何資料來源：

* 表單資料模型、OData或任何其他協力廠商服務
* JSON結構
* XSD結構描述

根據資料來源，您可以選擇產生含有或不含資料模型的最適化表單。

本文說明在選取資料來源並使用轉換服務產生最適化表單後，要預先填入欄位值和提交選項的建議工作流程。

<table> 
 <tbody> 
  <tr> 
   <th><strong>数据源</strong></th> 
   <th><strong>建議的工作流程</strong></th> 
  </tr> 
  <tr> 
   <td><p>表單資料模型、OData或任何其他協力廠商服務</p></td> 
   <td> 
    <p><strong>選項1</strong>：您選取表單資料模型、OData或任何其他協力廠商服務作為資料來源。 您 <a href="#generate-adaptive-forms-with-no-data-binding">產生無資料繫結的最適化表單</a> 使用Automated forms conversion服務。 您可以手動將最適化表單欄位繫結至表單資料模型實體，並使用「表單資料模型預填服務」選項來預填欄位值。 您可以使用「使用表單資料模型提交」選項來提交最適化表單。</p></td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
   <p><strong>選項2</strong>：您選取表單資料模型、OData或任何其他協力廠商服務作為資料來源。 您 <a href="#generate-adaptive-forms-with-no-data-binding">產生無資料繫結的最適化表單</a> 使用Automated forms conversion服務。 您可以使用規則編輯器繫結最適化表單欄位以預填欄位值。 如有必要，請修改欄位值，並將資料提交到crx-repository。</p>
    </td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
    <p>如需執行這些工作流程的逐步指示，請參閱 <a href="#sqldatasource">使用資料庫、OData或任何協力廠商服務做為資料來源。</a></p> </td> 
  </tr>
  <tr>
  <td><p>JSON結構描述</p></td> 
   <td> 
    <p>您可以選取JSON結構描述作為資料來源。 根據選取的資料來源：</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>選項1</strong>：您 <a href="#generate-adaptive-forms-with-no-data-binding">產生無資料繫結的最適化表單</a> 使用Automated forms conversion服務並設定JSON結構描述作為資料來源。 您可以手動將最適化表單欄位繫結到JSON結構描述，並且 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">使用任何支援的通訊協定</a> 以預填欄位值。 如有必要，請修改欄位值，並將資料提交到crx-repository。</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>如需執行工作流程的逐步指示，請參閱 <a href="#jsondatasource">使用JSON結構描述作為資料來源。</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>選項2</strong>：您 <a href="#generate-adaptive-forms-with-json-binding">產生具有JSON資料繫結的最適化表單</a> 使用Automated forms conversion服務。 預填服務與表單提交功能可順暢運作。 您不需要任何設定步驟。</p> </td> 
  </tr>
   <tr>
  <td></td> 
   <td> 
    <p>如需執行工作流程的逐步指示，請參閱 <a href="#jsonwithdatabinding">使用JSON結構描述作為資料來源。</a></p> </td> 
  </tr>
  <tr>
  <td><p>XSD結構描述</p></td> 
   <td> 
    <p>選取XSD結構描述作為資料來源。 根據所選的資料來源，您 <a href="#generate-adaptive-forms-with-no-data-binding">產生無資料繫結的最適化表單</a> 使用Automated forms conversion服務並設定XSD結構描述作為資料來源。 您手動將最適化表單欄位繫結到XSD結構描述，並且 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">使用任何支援的通訊協定</a> 以預填欄位值。 如有必要，請修改欄位值，並將資料提交到crx-repository。</p>
    </td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>如需執行工作流程的逐步指示，請參閱 <a href="#xsddatasource">使用XSD結構描述作為資料來源。</a></p>
    </td> 
  </tr>
 </tbody> 
</table>


如需Automated forms conversion服務的詳細資訊，請參閱下列文章：

* [自动化表单转换服务简介](introduction.md)
* [配置自动化表单转换服务](configure-service.md)
* [将打印表单转换为自适应表单](convert-existing-forms-to-adaptive-forms.md)
* [审阅并修正转换后的表单](review-correct-ui-edited.md)

本文提供的資訊是根據以下假設，即任何閱讀者都具備調適型表單概念的基本知識。

## 先決條件 {#pre-requisites}

* 設定 [AEM作者執行個體](https://helpx.adobe.com/cn/experience-manager/6-5/sites/deploying/using/deploy.html)
* 設定 [在AEM編寫執行個體上Automated forms conversion服務](configure-service.md)

## 最適化表單範例 {#sample-adaptive-form}

若要執行使用案例以預先填入最適化表單中的欄位值並將它們提交至資料來源，請下載以下範例PDF檔案。

貸款申請表範例

[获取文件](assets/sample_loan_application_form.pdf)

PDF檔案可作為Automated forms conversion服務的輸入。 此服務會將此檔案轉換為最適化表單。 下圖以PDF格式說明範例貸款申請。

![貸款申請表範例](assets/sample_form_new.png)

## 為表單模型準備資料 {#prepare-data-for-form-model}

AEM Forms資料整合可讓您設定並連線至不同的資料來源。 使用轉換程式產生最適化表單後，您可以根據表單資料模型、XSD或JSON結構描述定義表單模型。 您可以使用資料庫、Microsoft Dynamics或任何其他協力廠商服務來建立表單資料模型。

本教學課程使用MySQL資料庫作為建立表單資料模型的來源。 建立 **loanapplication** 資料庫中的綱要並新增 **應徵者** 根據最適化表單中可用的欄位，將表格變更為結構描述。

![範例資料mysql](assets/sample_data_mysql.png)

您可以使用下列DDL陳述式來建立 **應徵者** 資料庫的資料表。

```sql
CREATE TABLE `applicant` (
   `name` varchar(45) DEFAULT NULL,
   `address` varchar(45) DEFAULT NULL,
   `phonenumber` int(11) NOT NULL,
   `email` varchar(45) DEFAULT NULL,
   `occupation` varchar(45) DEFAULT NULL,
   `annualsalary` varchar(45) DEFAULT NULL,
   `familymembers` int(11) DEFAULT NULL,
   PRIMARY KEY (`phonenumber`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

如果您使用XSD結構描述作為表單模型來執行使用案例，請建立包含以下文字的XSD檔案：

```xml
<?xml version="1.0" encoding="utf-8" ?>
    <xs:schema targetNamespace="http://adobe.com/sample.xsd"
                    xmlns="http://adobe.com/sample.xsd"
                    xmlns:xs="http://www.w3.org/2001/XMLSchema">

<xs:element name="sample" type="SampleType"/>

  <xs:complexType name="SampleType">
    <xs:sequence>
      <xs:element name="name" type="xs:string"/>
   <xs:element name="address" type="xs:string"/>
   <xs:element name="phonenumber" type="xs:int"/>
   <xs:element name="email" type="xs:string"/>
   <xs:element name="occupation" type="xs:string"/>
   <xs:element name="annualsalary" type="xs:string"/>
   <xs:element name="familymembers" type="xs:string"/>
 </xs:sequence>
  </xs:complexType>

  </xs:schema>
```

或將XSD結構描述下載至本機檔案系統。

範例貸款應用程式XSD結構描述

[获取文件](assets/loanapplication.xsd)

如需有關在最適化表單中使用XSD結構描述作為表單模型的詳細資訊，請參閱 [使用XML結構描述建立調適型表單](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-xml-schema-form-model.html).

如果您使用JSON結構描述作為表單模型來執行使用案例，請建立包含以下文字的JSON檔案：

```JSON
{
    "$schema": "http://json-schema.org/draft-04/schema#",
    "definitions": {
        "loanapplication": {
            "type": "object",
            "properties": {
                "name": {
                    "type": "string"
                },
                "address": {
                    "type": "string"
                },
    "phonenumber": {
                    "type": "number"
                },
    "email": {
                    "type": "string"
                },
    "occupation": {
                    "type": "string"
                },
    "annualsalary": {
                    "type": "string"
                },
    "familymembers": {
                    "type": "number"
                }
            }
        }
 },
 "type": "object",
    "properties": {
        "employee": {
            "$ref": "#/definitions/loanapplication"
        }
    }
}
```

或將JSON結構描述下載至本機檔案系統。

範例貸款應用程式JSON結構描述

[获取文件](assets/demo_schema.json)

如需有關在最適化表單中使用JSON結構描述作為表單模型的詳細資訊，請參閱 [使用JSON結構描述建立調適型表單](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html).

## 產生無資料繫結的最適化表單 {#generate-adaptive-forms-with-no-data-binding}

使用 [要轉換的Automated forms conversion服務](convert-existing-forms-to-adaptive-forms.md) 此 [貸款申請表範例](#sample-adaptive-form) 至沒有資料繫結的最適化表單。 請務必選取 **[!UICONTROL Generate adaptive form(s) without data bindings]** 核取方塊以產生無資料繫結的最適化表單。

![無資料繫結的最適化表單](assets/generate_af_without_binding.png)

產生無資料繫結的最適化表單後，請為最適化表單選取資料來源：

* [資料庫、OData或任何協力廠商服務](#sqldatasource)
* [JSON結構](#jsondatasource)
* [XSD結構描述](#xsddatasource)

>[!NOTE]
> 如果您使用Automated forms conversion服務轉換的最適化表單包含多個同名欄位，請確保這些欄位已繫結至資料來源實體，以避免在提交期間可能遺失資料。

### 使用資料庫、OData或任何協力廠商服務做為資料來源 {#sqldatasource}

使用案例：您可以使用Automated forms conversion服務產生無資料繫結的最適化表單，並將MYSQL資料庫設定為資料來源。 您可以手動將最適化表單欄位繫結到表單資料模型實體，並使用 **[!UICONTROL Form Data Model Prefill Service]** 預填欄位值的選項。 您使用 **[!UICONTROL Submit using Form Data Model]** 提交最適化表單的選項。

執行使用案例之前：

* [將MySQL資料庫設定為資料來源](https://helpx.adobe.com/experience-manager/6-5/forms/using/configure-data-sources.html#configurerelationaldatabase)
* [建立表單資料模型](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html)

根據使用案例，建立 **loanapplication** 表單資料模型並將讀取服務引數繫結到 **[!UICONTROL Literal]** 值。 電話號碼常值必須是中設定的其中一個記錄 **應徵者** MySQL資料庫的綱要。 服務會使用值作為引數，從資料來源擷取詳細資料。 您也可以選取 [使用者設定檔屬性或請求屬性](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html#bindargument) 從 **[!UICONTROL Binding To]** 下拉式清單

![設定表單資料模型](assets/configure_model_object.png)

>[!NOTE]
>
>確定您已新增 **get** 和 **插入** 服務至表單資料模型，在執行使用案例前設定及測試服務。

執行以下步驟：

1. 選取已轉換的 **貸款申請表範例** 可在 **[!UICONTROL output]** 資料夾並點選 **[!UICONTROL Properties]**.
1. 點選 **[!UICONTROL Form Model]** 索引標籤，選取 **[!UICONTROL Form Data Model]** 從 **[!UICONTROL Select From]** 下拉式清單，然後點選 **[!UICONTROL Select Form Data Model]** 以選取 **loanapplication** 表單資料模型。 點選 **[!UICONTROL Save & Close]** 以儲存表單。
1. 選取 **貸款申請表範例** 並點選 **[!UICONTROL Edit]**.
1. 在 **[!UICONTROL Content]** 索引標籤，點選「設定」圖示：

   ![設定表單容器](assets/configure_form_container.png)

   1. 在 **[!UICONTROL Basic]** 區段，選取 **[!UICONTROL Form Data Model Prefill service]** 從 **[!UICONTROL Prefill Service]** 下拉式清單。

   1. 在 **[!UICONTROL Submission]** 區段，選取 **[!UICONTROL Submit using Form Data Model]** 從 **[!UICONTROL Submit Action]** 下拉式清單。

   1. 使用選取資料模型 **[!UICONTROL Data Model to submit]** 欄位。
   1. 點選 ![完成圖示](assets/save_icon.svg) 以儲存屬性。

1. 點選「應徵者名稱」文字方塊並選取 ![設定圖示](assets/configure_icon.svg) （設定）。

   1. 在「繫結參考」欄位中，選取 **應徵者** > **名稱**，然後點選 ![完成圖示](assets/save_icon.svg) 以儲存屬性。 同樣地，為建立資料繫結 **地址**， **電話號碼**， **電子郵件**， **職業**， **年薪（以美元計）**、和 **否。 家屬成員** 具有表單資料模型實體的欄位。

   ![繫結參考](assets/bind_references.png)

1. 點選 **[!UICONTROL Preview]** 以檢視預先填寫的最適化表單欄位值。
1. 如有需要，請修改欄位值，並提交最適化表單。 欄位值會提交至MySQL資料庫。 您可以重新整理 **應徵者** 資料庫中的表格，以檢視表格中更新的值。

**使用案例：** 您可以使用Automated forms conversion服務產生無資料繫結的最適化表單，並將MYSQL資料庫設定為資料來源。 您可以使用規則編輯器繫結最適化表單欄位以預填欄位值。 如有必要，請修改欄位值，並將資料提交到crx-repository。

執行以下步驟以使用 [規則編輯器](https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html) 若要叫用表單資料模型服務以繫結最適化表單中的欄位和預填值：

1. 選取 **貸款申請表範例** 在 **[!UICONTROL output]** 資料夾並點選 **[!UICONTROL Edit]**.
1. 在 **[!UICONTROL Content]** 索引標籤，點選「設定」圖示：

   ![設定表單容器](assets/configure_form_container.png)

   在 **[!UICONTROL Basic]** 區段，選取 **[!UICONTROL Form Data Model Prefill service]** 從 **[!UICONTROL Prefill Service]** 下拉式清單。

1. 點選 **[!UICONTROL Applicant Name]** 文字方塊並點選 **[!UICONTROL Edit Rules]**.

   ![編輯規則以建立資料繫結](assets/edit_rules_bind_reference.png)

1. 點選 **[!UICONTROL Create]** 在「規則編輯器」頁面上。
1. 於 **[!UICONTROL Rule Editor]** 頁面：

   1. 選取「應徵者姓名」文字方塊的州。 例如， **[!UICONTROL is initialized]**，這會導致 **[!UICONTROL Then]** 當您在中轉譯表單時的條件 **[!UICONTROL Preview]** 模式。

   1. 在 **[!UICONTROL Then]** 區段，選取 **[!UICONTROL Invoke Service]** 從 **[!UICONTROL Select Action]** 下拉式清單。 Forms執行個體上的所有服務都會顯示在下拉式清單中。

   1. 選取 **[!UICONTROL Get]** 服務來自列出表單資料模型的區段。 輸入欄位隨即顯示 **電話號碼**，此為為定義的主索引鍵 **應徵者** 資料模型。 系統會根據此欄位擷取並預填輸出區段中欄位的最適化表單的值。

   1. 使用「輸出」區段，以表單資料模型實體建立最適化表單欄位的繫結。 例如，繫結 **[!UICONTROL Applicant Name]** 使用的最適化表單欄位 **名稱** 實體。

   1. 点击&#x200B;**[!UICONTROL Done]**。點選 **[!UICONTROL Done]** 再次在規則編輯器頁面上。

   ![用於繫結參考的規則編輯器](assets/rule_editor_bind_references.png)

1. 點選 **[!UICONTROL Preview]** 以檢視預先填寫的最適化表單欄位值。

   >[!NOTE]
   >
   >確保 **[!UICONTROL Return Array]** 下列專案的屬性設定為OFF **get** 與最適化表單關聯的表單資料模型中的服務屬性。

1. 如有需要，請修改欄位值，並提交最適化表單。 提交的資料可在crx-repository中的以下位置找到：

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### 使用JSON結構描述作為資料來源 {#jsondatasource}

**使用案例：** 您可以使用Automated forms conversion服務產生無資料繫結的最適化表單，並將JSON結構描述設定為資料來源。 您可以手動將最適化表單欄位繫結至JSON結構描述，並使用 **使用資料預覽** 預填欄位值的選項。 如有必要，請修改欄位值，並將資料提交到crx-repository。

在執行使用案例之前，請確定您具備：

* [符合JSON結構描述結構的有效JSON結構描述](#prepare-data-for-form-model)
* [無資料繫結的最適化表單](#generate-adaptive-forms-with-no-data-binding)

執行以下步驟：

1. 選取已轉換的 **貸款申請表範例** 可在 **輸出** 資料夾並點選 **[!UICONTROL Properties]**.
1. 點選 **[!UICONTROL Form Model]** 索引標籤，選取 **[!UICONTROL Schema]** 從 **[!UICONTROL Select From]** 下拉式清單，然後點選 **[!UICONTROL Select Schema]** 上傳 **demo.schema JSON** 結構描述儲存在本機檔案系統上。 點選 **[!UICONTROL Save & Close]** 以儲存表單。
1. 選取 **貸款申請表範例** 並點選 **[!UICONTROL Edit]**.
1. 點選「應徵者名稱」文字方塊並選取 ![設定圖示](assets/configure_icon.svg) （設定）。

   在「繫結參考」欄位中，選取 **應徵者** > **名稱**，然後點選 ![完成圖示](assets/save_icon.svg) 以儲存屬性。 同樣地，為建立資料繫結 **地址**， **電話號碼**， **電子郵件**， **職業**， **年薪（以美元計）**、和 **否。 家屬成員** 具有JSON結構描述實體的欄位。

1. 選取已轉換的 **貸款申請表範例** 可在 **[!UICONTROL output]** 資料夾並選取 **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   下載範例資料檔案</br>

   [获取文件](assets/json_data_file.txt)</br>

1. 如有需要，請修改欄位值，並提交最適化表單。 提交的資料可在crx-repository中的以下位置找到：

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### 使用XSD結構描述作為資料來源 {#xsddatasource}

**使用案例：** 您可以使用Automated forms conversion服務產生無資料繫結的最適化表單，並將XSD結構描述設定為資料來源。 您可以手動將最適化表單欄位繫結到XSD結構描述，並使用 **使用資料預覽** 以預填欄位值。 如有必要，請修改欄位值，並將資料提交到crx-repository。

在執行使用案例之前，請確定您具備：

* [符合XML結構描述結構的有效XSD結構描述](#prepare-data-for-form-model)
* [無資料繫結的最適化表單](#generate-adaptive-forms-with-no-data-binding)

執行以下步驟：

1. 選取已轉換的 **貸款申請表範例** 可在 **[!UICONTROL output]** 資料夾並點選 **[!UICONTROL Properties]**.
1. 點選 **[!UICONTROL Form Model]** 索引標籤，選取 **[!UICONTROL Schema]** 從 **[!UICONTROL Select From]** 下拉式清單，然後點選 **[!UICONTROL Select Schema]** 上傳 **loanapplication** XSD結構描述儲存在本機檔案系統上。 選取XSD架構的根元素並點選 **[!UICONTROL Save & Close]** 以儲存表單。
1. 選取 **貸款申請表範例** 並點選 **[!UICONTROL Edit]**.
1. 點選「應徵者名稱」文字方塊並選取 ![設定圖示](assets/configure_icon.svg) （設定）。
在「繫結參考」欄位中，選取 **應徵者** > **名稱**，然後點選 ![完成圖示](assets/save_icon.svg) 以儲存屬性。 同樣地，為建立資料繫結 **地址**， **電話號碼**， **電子郵件**， **職業**， **年薪（以美元計）**、和 **否。 家屬成員** 具有XSD結構描述實體的欄位。

1. 選取已轉換的 **貸款申請表範例** 可在 **輸出** 資料夾並選取 **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   下載範例資料檔案</br>

   [获取文件](assets/loan-application-data-xml-data.zip)</br>


1. 如有需要，請修改欄位值，並提交最適化表單。 提交的資料可在crx-repository中的以下位置找到：

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## 產生具有JSON繫結的最適化表單 {#generate-adaptive-forms-with-json-binding}

使用 [要轉換的Automated forms conversion服務](convert-existing-forms-to-adaptive-forms.md) 此 [貸款申請表範例](#sample-adaptive-form) 變更為具有資料繫結的最適化表單。 請確定您沒有選取 **[!UICONTROL Generate adaptive form(s) without data bindings]** 產生最適化表單時勾選此方塊。

![具有JSON繫結的最適化表單](assets/generate_af_with_data_bindings.png)

### 使用JSON結構描述作為資料來源 {#jsonwithdatabinding}

**使用案例：** 您可以使用Automated forms conversion服務產生具有JSON資料繫結的最適化表單。 預填服務與表單提交功能可順暢運作。 您不需要任何設定步驟。

在執行使用案例之前，請確定您已 [具有資料繫結的最適化表單](#generate-adaptive-forms-with-json-binding).

執行以下步驟：

1. 選取已轉換的 **貸款申請表範例** 可在 **[!UICONTROL output]** 資料夾並選取 **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   下載範例資料檔案</br>

   [获取文件](assets/loan_application_data_source_json_data_binding.txt)</br>

1. 如有需要，請修改欄位值，並提交最適化表單。 提交的資料可在crx-repository中的以下位置找到：

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## 將提交的最適化表單JSON資料轉換為XML格式 {#convert-submitted-adaptive-form-data-to-xml}

當您在最適化表單欄位中輸入值並提交時，crx-repository中的資料會以JSON格式提供。 您可以使用以下任一方法將格式的JSON資料轉換為XML [org.apache.sling.commons.json.xml](https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString) API或以下範常式式碼：

```
import org.apache.sling.commons.json.JSONException;
import org.apache.sling.commons.json.JSONObject;
import org.apache.sling.commons.json.xml.XML;
 
public class ConversionUtils {
 
    public static String jsonToXML(String jsonString) throws JSONException {
        //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
        //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
        //Note: Need to extract boundData part before converting to XML
        return XML.toString(new JSONObject(jsonString));
    }
}
```
