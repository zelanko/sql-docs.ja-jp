---
title: "SQL Server 2017 年 1 リリース ノート |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/16/2017
ms.prod: sql-server-2017
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 67c1c0f3a9da6cc5d050da5db8a493f5da934c2a
ms.openlocfilehash: fa45fea4ebb378f035b4b4af2b1fa8a20bc152a5
ms.contentlocale: ja-jp
ms.lasthandoff: 06/23/2017

---
# <a name="sql-server-2017-release-notes"></a>SQL Server 2017 年 1 リリース ノートします。
このトピックでは、[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] での制限事項と問題について説明します。 関連の情報は、次を参照してください。

- [SQL Server 2017 年 1 の新機能](../sql-server/what-s-new-in-sql-server-2017.md)します。
- [Linux のリリース ノート SQL Server](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes)です。
- [SQL Server Reporting Services のリリース ノート](../reporting-services/reporting-services-release-notes.md)です。

 **お試しください:**    
   -   [![Evaluation Center からダウンロードする](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477) **[Evaluation Center から [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] をダウンロードする](http://go.microsoft.com/fwlink/?LinkID=829477)**

## <a name="sql-server-2017-ctp-21-may--2017"></a>SQL Server 2017 CTP 2.1 (2017 年 5 月)
### <a name="documentation-ctp-21"></a>ドキュメント (CTP 2.1)
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] のドキュメントは制限されており、コンテンツは [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] ドキュメント セットに付属しています。  記事の中で [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] に固有のコンテンツは、 **適用対象**で言及されます。 
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]の場合、オフライン コンテンツを利用できません。

### <a name="sql-server-reporting-services-ctp-21"></a>SQL Server Reporting Services (CTP 2.1)

- **問題およびユーザーへの影響:** SQL Server Reporting Services と Power BI でレポート サーバーを同じコンピューターし、それらのいずれかのアンインストールの両方があれば、不要になったことができます、残りのレポート サーバーはレポート Server 構成マネージャーに接続します。
- **回避策**この問題を回避するには、サーバーのいずれかをアンインストールした後に、次の操作を行う必要があります。

    1. 管理者モードでコマンド プロンプトを起動します。
    2. 残りのレポート サーバーがインストールされているディレクトリに移動します。

        *Power BI のレポート サーバーの既定の場所: C:\Program files \microsoft Power BI のレポート サーバー*

        *SQL Server Reporting Services の既定の場所: C:\Program files \microsoft SQL Server Reporting Services*

    3. 次のフォルダーに移動し、します。 これになります*SSRS*または*PBIRS*残っている新機能によって異なります。
    4. WMI フォルダーに移動します。
    5. 次のコマンドを実行します。

        ```
        regsvr32 /i ReportingServicesWMIProvider.dll
        ```

        表示する場合は、次のエラーを無視できます。

        ```
        The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
        ```

### <a name="tsqllanguageservicemsi-ctp-21"></a>TSqlLanguageService.msi (CTP 2.1)

- **問題およびユーザーへの影響:**の 2016年バージョンがあるコンピューターにインストールした後*TSqlLanguageService.msi* v13.* (SQL 2016) のバージョンのいずれか SQL セットアップで (スタンドアロン再頒布可能パッケージとして) をインストール*Microsoft.SqlServer.Management.SqlParser.dll*と*Microsoft.SqlServer.Management.SystemMetadataProvider.dll*が削除されます。 これらのアセンブリの 2016 バージョンに依存しているすべてのアプリケーションは、機能しなくのようなエラーを提供:*エラー: ファイルまたはアセンブリを読み込めませんでした ' Microsoft.SqlServer.Management.SqlParser, Version 13.0.0.0、カルチャを = = neutral, PublicKeyToken = 89845dcd8080cc91' またはその依存関係の 1 つです。システムでは、指定されたファイルを見つけることができません。*

   さらに、TSqlLanguageService.msi の 2016年バージョンを再インストールは失敗メッセージと共に:*マシンでより新しいバージョンが既に存在するので、インストールの Microsoft SQL Server 2016 T-SQL 言語サービスが失敗しました*です。

