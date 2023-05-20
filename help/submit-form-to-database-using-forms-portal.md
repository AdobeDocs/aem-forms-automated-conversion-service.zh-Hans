---
title: 使用Forms Portal提交最適化表單至資料庫
description: 擴充預設中繼模型以新增特定於貴組織的模式、驗證和實體，並在執行Automated forms conversion服務時將設定套用至調適型表單欄位。
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
source-git-commit: ead1b4ee177029c60f095dc596b1f3db5878760e
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 1%

---


# 使用Forms入口網站整合最適化表單與資料庫 {#submit-forms-to-database-using-forms-portal}

automated forms conversion服務可讓您將非互動式PDF表單、Acro表單或XFA型PDF表單轉換為最適化表單。 啟動轉換程式時，您可以選擇產生具有或不具有資料繫結的最適化表單。

如果您選擇產生沒有資料繫結的最適化表單，則可以在轉換後將轉換的最適化表單與表單資料模型、XML結構描述或JSON結構描述整合。 不過，如果您產生具有資料繫結的最適化表單，轉換服務會自動將最適化表單與JSON結構描述相關聯，並在最適化表單和JSON結構描述中可用的欄位之間建立資料繫結。 然後，您就可以將最適化表單與您選擇的資料庫整合、在表單中填寫資料，並使用Forms入口網站將其提交到資料庫。

下圖說明使用Forms入口網站將轉換的最適化表單與資料庫整合的不同階段：

![資料庫整合](assets/database_integration.gif)

本文會說明如何成功執行所有這些整合階段的逐步指示。

本文討論的範例是自訂資料和中繼資料服務的參考實作，以整合Forms入口網站頁面與資料庫。 範例實作中使用的資料庫是MySQL 5.6.24。不過，您可以將Forms入口網站頁面與您選擇的任何資料庫整合。

## 先決條件 {#pre-requisites}

