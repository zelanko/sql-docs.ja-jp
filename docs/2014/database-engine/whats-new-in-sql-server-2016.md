---
title: どのような&#39;s 新しい (データベース エンジン) |Microsoft Docs
ms.custom: ''
ms.date: 06/22/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- what's new [SQL Server Database Engine]
- Database Engine [SQL Server], what's new
ms.assetid: 8f625d5a-763c-4440-97b8-4b823a6e2439
caps.latest.revision: 206
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 25dab69d079cf758a58669437e3e481eebe204a0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37173343"
---
# <a name="what39s-new-database-engine"></a>どのような&#39;s 新しい (データベース エンジン)
  この最新リリースの [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]には、データ ストレージ システムを設計、開発、および管理する設計者、開発者、および管理者の能力や生産性を向上させる、以下のような新機能や機能強化が導入されています。 [!INCLUDE[ssDE](../includes/ssde-md.md)]の機能が強化された分野は以下のとおりです。  
  
##  <a name="Feature"></a> データベース エンジンの機能強化  
  
###  <a name="MemoryOpt"></a> メモリ最適化テーブル  
 インメモリ OLTP は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エンジンに統合されたメモリ最適化データベース エンジンです。 インメモリ OLTP は OLTP 向けに最適化されています。 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
 
  
###  <a name="DataFiles"></a> Windows Azure での SQL Server データ ファイル  
 [Windows Azure での SQL Server データ ファイル](../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md)のネイティブ サポートを有効に[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]データベース Windows Azure Blob として格納されているファイル。 この機能を使用すると、内部設置型の環境で実行されている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、または Windows Azure Blob ストレージに専用のデータ保存場所を持つ Windows Azure の仮想マシンで実行されている SQL Server 内にデータベースを作成できます。  
  
  
