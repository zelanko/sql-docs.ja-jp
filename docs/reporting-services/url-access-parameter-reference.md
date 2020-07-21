---
title: URL アクセス パラメーター リファレンス | Microsoft Docs
description: この記事のパラメーターを URL の一部として使用すると、Reporting Services レポートのルック アンド フィールを構成できます。
ms.date: 01/31/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], display options
- URL access [Reporting Services], report display parameters
ms.assetid: 1c3e680a-83ea-4979-8e79-fa2337ae12a3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0ac67de4831d1785f17029bc6c68fa6f7d8aeb16
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "77147385"
---
# <a name="url-access-parameter-reference"></a>URL アクセス パラメーター リファレンス

  次のパラメーターを URL の一部として使用すると、[!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] レポートのルック アンド フィールを構成できます。 ここでは、最も一般的なパラメーターについて説明します。 パラメーターは大文字と小文字が区別されます。レポート サーバーに出力する場合は *rs:* 、HTML ビューアーに出力する場合は *rc:* をパラメーターの先頭に追加します。 デバイスや表示拡張機能に固有のパラメーターを指定することもできます。 デバイスに固有のパラメーターの詳細については、「[URL でデバイス情報設定を指定する](../reporting-services/specify-device-information-settings-in-a-url.md)」を参照してください。
  
> [!IMPORTANT]  
>  SharePoint モード レポート サーバーの場合、SharePoint および `_vti_bin` HTTP プロキシ経由で要求をルーティングする [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] プロキシ構文を URL に含めることは重要です。 プロキシによって、HTTP 要求にコンテキストが追加されます。これは、SharePoint モード レポート サーバーに対してレポートを適切に実行するために必要なコンテキストです。 例については、「[URL アクセスを使用したレポート サーバー アイテムへのアクセス](../reporting-services/access-report-server-items-using-url-access.md)」を参照してください。
> 
> SharePoint と Reporting Services の統合は、SQL Server 2016 以降では使用できません。
  

##  <a name="html-viewer-commands-rc"></a><a name="bkmk_htmlviewer"></a> HTML ビューアー コマンド (rc:)
 - HTML ビューアー コマンドは HTML ビューアーを対象として使用され、接頭辞として *rc:* が付きます。
  
-   **Toolbar**:ツール バーの表示と非表示を切り替えます。 このパラメーターの値が **false**の場合、残りのオプションすべてが無視されます。 このパラメーターを省略すると、サポートされている表示形式でツール バーが自動的に表示されます。 このパラメーターの既定値は **true**です。
  
    > [!IMPORTANT]  
    >  *rc:Toolbar*=**false** は、SharePoint サイト上でホストされているレポートを対象とするために (ドメイン名ではなく) IP アドレスを使用する URL アクセス文字列に対しては機能しません。
  
-   **パラメーター**: ツール バーのパラメーター領域の表示と非表示を切り替えます。 このパラメーターを **true**に設定すると、ツール バーのパラメーター領域が表示されます。 このパラメーターを **false** に設定すると、パラメーター領域は表示されません。ユーザーが表示することもできません。 このパラメーターの値を **Collapsed** に設定すると、パラメーター領域は表示されませんが、ユーザーが表示と非表示を切り替えることができます。 このパラメーターの既定値は **true**です。  
  
     ネイティブ モードの例:
  
    ```  
    https://myrshost/reportserver?/Sales&rc:Parameters=Collapsed  
    ```  
  
     SharePoint モードの例:
  
    ```  
    https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales&rc:Parameters=Collapsed  
    ```  
  
-   **Zoom**: レポート ズーム値を整数のパーセンテージまたは文字列定数として設定します。 標準的な文字列値には **Page Width** と **Whole Page**などがあります。 Internet Explorer 5.0 よりも前のバージョンの Internet Explorer および[!INCLUDE[msCoName](../includes/msconame-md.md)] 以外のすべてのブラウザーでは、このパラメーターが無視されます。 このパラメーターの既定値は **100**です。
  
     ネイティブ モードの例:
  
    ```  
    https://myrshost/reportserver?/Sales&rc:Zoom=Page Width  
    ```  
  
     SharePoint モードの例:
  
    ```  
    https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales&rc:Zoom=Page Width  
    ```  
  
