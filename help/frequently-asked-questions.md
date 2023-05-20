---
title: 常见问题
seo-title: Frequently asked questions
description: 常見問答集或常見問題
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

1. **automated forms conversion服務支援哪個AEM Forms版本？**

   <p>automated forms conversion服務支援AEM 6.4 Forms和AEM 6.5 Forms。 它適用於OSGi上的AEM Forms和JEE上的AEM Forms。 您需要在AEM作者執行個體之上最新的AEM Forms附加元件套件，才能使用服務。 如需詳細指示，請參閱 <a href="configure-service.md">設定Automated forms conversion</a> 服務。</p> 
    <br>

1. **是否可以在內部部署安裝服務？**

   <p>Adobe會定期使用新資料集訓練Automated forms conversion服務的AI和ML演演算法，以提高轉換準確性。 更新後的演演算法會定期部署至Adobe Cloud上執行的轉換服務。 此服務的所有客戶都受益於更新的演演算法。 因此，雲端代管的中央部署最適合讓Automated forms conversion服務持續學習並提供改善給所有客戶。</p> 
    <p>此服務會將空白表單轉換為最適化表單。 此服務不支援填寫的表單以及從填寫的表單中擷取資料。 將表單傳送至服務進行轉換之前，請先從已填寫的表單中移除資料，並從表單中移除或允許列出專屬資訊</p> <br>