###  <a name="AzureVM"></a> Windows での SQL Server データベースをホストする Azure 仮想マシン  
 使用して、 [Windows Azure 仮想マシンに SQL Server データベースのデプロイ](http://msdn.microsoft.com/library/dn195938\(v=sql.120\).aspx)ウィザードのインスタンスからデータベースをホストする[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Windows Azure 仮想マシンでします。  
  
  
###  <a name="Backup"></a> バックアップと復元の機能強化  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] には、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のバックアップと復元に関する次の強化点が含まれています。  
  
-   **SQL Server Backup to URL**  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Backup to URL は [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] SP1 CU2 で導入され、[!INCLUDE[tsql](../includes/tsql-md.md)]、PowerShell、および SMO でのみサポートされています。 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] では、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して、Windows Azure BLOB ストレージ サービスからバックアップまたは復元を実行できます。 バックアップ タスクとメンテナンス プランの両方で、この新しいオプションを使用できます。 詳細については、次を参照してください[SQL Server Management Studio でのバックアップ タスクを使用して](../relational-databases/backup-restore/sql-server-backup-to-url.md#BackupTaskSSMS)、 [SQL Server Backup to URL を使用してメンテナンス プラン ウィザード](../relational-databases/backup-restore/sql-server-backup-to-url.md#MaintenanceWiz)、および[Windows Azure storage からの復元を使用して SQL。Server Management Studio](../relational-databases/backup-restore/sql-server-backup-to-url.md#RestoreSSMS)します。  
  
-   **Windows Azure への SQL Server マネージ バックアップ**  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Backup to URL を基盤とした [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] は、データベースとログのバックアップを管理およびスケジュール設定するために [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が提供するサービスです。 このリリースでは、Windows Azure ストレージへのバックアップのみがサポートされています。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] をデータベースとインスタンス レベルの両方で構成して、データベース レベルの詳細な制御とインスタンス レベルの自動化の両方を達成することもできます。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を、内部設置型で実行されている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスと、Windows Azure 仮想マシンで実行されている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスで構成することができます。 このサービスは、Windows Azure 仮想マシンで実行されている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスで使用することをお勧めします。 詳細については、次を参照してください。 [SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)します。  
  
-   **バックアップの暗号化**  
  
     バックアップ操作中にバックアップ ファイルを暗号化する方法を選択できるようになりました。  AES 128、AES 192、AES 256、Triple DES を含むいくつかの暗号化アルゴリズムがサポートされています。 バックアップ中に暗号化を実行するには、証明書または非対称キーを使用する必要があります。 詳細については、次を参照してください。[バックアップの暗号化](../relational-databases/backup-restore/backup-encryption.md)します。  
  
  
###  <a name="CE"></a> カーディナリティを推定するための新しいデザイン  
 カーディナリティ推定機能と呼ばれる、カーディナリティ推定ロジックがで再設計された[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]クエリ プランの品質を向上させるためクエリのパフォーマンスを向上させるためにします。 新しいカーディナリティ推定機能には、現在の OLTP ワークロードとデータ ウェアハウス ワークロードで適切に機能する想定とアルゴリズムが組み込まれています。 この機能は、現在のワークロードを対象とするカーディナリティ推定に関する詳細な調査、および SQL Server のカーディナリティ推定機能を向上させるための過去 15 年にわたる研究を土台としています。 お客様からのフィードバックによると、大半のクエリは今回の変更によって性能が向上するか、何も変化しないこと、一方で、少数のクエリは以前のカーディナリティ推定機能と比較すると性能が低下する可能性があることが示されています。 パフォーマンスの推奨事項のテストとチューニングでは、次を参照してください。[カーディナリティ推定&#40;SQL Server&#41;](../relational-databases/performance/cardinality-estimation-sql-server.md)します。  
   
  
###  <a name="Durability"></a> 遅延持続性  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] には、一部またはすべてのトランザクションを遅延持続性トランザクションとして指定することにより待機時間を短縮する機能が導入されています。 遅延持続性トランザクションがクライアントに制御を返した後、トランザクション ログ レコードがディスクに書き込まれます。 持続性は、データベース レベル、COMMIT レベル、または ATOMIC ブロック レベルで管理できます。  
  
 詳細については、トピックを参照してください。[トランザクションの持続性の制御](../relational-databases/logs/control-transaction-durability.md)します。  
  
  
###  <a name="AlwaysOn"></a> AlwaysOn の機能強化  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] では、AlwaysOn フェールオーバー クラスター インスタンスと AlwaysOn 可用性グループが次のように強化されています。  
  
-   Azure のレプリカ追加ウィザードにより、AlwaysOn 可用性グループ用の複合ソリューションを容易に作成できます。 詳細については、次を参照してください。 [Azure レプリカの追加ウィザードを使用して&#40;SQL Server&#41;](availability-groups/windows/use-the-add-azure-replica-wizard-sql-server.md)します。  
  
-   セカンダリ レプリカの最大数は、4 から 8 に増えています。  
  
-   プライマリ レプリカから切断された場合やクラスター クォーラムが存在しない場合でも、読み取り可能なセカンダリ レプリカを、読み取りワークロードに対して引き続き使用できるようになりました。  
  
-   フェールオーバー クラスター インスタンス (FCI) では、クラスターの共有ボリューム (CSV) を、クラスターの共有ディスクとして使用できます。 詳細については、次を参照してください。 [Always On フェールオーバー クラスター インスタンス](../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)します。  
  
-   新しいシステム関数では、 [sys.fn_hadr_is_primary_replica](/sql/relational-databases/system-functions/sys-fn-hadr-is-primary-replica-transact-sql)、および新しい DMV で[sys.dm_io_cluster_valid_path_names](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql)は使用できます。  
  
-   次の Dmv が FCI 情報を拡張し、返すようになりました: [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)、 [sys.dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)、および[sys.dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)します。  
  
  
###  <a name="OIR"></a> パーティションの切り替えとインデックス作成  
 パーティション テーブルの個々のパーティションを再構築できるようになりました。 詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。  
   
  
###  <a name="Lock"></a> オンライン操作のロックの優先順位を管理します。  
 `ONLINE = ON` オプションには、再構築プロセスで必要なロックを待機する時間を指定できるようにする `WAIT_AT_LOW_PRIORITY` オプションが追加されました。 `WAIT_AT_LOW_PRIORITY` オプションを使用すると、当該の再構築ステートメントに関連するブロック プロセスの終了を構成こともできます。 詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」および「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。 使用可能な新しい種類のロック状態のトラブルシューティング情報は[sys.dm_tran_locks &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)と[sys.dm_os_wait_stats &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql)します。  
 
  
###  <a name="CCI"></a> 列ストア インデックス  
 次の新機能は、列のインデックスで使用できます。  
  
-   **クラスター化列ストア インデックス**  
  
     クラスター化列ストア インデックスは、主に一括読み込みと読み取り専用クエリを実行するデータ ウェアハウスのワークロードでデータ圧縮とクエリ パフォーマンスを向上させるために使用します。 クラスター化列ストア インデックスは更新可能であるため、ワークロードは多くの挿入、更新、および削除操作を実行できます。 詳細については、次を参照してください。[列ストア インデックスの概念](../relational-databases/indexes/columnstore-indexes-described.md)と[Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md)します。  
  
-   **プラン表示**  
  
     SHOWPLAN には、列ストア インデックスに関する情報が表示されます。 **EstimatedExecutionMode**と**ActualExecutionMode**プロパティがある 2 つの値:**バッチ**または**行**します。  **ストレージ**プロパティが 2 つの値:**行ストア**と**ColumnStore**します。  
  
-   **保存用データ圧縮**  
  
     ALTER INDEX … 再構築が、さらに、列ストア インデックスの指定パーティションを圧縮する新しい COLUMNSTORE_ARCHIVE データ圧縮オプション。 保存用や、データ ストレージのサイズを減らす必要があり、しかも保存と取得に時間をかける余裕があるその他の状況で使用します。 詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)」を参照してください。  
   
  
###  <a name="Buffer"></a> バッファー プール拡張機能  
 [バッファー プール拡張機能](configure-windows/buffer-pool-extension.md)不揮発性ランダム アクセス メモリ (NvRAM) 拡張としてのソリッドステート ドライブ (SSD) のシームレスな統合を提供します、[!INCLUDE[ssDE](../includes/ssde-md.md)]バッファー プールの I/O のスループットを大幅に向上します。  
   
  
###  <a name="Stats"></a> 増分統計  
 CREATE STATISTICS と関連する統計ステートメントでは、INCREMENTAL オプションを使用してパーティションごとの統計を作成することが許可されるようになりました。 関連するステートメントは増分統計を許可または報告します。 影響を受ける構文には、UPDATE STATISTICS、sp_createstats、CREATE INDEX、ALTER INDEX、ALTER DATABASE SET のオプション、DATABASEPROPERTYEX、sys.databases、および sys.stats があります。詳細については、「[CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)」を参照してください。  
  
  
###  <a name="RG"></a> 物理 IO を制御のリソース ガバナーの機能強化  
 リソース ガバナーを使用すると、着信アプリケーション要求がリソース プール内で使用できる CPU、物理 IO、およびメモリの量に制限を指定できます。 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] で、新しい MIN_IOPS_PER_VOLUME 設定と MAX_IOPS_PER_VOLUME 設定を使用すると、特定のリソース プールのユーザー スレッドに対して発行された物理 IO を制御できます。 詳細については、次を参照してください。[リソース ガバナー リソース プール](../relational-databases/resource-governor/resource-governor-resource-pool.md)と[CREATE RESOURCE POOL &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql)します。  
  
 ALTER RESOURCE GOVENOR の MAX_OUTSTANDING_IO_PER_VOLUME 設定は、ディスク ボリュームごとに未処理の I/O 操作の最大数を設定します。 この設定を使用して、ディスク ボリュームの IO の特性に合わせて IO リソース管理を調整することや、SQL Server インスタンスの境界で発行される IO の数を制限することができます。 詳細については、「[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)」を参照してください。  
  
  
###  <a name="OnlineEvent"></a> Online Index Operation イベント クラス  
 Online index operation イベントのクラスの進行状況レポートが 2 つの新しいデータ列になりました: **PartitionId**と**PartitionNumber**します。 詳細については、次を参照してください。 [Progress Report: Online Index Operation イベント クラス](../relational-databases/event-classes/progress-report-online-index-operation-event-class.md)します。  
  
  
###  <a name="Compat"></a> データベースの互換性レベル  
 互換性レベル 90 は、[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] では無効です。 詳細については、次を参照してください[ALTER DATABASE 互換性レベル&#40;TRANSACT-SQL。&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
##  <a name="TSQL"></a> Transact-SQL の機能強化  
  
### <a name="inline-specification-of-clustered-and-nonclustered"></a>CLUSTERED および NONCLUSTERED のインライン指定  
 ディスク ベース テーブルに対する `CLUSTERED` および `NONCLUSTERED` インデックスのインライン指定が許可されるようになりました。 インライン インデックスを含むテーブルを作成することは、テーブルの作成ステートメントに続いて、対応する `CREATE INDEX` ステートメントを発行することと同じです。 付加列とフィルター条件は、インライン インデックスではサポートされていません。  
  
### <a name="select--into"></a>SELECT … INTO  
 `SELECT … INTO` ステートメントは改善され、並行して実行できるようになりました。 データベース互換性レベルを 110 以上に設定する必要があります。  
  
### <a name="includetsqlincludestsql-mdmd-enhancements-for-in-memory-oltp"></a>[!INCLUDE[tsql](../includes/tsql-md.md)] でのインメモリ OLTP の強化  
 については、[!INCLUDE[tsql](../includes/tsql-md.md)]では、インメモリ OLTP をサポートするために変更を参照してください[TRANSACT-SQL は、インメモリ OLTP のサポート](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)します。  
  
  
##  <a name="SystemTable"></a> システム ビューの機能強化  
  
### <a name="sysxmlindexes"></a>sys.xml_indexes  
 [sys.xml_indexes &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-xml-indexes-transact-sql)は 3 つの新しい列があります: `xml_index_type`、 `xml_index_type_description`、および`path_id`します。  
  
### <a name="sysdmexecqueryprofiles"></a>sys.dm_exec_query_profiles  
 [sys.dm_exec_query_profiles &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql)クエリの実行中にリアルタイムにクエリの進行状況を監視します。  
  
### <a name="syscolumnstorerowgroups"></a>sys.column_store_row_groups  
 [sys.column_store_row_groups &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql)下すシステム管理の管理者に役立つセグメント単位でクラスター化列ストア インデックス情報を提供します。  
  
### <a name="sysdatabases"></a>sys.databases  
 [sys.databases &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)は 3 つの新しい列があります: `is_auto_create_stats_incremental_on`、 `is_query_store_on`、および`resource_pool_id`します。  
  
### <a name="system-view-enhancements-for-in-memory-oltp"></a>インメモリ OLTP に関連するシステム ビューの強化  
 インメモリ OLTP をサポートするシステム ビューの機能強化については、次を参照してください。[システム ビュー、ストアド プロシージャ、Dmv とインメモリ OLTP での待機の種類](../../2014/database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)します。  
   
  
##  <a name="Security"></a> セキュリティの強化  
  
### <a name="connect-any-database-permission"></a>CONNECT ANY DATABASE 権限  
 新しいサーバー レベル権限です。 既存のあらゆるデータベースと今後作成されるすべての新規データベースに接続する必要のあるログインに、**CONNECT ANY DATABASE** を付与します。 接続以外の権限はどのデータベースにおいても一切付与されません。 組み合わせる**SELECT ALL USER SECURABLES**または`VIEW SERVER STATE`のインスタンス上のすべてのデータやデータベースの状態を確認する監査プロセスを許可する[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]します。  
  
### <a name="impersonate-any-login-permission"></a>IMPERSONATE ANY LOGIN 権限  
 新しいサーバー レベル権限です。 この権限が付与されていると、中間層プロセスがデータベースに接続するときに、そこに接続するクライアントのアカウントの権限を借用できます。 この権限が拒否されていると、高い特権を持つログインが他のログインの権限を借用するのをブロックできます。 たとえば、**CONTROL SERVER** 権限を持つログインが他のログインの権限を借用するのをブロックできます。  
  
### <a name="select-all-user-securables-permission"></a>SELECT ALL USER SECURABLES 権限  
 新しいサーバー レベル権限です。 付与されていると、監査担当者などログインが、ユーザーが接続できるすべてのデータベースのデータを表示できます。  
  
  
##  <a name="Deployment"></a> 展開の機能強化  
### <a name="azure-vm"></a>Azure 仮想マシン
[Microsoft Azure 仮想マシンに SQL Server データベースのデプロイ](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md)で展開できること、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Windows Azure VM へのデータベース。  

### <a name="refs"></a>ReFS
ReFS の上のデータベースの展開はサポートされています。   
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 の各エディションがサポートする機能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
   