-   **Section**: 表示するレポートのページを設定します。 レポートのページ数よりも大きい値を設定すると、最後のページが表示されます。 **0** よりも小さい値を設定すると、レポートの 1 ページが表示されます。 このパラメーターの既定値は **1**です。
  
     ネイティブ モードで、レポートの 2 ページ目を表示する例:
  
    ```  
    https://myrshost/reportserver?/Sales&rc:Section=2  
    ```  
  
     SharePoint モードで、レポートの 2 ページ目を表示する例:
  
    ```  
    https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales&rc:Section=2  
    ```  
  
-   **FindString**:レポート内で特定のテキスト セットを検索します。
  
     ネイティブ モードの例:
  
    ```  
    https://myrshost/reportserver?/Sales&rc:FindString=Mountain-400  
    ```  
  
     SharePoint モードの例:
  
    ```  
    https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales&rc:FindString=Mountain-400  
    ```  
  
-   **StartFind**: 検索する最後のセクションを指定します。 このパラメーターの既定値は、レポートの最終ページです。  
  
     Product Catalog サンプル レポートの 1 - 5 ページを検索し、最初に出現する "Mountain-400" という文字列を探す、ネイティブ モードの例。
  
    ```  
    https://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
    ```  
  
-   **EndFind**: 検索に使用する最終ページの番号を設定します。 たとえば、 **5** の値は、検索する最後のページがレポートの 5 ページであることを示します。 既定値は現在のページ番号です。 このパラメーターは、 *StartFind* パラメーターと一緒に使用します。 前の例を参照してください。
  
-   **FallbackPage**: 検索またはドキュメント マップの選択が失敗した場合に表示するページ番号を設定します。 既定値は現在のページ番号です。
  
-   **GetImage**: HTML ビューアー ユーザー インターフェイス用の特定のアイコンを取得します。
  
-   **Icon**: 特定の表示拡張機能のアイコンを取得します。
  
-   **Stylesheet**:HTML ビューアーに適用するスタイル シートを指定します。
  
