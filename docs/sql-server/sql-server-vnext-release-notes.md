---
title: "SQL Server vNext リリース ノート | Microsoft Docs"
ms.custom: 
ms.date: 03/12/2017
ms.prod: sql-vnext
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
caps.latest.revision: 41
author: craigg-msft
ms.author: craigg
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 93d6640c3842f36f1da10b035ae32b1f0dfc027b
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-vnext-release-notes"></a>SQL Server vNext リリース ノート
このトピックでは、[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] での制限事項と問題について説明します。

- このリリースの新機能については、「 [What's New in SQL Server vNext](../sql-server/what-s-new-in-sql-server-vnext.md)」 (SQL Server vNext の新機能) を参照してください。
- [SQL Server on Linux リリース ノート](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes) が拡大中の新しいドキュメント プラットフォームで公開されています。
- [SQL Server Reporting Services リリース ノート](../reporting-services/reporting-services-release-notes.md) は Reporting Services のセクションで公開されています。

 **お試しください:**    
   -   [![Evaluation Center からダウンロードする](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477) **[Evaluation Center から [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] をダウンロードする](http://go.microsoft.com/fwlink/?LinkID=829477)**


## <a name="sql-server-vnext-ctp-14-march--2017"></a>SQL Server vNext CTP 1.4 (2017 年 3 月)
### <a name="supported-installation-scenarios-ctp-14"></a>サポートされているインストール シナリオ (CTP 1.4)

### <a name="documentation-ctp-14"></a>ドキュメント (CTP 1.4)
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] のドキュメントは制限されており、コンテンツは [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] ドキュメント セットに付属しています。  記事の中で [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] に固有のコンテンツは、 **適用対象**で言及されます。 
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]の場合、オフライン コンテンツを利用できません。

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-vnext-ctp-13-february--2017"></a>SQL Server vNext CTP 1.3 (2017 年 2 月)
### <a name="supported-installation-scenarios-ctp-13"></a>サポートされているインストール シナリオ (CTP 1.3)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] はテスト バージョンとしてのみ使用できます。  運用環境での展開はサポートされません。 仮想マシンに [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] をインストールし、テストすることが推奨されます。

### <a name="documentation-ctp-13"></a>ドキュメント (CTP 1.3)
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] のドキュメントは制限されており、コンテンツは [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] ドキュメント セットに付属しています。  記事の中で [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] に固有のコンテンツは、 **適用対象**で言及されます。 
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]の場合、オフライン コンテンツを利用できません。

### <a name="sql-server-integration-services-ssis-ctp-13"></a>SQL Server Integration Services (SSIS) (CTP 1.3)
#### <a name="cdc-components-not-supported-in-this-ctp-release"></a>この CTP リリースでは、CDC コンポーネントはサポートされていません
-   **問題とユーザーへの影響**: この CTP リリースでは、CDC 制御タスク、CDC ソース、および CDC スプリッターはサポートされていません。
-   **回避策:**回避策はありません。


![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-vnext-ctp-12-january--2017"></a>SQL Server vNext CTP 1.2 (2017 年 1 月)
### <a name="supported-installation-scenarios-ctp-12"></a>サポートされているインストール シナリオ (CTP 1.2)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] はテスト バージョンとしてのみ使用できます。  運用環境での展開はサポートされません。 仮想マシンに [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] をインストールし、テストすることが推奨されます。

### <a name="sql-server-database-engine-ctp-12"></a>SQL Server データベース エンジン (CTP 1.2)
- **問題およびユーザーへの影響:** MSSQLSERVER サービスが "開始" 状態で停止する場合があります。
- **回避策:** この問題は次の方法で回避できます。
  -  `mssqlserver` サービスおよび `keyiso` サービスの間で依存関係を作成する。 これを行う方法の&1; つは、管理者特権のコマンド プロンプトから `sc config mssqlserver depend= keyiso`のコマンドを実行することです。
  - コンピューターを再起動します。

### <a name="documentation-ctp-12"></a>ドキュメント (CTP 1.2)
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] のドキュメントは制限されており、コンテンツは [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] ドキュメント セットに付属しています。  記事の中で [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] に固有のコンテンツは、 **適用対象:**で言及されます。 
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]の場合、オフライン コンテンツを利用できません。
 
### <a name="sql-server-integration-services-ssis-ctp-12"></a>SQL Server Integration Services (SSIS) (CTP 1.2)
#### <a name="deleting-the-ssis-catalog-may-fail-when-ssis-scale-out-is-installed"></a>SSIS Scale Out がインストールされているとき、SSIS カタログを削除できないことがある
**問題とユーザーへの影響**: SSIS Scale Out 機能をコンピューターにインストールするときに、“Could not drop login *'login'* as the user is currently logged in” (ユーザーがログイン中のため、ログイン 'login' を切断できません) というエラーが表示され、SSISDB カタログ データベースを削除できないことがあります。
   
