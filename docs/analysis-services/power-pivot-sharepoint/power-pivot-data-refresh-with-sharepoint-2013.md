---
title: Power Pivot SharePoint 2013 でのデータの更新 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 583059b93268f3652cf2e8f324574ec739d449dd
ms.sourcegitcommit: 706f3a89fdb98e84569973f35a3032f324a92771
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658233"
---
# <a name="power-pivot-data-refresh-with-sharepoint-2013"></a>SharePoint 2013 での PowerPivot データ更新
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  SharePoint 2013 での [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ モデルの更新に対応する設計では、主要なコンポーネントとして Excel Services を使用し、SharePoint モードで実行されている [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス上でデータ モデルを読み込んで更新します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーは、SharePoint ファームの外部で実行されます。 SharePoint 2013 の Excel Services のアーキテクチャでは、 **対話型のデータ更新** と **定期データ更新**の両方がサポートされています。  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013  
  
 **このトピックの内容:**  
  
-   [Interactive Data Refresh](#bkmk_interactive_refresh)  
  
-   [ブックのデータ接続と対話型のデータ更新による Windows 認証](#bkmk_windows_auth_interactive_data_refresh)  
  
-   [Scheduled Data Refresh](#bkmk_scheduled_refresh)  
  
-   [SharePoint 2013 の定期データ更新のアーキテクチャ](#bkmk_refresh_architecture)  
  
-   [認証に関するその他の注意点](#datarefresh_additional_authentication)  
  
-   [その他の情報](#bkmk_moreinformation)  
  
## <a name="background"></a>背景情報  
 SharePoint Server 2013 の Excel Services は、Excel 2013 ブックのデータ更新を管理し、SharePoint モードで実行されている [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーでデータ モデル処理をトリガーします。 Excel 2010 ブックの場合、Excel Services はブックおよびデータ モデルの読み込みと保存も管理します。 ただし、Excel Services は [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスを使用して処理コマンドをデータ モデルに送信します。 次の表は、データ更新の処理コマンドを送信するコンポーネントをブックのバージョンごとにまとめたものです。 想定した環境は、SharePoint モードで実行されている [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 分析サーバーを使用するように構成された SharePoint 2013 ファームです。  
  
||||  
|-|-|-|  
||Excel 2013 ブック|Excel 2010 ブック|  
|データ更新をトリガーする|**対話型。** Authenticated User<br /><br /> **スケジュール済み。**[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービス|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービス|  
|コンテンツ データベースからブックを読み込む|SharePoint 2013 の Excel Services|SharePoint 2013 の Excel Services|  
|Analysis Services インスタンスでデータ モデルを読み込む|SharePoint 2013 の Excel Services|SharePoint 2013 の Excel Services|  
|Analysis Services インスタンスに処理コマンドを送信する|SharePoint 2013 の Excel Services|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービス|  
|ブック データを更新する|SharePoint 2013 の Excel Services|SharePoint 2013 の Excel Services|  
|コンテンツ データベースにブックとデータ モデルを保存する|**対話型。** なし<br /><br /> **スケジュール済み。** SharePoint 2013 の Excel Services|SharePoint 2013 の Excel Services|  
  
 次の表は、SharePoint モードで実行されている [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 分析サーバーを使用するように構成された SharePoint 2013 ファームでサポートされている更新機能をまとめたものです。  
  
|ブックの作成環境|定期データ更新|対話型の更新|  
|-------------------------|----------------------------|-------------------------|  
|2008 R2 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel|サポートされていません。 ブックをアップグレードしてください **[メニューを開く]\*)**|サポートされていません。 ブックをアップグレードしてください **[メニューを開く]\*)**|  
|2012 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel|サポートされている|サポートされていません。 ブックをアップグレードしてください **[メニューを開く]\*)**|  
|Excel 2013|サポートされている|サポートされている|  
  
 **(\*)** ブックのアップグレードの詳細については、「[ブックのアップグレードと定期データ更新 (SharePoint 2013)](../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)」を参照してください。  
  
##  <a name="bkmk_interactive_refresh"></a> Interactive Data Refresh  
 SharePoint Server 2013 の Excel Services で、対話型または手動のデータ更新は、元のデータ ソースから取得したデータを使用してデータ モデルを更新できます。 対話型のデータ更新は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーに登録して Excel Services アプリケーションを構成すると使用できるようになり、SharePoint モードで実行されます。 詳細については、次を参照してください。 [Excel Services の管理のデータ モデルの設定 (SharePoint Server 2013)](http://technet.microsoft.com/library/jj219780.aspx) (http://technet.microsoft.com/library/jj219780.aspx)します。  
  
> [!NOTE]
>  対話型のデータ更新は、Excel 2013 で作成されたブックでのみ使用できます。 Excel Services がのようなエラー メッセージを表示する場合は、Excel 2010 ブックを更新しようとすると、"[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]操作が失敗しました。ブックが Excel の古いバージョンで作成されたと[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]ファイルがアップグレードされるまでに更新することはできません"です。 ブックのアップグレードの詳細については、「[ブックのアップグレードと定期データ更新 (SharePoint 2013)](../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)」を参照してください。  
  
 **対話型の更新の要点**  
  
-   対話型のデータ更新では、現在のユーザー セッションにあるデータのみが更新されます。 データは、SharePoint コンテンツ データベースにある元のブック アイテムには自動的に保存されません。  
  
-   **資格情報:** 対話型のデータ更新では、データ ソースに接続する場合、現在ログインしているユーザーの ID を資格情報として使用するか、または保存された資格情報を使用できます。 使用される資格情報は、外部データ ソースへのブックの接続用に定義された Excel Services の認証設定によって異なります。  
  
-   **サポートされるブック。** Excel 2013 で作成されたブック。  
  
 **データを更新するには**  
  
-   手順に沿った図を参照してください。  
  
1.  SharePoint ドキュメント ライブラリで、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックをブラウザーで開きます。  
  
2.  ブラウザー ウィンドウで **[データ]** メニューをクリックしたら、 **[選択した接続の更新]** または **[すべての接続の更新]** をクリックします。  
  
3.  Excel Services が [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データベースを読み込み、処理してからクエリを実行して、Excel ブックのキャッシュを更新します。  
  
4.  **注:** 更新されたブックは、元のドキュメント ライブラリには自動的に保存されません。  
  
 ![対話型のデータ更新](../../analysis-services/power-pivot-sharepoint/media/as-interactive-datarefresh-sharepoint2013.gif "対話型のデータ更新")  
  
###  <a name="bkmk_windows_auth_interactive_data_refresh"></a> ブックのデータ接続と対話型のデータ更新による Windows 認証  
 Excel Services は、ユーザー アカウントを借用するようサーバーに指示するプロセス コマンドを Analysis Services サーバーに送信します。 Analysis Services サービス アカウントで、ユーザーの権限借用委任プロセスを実行するのに十分なシステム権限を取得するには、ローカル サーバーに **[オペレーティング システムの一部として機能]** 権限が必要です。 また、Analysis Services サーバーでは、ユーザーの資格情報をデータ ソースに委任できる必要があります。 クエリの結果は Excel Services に送信されます。  
  
 一般的なユーザー エクスペリエンス:含んでいる Excel 2013 ブックで、顧客が"すべての接続の更新 を選択すると、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]モデルでは、次のようなエラー メッセージを表示します。  
  
-   **外部データの更新に失敗しました。** ブック内のデータ モデルでの作業中にエラーが発生しました。 再試行してください。 このブックの 1 つ以上のデータ接続を更新できません。  
  
 使用しているデータ プロバイダーによっては、ULS ログに次のようなメッセージが表示されます。  
  
 **SQL Native Client の場合**  
  
-   外部接続の作成またはクエリの実行を行うことができませんでした。 プロバイダー メッセージ:アウト オブ ライン オブジェクト 'DataSource' は ID(s) ' 20102481-39 c 8 4 d 21-bf63-68f583ad22bb を参照する '、指定されていますが、使用されていません。  OLE DB または ODBC エラー:SQL Server への接続を確立中に、ネットワークに関連するエラーまたはインスタンス固有のエラーが発生しました。 サーバーが見つからないか、アクセスできません。 インスタンス名が正しいことと、SQL Server がリモート接続を許可するように構成されていることを確認してください。 詳細については、SQL Server オンライン ブックで以下を参照してください: 08001。SSL プロバイダー: 要求されたセキュリティ パッケージが存在しません。08001;クライアント接続を確立できません。08001;暗号化クライアントでサポートされていません;。08001。  、ConnectionName:ThisWorkbookDataModel、ブック: book1.xlsx。  
  
 **Microsoft OLE DB Provider for SQL Server の場合**  
  
-   外部接続の作成またはクエリの実行を行うことができませんでした。 プロバイダー メッセージ:ID '6e711bfa-b62f-4879-a177-c5dd61d9c242' を参照するアウト オブ ライン オブジェクト 'DataSource' は指定されていますが、使用されていません。 OLE DB または ODBC エラー。 、ConnectionName:ThisWorkbookDataModel。ブック:OLEDB Provider.xlsx。  
  
 **.NET Framework Data Provider for SQL Server の場合**  
  
-   外部接続の作成またはクエリの実行を行うことができませんでした。 プロバイダー メッセージ:アウト オブ ライン オブジェクト 'DataSource' は id ' f5fb916c 3eac-4 d 07-a542-531524c0d44a' が指定されていますが、使用されていません。  高レベル リレーショナル エンジンでエラーが発生しました。 IDbConnection マネージド インターフェイスが使用されているときに、次の例外が発生しました。ファイルまたはアセンブリ 'System.Transactions, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'、またはその依存関係の 1 つが読み込めませんでした。 必要な偽装レベルが指定されなかったか、または指定された偽装レベルが無効です。 (HRESULT からの例外: 0x80070542)。  、ConnectionName:ThisWorkbookDataModel。ブック:NETProvider.xlsx。  
  
 **構成手順の概要** ローカル サーバーで **[オペレーティング システムの一部として機能]** 権限を構成するには  
  
1.  SharePoint モードで実行されている Analysis Services サーバーで、[オペレーティング システムの一部として機能] 権限に Analysis Services のサービス アカウントを追加します。  
  
    1.  実行"`secpol.msc`"  
  
    2.  **[ローカル セキュリティ ポリシー]**、 **[ローカル ポリシー]**、 **[ユーザー権利の割り当て]** の順にクリックします。  
  
    3.  サービス アカウントを追加します。  
  
2.  Excel Services を再開し、Analysis Services サーバーを再起動します。  
  
3.  Excel Services サービス アカウントまたは Claims to Windows Token Service (C2WTS) から Analysis Services インスタンスへの委任は必要ありません。 したがって、Excel Services または C2WTS から [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] AS サービスへの KCD の構成は必要ありません。 バックエンド データ ソースが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスと同じサーバーにある場合、Kerberos 制約付き委任は必要ありません。 ただし、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サービス アカウントには、オペレーティング システムの一部として機能する権限が必要です。  
  
 ![as_interactive_data_refresh2012SP1_windowsauth](../../analysis-services/power-pivot-sharepoint/media/as-interactive-data-refresh2012sp1-windowsauth.gif "as_interactive_data_refresh2012SP1_windowsauth")  
  
 詳細については、次を参照してください。[オペレーティング システムの一部として機能](http://technet.microsoft.com/library/cc784323\(WS.10\).aspx)(http://technet.microsoft.com/library/cc784323(WS.10).aspx)します。  
  
##  <a name="bkmk_scheduled_refresh"></a> Scheduled Data Refresh  
 **定期データ更新の要点**  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint アドインのデプロイが必要です。 詳細については、「 [Power Pivot for SharePoint アドインのインストールまたはアンインストール &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)」を参照してください。  
  
-   ユーザーはブックの更新スケジュールを構成します。 予定の時間になると、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスから Excel Services に対して次の要求が送信されます。  
  
    -   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データベースを読み込んで処理する。  
  
    -   ブックを更新する。  
  
    -   元のコンテンツ データベースにブックを保存する。  
  
-   **資格情報:** 保存された資格情報を使用します。 現在のユーザーの ID は使用しません。  
  
-   **サポートされるブック。** 使用して作成されたブック、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel 2010 アドインまたは Excel 2013 を使用します。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] アドインを使用して Excel 2010 で作成されたブックはサポートされていません。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 以上の形式でブックをアップグレードしてください。 ブックのアップグレードの詳細については、「[ブックのアップグレードと定期データ更新 (SharePoint 2013)](../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)」を参照してください。  
  
 **[データ更新の管理]** ページを表示するには  
  
-   手順に沿った図を参照してください。  
  
1.  SharePoint ドキュメント ライブラリで、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックの **[メニューを開く]** (**...**) をクリックします。  
  
2.  2 番目の **[メニューを開く]** をクリックしてから、**[[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] のデータ更新の管理]** をクリックします。  
  
3.  **[データ更新の管理]** ページで **[有効化]** をクリックし、更新のスケジュールを構成します。  
  
4.  指定の時間になると、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスから Excel Services に次の要求が送信されます。  
  
    -   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ モデルを読み込んで処理する。  
  
    -   ブックを更新する。  
  
    -   元のコンテンツ データベースにブックを保存する。  
  
 ![データ更新のコンテキスト メニューを管理](../../analysis-services/power-pivot-sharepoint/media/as-manage-datarefresh-sharepoint2013.gif "データ更新のコンテキスト メニューの管理")  
  
> [!TIP]  
>  SharePoint からオンライン ブックの更新方法の詳細については、次を参照してください。 [SharePoint Online (ホワイト ペーパー) からの埋め込みの Power Pivot モデルを使用した更新の Excel ブック](http://technet.microsoft.com/library/jj992650.aspx)(http://technet.microsoft.com/library/jj992650.aspx)します。  
  
##  <a name="bkmk_refresh_architecture"></a> SharePoint 2013 の定期データ更新のアーキテクチャ  
 次の図は、SharePoint 2013 および SQL Server 2012 SP1 のデータ更新のアーキテクチャをまとめたものです。  
  
 ![SQL Server 2012 SP1 データ更新のアーキテクチャ](../../analysis-services/power-pivot-sharepoint/media/as-scheduled-data-refresh2012sp1-architecture.gif "SQL Server 2012 SP1 データ更新のアーキテクチャ")  
  
||説明||  
|-|-----------------|-|  
|**(1)**|Analysis Services エンジン|SharePoint モードで実行されている [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーでデータ モデル処理をトリガーします。 サーバーは SharePoint ファームの外部で実行されます。|  
|**(2)**|ユーザー インターフェイス|ユーザー インターフェイスは 2 ページで構成されています。 スケジュールを定義するページと、更新履歴を表示するページです。 これらのページでは [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション データベースに直接アクセスしませんが、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスを使用してデータベースにアクセスします。|  
|**(3)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービス|サービスは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint アドインのデプロイ時にインストールされます。<br /><br /> サービスは次の目的に使用されます。|  
|||このサービスは、Excel 2013 ブックのデータ更新の Excel Services API を呼び出す更新スケジュール エンジンをホストします。 Excel 2010 ブックの場合、サービスはデータ モデル処理を直接実行しますが、データ モデルの読み込みとブックの更新には Excel Services を引き続き使用します。|  
|||このサービスには、システム サービスと通信するコンポーネントのメソッド (ユーザー インターフェイスのページなど) が用意されています。|  
|||[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Web サービスを経由して受信するブックへの外部アクセス要求をデータ ソースとして管理します。|  
|||タイマー ジョブと構成ページの定期データ更新要求の管理。 サービスは、サービス アプリケーション データベースの内外でのデータの読み取り要求と、Excel Services を使用したデータ更新のトリガーの要求を管理します。|  
|||使用状況の処理と関連するタイマー ジョブ。|  
|**(4)**|Excel Calculation Services|データ モデルの読み込みを管理します。|  
|**(5)**|Secure Store Service|ブックの認証設定が構成されているかどうかは**認証されたユーザーのアカウントを使用して、** または**None**、Secure Store ターゲット アプリケーション ID に格納されている資格情報をデータに使用されます更新します。 詳細については、このトピックの「 [認証に関するその他の注意点](#datarefresh_additional_authentication) 」を参照してください。|  
|**(6)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ更新タイマー ジョブ|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスに対し、データ モデルを更新する場合は Excel Services に接続するように指示します。|  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、SharePoint モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーがデータ ソースにアクセスできるように、適切なデータ プロバイダーとクライアント ライブラリが必要になります。  
  
> [!NOTE]  
>  現在、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスでは [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] モデルの読み込みと保存を行わないため、アプリケーション サーバーでのモデルのキャッシュに関する設定のほとんどは SharePoint 2013 ファームに適用されません。  
  
## <a name="data-refresh-log-data"></a>データ更新ログ データ  
 **使用状況データ:** データ更新の使用状況データを表示することができます、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]管理ダッシュ ボード。 使用状況データを表示するには、次の手順に従います。  
  
1.  SharePoint サーバーの全体管理の **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] [アプリケーションの全般設定]** グループで **管理ダッシュボード** をクリックします。  
  
2.  ダッシュ ボードの下部には、次を参照してください。、**データ更新 - 最近のアクティビティ**と**データ更新 - 最近のエラー**します。  
  
3.  使用状況データの詳細と使用状況データを有効にする方法については、「 [Power Pivot Management Dashboard and Usage Data](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)」を参照してください。  
  
 **診断ログ データ:** データ更新に関連する SharePoint の診断ログ データを表示できます。 まず、SharePoint サーバーの全体管理の **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] [監視]** ページで、 **サービス** の診断ログの構成を確認します。 「最も低いイベント」のログ記録のレベルを上げる必要がありますをログにします。 たとえば、値を一時的に **[詳細]** に設定して、データ更新操作を再実行します。  
  
 ログ エントリには次のものがあります。  
  
-   **サービス** の **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] [エリア]**。  
  
-   **[データ更新]** のカテゴリ。  
  
 **[診断ログの構成]** を確認します。 詳細については、「[SharePoint ログ ファイルと診断ログの構成と表示 &#40;Power Pivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md)」を参照してください。
  
##  <a name="datarefresh_additional_authentication"></a> 認証に関するその他の注意点  
 Excel 2013 の **[Excel Services の認証設定]** ダイアログ ボックスの設定によって、Excel Services および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] がデータ更新に使用する Windows ID が決まります。  
  
-   **認証されたユーザーのアカウントを使用して、**:Excel Services は、現在ログインしているユーザーの ID でデータ更新を実行します。  
  
-   **保存されたアカウントを使用して、**:SharePoint の Secure Store Service アプリケーションの ID が必要です。この ID を Excel Services で使用して、データ更新認証を認証するためのユーザー名とパスワードを取得します。  
  
-   **[なし]**:Excel Services**無人サービス アカウント**使用されます。 サービス アカウントは、Secure Store プロキシに関連付けられます。 **[外部データ]** セクションの **[Excel Services アプリケーションの設定]** ページの設定を構成します。  
  
 認証の設定のダイアログを開くには  
  
1.  Excel 2013 の **[データ]** タブをクリックします。  
  
2.  リボンで **[接続]** をクリックします。  
  
3.  **[ブックの接続]** ダイアログで、接続を選択して **[プロパティ]** をクリックします。  
  
4.  **接続プロパティ**ダイアログ ボックスで、をクリックして**定義**、順にクリックします、**認証設定しています.** ボタンをクリックします。  
  
 ![excel services authentication settings](../../analysis-services/power-pivot-sharepoint/media/as-authentication-settings-4-ecs-in-excel2013.gif "excel services authentication settings")  
  
 データ更新認証と資格情報の利用状況の詳細については、ブログ記事「 [SharePoint 2013 での PowerPivot データの更新](http://blogs.msdn.com/b/analysisservices/archive/2012/12/21/refreshing-powerpivot-data-in-sharepoint-2013.aspx)」を参照してください。  
  
##  <a name="bkmk_moreinformation"></a> その他の情報  
 [PowerPivot データ更新のトラブルシューティング](http://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx)。  
  
 [Excel Services が SharePoint で](/sharepoint/dev/general-development/excel-services-in-sharepoint)します。  
  
## <a name="see-also"></a>参照  
 [Power Pivot モードでの Analysis Services のインストール](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
  