-   **デバイス情報設定**: `rc:tag=value` の形式でデバイス情報設定を指定します。この *tag* は、現在使用されている表示拡張機能に固有のデバイス情報設定の名前です (*Format* パラメーターの説明を参照してください)。たとえば、IMAGE 表示拡張機能の *OutputFormat* デバイス情報設定を使用すると、URL アクセス文字列に `...&rs:Format=IMAGE&rc:OutputFormat=JPEG` パラメーターを指定することで、レポートを JPEG 画像で表示できます。 拡張機能に固有のすべてのデバイス情報設定の詳細については、「[表示拡張機能のデバイス情報設定 &#40;Reporting Services&#41;](../reporting-services/device-information-settings-for-rendering-extensions-reporting-services.md)」を参照してください。
  
##  <a name="report-server-commands-rs"></a><a name="bkmk_reportserver"></a> レポート サーバー コマンド (rs:)
 レポート サーバー コマンドには接頭辞として *rs:* が付き、レポート サーバーを対象として使用されます。
  
-   **コマンド**:アイテムの種類に応じて、カタログ アイテムに対して操作を実行します。 既定値は、URL アクセス文字列で参照されるカタログ アイテムの種類で決まります。 有効な値は次のとおりです。
  
    -   **ListChildren** と **GetChildren**: フォルダーの内容が表示されます。 フォルダー アイテムは、汎用アイテム ナビゲーション ページに表示されます。
  
         ネイティブ モードの例:
  
        ```  
        https://myrshost/reportserver?/Sales&rs:Command=GetChildren  
        ```  
  
         ネイティブ モードの名前付きインスタンスの例:
  
        ```  
        https://myssrshost/Reportserver_THESQLINSTANCE?/reportfolder&rs:Command=listChildren  
        ```  
  
         SharePoint モードの例:
  
        ```  
        https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales&rs:Command=GetChildren  
        ```  
  
    -   **Render**: レポートはブラウザーでレンダリングされ、ユーザーに表示されます。
  
         ネイティブ モードの例:
  
        ```  
        https://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render  
        ```  
  
         SharePoint モードの例:
  
        ```  
        https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render  
        ```  
  
    -   **GetSharedDatasetDefinition**: 共有データセットに関連付けられた XML 定義を表示します。 クエリ、データセット パラメーター、既定値、データセット フィルター、照合順序や大文字と小文字の区別などのデータ オプションを含む共有データセット プロパティは、定義内に保存されます。 この値を使用するには、共有データセットに対する **Read Report Definition** 権限が必要です。
  
         ネイティブ モードの例:
  
        ```  
        https://localhost/reportserver/?/DataSet1&rs:command=GetShareddatasetDefinition  
        ```  
  
    -   **GetDataSourceContents**: 指定した共有データ ソースのプロパティを XML 形式で表示します。 ブラウザーで XML がサポートされていて、目的のデータ ソースに対して **Read Contents** 権限が与えられている認証ユーザーである場合は、そのデータ ソース定義が表示されます。
  
         ネイティブ モードの例:
  
        ```  
        https://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents  
        ```  
  
         SharePoint モードの例:
  
        ```  
        https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents  
        ```  
  
    -   **GetResourceContents**: リソースを表示し、リソースとブラウザーの互換性がある場合は、そのリソースを HTML ページ内に表示します。 それ以外の場合は、ファイルまたはリソースを開くか、ディスクに保存するように求められます。  
  
         ネイティブ モードの例:
  
        ```  
        https://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents  
        ```  
  
         SharePoint モードの例:
  
        ```  
        https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents  
        ```  
  
    -   **GetComponentDefinition**: パブリッシュ済みレポート アイテムに関連付けられた XML 定義を表示します。 この値を使用するには、パブリッシュ済みレポート アイテムに対する **Read Contents** 権限が必要です。
  
-   **Format**: レポートをレンダリングし、表示する形式を指定します。 一般的な値:
  
    -   **HTML5**  
  
    -   **PPTX**  
  
    -   **ATOM**  
  
    -   **HTML4.0**  
  
    -   **MHTML**  
  
    -   **IMAGE**  
  
    -   **EXCEL** (.xls 用)
    
    -   **EXCELOPENXML** (.xlsx 用)
  
    -   **WORD** (.doc 用)
    
    -   **WORDOPENXML** (.docx 用)
  
    -   **CSV**  
  
    -   **PDF**  
  
    -   **XML**  
  
     既定値は **HTML5**です。 詳細については、「[URL アクセスを使用してレポートをエクスポートする](../reporting-services/export-a-report-using-url-access.md)」を参照してください。
  
     完全な一覧が必要な場合、レポート サーバー rsreportserver.config ファイルの **\<Render>** 拡張セクションを参照してください。 ファイルの場所については、「[RsReportServer.config 構成ファイル](../reporting-services/report-server/rsreportserver-config-configuration-file.md)」を参照してください。
  
     たとえば、ネイティブ モードのレポート サーバーから直接レポートの PDF コピーを取得するには、次の URL を使用します。
  
    ```  
    https://myrshost/ReportServer?/myreport&rs:Format=PDF  
    ```  
  
     SharePoint モード レポート サーバーからレポートの PDF コピーを直接取得する例:
  
    ```  
    https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/myrereport.rdl&rs:Format=PDF  
    ```  
  
-   **ParameterLanguage**:ブラウザーの言語とは関係なく、URL で渡されるパラメーターの言語を指定します。 既定値は、ブラウザーの言語です。 値は、 **en-us** や **de-de**などのカルチャ値に設定できます。
  
     ネイティブ モードで、ブラウザーの言語をオーバーライドし、de-DE というカルチャ値を指定する例:
  
    ```  
    https://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008&rs:ParameterLanguage=de-DE  
    ```  
  
-   **スナップショット**:レポート履歴スナップショットに基づいたレポートを表示します。 詳細については、「[URL アクセスを使用してレポート履歴スナップショットを表示する](../reporting-services/render-a-report-history-snapshot-using-url-access.md)」を参照してください。
  
     ネイティブ モードで、日付が 2003-04-07 でタイムスタンプが 13:40:02 のレポート履歴スナップショットを取得する例:
  
    ```  
    https://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
    ```  
  
-   **PersistStreams**:1 つの永続化ストリームでレポートを表示します。 このパラメーターは、表示レポートをチャンク単位で送信するために画像レンダラーによって使用されます。 URL アクセス文字列でこのパラメーターを使用した後、同じ URL アクセス文字列を、 *GetNextStream* パラメーターではなく *PersistStreams* パラメーターと共に使用すると、永続化ストリームの次のチャンクを取得できます。 この URL コマンドは、最終的に永続化ストリームの末尾に到達した時点で 0 バイト ストリームを返します。 既定値は **false** です。
  
-   **GetNextStream**:*PersistStreams* パラメーターを使用してアクセスした永続化ストリームの次のデータ チャンクを取得します。 詳細については、 *PersistStreams*の説明を参照してください。 既定値は **false** です。
  
-   **SessionID**:クライアント アプリケーションとレポート サーバー間で確立されたアクティブ レポート セッションを指定します。 このパラメーターの値は、セッション ID に設定されます。
  
     セッション ID をクッキーまたは URL の一部として指定できます。 セッション クッキーを使用しないようにレポート サーバーを構成している場合、指定したセッション ID なしの最初の要求はセッション ID 付きでリダイレクトされます。 レポート サーバーのセッションの詳細については、「[実行状態の識別](../reporting-services/report-server-web-service-net-framework-soap-headers/identifying-execution-state.md)」を参照してください。
  
-   **ClearSession**:値が **true** の場合は、レポート セッションからレポートを削除するようにレポート サーバーに指示します。 認証されているユーザーに関連付けられたすべてのレポート インスタンスがレポート セッションから削除されます (レポート インスタンスは、別のレポート パラメーターの値を指定して、レポートを複数回実行するように定義されます)。既定値は **false** です。
  
-   **ResetSession**:値が **true** の場合は、レポート セッションのすべてのレポート スナップショットとの関連付けを削除することによって、レポート セッションをリセットするようレポート サーバーに指示します。 既定値は **false** です。
  
-   **ShowHideToggle**:レポートのセクションの表示と非表示を切り替えます。 切り替えるセクションを表す正の整数を指定します。
  
##  <a name="report-viewer-web-part-commands-rv"></a><a name="bkmk_webpart"></a> レポート ビューアー Web パーツのコマンド (rv:)
 次の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] レポート パラメーター名は予約されており、SharePoint と統合されているレポート ビューアー Web パーツを対象とするために使用されます。 これらのパラメーター名の先頭には *rv:* が付いています。 レポート ビューアー Web パーツでは、*rs:ParameterLanguage* パラメーターも受け取られます。
  
