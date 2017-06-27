---
title: "SQL Server 2017 の新機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/19/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b57f375-9242-4bb2-9d4b-c560d5a93524
caps.latest.revision: 71
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: aa08b5e7de9bb317fd781a98ee5d829431b92df6
ms.openlocfilehash: 66c9bc4f2cba20076c357d27fdfacbc767a94c5c
ms.contentlocale: ja-jp
ms.lasthandoff: 06/23/2017

---
# <a name="what39s-new-in-sql-server-2017"></a>SQL Server 2017 の新機能
SQL Server 2017 では、SQL Server、Linux、Linux ベースの Docker コンテナー、および Windows を SQL Server の電源を戻すことによって、開発言語のデータ型、内部設置型のクラウドとオペレーティング システム間での選択肢を提供するプラットフォームを行う方向に主要なステップを表します。

このトピックでは、最新の Community Technical Preview (CTP) リリースと特定の機能領域の新しい情報より詳細なへのリンクの新機能の概要を示します。

![info_tip](../sql-server/media/info-tip.png) SQL Server を Linux で実行できます。 詳細については、以下をご覧ください。
-  [Linux 上の SQL Server 2017 の新機能します。](https://docs.microsoft.com/sql/linux/sql-server-linux-whats-new)
-  [SQL Server on Linux ドキュメント](https://docs.microsoft.com/sql/linux/)


**お試しください:**    
   -   [![Evaluation Center からダウンロード](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  **[SQL Server 2017 Community Technology Preview をダウンロード](http://go.microsoft.com/fwlink/?LinkID=829477)**

## <a name="whats-new-in-sql-server-2017-ctp-21-may-2017"></a>SQL Server 2017 CTP 2.1 (2017 年 5 月) の新機能
### <a name="sql-server-database-engine"></a>SQL Server データベース エンジン  
- 新しい DMF、 [sys.dm_db_log_stats](../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md)、概要レベルの属性とトランザクション ログ ファイルに情報を公開する導入されたもの以外のトランザクション ログの正常性を監視するのに役立ちます。  
- この CTP には、バグ修正とパフォーマンスの向上、データベース エンジンが含まれています。
- 2017 年の詳細な一覧については、以前の CTP リリースで CTP の機能強化を参照してください[SQL Server 2017 (データベース エンジン) の新](../database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md)です。

### <a name="sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS)
- SQL Server Reporting Services では、CTP 2.1 の時点での SQL Server のセットアップでインストールできるように不要になったです。
- コメントは、レポートに使用できるようになりました。 コメントでは、レポート内に何がパースペクティブを追加し、組織内の他のユーザーと共同作業を行うことができます。 コメントに、添付ファイルを含めることもできます。
- 以前のリリースの詳細など、SSRS の新しい情報については、「 [Reporting Services の新機能 (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)」を参照してください。 
- Power BI のレポート サーバーについては、次を参照してください。 [Power BI のレポート サーバーの概要](https://powerbi.microsoft.com/documentation/reportserver-get-started/)です。

### <a name="sql-server-machine-learning-services"></a>SQL Server コンピューターのサービスの学習
- この CTP では、Machine Learning のサービスの新機能はありません。
- Machine Learning のサービスの詳細の以前の Ctp から詳細を含む、新しい情報に表示される内容[SQL Server の Machine Learning のサービスの新](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md)です。  

### <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS)
- この CTP に新しい SSAS 機能はありません。  
- 機能強化とバグ修正を行いました。 このリリースの詳細については、次を参照してください。 [SQL Server 2017 Analysis Services の新](../analysis-services/what-s-new-in-sql-server-analysis-services-2017.md)です。  

### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
-   使用できるように、 **Use32BitRuntime**パラメーター。
-   ログのパフォーマンスが改善されました。
- 詳細な SSIS の以前の Ctp から詳細を含む、新しい情報に表示される内容[SQL Server 2017 Integration Services の新](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md)です。  

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="whats-new-in-sql-server-2017-ctp-20-april-2017"></a>SQL Server 2017 CTP 2.0 (2017 年 4 月) の新機能
### <a name="sql-server-database-engine"></a>SQL Server データベース エンジン
- **再開可能なオンライン インデックス再構築**です。 再開可能なオンライン インデックス再構築では、障害の後に停止したところから、オンライン インデックス再構築の操作を再開することができます。 たとえば、レプリカまたは十分なディスク領域のような状況にフェールオーバーします。 だけを一時停止し、その後、オンライン インデックス再構築操作を再開できます。 たとえば、一時的に優先度の高いタスクの実行または使用可能なメンテナンス期間が大規模なテーブルに対して短すぎる場合は、miniatous を別のウィンドウで、インデックスの再構築を完了するためにシステム リソースを解放する必要があります。 最後に、再開可能なオンライン インデックス再構築するために、大量のログ領域は、再開可能な状態の再構築操作の実行中に、ログの切り捨てを実行できるようにする必要はありません。 参照してください[ALTER INDEX](../t-sql/statements/alter-index-transact-sql.md)と[オンライン インデックス操作のガイドライン](../relational-databases/indexes/guidelines-for-online-index-operations.md)です。
- **ALTER DATABASE SCOPED CONFIGURATION を IDENTITY_CACHE オプション**です。 ALTER データベース スコープ構成 T-SQL ステートメントを IDENTITY_CACHE の新しいオプションが追加されました。 このオプションが OFF に設定されている場合、サーバーが予期せず再起動またはがセカンダリ サーバーにフェールオーバーした場合にギャップは identity 列の値で回避できます。 参照してください[ALTER データベース スコープ ベースの構成](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)です。  
- CLR は、セキュリティ境界としてはサポートされなくなる .NET framework コード アクセス セキュリティ (CAS) を使用します。 作成された CLR アセンブリ`PERMISSION_SET = SAFE`外部システム リソースにアクセスし、アンマネージ コードを呼び出し、sysadmin 特権を取得できる場合があります。 以降で[!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)]、`sp_configure`と呼ばれるオプション`clr strict security`は CLR アセンブリのセキュリティを強化するために導入されました。 `clr strict security`既定では、有効になり、処理`SAFE`と`EXTERNAL_ACCESS`アセンブリ マークされている場合と`UNSAFE`です。 `clr strict security`オプションは、旧バージョンと互換性のため、無効にすることができますが推奨されていません。 Microsoft では、すべてのアセンブリは、証明書または非対称キーに対応するログインが与えられているによって署名することをお勧め`UNSAFE ASSEMBLY`master データベースにアクセスを許可します。 詳細については、次を参照してください。 [CLR 厳格なセキュリティ](../database-engine/configure-windows/clr-strict-security.md)です。  
- 多対多リレーションシップをモデル化するグラフのデータベース機能です。 これが新規に含まれます[CREATE TABLE](../t-sql/statements/create-table-sql-graph.md)ノードとエッジ テーブルとキーワードを作成するための構文[一致](../t-sql/queries/match-sql-graph.md)クエリ。 詳細については、次を参照してください。[グラフは、SQL Server 2017 を使用した処理](../relational-databases/graphs/sql-graph-overview.md)です。   
- パフォーマンスの問題の潜在的なクエリに関する洞察を提供するデータベース機能は、自動チューニング、ソリューションを推奨して、修正プログラムが自動的に問題を識別します。 自動チューニング[!INCLUDE[ssnoversion](../includes/ssnoversion.md)]潜在的なパフォーマンスの問題が検出され、修正措置を適用することができます常に通知する、またはにより、[!INCLUDE[ssde](../includes/ssde-md.md)]パフォーマンスの問題を自動的に修復します。 詳細については、次を参照してください。[自動チューニング](../relational-databases/automatic-tuning/automatic-tuning.md)です。  
-   バッチ モード アダプティブへの参加 (データベースの互換性 140) プランの品質向上します。
-   (データベースの互換性 140) プランの品質を向上させるために複数ステートメントの T-SQL Tvf の逐次的実行します。
- クエリのストア今すぐも追跡待機の統計情報の概要情報。 1 つのクエリのストア内のクエリの待機統計情報のカテゴリを追跡するには、エクスペリエンスのトラブルシューティング、さらに強化、ワークロードのパフォーマンスおよびクエリのストアのキーの利点を維持しながら、ボトルネックを把握を提供するパフォーマンスの次のレベルが有効にします。
- Always On 可用性グループの同じインスタンスの一部であるデータベースを含む、可用性グループの一部であるデータベース間のすべての複数のデータベースにトランザクションのサポートを DTC。 詳細については、次を参照してください[トランザクション - Always On 可用性グループとデータベース ミラーリング。](../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)
- 新しい列**modified_extent_page_count**で導入された[sys.dm_db_file_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)データベースの各データベース ファイル差分変更を追跡します。
- [SELECT INTO](../t-sql/queries/select-into-clause-transact-sql.md)を使用して、ユーザーの既定のファイル グループ以外のファイル グループにテーブルを読み込むようになりました、 **ON**キーワード。
- SQL Server セットアップは、初期の tempdb ファイル サイズの最大指定をサポート**(262,144 MB) は 256 GB**ファイルのサイズがより大きい値に設定されている場合、警告とファイルあたり**1 GB** IFI が有効になっていない場合。
- 新しい動的管理ビュー (DMV) [sys.dm_tran_version_store_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-space-usage.md)データベースごとのバージョン ストアの使用状況を追跡するために導入されました。
- 新しい DMV [sys.dm_db_log_info](../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md) DBCC LOGINFO のような VLF 情報を公開するが導入されました。
- システム バージョン管理されたテンポラル テーブルは、連鎖削除と連鎖更新をサポートします。
- この CTP にはデータベース エンジンのバグ修正が含まれています。
- 2017 年の詳細な一覧については、以前の CTP リリースで CTP の機能強化を参照してください[SQL Server 2017 (データベース エンジン) の新](../database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md)です。   

### <a name="sql-server-machine-learning-services"></a>SQL Server コンピューターのサービスの学習
- SQL Server R Services では、CTP 2.0 での Python 言語のサポートを反映するように、新しい名前を持ちます。 SQL Server マシン ラーニング Services (In-database) を使用して、SQL Server で R または Python スクリプトを実行するようになりましたことができます。 または、展開および SQL Server を必要としない R、Python のモデルを使用する Microsoft Machine Learning Server (スタンドアロン) をインストールします。 
- 両方のプラットフォームには、分散の機械学習、および Microsoft R (バージョン 9.1.0) の最新バージョンの新しい MicrosoftML アルゴリズムが含まれます。
- 詳細については、次を参照してください。[機械学習新](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md)です。

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="whats-new-in-sql-server-2017-ctp-14-march-2017"></a>SQL Server 2017 CTP 1.4 の新機能 (2017 年 3 月)
### <a name="sql-server-database-engine"></a>SQL Server データベース エンジン
- この CTP に新しいデータベース エンジン機能はありません。
- この CTP にはデータベース エンジンのバグ修正が含まれています。
- 2017 年の詳細な一覧については、以前の CTP リリースで CTP の機能強化を参照してください[SQL Server 2017 (データベース エンジン) の新](../database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md)です。

### <a name="sql-server-r-services"></a>SQL Server R サービス
- この CTP に新しい R Services 機能はありません。
- 以前の CTP の詳細など、R Services の新しい情報については、「 [SQL Server R Services の新機能](../advanced-analytics/r-services/what-s-new-in-sql-server-r-services.md)」を参照してください。  

### <a name="sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS)
- この CTP に新しい SSRS 機能はありません。
- 以前のリリースの詳細など、SSRS の新しい情報については、「 [Reporting Services の新機能 (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)」を参照してください。 

### <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS)
- この CTP に新しい SSAS 機能はありません。  
- Analysis Services 用の SSDT および SSMS で、最新のプレビュー リリースの新などの詳細を参照してください[Analysis Services 2017 新](../analysis-services/what-s-new-in-sql-server-analysis-services-2017.md)です。  

### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
- この CTP に新しい SSIS 機能はありません。
- 詳細な SSIS の以前の Ctp から詳細を含む、新しい情報に表示される内容[Integration Services 2017 新](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md)です。  

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="whats-new-in-sql-server-2017-ctp-13-february-2017"></a>SQL Server 2017 CTP 1.3 の新機能 (2017 年 2 月)
### <a name="sql-server-database-engine"></a>SQL Server データベース エンジン
- 間接チェックポイントのパフォーマンスが強化されました。
- クラスターレス可用性グループのサポートが追加されました。
- ミニマム レプリカ コミット可用性グループの設定が追加されました。
- Windows と Linux 間で可用性グループが利用できるようになり、OS 間での移行とテストができるようになりました。
- テンポラル テーブルの保有ポリシーのサポートが追加されました。 詳細については、次を参照してください。[保有期間の履歴データの管理システムでバージョン管理されたテンポラル テーブルで](../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md#using-temporal-history-retention-policy-approach)です。
- DMV SYS.DM_DB_STATS_HISTOGRAM が新しくなりました。
- オンラインの非クラスター化列ストア インデックスの構築と追加のサポートを再構築
- Linux プロセスの情報を返す動的管理ビューが&5; つ追加されました。 詳細については、 [Linux のサービスの動的管理ビュー](../relational-databases/system-dynamic-management-views/linux-process-dynamic-management-views-transact-sql.md)に関する記事を参照してください。   
- 統計情報を確認するための[sys.dm_db_stats_histogram (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) が追加されました。

### <a name="sql-server-analysis-services-ssas-ctp-13"></a>SQL Server Analysis Services (SSAS) (CTP 1.3)
- エンコードのヒント。これは、大規模なメモリ内のテーブル モデルの処理 (データの更新) を最適化するために使用される高度な機能です。 詳細については、次を参照してください。 [Analysis Services 2017 新](../analysis-services/what-s-new-in-sql-server-analysis-services-2017.md)です。 


![horizontal_bar](../sql-server/media/horizontal-bar.png)

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) SQL Server エンジニアリング チームと連携する 
- [スタック オーバーフロー (tag sql-server)](http://stackoverflow.com/questions/tagged/sql-server)
- [MSDN フォーラム](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect - バグ報告と機能依頼](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit - R に関する一般的なディスカッション](https://www.reddit.com/r/SQLServer/)

## <a name="see-also"></a>参照    
- ![リリース ノート](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png) [SQL Server 2017 年 1 リリース ノート](../sql-server/sql-server-2017-release-notes.md)です。 
- [SQL Server&2016; の各エディションとサポートされる機能](https://msdn.microsoft.com/library/cc645993.aspx)
- [SQL Server&2016; のインストールに必要なハードウェアおよびソフトウェア](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)
- [SQL Server インストール ウィザード](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)
- [SQL Server サービスの更新プログラムをインストールします。](http://msdn.microsoft.com/library/6df72a78-6b36-4bc1-948e-04b4ebe46094)
 
 ![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)

