---
title: Reporting Services データ ソースに資格情報を保存する | Microsoft Docs
ms.custom: ''
ms.date: 09/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- credentials [Reporting Services]
- security [Analysis Services], data sources
- stored credentials [Reporting Services]
- data sources [Reporting Services], stored credentials
ms.assetid: dc700922-97fa-4b30-9547-05bbbec4f09c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d70d5570735d2861f8cf62d3b8c0c61a3bae938
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78173041"
---
# <a name="store-credentials-in-a-reporting-services-data-source"></a>Store Credentials in a Reporting Services Data Source
  
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] レポート サーバーが、レポートに必要な外部データにアクセスするときに使用する、保存された資格情報を構成できます。 保存された資格情報は、レポートを自動実行する場合に使用されます。たとえば、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] サブスクリプションがレポートを電子メールとしてパブリッシュする場合などです。 この資格情報は、レポート処理がスケジュールで設定されている場合、または、レポート処理がトリガーされた場合に、レポート サーバーによって取得されて使用されます。 このトピックでは、ネイティブ モードと SharePoint モードの両方のレポート サーバーに対して、保存された資格情報を構成する方法について説明します。

||
|-|
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]ネイティブモード &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint モード|

 **このトピックの内容:**

-   [レポート固有のデータソース用の保存された資格情報を構成する (ネイティブモード)](#bkmk_stored_credentials_data_source_native)

-   [レポート固有のデータソース用の保存された資格情報の構成 (SharePoint モード)](#bkmk_stored_credentials_data_source_sharepoint)

-   [共有データソース用の保存された資格情報を構成する (ネイティブモード)](#bkmk_stored_credentials_shared_data_source_native)

-   [共有データソース用の保存された資格情報の構成 (SharePoint モード)](#bkmk_stored_credentials_shared_data_source_sharepoint)

##  <a name="bkmk_top"></a>保存された資格情報のセキュリティポリシー要件
 ![as_powerpivot_refresh_sss_set_key](https://docs.microsoft.com/analysis-services/analysis-services/media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")保存された資格情報に使用するアカウントは、レポートサーバー上の次のいずれかのセキュリティポリシーに対して構成する必要があります。 環境に必要な最小レベルの権限を持つポリシーを選択することをお勧めします。

1.  **ローカルログオンを許可**します。 詳細については、「 [ローカル ログオンを許可する](https://technet.microsoft.com/library/cc756809\(v=WS.10\).aspx)」を参照してください。

2.  **バッチジョブとしてログオン**します。 詳細については、「 [バッチ ジョブとしてログオン](https://technet.microsoft.com/library/cc755659\(v=ws.10\).aspx)」を参照してください。

3.  ポリシーに関する一般的な情報については、「 [グループ ポリシー オブジェクトのセキュリティの設定を編集する](https://technet.microsoft.com/library/cc736516\(v=ws.10\).aspx)」を参照してください。

##  <a name="bkmk_stored_credentials_data_source_native"></a>レポート固有のデータソース用の保存された資格情報を構成する (ネイティブモード)

1.  ネイティブ モードのレポート マネージャーで、レポートが含まれているフォルダーに移動します。 ![Ssrs 項目については、レポートマネージャーで項目の](../media/ssrs-report-manager-item-context-menu.png "レポート マネージャーの、SSRS アイテム用のコンテキスト メニュー")コンテキストメニューのコンテキストメニューをクリックします。

2.  
  **[管理]** をクリックして、 **[データ ソース]** をクリックします。

3.  
  **[カスタム データ ソース]** をクリックします。

4.  
  **[データ ソースの種類]** の一覧で、データ ソースから取得したデータの処理に使用するデータ処理拡張機能を選択します。

5.  [**接続文字列**] には、レポートサーバーがデータソースへの接続に使用する接続文字列を指定します。 次の例は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]データベースへの接続に使用される接続文字列を示しています。

    ```
    data source=<servername>;initial catalog=AdventureWorks2012
    ```

6.  
  **[接続に使用する認証]** で、 **[レポート サーバーに保存され、セキュリティで保護された資格情報]** をクリックします。

7.  ユーザー名とパスワードを入力します。

    -   アカウントが\<Windows ドメインユーザーアカウントの場合は、ドメイン>\\<アカウント\>の形式で指定し、[**データソースへの接続時に Windows 資格情報として使用**する] を選択します。

    -   ユーザー名とパスワードがデータベースの資格情報である場合は、 **[データ ソースへの接続時に Windows 資格情報として使用する]** を選択しないでください。 データベース サーバーが権限の借用または委譲をサポートしている場合は、 **[データ ソースへの接続が確立した後に、認証されているユーザーの権限を借用する]** を選択できます。

8.  **[Apply]** をクリックします。

     "![トップに戻る" リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[保存された資格情報のセキュリティポリシー要件](#bkmk_top)

##  <a name="bkmk_stored_credentials_data_source_sharepoint"></a>レポート固有のデータソース用の保存された資格情報の構成 (SharePoint モード)

1.  レポートが含まれているドキュメントライブラリを参照し、ssrs 項目の [開く] メニューの [![ドキュメントライブラリ] コンテキストメニュー](../media/ssrs-sharepoint-item-context-menu.png "ssrs 項目のドキュメント ライブラリのコンテキスト メニュー")をクリックします。

2.  2番目の [開く] メニューをクリックし![て、ssrs 項目のドキュメントライブラリのコンテキストメニュー](../media/ssrs-sharepoint-item-context-menu.png "ドキュメント ライブラリの、SSRS アイテム用のコンテキスト メニュー")を表示し、[**データソースの管理**] をクリックします。

3.  資格情報を使用して構成する **[カスタム]** データ ソースの名前をクリックします。

4.  
  **[データ ソースの種類]** の一覧で、データ ソースから取得したデータの処理に使用するデータ処理拡張機能を選択します。

5.  [**接続文字列**] には、レポートサーバーがデータソースへの接続に使用する接続文字列を指定します。 次の例は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]データベースへの接続に使用される接続文字列を示しています。

    ```
    data source=<servername>;initial catalog=AdventureWorks2012
    ```

6.  
  **[資格情報]** で、 **[格納された資格情報]** を選択します。

7.  
  **[ユーザー名]** と **[パスワード]** を入力します。

    -   アカウントが\<Windows ドメインユーザーアカウントの場合は、ドメイン>\\<アカウント\>の形式で指定し、[**データソースへの接続時に Windows 資格情報として使用**する] を選択します。

    -   ユーザー名とパスワードがデータベースの資格情報である場合は、 **[Windows 資格情報として使用する]** を選択しないでください。 データベースサーバーで権限借用または委任がサポートされている場合は、[**実行コンテキストをこのアカウントに設定**する] を選択できます。

8.  [ **Ok]** をクリックします。

     "![トップに戻る" リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[保存された資格情報のセキュリティポリシー要件](#bkmk_top)

##  <a name="bkmk_stored_credentials_shared_data_source_native"></a>共有データソース用の保存された資格情報を構成する (ネイティブモード)

1.  ネイティブ モードのレポート マネージャーで、共有データ ソース アイテムに移動します。 ![共有データソースのアイコン](../media/hlp-16datasource.png "Shared data source icon")

2.  ![レポートマネージャーの ssrs 項目について](../media/ssrs-report-manager-item-context-menu.png "レポート マネージャーの、SSRS アイテム用のコンテキスト メニュー")、コンテキストメニューのコンテキストメニューをクリックし、[**管理**] をクリックします。

3.  [**データソースの種類**] ボックスの一覧で、データソースからのデータを処理するために使用するデータ処理拡張機能を指定します。

4.  [**接続文字列**] には、レポートサーバーがデータソースへの接続に使用する接続文字列を指定します。 
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] では、接続文字列に資格情報を指定しないことをお勧めします。

     次の例は、ローカル[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]データベースへの接続に使用される接続文字列を示しています。

    ```
    data source=<localservername>; initial catalog=AdventureWorks2012
    ```

5.  ユーザー名とパスワードを入力します。

    -   アカウントが\<Windows ドメインユーザーアカウントの場合は、ドメイン>\\<アカウント\>の形式で指定し、[**データソースへの接続時に Windows 資格情報として使用**する] を選択します。

    -   ユーザー名とパスワードがデータベースの資格情報である場合は、 **[データ ソースへの接続時に Windows 資格情報として使用する]** を選択しないでください。 データベース サーバーが権限の借用または委譲をサポートしている場合は、 **[データ ソースへの接続が確立した後に、認証されているユーザーの権限を借用する]** を選択できます。

6.  **[Apply]** をクリックします。

     "![トップに戻る" リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[保存された資格情報のセキュリティポリシー要件](#bkmk_top)

##  <a name="bkmk_stored_credentials_shared_data_source_sharepoint"></a>共有データソース用の保存された資格情報の構成 (SharePoint モード)

1.  ドキュメントライブラリで、共有データソースアイテムを参照します。![共有データソースのアイコン](../media/hlp-16datasource.png "Shared data source icon")

2.  ![Ssrs 項目のコンテキストメニュードキュメントライブラリのコンテキスト](../media/ssrs-sharepoint-item-context-menu.png "ドキュメント ライブラリの、SSRS アイテム用のコンテキスト メニュー")メニューをクリックし、次に、 ![ssrs 項目の](../media/ssrs-sharepoint-item-context-menu.png "ドキュメント ライブラリの、SSRS アイテム用のコンテキスト メニュー")2 つ目のコンテキストメニュードキュメントライブラリのコンテキストメニューをクリックします。

3.  
  **[データ ソース定義の編集]** をクリックします。

4.  [**データソースの種類**] ボックスの一覧で、データソースからのデータを処理するために使用するデータ処理拡張機能を指定します。

5.  [**接続文字列**] には、レポートサーバーがデータソースへの接続に使用する接続文字列を指定します。 
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] では、接続文字列に資格情報を指定しないことをお勧めします。

     次の例は、ローカル[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]データベースへの接続に使用される接続文字列を示しています。

    ```
    data source=<localservername>; initial catalog=AdventureWorks2012
    ```

6.  ユーザー名とパスワードを入力します。

    -   このアカウントが Windows ドメイン ユーザー アカウントである場合は、\<ドメイン>\\<アカウント\> という形式で指定し、**[Windows 資格情報として使用する]** を選択します。

    -   ユーザー名とパスワードがデータベースの資格情報である場合は、 **[Windows 資格情報として使用する]** を選択しないでください。 データベース サーバーが権限の借用または委譲をサポートしている場合は、 **[実行コンテキストをこのアカウントに設定する]** を選択できます。

7.  
  **[OK]** をクリックします。

     "![トップに戻る" リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[保存された資格情報のセキュリティポリシー要件](#bkmk_top)

## <a name="see-also"></a>参照
 [レポートデータソースの資格情報と接続情報を指定する](../../integration-services/connection-manager/data-sources.md)[レポートのデータソースのプロパティを構成する &#40;レポートマネージャー&#41;](configure-data-source-properties-for-a-report-report-manager.md) [共有データソースを作成、削除、または変更する &#40;レポートマネージャー](../create-delete-or-modify-a-shared-data-source-report-manager.md)&#41;データソース][プロパティページ](../data-sources-properties-page-report-manager.md)&#40;レポートマネージャー [[新しいデータソース] ページ](../new-data-source-page-report-manager.md)&#41;&#40;レポートマネージャー


