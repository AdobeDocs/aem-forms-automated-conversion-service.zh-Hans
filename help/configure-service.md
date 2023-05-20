---
title: 配置自动化表单转换服务
description: 準備好您的AEM執行個體以使用Automated forms conversion服務
role: User, Admin
exl-id: 8f21560f-157f-41cb-ba6f-12a4d6e18555
source-git-commit: 47261710e6616c27c210ac53bffcc2387a06ea7a
workflow-type: tm+mt
source-wordcount: '2684'
ht-degree: 7%

---

# 配置自动化表单转换服务 {#about-this-help}

此說明說明AEM管理員如何設定Automated forms conversion服務，以自動將其PDF forms轉換為最適化表單。 此說明適用於貴組織的IT和AEM管理員。 所提供的資訊是根據以下假設，即任何閱讀本「說明」的人員都熟悉以下技術：

* 安裝、設定和管理Adobe Experience Manager和AEM套件，

* 使用Linux®和Microsoft® Windows®作業系統，

* 設定SMTP郵件伺服器

<!--- >[!VIDEO](https://video.tv.adobe.com/v/29267/) 

**Watch the video or read the article to configure Automated Forms Conversion service** -->

## 入门培训{#onboarding}

AEM 6.4 Forms和AEM 6.5 Forms內部部署定期客戶和Adobe管理服務企業客戶可免費使用該服務。 欲访问服务，请联系 Adobe 销售团队或 Adobe 代表。AEM Formsas a Cloud Service客戶也可以免費使用此服務並預先啟用該服務。

Adobe 可为您的组织开启访问渠道，并为您指定为组织中管理员的人员提供所需的权限。管理员可以向贵企业的 AEM Forms 开发人员（用户）授予权限并连接到该服务。 

## 前提条件 {#prerequisites}

您需要下列專案才能使用Automated forms conversion服務：

* 已為貴組織啟用Automated forms conversion服務
* 具有轉換服務之管理員許可權的Adobe ID帳戶
* 具備最新AEM Service Pack或最新更新且運作中的AEM 6.4、AEM 6.5或AEM Formsas a Cloud Service製作執行個體。
* 屬於表單 — 使用者群組成員的AEM使用者(在您的AEM執行個體上)

## 設定環境 {#setuptheservice}

在使用服務之前，請準備您的AEM編寫執行個體以連線到Adobe Cloud上執行的服務。 請依照列出的順序執行下列步驟，為服務準備您的執行個體：

1. [下載並安裝AEM 6.4、AEM 6.5或內建AEM Formsas a Cloud Service](#aemquickstart)
1. [下載並安裝最新的AEM Service Pack](#servicepack)
1. [下載並安裝最新的AEM Forms附加元件套件](#downloadaemformsaddon)
1. （選擇性） [下載並安裝最新的聯結器套件](#installConnectorPackage)
1. [建立自訂主題和範本](#referencepackage)

### 下載並安裝AEM 6.4、AEM 6.5或內建AEM Formsas a Cloud Service {#aemquickstart}


automated forms conversion服務會在AEM編寫執行個體上執行。 您需要AEM 6.4、AEM 6.5或AEM Formsas a Cloud Service才能設定AEM編寫執行個體。

* 如果您尚未啟動並執行AEM 6.4或AEM 6.5，請從以下位置下載。 下載AEM後，如需設定AEM編寫執行個體的指示，請參閱 [部署和維護](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall).：

   * 如果您是AEM的現有客戶，請從下載AEM 6.4或AEM 6.5 [Adobe授權網站](http://licensing.adobe.com).

   * 如果您是Adobe合作夥伴，請使用 [Adobe合作夥伴訓練計畫](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) 請求AEM 6.4或AEM 6.5。

* 如果您正在使用AEM Formsas a Cloud Service，請參閱上線至 [AEM Formsas a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-forms-cloud-service.html?lang=en#setup-environment) 和 [設定本機開發環境](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-local-development-environment.html?lang=en#setup-environment).

### (僅適用於AEM 6.4和AEM 6.5)下載並安裝AEM最新Service Pack {#servicepack}

下載並安裝最新的AEM Service Pack。 如需詳細指示，請參閱或 [AEM 6.4 Service Pack發行說明](https://helpx.adobe.com/cn/experience-manager/6-4/release-notes/sp-release-notes.html) 或 [AEM 6.5 Service Pack發行說明](https://helpx.adobe.com/cn/experience-manager/6-5/release-notes/sp-release-notes.html).

### (僅適用於AEM 6.4和AEM 6.5)下載並安裝AEM Forms附加元件套件  {#downloadaemformsaddon}

AEM執行個體包含基本表單功能。 轉換服務需要AEM Forms的完整功能。 下載並安裝AEM Forms附加元件套件，以使用AEM Forms的所有功能。 需要套件才能設定並執行轉換服務。 如需詳細指示，請參閱 [安裝及設定資料擷取功能。](https://helpx.adobe.com/cn/experience-manager/6-5/forms/using/installing-configuring-aem-forms-osgi.html)

>[!NOTE]
> 在安裝附加元件套件後，請務必執行必要的安裝後設定。

<!-- ### (Optional) Download and install connector package  {#installConnectorPackage}

The connector package provides early access to the [Auto-detect logical sections](convert-existing-forms-to-adaptive-forms.md#run-the-conversion) features and improvements delivered in release AFC-2020.03.1. Do not install the package if you do not require feature and improvements delivered in AFC-2020.03.1.  You can [download the connector package from AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1). -->


### 建立自訂主題和範本 {#referencepackage}

如果您啟動AEM 6.4或AEM 6.5於 [生產模式](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/production-ready.html) （nosamplecontent執行模式），未安裝參考套件。 參考套件包含範例主題和範本。 automated forms conversion服務需要至少一個主題和一個範本，才能將PDF表單轉換為最適化表單。 建立您自己的自訂主題和範本及點 [服務設定](#configure-the-cloud-service) 使用服務之前使用自訂範本和佈景主題。

您也可以下載並安裝 [AEM Forms參考資產](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 封裝在您的Author執行個體上。 它會建立一些參考主題和範本。

## 配置服务 {#configure-the-service}

繼續設定服務並將本機執行個體與Adobe Cloud上執行的服務連線之前，請先瞭解連線至服務所需的角色和許可權。 此服務使用兩種不同型別的角色：管理員和開發人員：

* **管理員**：管理員負責管理組織的Adobe軟體和服務。 管理員可向組織內的開發人員授予存取權，以連線至Adobe雲端上執行的Automated forms conversion服務。 為組織布建管理員時，管理員會收到一封包含標題的電子郵件 **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']**. 如果您是管理員，請檢查您的信箱是否有包含先前提及標題的電子郵件，並繼續 [向貴組織的開發人員授與存取權](#adduseranddevs).

![管理員存取權授予電子郵件](assets/admin-console-adobe-io-access-grantedx75.png)

* **開發人員**：開發人員將本機AEM Forms作者執行個體連線到在Adobe Cloud上執行的Automated forms conversion服務。 當管理員授予開發人員連線Automated forms conversion服務的許可權時，會向開發人員傳送一封電子郵件，標題為「您現在擁有管理組織AdobeAPI整合的開發者存取權」。 如果您是開發人員，請檢查您的信箱是否有包含先前提及標題的電子郵件，並繼續 [將您的本機AEM執行個體連線至Adobe Cloud上的Automated forms conversion服務。](#connectafcadobeio)

![開發人員存取許可權授權電子郵件](assets/email-developer-accessx94.png)

### (僅適用於AEM 6.4和AEM 6.5的管理員)授予組織開發人員的存取權 {#adduseranddevs}

Adobe為您的組織啟用存取權並提供必要的許可權給管理員後，管理員可以登入Admin Console（詳細指示如下）、建立設定檔，並將開發人員新增到設定檔。 開發人員可以將AEM Forms的本機執行個體連線至Adobe Cloud上的Automated forms conversion服務。

開發人員是您指定執行轉換服務的組織成員。 只有新增至AdobeAutomated forms conversion服務設定檔的開發人員才有權使用Automated forms conversion服務。 執行以下步驟來建立設定檔並新增開發人員。 至少需要一個設定檔，才能將必要的存取權授予您組織的開發人員：

1. 登入 [Admin Console](https://adminconsole.adobe.com/). 使用 **Adobe ID** 已布建為使用Automated forms conversion服務登入的管理員。 請勿登入任何其他ID或Federated ID。
1. 按一下 **[!UICONTROL Automated Forms Conversion]** 選項。
1. 按一下 **[!UICONTROL New Profile]** 在 **[!UICONTROL Products]** 標籤。
1. 指定 **[!UICONTROL Name]**， **[!UICONTROL Display Name]**、和 **[!UICONTROL Description]** 用於設定檔。 单击 **[!UICONTROL Done]**. 設定檔已建立。

   ![指定新設定檔的詳細資料。](assets/create-new-profile-details.png)

1. 將開發人員新增至設定檔。 若要新增開發人員：
   1. 在 [Admin Console](https://adminconsole.adobe.com/enterprise)，導覽至「概述」標籤。
   1. 按一下 **[!UICONTROL Assign Developers]** 在所需的產品卡上。
   1. 輸入開發人員的電子郵件地址，以及名字和姓氏（可選）。
   1. 選取產品設定檔。 点击&#x200B;**[!UICONTROL Save]**。

對所有使用者重複上述步驟。 如需新增開發人員的詳細資訊，請參閱 [管理開發人員](https://helpx.adobe.com/enterprise/using/manage-developers.html).

管理員將開發人員新增至Adobe I/O設定檔後，開發人員會透過電子郵件收到通知。 收到電子郵件後，開發人員可以繼續前往 [將本機AEM Forms執行個體與Adobe Cloud上的Automated forms conversion服務連線](#connectafcadobeio).

### （僅適用於開發人員）將本機AEM Forms執行個體連結至Adobe Cloud上的Automated forms conversion服務 {#connectafcadobeio}

管理員提供開發人員存取權後，您就可以將本機AEM Forms執行個體連結至Automated forms conversion服務，在Adobe Cloud上執行。 以所列順序執行下列步驟，將您的AEM Forms執行個體連線到服務：

* [設定電子郵件通知](configure-service.md#configureemailnotification)
* [新增使用者至表單 — 使用者群組](#adduserstousergroup)
* [取得公開憑證](#obtainpubliccertificates)
* [在Adobe Developer主控台設定服務API](#createintegration)
* [設定雲端服務](configure-service.md#configure-the-cloud-service)

#### 設定電子郵件通知 {#configureemailnotification}

automated forms conversion服務會使用Day CQ郵件服務來傳送電子郵件通知。 這些電子郵件通知包含成功或失敗轉換的相關資訊。 如果您選擇不接收通知，請略過這些步驟。 執行以下步驟來設定Day CQ Mail Service：

* 對於AEM 6.4 Forms或AEM 6.5 Forms：

   1. 前往AEM設定管理員，網址為 `http://localhost:4502/system/console/configMgr`
   1. 開啟Day CQ Mail Service設定。 指定 **[!UICONTROL SMTP server host name]**， **[!UICONTROL SMTP server port]**、和 **[!UICONTROL From address]** 欄位。 单击 **[!UICONTROL Save]**.

      您可以連絡您的電子郵件服務提供者或IT管理員，取得有關SMTP伺服器主機名稱和連線埠的資訊。 您可以在「寄件者」欄位中使用任何有效的電子郵件地址。 例如，notification@example.com或donotreply@example.com。

   1. 開啟 **[!UICONTROL Day CQ Link Externalizer]** 設定。 在 **[!UICONTROL Domains]** 欄位中，指定本機、作者和發佈執行個體的實際主機名稱或IP位址和連線埠號碼。 单击 **[!UICONTROL Save]**.

* 若為AEM Formsas a Cloud Service， [記錄支援票證以啟用電子郵件服務](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#sending-email).

#### 新增使用者至表單 — 使用者群組 {#adduserstousergroup}

在指定要執行服務的AEM使用者的設定檔中指定電子郵件地址。 確定使用者是 [表單使用者](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/forms-groups-privileges-tasks.html) 群組。 電子郵件會傳送至執行轉換之使用者的電子郵件地址。 若要指定使用者的電子郵件地址，並將使用者新增至表單使用者群組：

1. 以AEM管理員身分登入您的AEM Forms作者執行個體。 使用您的本機AEM憑證登入。 請勿使用Adobe ID登入。 點選 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. 選取指定要執行轉換服務的使用者，然後點選 **[!UICONTROL Properties]**. 「編輯使用者設定」頁面隨即開啟。
1. 在中指定電子郵件地址 **[!UICONTROL Email]** 欄位並點選 **[!UICONTROL Save]**. 成功完成或轉換失敗時，會將電子郵件傳送至指定的電子郵件地址。
1. 點選 **群組** 標籤。 在「選取群組」標籤中，輸入並選取 **forms-users** 群組。 點選 **儲存並關閉**. 使用者現在是forms-users群組的成員。

#### (僅適用於AEM 6.4和AEM 6.5)取得公開憑證 {#obtainpubliccertificates}

公開憑證可讓您在Adobe I/O時驗證設定檔。

1. 登入您的AEM Forms作者執行個體。 导航至 **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. 点击&#x200B;**[!UICONTROL Create]**。此 **[!UICONTROL Adobe IMS Technical Account Configuration]** 頁面便會顯示。

   ![Adobe IMS技術帳戶設定頁面](assets/adobe-ims-technical-account-configuration.png)

1. 選取 **[!UICONTROL Automated Forms Conversion Service]** 雲端解決方案中的。

1. 選取 **[!UICONTROL Create new certificate]** 核取方塊並指定別名。 别名将用作对话框的名称。点击&#x200B;**[!UICONTROL Create certificate]**。将显示一个对话框。单击 **[!UICONTROL OK]**. 憑證已建立。

1. 點選 **[!UICONTROL Download Public Key]** 並儲存 *AEM-Adobe-IMS.crt* 您的電腦上的憑證檔案。 憑證檔案用於 [在Adobe Developer主控台設定服務API](#createintegration). 点击&#x200B;**[!UICONTROL Next]**。

1. 指定下列專案：

   * 標題：指定標題。
   * 授權伺服器： [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)\

   其他欄位暫時保留空白（稍後提供）。 保持頁面開啟。

   <!--
   Comment Type: draft

   <li> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

#### (僅適用於AEM 6.4和AEM 6.5)在Adobe Developer主控台設定服務API {#createintegration}

若要使用Automated forms conversion服務，請建立專案，並將Automated Forms Configuration Service API新增至Adobe Developer Console上的專案。 整合會產生API金鑰、使用者端密碼、裝載(JWT)。

1. 登入 [https://console.adobe.io/](https://console.adobe.io/). 使用您的管理員已布建登入Adobe I/O控制檯的Adobe ID開發人員帳戶登入。
1. 從右上角選取您的組織。 如果您不了解您的组织，请与管理员联系。
1. 点击&#x200B;**[!UICONTROL Create new project]**。隨即顯示開始使用新專案的畫面。 点击&#x200B;**[!UICONTROL Add API]**。畫面上會顯示為您的帳戶啟用的所有API清單。
1. 選取 **[!UICONTROL Automated Forms Conversion service]** 並點選 **[!UICONTROL Next]**. 隨即顯示設定API的畫面。
1. 選取 [!UICONTROL Upload your public key] 選項，上傳在中下載的AEM-Adobe-IMS.crt檔案 [取得公開憑證](#obtainpubliccertificates) 區段並點選 **[!UICONTROL Next]**. 「建立新的服務帳戶(JWT)認證」選項就會出現。 点击&#x200B;**[!UICONTROL Next]**。
1. 選取產品設定檔並點選 **[!UICONTROL Save configured API]**. 選取建立時間 [向您組織的開發人員授與存取權](#adduseranddevs). 如果您不知道要選取的設定檔，請聯絡管理員。
1. 點選 **[!UICONTROL Service Account (JWT)]** 檢視API金鑰、使用者端密碼和將本機AEM執行個體連線至Automated forms conversion服務所需的其他資訊。 頁面上的資訊會用於在本機電腦上建立IMS設定。

1. 在本機執行個體上開啟IMS設定頁面。 保持打开该页面[获取公共证书](#obtainpubliccertificates)的结尾部分。

   ![指定標題、API金鑰、使用者端密碼和裝載 ](assets/ims-configuration-details.png)

1. 在Adobe IMS技術頁面上，指定API金鑰和使用者端密碼。 使用Adobe Developer主控台頁面的服務帳戶(JWT)上指定的值。

   >[!NOTE]
   >
   >
   >對於裝載，請使用Adobe Developer主控台的「服務帳戶(JWT)」頁面的「產生JWT」標籤中提供的代碼。

1. 点击&#x200B;**[!UICONTROL Save]**。IMS設定已建立。

   >[!CAUTION]
   >
   >僅建立一個IMS設定。 請勿建立多個IMS設定。

1. 選取IMS設定並點選 **[!UICONTROL Check Health]**. 将显示一个对话框。点击&#x200B;**[!UICONTROL Check]**。成功连接时，将显示&#x200B;*已成功检索令牌*&#x200B;消息。

   ![成功連線時，已成功擷取Token訊息就會顯示。 ](assets/health-check.png)

   <br/> <br/>

#### 設定Cloud Service {#configure-the-cloud-service}

建立Cloud Service設定，以將您的AEM執行個體連線到轉換服務。 它也可讓您指定轉換的範本、主題和表單片段。 您可以為每組表單分別建立多個雲端服務設定。 例如，您可以針對銷售部門表單設定不同的組態，而針對客戶支援表單設定不同的組態。 執行以下步驟來建立雲端服務設定：

1. 在您的AEM Forms執行個體上，點選 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]**> **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**.
1. 點選 **[!UICONTROL Global]** 資料夾並點選 **[!UICONTROL Create]**. 隨即顯示建立Automated forms conversion組態的頁面。 設定會在全域資料夾中建立。 您也可以在現有的不同資料夾中建立設定，或為您的設定建立資料夾。

1. 於 **[!UICONTROL Create Automated Forms Conversion Configuration]** 頁面，指定以下欄位的值，然後點選 **[!UICONTROL Next]**.

   | 字段 | 描述 |
   |--- |--- |
   | 标题 | 設定的唯一標題。 標題會顯示在用於開始轉換的UI中。 |
   | 名称 | 設定的唯一名稱。 設定會以指定的名稱儲存在CRX-Repository中。 名稱可與標題相同。 |
   | 縮圖位置 | 設定的縮圖位置。 |
   | 服务 URL | Adobe雲端上Automated forms conversion服務的URL。 使用 `https://aemformsconversion.adobe.io/` URL。 |
   | 模板 | 要套用至轉換表單的預設範本。 在開始轉換之前，您一律可以指定不同的範本。 範本包含最適化表單的基本結構和初始內容。 您可以從提供的現成範本中選擇範本。 您也可以建立自訂範本。 |
   | 主题 | 要套用至轉換表單的預設主題。 在開始轉換之前，您可以隨時指定不同的主題。  您可以按一下圖示，選擇現成可用的主題。 您也可以建立自訂主題。 |
   | 现有片段 | 現有片段的位置（如果有）。 |
   | 自定义元模型 | 自訂中繼模型的.schema.json檔案路徑。 您可以為英文、法文、德文、西班牙文、義大利文和葡萄牙文建立單獨的中繼模型。 |

1. 在 **[!UICONTROL Advanced]** 的標籤 **[!UICONTROL Create Automated Forms Conversion Configuration]** 頁面，指定下列欄位的值：

   <table>
   <thead>
   <tr>
   <th>字段</th>
   <th>描述</th>
   </tr>
   </thead>
   <tbody>
   <tr>
   <td >生成记录文档</td>
   <td>選取選項，為轉換的表單自動產生記錄檔案。 此選項僅適用於XFA型表單(XDP和PDF forms)。 啟用此選項後，在提交表單後，您可以允許客戶以列印或檔案格式來記錄他們在表單中填寫的資訊，以供日後參考。 這稱為記錄檔案。</td>
   </tr>
   <tr>
   <td>启用 Analytics</td>
   <td>(僅適用於AEM 6.4和AEM 6.5)選取選項，以在所有轉換的表單上啟用Adobe Analytics。 在使用選項之前，請確定您的AEM Forms執行個體已啟用Adobe Analytics 。</td>
   </tr>
   </tbody>
   </table>

   * 如果來源是副檔名為.XDP的XFA型表單，則輸出DOR會保留XFA配置，否則轉換服務會使用現成的範本為其他XFA型表單產生DOR。
   * 提交XFA表單時，表單的提交資料會儲存為XML元素或屬性。 例如， `<Amount currency="USD"> 10.00 </Amount>`. 貨幣會儲存為屬性和貨幣金額，10.00會儲存為元素。 最適化表單的提交資料沒有屬性，只有元素。 因此，當以XFA為基礎的表單轉換為最適化表單時，最適化表單提交資料會包含每個這類屬性的元素。 例如，

   ```css
      {
         "Type": "Principal",
   
         "Amount": "10.00",
   
         "currency": "USD"
      }
   ```

1. 点击&#x200B;**[!UICONTROL Create]**。将创建云配置。您的AEM Forms執行個體已準備好開始將舊版表單轉換為最適化表單。
