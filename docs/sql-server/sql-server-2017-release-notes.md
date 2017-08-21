---
title: "SQL Server 2017 リリース ノート | Microsoft Docs"
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
ms.sourcegitcommit: 04245fd42b770129ce4074f8a4ae8377b10cf384
ms.openlocfilehash: 6494051851601ead6fb3d51e1688b8f1320ed5d4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/15/2017

---
# <a name="sql-server-2017-release-notes"></a>SQL Server 2017 リリース ノート
このトピックでは、 [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]での制限事項と問題について説明します。 関連情報については、次を参照してください。
- [SQL Server 2017 の新機能](../sql-server/what-s-new-in-sql-server-2017.md)。
- [SQL Server on Linux リリース ノート](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes)。
  
[![Evaluation Center からダウンロードしてください。](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  **[Evaluation Center](http://go.microsoft.com/fwlink/?LinkID=829477)** から [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] をダウンロードしてください

## <a name="sql-server-2017-release-candidate-rc2---august-2017"></a>SQL Server 2017 リリース候補 (RC2、2017 年 8 月)
このリリースに対する、Windows 上の SQL Server のリリース ノートはありません。 [Linux 上の SQL Server のリリース ノート](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes)に関する記事をご覧ください。

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-release-candidate-rc1---july-2017"></a>SQL Server 2017 リリース候補 (RC1 - 2017 年 7 月)
### <a name="sql-server-integration-services-ssis-rc1---july-2017"></a>SQL Server Integration Services (SSIS) (RC1 - 2017 年 7 月)
- **問題とユーザーへの影響:** ストアド プロシージャ **[catalog].[create_execution]** の *runincluster* パラメーターは、一貫性とわかりやすさを理由に、名前が *runinscaleout* に変更されました。
- **回避策:** Scale Out でパッケージを実行する既存のスクリプトがある場合は、スクリプトが RC1 で動作するように、パラメーター名を *runincluster* から *runinscaleout* に変更します。

- **問題とユーザーへの影響:** SQL Server Management Studio (SSMS) 17.1 とそれより前のバージョンでは、RC1 の Scale Out でパッケージの実行を開始できません。 エラー メッセージ: "*@runincluster* はプロシージャ **create_execution** のパラメーターではありません。" この問題は、SSMS の次のリリースであるバージョン 17.2 で解決されています。 SSMS のバージョン 17.2 以降では、新しいパラメーター名と Scale Out でのパッケージ実行がサポートされています。 
- **回避策:** SSMS バージョン 17.2 が利用可能になるまで、以下のようにします。
  1. 既存のバージョンの SSMS を使用して、パッケージ実行スクリプトを生成します。
  2. スクリプトの *runincluster* パラメーターの名前を *runinscaleout* に変更します。
  3. スクリプトを実行します。

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-ctp-21-may--2017"></a>SQL Server 2017 CTP 2.1 (2017 年 5 月)
### <a name="documentation-ctp-21"></a>ドキュメント (CTP 2.1)
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] のドキュメントは制限されており、コンテンツは [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] ドキュメント セットに付属しています。  記事の中で [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] に固有のコンテンツは、**適用対象**で言及されています。 
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]の場合、オフライン コンテンツを利用できません。

### <a name="sql-server-reporting-services-ctp-21"></a>SQL Server Reporting Services (CTP 2.1)

- **問題およびユーザーへの影響:** SQL Server Reporting Services と Power BI レポート サーバーの両方が同じコンピューター上にあり、いずれかをアンインストールすると、残ったレポート サーバーにレポート サーバーの構成マネージャーで接続できなくなります。
- **回避策:** この問題を回避するには、どちらかのサーバーをアンインストールした後、次の操作を行う必要があります。

    1. 管理者モードでコマンド プロンプトを起動します。
    2. 残りのレポート サーバーがインストールされているディレクトリに移動します。

        *Power BI レポート サーバーの既定の場所: C:\Program Files\Microsoft Power BI Report Server*

        *SQL Server Reporting Services の既定の場所: C:\Program Files\Microsoft SQL Server Reporting Services*

    3. 次に、残っているものに応じて、次のフォルダー *SSRS* または *PBIRS* のいずれかに移動します。
    4. WMI フォルダーに移動します。
    5. 次のコマンドを実行します。

        ```
        regsvr32 /i ReportingServicesWMIProvider.dll
        ```

        以下のエラーが表示された場合は無視します。

        ```
        The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
        ```

### <a name="tsqllanguageservicemsi-ctp-21"></a>TSqlLanguageService.msi (CTP 2.1)

- **問題およびユーザーへの影響:** *TSqlLanguageService.msi* の 2016 バージョンが (SQL セットアップにより、またはスタンドアロンの再頒布可能コンポーネントとして) インストールされているコンピューターにインストールした後、v13.* (SQL 2016) バージョンの *Microsoft.SqlServer.Management.SqlParser.dll* および *Microsoft.SqlServer.Management.SystemMetadataProvider.dll* が削除されます。 これらのアセンブリの 2016 バージョンに依存しているすべてのアプリケーションは機能を停止し、次のようなエラーが発生します。"*エラー: ファイルまたはアセンブリ 'Microsoft.SqlServer.Management.SqlParser, Version=13.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91'、またはその依存関係の 1 つが読み込めませんでした。指定されたファイルが見つかりません。*"

   さらに、2016 バージョンの TSqlLanguageService.msi をインストールしようとすると、次のようなメッセージで失敗します。"*Microsoft SQL Server 2016 T-SQL 言語サービスのインストールに失敗しました。この製品の新しいバージョンが既にこのコンピューターにインストールされています。*"

- **回避策:** この問題を回避して、アセンブリの v13 バージョンに依存するアプリケーションを修正するには、以下の手順のようにします。

   1. **[プログラムの追加と削除]** に移動します
   2. *Microsoft SQL Server vNext T-SQL Language Service CTP2.1* を探し、右クリックして、**[アンインストール]** を選びます。
   3. コンポーネントを削除した後、破損したアプリケーションを修復します。または、適切なバージョンの *TSqlLanguageService.MSI* を再インストールします。

   この回避策はこれらのアセンブリの v14 バージョンを削除するので、v14 バージョンに依存するアプリケーションは機能しなくなります。 これらのアセンブリが必要な場合は、side-by-side 2016 インストールを含まない別のインストールが必要です。

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-ctp-20-april--2017"></a>SQL Server 2017 CTP 2.0 (2017 年 4 月)
### <a name="documentation-ctp-20"></a>ドキュメント (CTP 2.0)
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] のドキュメントは制限されており、コンテンツは [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] ドキュメント セットに付属しています。  記事の中で [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] に固有のコンテンツは、**適用対象**で言及されています。 
- **問題およびユーザーへの影響:** [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]の場合、オフライン コンテンツを利用できません。

