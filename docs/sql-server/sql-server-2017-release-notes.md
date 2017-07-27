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
ms.translationtype: HT
ms.sourcegitcommit: 6aa73e749d4f308265dfe27a160802c15a391a3e
ms.openlocfilehash: a2950b6aef0e12653efbb9eb26fd3f1ae6cb951e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/17/2017

---
# <a name="sql-server-2017-release-notes"></a>SQL Server 2017 年 1 リリース ノートします。
このトピックでは、[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] での制限事項と問題について説明します。 関連情報については、次のトピックを参照してください。

- [SQL Server 2017 年 1 の新機能](../sql-server/what-s-new-in-sql-server-2017.md)します。
- [Linux のリリース ノート SQL Server](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes)です。
- [SQL Server Reporting Services のリリース ノート](../reporting-services/reporting-services-release-notes.md)です。

 **お試しください:**    
   -   [![Evaluation Center からダウンロードする](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477) **[Evaluation Center から [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] をダウンロードする](http://go.microsoft.com/fwlink/?LinkID=829477)**

## <a name="sql-server-2017-release-candidate-rc1---july-2017"></a>SQL Server 2017 リリース候補 (RC1 - 2017 年 7 月)

### <a name="sql-server-integration-services-ssis-rc1---july-2017"></a>SQL Server Integration Services (SSIS) (RC1 - 2017 年 7 月)
- **問題とユーザーへの影響:** ストアド プロシージャ **[catalog].[create_execution]** の *runincluster* パラメーターは、一貫性とわかりやすさを理由に、名前が *runinscaleout* に変更されました。
- **回避策:** Scale Out でパッケージを実行する既存のスクリプトがある場合は、スクリプトが RC1 で動作するように、パラメーター名を *runincluster* から *runinscaleout* に変更します。

- **問題とユーザーへの影響:** SQL Server Management Studio (SSMS) 17.1 とそれより前のバージョンでは、RC1 の Scale Out でパッケージの実行を開始できません。 エラー メッセージ: "*@runincluster* is not a parameter for procedure **create_execution**" (@runincluster はプロシージャ create_execution のパラメーターではありません)。 この問題は、SSMS の次のリリースであるバージョン 17.2 で解決されています。 SSMS のバージョン 17.2 以降では、新しいパラメーター名と Scale Out でのパッケージ実行がサポートされています。 
- **回避策:** SSMS バージョン 17.2 が利用可能になるまでは、既存バージョンの SSMS を使用してパッケージ実行スクリプトを生成し、そのスクリプトで *runincluster* パラメーターの名前を *runinscaleout* に変更したうえで、スクリプトを実行します。

![horizontal_bar](../sql-server/media/horizontal-bar.png)
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

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) SQL Server エンジニアリング チームと連携する 
- [スタック オーバーフロー (tag sql-server) - 技術的な質問](http://stackoverflow.com/questions/tagged/sql-server)
- [MSDN フォーラム - 技術的な質問](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect - バグ報告と機能依頼](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit - R に関する一般的なディスカッション](https://www.reddit.com/r/SQLServer/)

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
