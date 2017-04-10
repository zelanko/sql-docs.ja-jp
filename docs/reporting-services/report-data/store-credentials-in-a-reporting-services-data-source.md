---
title: "Store Credentials in a Reporting Services Data Source | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "09/23/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "credentials [Reporting Services]"
  - "security [Analysis Services], data sources"
  - "stored credentials [Reporting Services]"
  - "data sources [Reporting Services], stored credentials"
ms.assetid: dc700922-97fa-4b30-9547-05bbbec4f09c
caps.latest.revision: 42
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 42
---
# Store Credentials in a Reporting Services Data Source
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーが、レポートに必要な外部データにアクセスするときに使用する、保存された資格情報を構成できます。 保存された資格情報は、レポートを自動実行する場合に使用されます。たとえば、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サブスクリプションがレポートを電子メールとしてパブリッシュする場合などです。 この資格情報は、レポート処理がスケジュールで設定されている場合、または、レポート処理がトリガーされた場合に、レポート サーバーによって取得されて使用されます。 このトピックでは、ネイティブ モードと SharePoint モードの両方のレポート サーバーに対して、保存された資格情報を構成する方法について説明します。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード|  
  
-   [レポート固有のデータ ソース用の保存された資格情報を構成する (ネイティブ モード)](#bkmk_stored_credentials_data_source_native)  
  
-   [レポート固有のデータ ソース用の保存された資格情報を構成する (SharePoint モード)](#bkmk_stored_credentials_data_source_sharepoint)  
  
-   [共有データ ソース用の保存された資格情報を構成する (ネイティブ モード)](#bkmk_stored_credentials_shared_data_source_native)  
  
-   [共有データ ソース用の保存された資格情報を構成する (SharePoint モード)](#bkmk_stored_credentials_shared_data_source_sharepoint)  
  
##  <a name="bkmk_top"></a> 保存された資格情報のセキュリティ ポリシー要件  
 ![as_powerpivot_refresh_sss_set_key](../../analysis-services/power-pivot-sharepoint/media/as-powerpivot-refresh-sss-set-key.png "as_powerpivot_refresh_sss_set_key") 保存された資格情報に使用するアカウントを、レポート サーバー上で、次のいずれかのセキュリティ ポリシー用に構成する必要があります。 環境に必要な最小レベルの権限を持つポリシーを選択することをお勧めします。  
  
1.  **ローカル ログオンを許可する**。 詳細については、「 [ローカル ログオンを許可する](http://technet.microsoft.com/library/cc756809\(v=WS.10\).aspx)」を参照してください。  
  
2.  **バッチ ジョブとしてログオン**。 詳細については、「 [バッチ ジョブとしてログオン](http://technet.microsoft.com/library/cc755659\(v=ws.10\).aspx)」を参照してください。  
  
3.  ポリシーに関する一般的な情報については、「 [グループ ポリシー オブジェクトのセキュリティの設定を編集する](http://technet.microsoft.com/library/cc736516\(v=ws.10\).aspx)」を参照してください。  
  
##  <a name="bkmk_stored_credentials_data_source_native"></a> レポート固有のデータ ソース用の保存された資格情報を構成する (ネイティブ モード)  
  
1.  ネイティブ モードのレポート マネージャーで、レポートが含まれているフォルダーに移動します。 コンテキスト メニュー項目 ![レポート マネージャーの、SSRS アイテム用のコンテキスト メニュー](../../reporting-services/report-data/media/ssrs-report-manager-item-context-menu.png "レポート マネージャーの、SSRS アイテム用のコンテキスト メニュー") をクリックします。  
  
2.  **[管理]** をクリックして、 **[データ ソース]**をクリックします。  
  
3.  **[カスタム データ ソース]**をクリックします。  
  
4.  **[データ ソースの種類]** の一覧で、データ ソースから取得したデータの処理に使用するデータ処理拡張機能を選択します。  
  
5.  **[接続文字列]**でレポート サーバーがデータ ソースへの接続に使用する接続文字列を指定します。 以下に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースへの接続に使用する接続文字列の例を示します。  
  
    ```  
    data source=<servername>;initial catalog=AdventureWorks2012  
    ```  
  
6.  **[接続に使用する認証]**で、 **[レポート サーバーに保存され、セキュリティで保護された資格情報]**をクリックします。  
  
7.  ユーザー名とパスワードを入力します。  
  
    -   このアカウントが Windows ドメイン ユーザー アカウントである場合は、「\<domain>\\<account\>」という形式で指定し、**[データ ソースへの接続時に Windows 資格情報として使用する]** チェック ボックスをオンにします。  
  
    -   ユーザー名とパスワードがデータベースの資格情報である場合は、 **[データ ソースへの接続時に Windows 資格情報として使用する]**を選択しないでください。 データベース サーバーが権限の借用または委譲をサポートしている場合は、 **[データ ソースへの接続が確立した後に、認証されているユーザーの権限を借用する]**を選択できます。  
  
8.  **[適用]**をクリックします。  
  
     ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [保存された資格情報のセキュリティ ポリシー要件](#bkmk_top)  
  
##  <a name="bkmk_stored_credentials_data_source_sharepoint"></a> レポート固有のデータ ソース用の保存された資格情報を構成する (SharePoint モード)  
  
1.  レポートを含むドキュメント ライブラリを参照し、開くメニュー ![ドキュメント ライブラリの、SSRS アイテム用のコンテキスト メニュー](../../reporting-services/report-data/media/ssrs-sharepoint-item-context-menu.png "ドキュメント ライブラリの、SSRS アイテム用のコンテキスト メニュー") をクリックします。  
  
2.  2 つ目の開くメニュー ![ドキュメント ライブラリの、SSRS アイテム用のコンテキスト メニュー](../../reporting-services/report-data/media/ssrs-sharepoint-item-context-menu.png "ドキュメント ライブラリの、SSRS アイテム用のコンテキスト メニュー") をクリックして、**[データ ソースの管理]** をクリックします。  
  
3.  資格情報を使用して構成する **[カスタム]** データ ソースの名前をクリックします。  
  
4.  **[データ ソースの種類]** の一覧で、データ ソースから取得したデータの処理に使用するデータ処理拡張機能を選択します。  
  
5.  **[接続文字列]**でレポート サーバーがデータ ソースへの接続に使用する接続文字列を指定します。 以下に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースへの接続に使用する接続文字列の例を示します。  
  
    ```  
    data source=<servername>;initial catalog=AdventureWorks2012  
    ```  
  
6.  **[資格情報]**で、 **[格納された資格情報]**を選択します。  
  
7.  **[ユーザー名]** と **[パスワード]**を入力します。  
  
    -   このアカウントが Windows ドメイン ユーザー アカウントである場合は、「\<domain>\\<account\>」という形式で指定し、**[データ ソースへの接続時に Windows 資格情報として使用する]** チェック ボックスをオンにします。  
  
    -   ユーザー名とパスワードがデータベースの資格情報である場合は、 **[Windows 資格情報として使用する]**を選択しないでください。 データベース サーバーが権限の借用または委譲をサポートしている場合は、 **[実行コンテキストをこのアカウントに設定する]**を選択できます。  
  
8.  **[OK]**をクリックします。  
  
     ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [保存された資格情報のセキュリティ ポリシー要件](#bkmk_top)  
  
##  <a name="bkmk_stored_credentials_shared_data_source_native"></a> 共有データ ソース用の保存された資格情報を構成する (ネイティブ モード)  
  
1.  ネイティブ モードのレポート マネージャーで、共有データ ソース アイテムに移動します。 ![共有データ ソースのアイコン](../../reporting-services/report-data/media/hlp-16datasource.png "共有データ ソースのアイコン")  
  
2.  コンテキスト メニュー ![レポート マネージャーの、SSRS アイテム用のコンテキスト メニュー](../../reporting-services/report-data/media/ssrs-report-manager-item-context-menu.png "レポート マネージャーの、SSRS アイテム用のコンテキスト メニュー") をクリックし、**[管理]** をクリックします。  
  
3.  **[データ ソースの種類]** の一覧で、データ ソースから取得したデータの処理に使用するデータ処理拡張機能を指定します。  
  
4.  **[接続文字列]**でレポート サーバーがデータ ソースへの接続に使用する接続文字列を指定します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、接続文字列に資格情報を指定しないことをお勧めします。  
  
     以下に、ローカルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースへの接続に使用する接続文字列の例を示します。  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
5.  ユーザー名とパスワードを入力します。  
  
    -   このアカウントが Windows ドメイン ユーザー アカウントである場合は、「\<domain>\\<account\>」という形式で指定し、**[データ ソースへの接続時に Windows 資格情報として使用する]** チェック ボックスをオンにします。  
  
    -   ユーザー名とパスワードがデータベースの資格情報である場合は、 **[データ ソースへの接続時に Windows 資格情報として使用する]**を選択しないでください。 データベース サーバーが権限の借用または委譲をサポートしている場合は、 **[データ ソースへの接続が確立した後に、認証されているユーザーの権限を借用する]**を選択できます。  
  
6.  **[適用]**をクリックします。  
  
     ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [保存された資格情報のセキュリティ ポリシー要件](#bkmk_top)  
  
##  <a name="bkmk_stored_credentials_shared_data_source_sharepoint"></a> 共有データ ソース用の保存された資格情報を構成する (SharePoint モード)  
  
1.  ドキュメント ライブラリで、共有データ ソース アイテムに移動します。![共有データ ソースのアイコン](../../reporting-services/report-data/media/hlp-16datasource.png "共有データ ソースのアイコン")  
  
2.  コンテキスト メニュー ![ドキュメント ライブラリの、SSRS アイテム用のコンテキスト メニュー](../../reporting-services/report-data/media/ssrs-sharepoint-item-context-menu.png "ドキュメント ライブラリの、SSRS アイテム用のコンテキスト メニュー") をクリックし、2 つ目のコンテキスト メニュー ![ドキュメント ライブラリの、SSRS アイテム用のコンテキスト メニュー](../../reporting-services/report-data/media/ssrs-sharepoint-item-context-menu.png "ドキュメント ライブラリの、SSRS アイテム用のコンテキスト メニュー") をクリックします。  
  
3.  **[データ ソース定義の編集]**をクリックします。  
  
4.  **[データ ソースの種類]** の一覧で、データ ソースから取得したデータの処理に使用するデータ処理拡張機能を指定します。  
  
5.  **[接続文字列]**でレポート サーバーがデータ ソースへの接続に使用する接続文字列を指定します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、接続文字列に資格情報を指定しないことをお勧めします。  
  
     以下に、ローカルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースへの接続に使用する接続文字列の例を示します。  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
6.  ユーザー名とパスワードを入力します。  
  
    -   このアカウントが Windows ドメイン ユーザー アカウントである場合は、「\<domain>\\<account\>」という形式で指定し、**[Windows 資格情報として使用する]** を選択します。  
  
    -   ユーザー名とパスワードがデータベースの資格情報である場合は、 **[Windows 資格情報として使用する]**を選択しないでください。 データベース サーバーが権限の借用または委譲をサポートしている場合は、 **[実行コンテキストをこのアカウントに設定する]**を選択できます。  
  
7.  **[OK]**をクリックします。  
  
     ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [保存された資格情報のセキュリティ ポリシー要件](#bkmk_top)  
  
## 参照  
 [レポート データ ソースに関する資格情報と接続情報を指定する](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [レポートのデータ ソースのプロパティを構成する &#40;レポート マネージャー&#41;](../../reporting-services/report-data/configure-data-source-properties-for-a-report-report-manager.md)   
 [共有データ ソースを作成、削除、または変更する &#40;レポート マネージャー&#41;](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)   
 [[データ ソース] プロパティ ページ &#40;レポート マネージャー&#41;](../Topic/Data%20Sources%20Properties%20Page%20\(Report%20Manager\).md)   
 [[新しいデータ ソース] ページ &#40;レポート マネージャー&#41;](../Topic/New%20Data%20Source%20Page%20\(Report%20Manager\).md)  
  
  