### <a name="always-on-availability-groups"></a>Always On 可用性グループ

- **問題およびユーザーへの影響:** SQL Server のメジャー バージョンがプライマリ レプリカをホストしているインスタンスより小さい場合、可用性グループのセカンダリ レプリカをホストする SQL Server インスタンスがクラッシュします。 可用性グループをホストするすべてのサポートされている SQL Server のバージョンから SQL Server [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 2.0 へのアップグレードに影響を与えます。 これは、次の手順で発生します。 

> 1. ユーザーが[ベスト プラクティス](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md)に従ってセカンダリ レプリカをホストする SQL Server インスタンスをアップグレードします。
> 2. アップグレード後、フェールオーバーが発生し、可用性グループ内のすべてのセカンダリ レプリカのアップグレードが完了する前に、新しくアップグレードされたセカンダリがプライマリになります。 古いプライマリは、プライマリよりも古いバージョンのセカンダリになります。
> 3. 可用性グループはサポートされていない構成であり、残りのセカンダリ レプリカはクラッシュする恐れがあります。 

- **回避策:** 新しいプライマリ レプリカをホストしている SQL Server インスタンスに接続し、構成から障害のあるセカンダリ レプリカを削除します。

   `ALTER AVAILABILITY GROUP agName REMOVE REPLICA ON NODE instanceName`

   セカンダリ レプリカをホストしていた SQL Server のインスタンスが回復します。

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) SQL Server エンジニアリング チームと連携する 
- [スタック オーバーフロー (tag sql-server) - 技術的な質問](http://stackoverflow.com/questions/tagged/sql-server)
- [MSDN フォーラム - 技術的な質問](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect - バグ報告と機能依頼](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit - SQL Server に関する一般的なディスカッション](https://www.reddit.com/r/SQLServer/)

## <a name="more-information"></a>詳細情報
- [SQL Server Reporting Services リリース ノート](../reporting-services/reporting-services-release-notes.md)での制限事項と問題について説明します。
- [Machine Learning サービスの既知の問題](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)