**回避策**:
-   Scale Out Master コンピューターで、"services.msc" コマンドを実行して [サービス] ウィンドウを開きます。 SQL Server Integration Services Cluster Master サービスを停止します。
-   マスターに接続する Scale Out Worker コンピューターで、コマンド "services.msc" を実行し、[サービス] ウィンドウを開きます。 SQL Server Integration Services Cluster Worker サービスを停止します。

SSISDB カタログ データベースを削除できるようになりました。

### <a name="sql-server-master-data-services-ctp-12"></a>SQL Server マスター データ サービス (CTP 1.2)
#### <a name="transaction-may-not-work-when-the-entity-transaction-log-type-is-set-to-attribute"></a>エンティティ トランザクション ログ タイプが属性に設定されているとき、トランザクションが機能しないことがある
**問題およびユーザーへの影響:** エンティティ トランザクション ログ タイプが **で** [属性] [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] に設定されているとき (既定値は **[メンバー]**)、次のシナリオが失敗します。

* エンティティ変更のトランザクションは Web サイトに表示されません。
* Web サイトの **[トランザクション]** ページを開いたり、トランザクションを破棄したりできません。
* Web サイトで、エンティティをトランザクションの注釈で更新できません。

**回避策:**回避策はありません。

#### <a name="copy-version-may-not-work-when-copy-only-committed-version-is-set-to-false"></a>**[コミットされたバージョンのみをコピーする]** が偽に設定されているとき、バージョンをコピーできないことがある
-  **問題およびユーザーへの影響:** **[コミットされたバージョンのみをコピーする]** 設定が **[いいえ]** に設定されていると (既定値は **[はい]**)、バージョン コピー操作が失敗することがあります。 エラー メッセージがありません。
-  **回避策:**回避策はありません。

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-vnext-ctp-11-december--2016"></a>SQL Server vNext CTP 1.1 (2016 年 12 月)
### <a name="supported-installation-scenarios-ctp-11"></a>サポートされているインストール シナリオ (CTP 1.1)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] はテスト バージョンとしてのみ使用できます。  運用環境での展開はサポートされません。 仮想マシンに [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] をインストールし、テストすることが推奨されます。

厳密に言うと、次のシナリオは機能する場合もありますが、完全にはテストされておらず、 **では** サポートされていません [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]。
- CTP 1.1 のアンインストール。
- 古いバージョンの SQL Server とのサイド バイ サイド インストール。
- 以前のバージョンの SQL Server からのアップグレード。
- [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] インストールでは、SQL Server 機能パック コンポーネントは利用できません。

### <a name="documentation-ctp-11"></a>ドキュメント (CTP 1.1)
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] のドキュメントは制限されており、コンテンツは [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] ドキュメント セットに付属しています。  記事の中で [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] に固有のコンテンツは、 **適用対象:**で言及されます。 
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]の場合、オフライン コンテンツを利用できません。

### <a name="sql-server-master-data-services-ctp-11"></a>SQL Server マスター データ サービス (CTP 1.1)
#### <a name="transaction-may-not-work-when-the-entity-transaction-log-type-is-set-to-attribute"></a>エンティティ トランザクション ログ タイプが属性に設定されているとき、トランザクションが機能しないことがある
**問題およびユーザーへの影響:** エンティティ トランザクション ログ タイプが **で** [属性] [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] に設定されているとき (既定値は **[メンバー]**)、次のシナリオが失敗します。

* エンティティ変更のトランザクションは Web サイトに表示されません。
* Web サイトの **[トランザクション]** ページを開いたり、トランザクションを破棄したりできません。
* Web サイトで、エンティティをトランザクションの注釈で更新できません。

**回避策:**回避策はありません。

#### <a name="copy-version-may-not-work-when-copy-only-committed-version-is-set-to-false"></a>**[コミットされたバージョンのみをコピーする]** が偽に設定されているとき、バージョンをコピーできないことがある
-  **問題およびユーザーへの影響:** **[コミットされたバージョンのみをコピーする]** 設定が **[いいえ]** に設定されていると (既定値は **[はい]**)、バージョン コピー操作が失敗することがあります。 エラー メッセージがありません。
-  **回避策:**回避策はありません。

### <a name="sql-server-integration-services-ssis-ctp-11"></a>SQL Server Integration Services (SSIS) (CTP 1.1)
#### <a name="deleting-the-ssis-catalog-may-fail-when-ssis-scale-out-is-installed"></a>SSIS Scale Out がインストールされているとき、SSIS カタログを削除できないことがある
**問題とユーザーへの影響**: SSIS Scale Out 機能をコンピューターにインストールするときに、“Could not drop login *'login'* as the user is currently logged in” (ユーザーがログイン中のため、ログイン 'login' を切断できません) というエラーが表示され、SSISDB カタログ データベースを削除できないことがあります。
   