* 設定AEM 6.4或6.5編寫執行個體
* 安裝 [最新Service Pack](https://helpx.adobe.com/cn/experience-manager/aem-releases-updates.html) 適用於您的AEM執行個體
* 最新版本的AEM Forms附加元件套件
* 設定 [automated forms conversion服務](configure-service.md)
* 設定資料庫。 範例實作中使用的資料庫是MySQL 5.6.24。不過，您可以將轉換後的最適化表單與您選擇的任何資料庫整合。

## 設定AEM執行個體與資料庫之間的連線 {#set-up-connection-aem-instance-database}

設定AEM執行處理與MYSQL資料庫之間的連線包含：

* [安裝MYSQL聯結器套件](#install-mysql-connector-java-file)

* [在資料庫中建立綱要和表格](#create-schema-and-tables-in-database)

* [正在設定連線設定](#configure-connection-between-aem-instance-and-database)

* [設定和設定Forms入口網站整合的範例套件](#set-up-and-configure-sample)

### 安裝mysql-connector-java-5.1.39-bin.jar檔案 {#install-mysql-connector-java-file}

在所有作者和發佈執行個體上執行下列步驟，安裝mysql-connector-java-5.1.39-bin.jar檔案：

1. 導覽至http://[伺服器]：[連線埠]/system/console/depfinder和搜尋com.mysql.jdbc套件。
1. 在「匯出者」欄中，檢查封裝是否已由任何束匯出。 如果套件未由任何套件組合匯出，請繼續。
1. 導覽至http://[伺服器]：[連線埠]/system/console/bundles並按一下 **[!UICONTROL Install/Update]**.
1. 按一下 **[!UICONTROL Choose File]** 並瀏覽以選取mysql-connector-java-5.1.39-bin.jar檔案。 此外，請選取 **[!UICONTROL Start Bundle]** 和 **[!UICONTROL Refresh Packages]** 核取方塊。
1. 按一下 **[!UICONTROL Install]** 或 **[!UICONTROL Update]**. 完成後，請重新啟動伺服器。
1. （僅限Windows）關閉作業系統的系統防火牆。

### 在資料庫中建立方案和表格 {#create-schema-and-tables-in-database}

執行以下步驟，在資料庫中建立綱要和表格：

1. 使用下列SQL敘述句在資料庫中建立綱要：

   ```sql
   CREATE SCHEMA `formsportal` ;
   ```

   位置 **formsportal** 是指結構描述的名稱。

1. 建立 **資料** 資料庫綱要中的表格，使用下列SQL敘述句：

   ```sql
    CREATE TABLE `data` (
        `owner` varchar(255) DEFAULT NULL,
        `data` longblob,
        `metadataId` varchar(45) DEFAULT NULL,
        `id` varchar(45) NOT NULL,
        PRIMARY KEY (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. 建立 **中繼資料** 資料庫綱要中的表格，使用下列SQL敘述句：

   ```sql
   CREATE TABLE `metadata` (
       `formPath` varchar(1000) DEFAULT NULL,
       `formType` varchar(100) DEFAULT NULL,
       `description` text,
       `formName` varchar(255) DEFAULT NULL,
       `owner` varchar(255) DEFAULT NULL,
       `enableAnonymousSave` varchar(45) DEFAULT NULL,
       `renderPath` varchar(1000) DEFAULT NULL,
       `nodeType` varchar(45) DEFAULT NULL,
       `charset` varchar(45) DEFAULT NULL,
       `userdataID` varchar(45) DEFAULT NULL,
       `status` varchar(45) DEFAULT NULL,
       `formmodel` varchar(45) DEFAULT NULL,
       `markedForDeletion` varchar(45) DEFAULT NULL,
       `showDorClass` varchar(255) DEFAULT NULL,
       `sling:resourceType` varchar(1000) DEFAULT NULL,
       `attachmentList` longtext,
       `draftID` varchar(45) DEFAULT NULL,
       `submitID` varchar(45) DEFAULT NULL,
       `id` varchar(60) NOT NULL,
       `profile` varchar(255) DEFAULT NULL,
       `submitUrl` varchar(1000) DEFAULT NULL,
       `xdpRef` varchar(1000) DEFAULT NULL,
       `agreementId` varchar(255) DEFAULT NULL,
       `nextSigners` varchar(255) DEFAULT NULL,
       `eSignStatus` varchar(45) DEFAULT NULL,
       `pendingSignID` varchar(45) DEFAULT NULL,
       `agreementDataId` varchar(255) DEFAULT NULL,
       `enablePortalSubmit` varchar(45) DEFAULT NULL,
       `submitType` varchar(45) DEFAULT NULL,
       `dataType` varchar(45) DEFAULT NULL,
       `jcr:lastModified` varchar(45) DEFAULT NULL,
       PRIMARY KEY (`id`),
       UNIQUE KEY `ID_UNIQUE` (`id`)
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. 建立 **additionalmetadatable** 資料庫綱要中的表格，使用下列SQL敘述句：

   ```sql
   CREATE TABLE `additionalmetadatatable` (
       `value` text,
       `key` varchar(255) NOT NULL,
       `id` varchar(60) NOT NULL,
       PRIMARY KEY (`id`,`key`),
       CONSTRAINT ‘additionalmetadatatable_fk’ FOREIGN KEY (`id`) REFERENCES `metadata` (`id`) ON DELETE CASCADE
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. 建立 **註解** 資料庫綱要中的表格，使用下列SQL敘述句：

   ```sql
   CREATE TABLE `commenttable` (
       `commentId` varchar(255) DEFAULT NULL,
       `comment` text DEFAULT NULL,
       `ID` varchar(255) DEFAULT NULL,
       `commentowner` varchar(255) DEFAULT NULL,
       `time` varchar(255) DEFAULT NULL);
   ```

### 設定AEM執行個體與資料庫之間的連線 {#configure-connection-between-aem-instance-and-database}

執行以下設定步驟來建立AEM執行處理與MYSQL資料庫之間的連線：

1. 前往AEM Web主控台組態頁面，網址為 *http://[主機]：[連線埠]/system/console/configMgr*.
1. 按一下以開啟 **[!UICONTROL Forms Portal Draft and Submission Configuration]** 在編輯模式中。
1. 依照下表的說明，指定屬性的值：

   <table> 
    <tbody> 
    <tr> 
    <th><strong>属性</strong></th> 
    <th><strong>描述</strong></th>
    <th><strong>价值</strong></th> 
    </tr> 
    <tr> 
    <td><p>Forms入口網站草稿資料服務</p></td> 
    <td><p>草稿資料服務的識別碼</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms入口網站草稿中繼資料服務</p></td> 
    <td><p>草稿中繼資料服務的識別碼</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms入口網站提交資料服務</p></td> 
    <td><p>用於提交資料服務的識別碼</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms入口網站提交中繼資料服務</p></td> 
    <td><p>用於提交中繼資料服務的識別碼</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms入口網站擱置中簽署資料服務</p></td> 
    <td><p>擱置中簽署資料服務的識別碼</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms入口網站擱置簽署中繼資料服務</p></td> 
    <td><p>擱置簽署中繼資料服務的識別碼</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    </tbody> 
    </table>
1. 將其他設定維持原狀，然後按一下 **[!UICONTROL Save]**.
1. 尋找並按一下以開啟 **[!UICONTROL Apache Sling Connection Pooled DataSource]** 在「Web主控台設定」的編輯模式中。 依照下表的說明，指定屬性的值：

   <table> 
    <tbody> 
    <tr> 
    <th><strong>属性</strong></th> 
    <th><strong>价值</strong></th> 
    </tr> 
    <tr> 
    <td><p>資料來源名稱</p></td> 
    <td><p>從資料來源集區篩選驅動程式的資料來源名稱。 範例實作使用FormsPortal作為資料來源名稱。</p></td>
    </tr>
    <tr> 
    <td><p>JDBC驅動程式類別</p></td> 
    <td><p>com.mysql.jdbc.Driver</p></td>
    </tr>
    <tr> 
    <td><p>JDBC連線URI</p></td> 
    <td><p>jdbc:mysql://[host]：[port]/[schema_name]</p></td>
    </tr>
    <tr> 
    <td><p>用户名</p></td> 
    <td><p>用於驗證資料庫表格並執行動作的使用者名稱</p></td>
    </tr>
    <tr> 
    <td><p>密码</p></td> 
    <td><p>與使用者名稱相關聯的密碼</p></td>
    </tr>
    <tr> 
    <td><p>交易隔離</p></td> 
    <td><p>READ_COMMITTED</p></td>
    </tr>
    <tr> 
    <td><p>最大使用中連線數</p></td> 
    <td><p>1000</p></td>
    </tr>
    <tr> 
    <td><p>最大閒置連線</p></td> 
    <td><p>100</p></td>
    </tr>
    <tr> 
    <td><p>最小閒置連線</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>初始大小</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>最長等待</p></td> 
    <td><p>100000</p></td>
    </tr>
     <tr> 
    <td><p>借入時測試</p></td> 
    <td><p>已选中</p></td>
    </tr>
     <tr> 
    <td><p>閒置時測試</p></td> 
    <td><p>已选中</p></td>
    </tr>
     <tr> 
    <td><p>驗證查詢</p></td> 
    <td><p>範例值為SELECT 1(mysql)、select 1 from dual(oracle)、SELECT 1(MS Sql Server) (validationQuery)</p></td>
    </tr>
     <tr> 
    <td><p>驗證查詢逾時</p></td> 
    <td><p>10000</p></td>
    </tr>
    </tbody> 
    </table>

### 設定和設定範例 {#set-up-and-configure-sample}

在所有製作和發佈執行個體上執行下列步驟，以安裝和設定範例：

1. 下載下列專案 **aem-fp-db-integration-sample-pkg-6.1.2.zip** 封裝至您的檔案系統。

[获取文件](assets/aem-fp-db-integration-sample-pkg-6.1.2.zip)

1. 前往AEM封裝管理員，網址為 *http://[主機]：[連線埠]/crx/packmgr/*.
1. 单击 **[!UICONTROL Upload Package]**.
1. 瀏覽以選取 **aem-fp-db-integration-sample-pkg-6.1.2.zip** 封裝並按一下 **[!UICONTROL OK]**.
1. 按一下 **[!UICONTROL Install]** 在套件旁邊，以安裝套件。

## 設定轉換後的最適化表單，以用於Forms Portal整合 {#configure-converted-adaptive-form-for-forms-portal-integration}

執行以下步驟，透過Forms Portal頁面啟用最適化表單提交：
1. [執行轉換](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) 將來源表單轉換為最適化表單。
1. 在編輯模式下開啟最適化表單。
1. 點選「表單容器」並選取「設定」 ![設定自適應表單](assets/configure-adaptive-form.png).
1. 在 **[!UICONTROL Submission]** 區段，選取 **[!UICONTROL Forms Portal Submit Action]** 從 **[!UICONTROL Submit Action]** 下拉式清單。
1. 點選 ![儲存範本原則](assets/edit_template_done.png) 以儲存設定。

## 建立和設定Forms入口網站頁面 {#create-configure-forms-portal-page}

執行以下步驟來建立Forms Portal頁面並加以設定，以便您可以使用此頁面提交調適型表單：

1. 登入AEM編寫執行個體並點選 **[!UICONTROL Adobe Experience Manager]** >  **[!UICONTROL Sites]**.
1. 選取您要儲存新Forms入口網站頁面的位置，然後點選 **[!UICONTROL Create]** > **[!UICONTROL Page]**.
1. 選取頁面的範本，點選 **[!UICONTROL Next]**，指定頁面的標題並點選 **[!UICONTROL Create]**.
1. 點選 **[!UICONTROL Edit]** 以設定頁面。
1. 在頁首中，點選 ![編輯範本](assets/edit_template_sites.png)  > **[!UICONTROL Edit Template]** 以開啟頁面的範本。
1. 點選「版面容器」並點選 ![編輯範本原則](assets/edit_template_policy.png). 在 **[!UICONTROL Allowed Components]** 標籤，啟用 **[!UICONTROL Document Services]** 和 **[!UICONTROL Document Services Predicates]** 選項，然後點選 ![儲存範本原則](assets/edit_template_done.png).
1. 插入 **[!UICONTROL Search & Lister]** 元件時。 因此，頁面上會列出AEM執行個體上可用的所有現有調適型表單。
1. 插入 **[!UICONTROL Drafts & Submissions]** 元件時。 兩個標籤， **[!UICONTROL Draft Forms]** 和 **[!UICONTROL Submitted Forms]**，即會顯示在Forms Portal頁面上。 此 **[!UICONTROL Draft Forms]** 索引標籤也會顯示使用中所述步驟產生的轉換後的最適化表單 [設定轉換後的最適化表單，以用於Forms Portal整合](#configure-converted-adaptive-form-for-forms-portal-integration)

1. 點選 **[!UICONTROL Preview]**，點選轉換後的最適化表單，指定最適化表單欄位的值並提交它。 您為最適化表單欄位指定的值會提交至整合式資料庫。