- **回避策**アセンブリのバージョンをこの問題を回避して、v13 に依存するアプリケーションを修正するには、以下の手順。

   1. 移動して**プログラムの追加と削除**
   1. 検索*Microsoft SQL Server vNext T-SQL 言語サービス CTP2.1*、右クリックし、選択**アンインストール**です。
   1. コンポーネントが削除された後に修復が破損するアプリケーション (適切なバージョンの再インストールまたは*TSqlLanguageService.MSI*)

   V14 バージョンに依存する任意のアプリケーションが機能しなくなるために、この回避策は、これらのアセンブリの v14 バージョンを削除します。 これらのアセンブリが必要な場合は、サイド バイ サイドの 2016 インストールせずに個別のインストールが必要です。

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-ctp-20-april--2017"></a>SQL Server 2017 CTP 2.0 (2017 年 4 月)
### <a name="documentation-ctp-20"></a>ドキュメント (CTP 2.0)
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] のドキュメントは制限されており、コンテンツは [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] ドキュメント セットに付属しています。  記事の中で [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] に固有のコンテンツは、 **適用対象**で言及されます。 
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]の場合、オフライン コンテンツを利用できません。

### <a name="always-on-availability-groups"></a>Always On 可用性グループ

- **問題およびユーザーへの影響:** SQL Server のメジャー バージョンがプライマリ レプリカをホストしているインスタンスよりも小さい場合、可用性グループのセカンダリ レプリカをホストする SQL Server インスタンスがクラッシュします。 SQL Server の SQL Server への可用性グループをホストするすべてのサポートされているバージョンからのアップグレードに影響を与える[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]CTP 2.0。 これは、次の手順では発生します。 

> 1. SQL Server インスタンス ホスト セカンダリ レプリカをに従ってアップグレード[ベスト プラクティス](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md)です。
> 2. アップグレード後は、フェールオーバーが発生したし、可用性グループ内のすべてのセカンダリ レプリカに対してアップグレードを完了する前に新たにアップグレードされたセカンダリがプライマリになります。 以前のプライマリは、プライマリよりも古いバージョンであるセカンダリであるようになりました。
> 3. 可用性グループはサポートされていない構成であり、残りのセカンダリ レプリカがクラッシュするされる恐れがあります。 

- **回避策**構成から障害のあるセカンダリ レプリカの削除、新しいプライマリ レプリカをホストしている SQL Server インスタンスに接続します。

   `ALTER AVAILABILITY GROUP agName REMOVE REPLICA ON NODE instanceName`

   セカンダリ レプリカをホストしている SQL Server のインスタンスを回復します。


![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-2017-ctp-14-march--2017"></a>SQL Server 2017 CTP 1.4 (2017 年 3 月)

### <a name="documentation-ctp-14"></a>ドキュメント (CTP 1.4)
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] のドキュメントは制限されており、コンテンツは [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] ドキュメント セットに付属しています。  記事の中で [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] に固有のコンテンツは、 **適用対象**で言及されます。 
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]の場合、オフライン コンテンツを利用できません。

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-2017-ctp-13-february--2017"></a>SQL Server 2017 CTP 1.3 (2017 年 2 月)
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

## <a name="sql-server-2017-ctp-12-january--2017"></a>SQL Server 2017 CTP 1.2 (2017 年 1 月)
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

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) SQL Server エンジニアリング チームと連携する 
- [スタック オーバーフロー (tag sql-server) - 技術的な質問](http://stackoverflow.com/questions/tagged/sql-server)
- [MSDN フォーラム - 技術的な質問](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect - バグ報告と機能依頼](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit - R に関する一般的なディスカッション](https://www.reddit.com/r/SQLServer/)


![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)