**回避策**:
-   Scale Out Master コンピューターで、"services.msc" コマンドを実行して [サービス] ウィンドウを開きます。 SQL Server Integration Services Cluster Master サービスを停止します。
-   マスターに接続する Scale Out Worker コンピューターで、コマンド "services.msc" を実行し、[サービス] ウィンドウを開きます。 SQL Server Integration Services Cluster Worker サービスを停止します。

SSISDB カタログ データベースを削除できるようになりました。

#### <a name="odbc-components-are-not-supported-in-this-ctp-release"></a>この CTP リリースでは、ODBC コンポーネントはサポートされていません。
**問題とユーザーへの影響**: この CTP リリースでは、ODBC 接続マネージャー、入力元、入力先はサポートされていません。

**回避策:**回避策はありません。

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-vnext-ctp-10-november-2016"></a>SQL Server vNext CTP 1.0 (2016 年 11 月)
### <a name="supported-installation-scenarios-ctp10"></a>サポートされているインストール シナリオ (CTP&1;.0)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] はテスト バージョンとしてのみ使用できます。  運用環境での展開はサポートされません。 仮想マシンに [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] をインストールし、テストすることが推奨されます。

厳密に言うと、次のシナリオは機能する場合もありますが、完全にはテストされておらず、 **では** サポートされていません [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]。
- CTP 1.0 のアンインストール。
- 古いバージョンの SQL Server とのサイド バイ サイド インストール。
- 以前のバージョンの SQL Server からのアップグレード。
- [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] インストールでは、SQL Server 機能パック コンポーネントは利用できません。

### <a name="documentation-ctp-10"></a>ドキュメント (CTP 1.0)
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] のドキュメントは制限されており、コンテンツは [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] ドキュメント セットに付属しています。  記事の中で [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] に固有のコンテンツは、 **適用対象:**で言及されます。 
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]の場合、オフライン コンテンツを利用できません。

### <a name="sql-server-database-engine-ctp-10"></a>SQL Server データベース エンジン (CTP 1.0)
-  **問題およびユーザーへの影響:** CTP1 の `STRING_AGG` 関数は結果として LOB 型を返します (例: `NVARCHAR(MAX)`)。 今後の CTP リリースでは、この動作は変更される可能性があります。入力値が LOB 型ではない場合、 `STRING_AGG` は `NVARCHAR(4000)` を返す可能性があります。 連結結果が `NVARCHAR(4000)`に収まらない場合、オーバーフロー エラーがスローされる可能性があります。

-  **問題およびユーザーへの影響:** `STRING_AGG` 式のエイリアスとして、`WITHIN` など、予約されていないキーワードを使用することは避けてください。 (たとえば、`SELECT Company.Name, STRING_AGG(Product.Name, ',') AS WITHIN FROM TableA;`)今後の CTP リリースでは、`STRING_AGG` 呼び出しの後の `WITHIN` トークンは、`STRING_AGG` 関数の一部として使用される可能性があります。

-  **回避策:** `WITHIN` エイリアスの使用を避けるか、`STRING_AGG` 関数に追加される可能性がある将来の変更との競合を回避するためにエイリアスの仕様として `AS WITHIN` を追加します。


### <a name="sql-server-integration-services-ctp-10"></a>SQL Server Integration Services (CTP 1.0)
#### <a name="stop-operation-in-ssis-catalog-may-fail"></a>SSIS カタログの操作停止が失敗することがある
**問題およびユーザーへの影響:** [!INCLUDE[ssIS_md](../includes/ssis-md.md)] または catalog.stop_operation ストアド プロシージャによる [!INCLUDE[ssManStudio_md](../includes/ssmanstudio-md.md)] の操作停止が失敗し、“A .NET Framework error occurred during execution of user-defined routine or aggregate 'stop_operation_internal'” (ユーザーが定義したルーチンまたは集計関数 'stop_operation_internal' の実行中に .NET Framework エラーが発生しました) というエラーが表示される可能性があります。

-  **回避策:** Windows タスク マネージャーを開きます。 **[プロセス]** タブで、 **ISServerExec** という名前のプロセスを見つけ、 **[タスクの終了]** をクリックしてプロセスを終了します。

#### <a name="create-dump-of-ssis-pacakge-execution-may-fail"></a>SSIS パッケージ実行のダンプ作成が失敗することがある
**問題およびユーザーへの影響:** catalog.create_execution_dump ストアド プロシージャによるパッケージの実行のダンプ作成が失敗し、“A .NET Framework error occurred during execution of user-defined routine or aggregate 'create_execution_dump_internal'” (ユーザーが定義したルーチンまたは集計関数 'create_execution_dump_internal' の実行中に .NET Framework エラーが発生しました) というエラーが表示される可能性があります。

