---
title: 已知问题
seo-title: Known Issues
description: automated forms conversion服務的已知問題和限制
seo-description: Before you begin using AEM Forms Automated Forms Conversion service, learn about the known issues and limitations of the service
uuid: b1dc661b-ccd3-457f-acbb-4bd25db86e1e
topic-tags: introduction
discoiquuid: 9cd2363c-47a0-46e9-98cd-1fe088b9cd6e
exl-id: 35f59e02-e38e-473a-94c8-123e0a85ac8e
source-git-commit: 47261710e6616c27c210ac53bffcc2387a06ea7a
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 1%

---

# 已知問題和限制 {#known-issues-limitations}

開始使用AEM FormsAutomated forms conversion服務之前，請檢閱下列已知問題和限制：

## 已知问题 {#known-issues}

* 包含轉換表單的資料夾的表單和頁面總數不應超過15個。 來源資料夾的大小不應超過10 MB。 請勿在來源資料夾中建立子資料夾。
* 某些表單物件很容易被肉眼看見，但是 [難以識別服務](styles-and-pattern-considerations-and-best-practices.md). 使用 [檢閱並修正編輯器](review-correct-ui-edited.md) 以識別及轉換這類表單物件。
* 檢閱並修正編輯器：

   * 沒有復原動作。 「儲存」按鈕會永久儲存變更。
   * 不支援XFA型表單的可重複面板。
   * 如果您使用「稽核並修正」編輯器修改表格中的清單，列寬不會自動調整，且文字可能會溢位到表格的下一列。
   * 此 **[!UICONTROL Auto-detect multi-column layout from input forms]** 功能無法用於檢閱和修正編輯器和表單片段。
   * 使用「稽核並修正」編輯器建立的手寫簽名無法載入已發佈的最適化表單。


* 對於XFA型表單：
   * 不支援從XFA型表單擷取片段。
   * 不支援XFA指令碼。 例如，自動為下拉式元件產生值的指令碼。
   * 中繼模型不適用於選擇群組
   * 無法識別含有單一字元的「選擇群組」選項
   * 當來原始檔是動態XFA (.XDP)並且它是 [定義最適化表單中XFA屬性的行為](https://helpx.adobe.com/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr)，則不會遵循來原始檔的presence屬性。 例如，來原始檔中的欄位標籤為隱藏，而指令碼使欄位可見，則欄位在輸出最適化表單中保持可見。

* 當您使用 **針對產生的最適化表單，使用輸入AcroForm作為記錄檔案(DoR)** 選項，請考量下列事項：

<table>
    <tr>
        <td>複合文字欄位的繫結和資料遺失。 複合文字欄位有多個文字方塊彼此對齊。 例如，在AcroForm中，信用卡號碼會分割成多個文字方塊，而每個文字方塊都有個別的繫結。 當AcroForm轉換為最適化表單時，轉換後的最適化表單具有適用於所有文字方塊的單一繫結。 做為因應措施，在將AcroForm轉換為最適化表單之前，請修改AcroForm以使用單一文字方塊來接受信用卡號碼。</td>
        <td><img  src="assets/creditCard_Composite.png"/>                                                            </td>
    </tr>
    <tr>
        <td>複合日期欄位的繫結和資料遺失。 複合日期欄位由三個不同的欄位組成。 例如，AcroForm中的出生日期欄位會分割為三個個別的欄位。 最適化表單提供現成的日期選擇器元件。 若要使用最適化表單的日期選擇器元件同時保留AcroForm的繫結，在將AcroForm轉換為最適化表單之前，請修改AcroForm以使用單一日期欄位。</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>如果核取方塊的大小大於隨附的文字，則不會偵測到核取方塊，且AcroForm中的繫結會遺失。 修改AcroForm，使核取方塊的大小小於隨附的文字。</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>如果輸入欄位未對齊對應的文字欄位，則不會偵測到輸入欄位。  </td>
        <td><img  src="assets/non-alingned-fields.png"/></td>
    </tr>
    <tr >
        <td>此服務會將AcroForm的所有核取方塊轉換為個別的選擇群組。 會建立個別的選擇群組以保留與AcroForm的繫結。 請勿在最適化表單中合併選擇群組。 這會導致連結遺失。 如果您合併選擇群組，請再次轉換表單以重新取得遺失的繫結。 </td>
        <td></td>
    </tr>
    <tr >
        <td>某些表格的邊界會延伸出自動產生的記錄檔案(DoR)中的頁面。 </td>
        <td></td>
    </tr>
</table>

## 限制 {#limitations}

* 不支援具有複雜動態版面的PDF forms、具有虛線外框的欄位或填滿的欄位。
* 無法識別影像內的影像和文字。 手動將影像新增至轉換後的表單。
* 不支援圖稿XDP檔案。
* 不支援超過15頁的PDF forms。
* 加密、密碼保護及安全檔案不會轉換。 執行轉換前，請先移除加密或密碼。
* 不支援複雜表格，例如無邊框表格、巢狀表格和具有預留位置值的表格。 轉換後，使用最適化表單編輯器新增或修改複雜表格。 僅支援具有空白欄位、適當標題和清除邊界的簡單表格。
* 此服務僅能將英文、法文、德文、西班牙文、義大利文和葡萄牙文的語言表單轉換為最適化表單。 您可以使用將已轉換的最適化表單翻譯成另一種語言 [AEM翻譯工作流程](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html).
* AEM 6.4 Forms不支援自動偵測輸入表單的多欄配置。
* 使用來源PDF表單中的顏色編碼的資訊不會轉存至最適化表單。
* 來源PDF表單的顏色不會移轉至最適化表單主題。
* 會將彩色PDF forms視為灰階表單，並據此偵測欄位。