-   **Toolbar**:レポート ビューアー Web パーツのツール バーの表示を制御します。 既定値は **Full**です。 可能な値は次のとおりです。
  
    -   **Full**:ツール バーを完全に表示します。
  
    -   **ナビゲーション**: ツール バーに改ページのみを表示します。
  
    -   **なし**: ツール バーを表示しません。
  
     SharePoint モードで、ツール バーに改ページのみを表示する例:
  
    ```  
    https://myspsite/_vti_bin/reportserver?https://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:Toolbar=Navigation  
    ```  
  
-   **HeaderArea**:レポート ビューアー Web パーツのヘッダーの表示を制御します。 既定値は **Full**です。 可能な値は次のとおりです。
  
    -   **Full**:ヘッダーを完全に表示します。
  
    -   **BreadCrumbsOnly**: ヘッダーに階層リンクのナビゲーションのみを表示して、アプリケーションでの現在位置をユーザーに示します。
  
    -   **なし**: ヘッダーを表示しません。
  
     SharePoint モードで、ヘッダーに階層リンクのナビゲーションのみを表示する例:
  
    ```  
    https://myspsite/_vti_bin/reportserver?https://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:HeaderArea=BreadCrumbsOnly  
    ```  
  
-   **DocMapAreaWidth**:レポート ビューアー Web パーツのパラメーター領域の表示幅をピクセル単位で制御します。 既定値は、レポート ビューアー Web パーツの既定値と同じです。 値には、負以外の整数値を指定する必要があります。
  