-  **回避策:** Windows タスク マネージャーを開きます。 **[プロセス]** タブで、「 **ISServerExec**」という名前のプロセスを見つけ、そのプロセスを右クリックし、 **[ダンプ ファイルの作成]**をクリックします。

#### <a name="get-perf-counter-of-ssis-package-execution-may-fail"></a>SSIS パッケージ実行のパフォーマンス カウンターの取得が失敗することがある
**問題およびユーザーへの影響:** テーブル値関数の  を利用して [!INCLUDE[ssIS_md](../includes/ssis-md.md)] パフォーマンス カウンターに問い合わせると、失敗して “A .NET Framework error occurred during execution of user-defined routine or aggregate 'get_execution_perf_counters'” (ユーザーが定義したルーチンまたは集計関数 'get_execution_perf_counters' の実行中に .NET Framework エラーが発生しました) というエラーが表示される可能性があります。

-  **回避策**: Windows パフォーマンス モニターを使用し、パフォーマンス カウンターの値を直接監視します。 特定のパッケージ実行のためのパフォーマンス カウンターの場合、回避策はありません。

#### <a name="deleting-catalog-may-fail-when-ssis-scale-out-master-is-installed"></a>SSIS Scale Out Master がインストールされているとき、カタログを削除できないことがある
**問題およびユーザーへの影響:** [!INCLUDE[ssIS_md](../includes/ssis-md.md)] Scale Out 機能がコンピューターにインストールされているとき、 **SSISDB** カタログを削除すると、“Could not drop login ‘…’ as the user is currently logged in” (ユーザーがログイン中のため、ログイン 'login' を切断できません) というエラーが表示され、SSISDB カタログ データベースを削除できないことがあります。 

**回避策**: 
* Scale Out Master コンピューターでコマンド “services.msc” を実行し、 **[サービス]** ウィンドウを開き、 **SQL Server Integration Services Cluster Master** サービスを停止します。 

* マスターに接続する Scale Out Worker コンピューターで、コマンド "services.msc" を実行し、 **[サービス]** ウィンドウを開きます。 **SQL Server Integration Services Cluster Worker** サービスを停止します。 

これで **SSISDB** カタログを削除できるはずです。

#### <a name="odbc-connector-in-ssis-is-not-supported"></a>SSIS の ODBC コネクタがサポートされない
-  **問題およびユーザーへの影響:** [!INCLUDE[ssIS_md](../includes/ssis-md.md)] の ODCB コネクタはサポートされていません。
-  **回避策:** 回避策はありません。

### <a name="sql-server-reporting-services-ctp-10"></a>SQL Server Reporting Services (CTP 1.0)

SQL Server Reporting Services では、 [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]の新機能はリリースされません。

### <a name="sql-server-master-data-services-ctp-10"></a>SQL Server マスター データ サービス (CTP 1.0)
#### <a name="transaction-may-not-work-when-the-entity-transaction-log-type-is-set-to-attribute"></a>エンティティ トランザクション ログ タイプが属性に設定されているとき、トランザクションが機能しないことがある
**問題およびユーザーへの影響:** エンティティ トランザクション ログ タイプが **で** [属性] [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] に設定されているとき (既定値は **[メンバー]**)、次のシナリオが失敗します。

* エンティティ変更のトランザクションは Web サイトに表示されません。
* Web サイトの **[トランザクション]** ページを開いたり、トランザクションを破棄したりできません。
* Web サイトで、エンティティをトランザクションの注釈で更新できません。

**回避策:**回避策はありません。

#### <a name="copy-version-may-not-work-when-copy-only-committed-version-is-set-to-false"></a>**[コミットされたバージョンのみをコピーする]** が偽に設定されているとき、バージョンをコピーできないことがある
**問題およびユーザーへの影響:** **[コミットされたバージョンのみをコピーする]** 設定が **[いいえ]** に設定されていると (既定値は **[はい]**)、バージョン コピー操作が失敗することがあります。 エラー メッセージがありません。

**回避策:**回避策はありません。
 
### <a name="sql-server-management-studio-ssms-ctp-10"></a>SQL Server Management Studio (SSMS) (CTP 1.0)
SQL Server Management Studio は別個のダウンロードです。  最新情報については、「 [SQL Server Management Studio - リリース ノート](https://msdn.microsoft.com/library/mt238486.aspx)」を参照してください。

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) SQL Server エンジニアリング チームと連携する 
- [スタック オーバーフロー (tag sql-server) - 技術的な質問](http://stackoverflow.com/questions/tagged/sql-server)
- [MSDN フォーラム - 技術的な質問](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect - バグ報告と機能依頼](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit - R に関する一般的なディスカッション](https://www.reddit.com/r/SQLServer/)


![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)