1. **此服務是否支援所有格式的PDF forms？ 支援哪些所有語言？**

   <p>此服務可將非互動式PDF forms、XFA型XDP和PDF forms以及AcroForms轉換為最適化表單。 此服務不支援掃描或填寫的表單。 如需其他限制，請參閱 <a href="known-issues.md">已知問題</a> 文章。<br /> </p> 
    <p>我們定期新增對其他來源型別的支援。 保留 <a href="introduction.md">supportedPDF forms</a> 區段，以定期更新新增加的特性和功能。</p>

   此服務僅能將英文、法文、德文、西班牙文、義大利文和葡萄牙文的語言表單轉換為最適化表單。 您可以使用將生成的最適化表單翻譯成另一種語言 [AEM翻譯工作流程。](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **此服務是否可產生XDP而不是最適化表單？**

   <p>此服務未產生XDP輸出。 我們定期為服務新增功能與功能。 保留 <a href="introduction.md">支援的語言和PDF forms</a> 區段，以定期更新新增加的特性和功能。</p> <br>

1. **產生的結構描述型別為何？**

   <p>您可以使用服務來產生： </p>

   * 與JSON結構描述和連結的最適化表單
   * 未繫結至任何結構描述的最適化表單 <br><br>

1. **此服務可以將Microsoft Word表單轉換為最適化表單嗎？**

   <p>否，此服務不會將Microsoft Word表單轉換為最適化表單。 您可以將Microsoft Word表單儲存為PDF表單，並將PDF表單轉換為最適化表單。 完整的程式是 </p> <br>

   1. 使用Adobe Acrobat來 [將Word檔案轉換為非互動式PDF](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html).
   1. 使用Adobe Acrobat來 [將產生的PDF forms轉換為可填寫的PDF表單](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html).
   1. 使用Adobe Acrobat手動更新和修正表單欄位。
   1. 儲存PDF表單。 現在，您可以將此表單與轉換服務搭配使用，以產生最適化表單。 您也可以使用表單作為記錄檔案範本。


1. **此服務是否可將掃描的紙張表單和彩色表單轉換為最適化表單？**

   <p>此服務可將色彩PDF forms轉換為最適化表單。 此服務不支援掃描或填寫的表單。 如需其他限制，請參閱 <a href="known-issues.md">已知問題</a> 文章。</p> <br>

1. **此服務是否可將掃描的表單或僅表單影像轉換為最適化表單？**

   <p>此服務不支援直接將掃描後的表單或表單影像轉換為最適化表單。 但您可以使用 Adobe Acrobat 将表单图像转换为 PDF 表单。 然后再使用本服务将 PDF 表单转换为自适应表单。 对于 Acrobat，请务必使用高质量的表单图像进行转换。 这样可以提高转换质量。</p> <br>

1. **有些XDP型表單會使用表單片段，這些表單片段應該上傳到哪裡？**

   <p class="MsoNormal">將表單片段上傳至轉換資料夾並保留原始資料夾結構。 它有助於保留在XDP型表單和表單片段中使用的相對路徑。</p> <br>

1. **此服務是否支援結構描述繫結的XDP表單？ 如果我有XDP繫結到結構描述，我是否需要將結構描述內嵌到XDP？**

   <p>是，此服務支援結構描述繫結的XDP表單，並要求將結構描述內嵌到來源XDP表單中。 當您轉換結構描述繫結的XDP表單時，服務會產生JSON結構描述。 JSON結構描述在結構上與來源XDP表單的XSD結構描述類似。</p> <br>

1. **此服務無法轉換表單。 問題的原因和解決方式？**
轉換失敗的最常見原因是：
</p>
   * 為轉換提供安全的PDF forms。 請勿使用受密碼保護或安全的PDF forms進行轉換。
   * 網際網路連線中斷。 確保您在轉換期間已連線至網際網路。
   * 來源PDF有表單影像，而不是實際表單。
   * 服務設定不正確、未提供服務URL或提供的服務URL不正確。 檢查 [服務設定](configure-service.md#configure-the-cloud-service) 於 **[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**.
   * IMS設定未正確設定。 對IMS設定執行健康狀態檢查以確保其正常運作。 若要檢查IMS設定是否正確：
      1. 转到 `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. 選取設定。 按一下 **[!UICONTROL Check Health]** ，然後按一下 **[!UICONTROL Check]**. 如果成功，您將獲得 **[!UICONTROL Token retrieved successfully!]** 訊息。 <br> <br>

1. **使用自訂字型是否會影響轉換？**

   <p>當非互動式PDF表單轉換為最適化表單時，為了提高轉換品質，字型會嵌入到PDF表單中。 內嵌字型的支援僅限於非互動式PDF forms。 為了最佳化AcroForm和XFA型PDF forms的轉換，使用備援字型。</p> 
    <p>僅自訂字型目錄中列出的表單可用 <strong>Customer fonts目錄</strong> 的欄位 <strong> CQ-DAM-Handler-Gibson Font Manager服務</strong> 設定內嵌在非互動式PDF表單中。</p> 
    <p> </p> <br>

1. **此服務是否會在輸出的最適化表單中識別並使用來源PDF的字型？**

   <p>回應式HTML表單的樣式和版面通常與PDF或紙張表單不同。 為了支援組織間一致的版面和樣式，最適化表單會使用 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">設定表單樣式的主題</a>. 轉換服務會使用轉換期間套用之主題中指定的字型和字型樣式。 您可以變更佈景主題的字型和字型樣式，為最適化表單的元件提供獨特的外觀和風格。</p> <br>

1. **此服務會自動從XDP型表單中擷取JavaScript，並將其套用至對應的調適型表單嗎？**

   <p>此服務不會自動將XFA型表單或Acro Forms的指令碼轉換為對應的調適型表單規則。 您（表單作者）可以使用 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">規則編輯器</a> 將互動性新增至最適化表單。</p> <br>

1. **部分表單物件無法正確轉換為最適化表單元件。 如何解決問題？**

   <p>automated forms conversion服務會接受大量表單的訓練。 但AI/ML型應用程式受到訓練資料和模式的限制。 可能有多種欄位型別、版面配置、模式和上下文可供人類感知辨識，但難以進行自動辨識。 服務可能無法識別這類物件，或可能無法正確識別它們。 您可以使用 <a href="review-correct-ui-edited.md" target="_blank">檢閱並更正</a> 編輯者，以在輸入表單的熟悉紙張表單版面配置中進行必要的修改。</p> <br/>

1. **表格間會重複進行某些修正。 此服務是否可以在未來的轉換中識別並修正所有這類執行個體？**

   此服務會持續訓練您的表單和模式。 它會每天學習新模式。 尚未開始自動套用表單間重複的更正。 請留意發行前表單，瞭解是否提供此類功能。 <br/><br/>

   您可以使用中繼模型將表單物件對應至您選擇的最適化表單元件，並預先設定元件的驗證、規則、資料模式、說明文字和協助工具屬性。 轉換期間會套用所有指定的屬性。 您可以使用元模型來將通用屬性套用至欄位。 這可協助您減少表單間的一些重複問題。<br/><br/>

1. **含有敏感資料(例如個人識別資訊(PII)資訊)的表單有哪些選項？**
此服務僅支援空白或未填寫的表單。 請勿上傳含有個人識別資訊(PII)的已填寫表單或表單。 此外，請移除來源表單中預先填寫的資料、個人識別資訊(PII)、機密和專屬資訊。 
<br/>

1. **頁首和頁尾應放置在何處？**

   <p>將頁首和頁尾放入最適化表單範本中。 如果來源PDF表單有頁首和頁尾，服務會在轉換期間偵測偵測偵測到的頁首和頁尾，並將其取代為適用性表單範本中可用的頁首和頁尾。 如果最適化表單中包含任何額外的頁首或頁尾，您可以使用 <a href="review-correct-ui-edited.md">檢閱並更正</a> 編輯器以修正或移除此類頁首或頁尾。</p> <br />

1. **與手動規劃、建立資產（主題、範本）、建立及發佈最適化表單的程式相比，此服務可節省多少時間？**

   <p>時間長短取決於輸入表單的大小和複雜性，以及請求數量。 此服務旨在透過以快得多的速度將PDF forms轉換為最適化表單，大幅縮短實現價值的時間，而不是手動轉換表單的程式。 </p> <br />

1. **如果我遇到與RSA資料庫相關的錯誤，該怎麼辦？ 錯誤訊息類似於以下提及的訊息：** <br/>

未針對RSA/BouncyCastle程式庫設定開機委派時，會發生上述錯誤。 執行以下步驟以解決問題：   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
未針對RSA/BouncyCastle程式庫設定開機委派時，會發生上述錯誤。 執行以下步驟以解決問題：
   <p> </p>

   1. 停止AEM執行個體。 導覽至 `[AEM installation directory]\crx-quickstart\conf\` 資料夾。 開啟sling.properties檔案以進行編輯。 如果您使用 `[AEM installation directory]\crx-quickstart\bin\start.bat` 若要啟動AEM執行個體，請編輯位於的sling.properties `[AEM_root]\crx-quickstart\`.
   1. 將下列屬性新增至sling.properties檔案：<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. 儲存並關閉檔案。 <br/>
   1. 启动 AEM 实例。<br/>

   <br/>

1. **如何自動變更最適化表單文字的大小寫？**

   <p>您可以使用主題或樣式編輯器的最適化來變更最適化表單欄位的大小寫。 例如，您可以開啟主題編輯器，並將表單中所有文字的Case屬性值設定為大寫、小寫或駝峰式大小寫。 您也可以使用主題編輯器中的「CSS覆寫」選項來建立不同型別的樣式。</p>

1. **我可以對Automated forms conversion服務使用Adobe Sign文字標籤嗎？**

   <p> 當您使用Automated forms conversion服務將PDF表單轉換為最適化表單，且PDF表單具有Adobe Sign文字標籤時，這些標籤會轉換為對應的最適化表單欄位，並自動填入簽署者詳細資訊。  此功能僅適用於Acro Forms，且適用性表單支援有限數量的Adobe Sign欄位。</p>  </br>

1. **如何建立啟用Adobe Sign的PDF表單？**

   </p>若要建立啟用Adobe Sign的PDF表單：</p>

   新增 [Adobe Sign文字標籤](https://helpx.adobe.com/sign/using/text-tag.html) 至欄位名稱或使用 [轉換為Adobe Sign表單](https://helpx.adobe.com/sign/using/create-forms-with-acrobat.html) 選項。