-   **AsyncRender**:レポートが非同期に表示されるかどうかを制御します。 既定値は **true**で、レポートが非同期に表示されることを示します。 この値には、 **true** または **false**のブール値を指定する必要があります。
  
-   **ParamMode**:レポート ビューアー Web パーツのパラメーター プロンプト領域を全体表示で表示する方法を制御します。 既定値は **Full**です。 有効な値は次のとおりです。
  
    -   **Full**:パラメーター プロンプト領域を表示します。
  
    -   **Collapsed**: パラメーター プロンプト領域を折りたたみます。
  
    -   **Hidden**: パラメーター プロンプト領域を非表示にします。
  
     SharePoint モードで、パラメーター プロンプト領域を折りたたむ例:
  
    ```  
    https://myspsite/_vti_bin/reportserver?https://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:ParamMode=Collapsed  
    ```  
  
-   **DocMapMode**:レポート ビューアー Web パーツのドキュメント マップ領域を全体表示で表示する方法を制御します。 既定値は **Full**です。 有効な値は次のとおりです。
  
    -   **Full**:ドキュメント マップ領域を表示します。
  
    -   **Collapsed**: ドキュメント マップ領域を折りたたみます。
  
    -   **Hidden**: ドキュメント マップ領域を非表示にします。
  
-   **DockToolBar**:レポート ビューアー Web パーツのツール バーを上部にドッキングするか、下部にドッキングするかを制御します。 有効値は **Top** および **Bottom**です。 既定値は **Top**です。
  
     SharePoint モードで、下部にツール バーをドッキングする例:
  
    ```  
    https://myspsite/_vti_bin/reportserver?https://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:DockToolBar=Bottom  
    ```  
  
-   **ToolBarItemsDisplayMode**:表示するツール バー項目を制御します。 これはビットごとの列挙値です。 ツール バー項目を含めるには、項目の値を合計値に加算します。 たとえば、 **[操作]** メニューなしにする場合は、*rv:ToolBarItemsDisplayMode=63* (または 0x3F) を使用します。これは、1 + 2 + 4 + 8 + 16 + 32 です。 **[操作]** メニュー項目のみにする場合は、*rv:ToolBarItemsDisplayMode=960* (or 0x3C0) を使用します。 既定値は **-1**です。すべてのツール バー項目を表示します。 有効な値は次のとおりです。
  
    -   **1 (0x1)** : **[戻る]** ボタン  
  
    -   **2 (0x2)** : テキスト検索コントロール  
  
    -   **4 (0x4)** : ページ ナビゲーションのコントロール  
  
    -   **8 (0x8)** : **[更新]** ボタン  
  
    -   **16 (0x10)** : **[ズーム]** リスト ボックス  
  
    -   **32 (0x20)** : **[Atom フィード]** ボタン  
  
    -   **64 (0x40)** : **[操作]** の **[印刷]** メニュー オプション  
  
    -   **128 (0x80)** : **[操作]** の **[エクスポート]** サブメニュー  
  
    -   **256 (0x100)** : **[操作]** の **[レポート ビルダーで開く]** メニュー オプション  
  
    -   **512 (0x200)** : **[操作]** の **[サブスクライブ]** メニュー オプション  
  
    -   **1024 (0x400)** : **[操作]** の **[新しいデータの警告]** メニュー オプション  
  
     SharePoint モードで、 **[戻る]** ボタン、テキスト検索コントロール、ページ ナビゲーション コントロール、 **[更新]** ボタンのみを表示する例:
  
    ```  
    https://myspsite/_vti_bin/reportserver?https://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:ToolBarItemsDisplayMode=15  
    ```  
  
## <a name="see-also"></a>関連項目
 - [URL アクセス &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)
 - [URL アクセスを使用してレポートをエクスポートする](../reporting-services/export-a-report-using-url-access.md)
  
  
