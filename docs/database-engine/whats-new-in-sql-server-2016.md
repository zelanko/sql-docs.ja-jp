---
title: データベース エンジンの新機能 - SQL Server 2016 | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- what's new [SQL Server Database Engine]
- Database Engine [SQL Server], what's new
ms.assetid: 8f625d5a-763c-4440-97b8-4b823a6e2439
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 440855051e0927bf4d660224fdbeba64bace1a4d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68059042"
---
# <a name="whats-new-in-database-engine---sql-server-2016"></a>データベース エンジンの新機能 - SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

このトピックでは、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]リリースで導入された機能強化の概要を示します。  新機能と機能拡張により、データ ストレージ システムを設計、開発、および管理する設計者、開発者、および管理者の能力や生産性が向上します。

他の SQL Server コンポーネントの新機能を確認する場合は、「 [SQL Server 2016 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)」を参照してください。

> [!NOTE]
>  [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] は 64 ビット アプリケーションです。 32 ビット版のインストールは廃止されましたが、いくつかの要素が 32 ビット コンポーネントとして実行されます。

#### <a name="try-it-out"></a>お試しください

- [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] をダウンロードするには、 **[評価センター](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)** ![ダウンロード](../analysis-services/media/download.png "ダウンロード")に移動してください。

- Azure アカウントをすでにお持ちですか?  既にお持ちの場合は、 **[こちら](https://azure.microsoft.com/services/virtual-machines/sql-server/)** にアクセスして、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] がインストール済みの仮想マシンをすぐにご利用いただけます。

> [!NOTE]
> 最新のリリース ノートについては、「[SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md)」を参照してください。
  
## <a name="sql-server-2016-service-pack-1-sp1"></a>SQL Server 2016 Service Pack 1 (SP1)  
-  `CREATE OR ALTER <object>` 構文を[プロシージャ](../t-sql/statements/create-procedure-transact-sql.md)、[ビュー](../t-sql/statements/create-view-transact-sql.md)、[関数](../t-sql/statements/create-function-transact-sql.md)、[トリガー](../t-sql/statements/create-trigger-transact-sql.md)に使用できるようになりました。
-   より汎用的なクエリ ヒント モデルのサポートが追加されました ( `OPTION (USE HINT('<hint1>', '<hint2>'))`)。 詳細については、「 [クエリ ヒント (Transact-SQL)](../t-sql/queries/hints-transact-sql-query.md)」を参照してください。  
- ヒントを列挙する [sys.dm_exec_valid_use_hints](../relational-databases/system-dynamic-management-views/sys-dm-exec-valid-use-hints-transact-sql.md) DMV が追加されました。  
- showplan XML の一時的な統計情報を返す [sys.dm_exec_query_statistics_xml](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md) が追加されました。  
- 指定されたテーブルの増分統計情報に [sys.dm_db_incremental_stats_properties](../relational-databases/system-dynamic-management-views/sys-dm-db-incremental-stats-properties-transact-sql.md) DMV が追加されました。  
- `instant_file_initialization_enabled` 列が [sys.dm_server_services](../relational-databases/system-dynamic-management-views/sys-dm-server-services-transact-sql.md) に追加されました。  
- `estimated_read_row_count` 列が [sys.dm_exec_query_profiles](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md) に追加されました。  
-  メモリ ページのロック モデルに関する情報を提供する `sql_memory_model` 列と `sql_memory_model_desc` 列が [sys.dm_os_sys_info](../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md) に追加されました。
-  多数の機能をサポートするエディションが拡張されました。 これには、すべてのエディションへの行レベルのセキュリティ、Always Encrypted、動的なデータ マスキング、データベースの監査、インメモリ OLTP および他のいくつかの機能の追加が含まれます。 詳細については、「 [SQL Server 2016 の各エディションでサポートされる機能](../sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。   
-  [sp_refresh_parameter_encryption](../relational-databases/system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md) によって、Always On を使用して暗号化されたオブジェクトが再定義されたときに、Always On 暗号化でメタデータを更新できます。  


##  <a name="Feature"></a> SQL Server 2016 (RTM)
このセクションには、次のサブセクションが含まれています。

-   [列ストア インデックス](#columnstore-indexes)
-   [データベース スコープ構成](#database-scoped-configurations)
-   [インメモリ OLTP](#in-memory-oltp)
-   [クエリ オプティマイザー](#query-optimizer)
-   [ライブ クエリ統計](#live-query-statistics)
-   [クエリ ストア](#query-store)
-   [テンポラル テーブル](#temporal-tables)
-   [Microsoft Azure BLOB Storage へのストライプ バックアップ](#striped-backups-to-microsoft-azure-blob-storage)
-   [Microsoft Azure BLOB Storage へのファイル スナップショット バックアップ](#file-snapshot-backups-to-microsoft-azure-blob-storage)
-   [管理対象のバックアップ](#managed-backup)
-   [TempDB データベース](#tempdb-database)
-   [組み込みの JSON サポート](#built-in-json-support)
-   [PolyBase](#polybase)
-   [Stretch Database](#stretch-database)
-   [UTF-8 のサポート](#support-for-utf-8)
-   [新しい既定のデータベース サイズと自動拡張値](#new-default-database-size-and-autogrow-values)
-   [Transact-SQL の機能強化](#transact-sql-enhancements)
-   [システム ビューの機能強化](#system-view-enhancements)
-   [セキュリティの強化](#security-enhancements)
-   [高可用性に関する機能強化](#high-availability-enhancements)
-   [レプリケーションの機能強化](#replication-enhancements)
-   [ツールの機能強化](#tools-enhancements)

## <a name="columnstore-indexes"></a>列ストア インデックス

このリリースでは、更新可能な非クラスター化列ストア インデックス、インメモリ テーブルでの列ストア インデックス、運用分析のための多数の新機能など、列ストア インデックスの機能が強化されています。

- 読み取り専用の非クラスター化列ストア インデックスは、アップグレード後に更新できます。  更新できるようにするためにインデックスを再構築する必要はありません。

- 列ストア インデックスでの分析クエリ (特に、集計や文字列の述語) のパフォーマンスが改善されています。

- DMV および XEvent ではサポート性が改善されています。

詳細については、オンライン ブックの「[列ストア インデックスの説明](../relational-databases/indexes/columnstore-indexes-overview.md)」セクションにある次のトピックを参照してください。

- [列ストア インデックスのバージョン管理機能の概要](~/relational-databases/indexes/columnstore-indexes-what-s-new.md) - 新機能が含まれています。

- [列ストア インデックス データの読み込み](../relational-databases/indexes/columnstore-indexes-data-loading-guidance.md)

- [列ストア インデックスのクエリ パフォーマンス](~/relational-databases/indexes/columnstore-indexes-query-performance.md)

- [列ストアを使用したリアルタイム運用分析の概要](../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)

- [データ ウェアハウスの列ストア インデックス](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md)

- [列ストア インデックスの最適化](~/relational-databases/indexes/columnstore-indexes-defragmentation.md)


## <a name="database-scoped-configurations"></a>データベース スコープ構成


新しい [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) ステートメントを使用すると、特定のデータベースの特定の構成を制御できます。 構成の設定は、アプリケーションの動作に影響します。

新しいステートメントは、[!INCLUDE[ssSQL15](../includes/sssql15-md.md)] および [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] の両方で使用できます。



## <a name="in-memory-oltp"></a>インメモリ OLTP


### <a name="storage-format-change"></a>ストレージ形式の変更

SQL Server 2014 と 2016 の間で、メモリ最適化テーブルのストレージ形式が変更されています。 SQL Server 2014 からのアップグレード、アタッチ/復元については、新しいストレージ形式がシリアル化され、データベースの復元中に 1 回再起動します。

- [SQL Server 2016 へのアップグレード](../database-engine/install-windows/upgrade-sql-server.md)


### <a name="alter-table-is-log-optimized-and-runs-in-parallel"></a>ALTER TABLE がログ最適化され、並列で実行される

メモリ最適化テーブルで ALTER TABLE ステートメントを実行するときに、メタデータの変更のみがログに書き込まれるようになりました。 これにより、ログ IO が大幅に減少します。 また、ほとんどの ALTER TABLE シナリオが並列実行されるようになったので、ステートメントの実行期間を大幅に短縮できます。

- 並列処理されない例外的なケース (LOB を含む) については、「[メモリ最適化テーブルの変更](../relational-databases/in-memory-oltp/altering-memory-optimized-tables.md)」を参照してください。



### <a name="statistics"></a>統計

[メモリ最適化テーブルの統計](../relational-databases/in-memory-oltp/statistics-for-memory-optimized-tables.md)は自動的に更新されるようになりました。 さらに統計収集方式としてサンプリングがサポートされるようになったので、高価なフルスキャン方式を避けることができます。


### <a name="parallel-and-heap-scan-for-memory-optimized-tables"></a>メモリ最適化テーブルの並列/ヒープ スキャン

メモリ最適化テーブルとメモリ最適化テーブルのすべてのインデックスで並列スキャンがサポートされるようになりました。 これにより、分析クエリのパフォーマンスが向上します。

また、ヒープ スキャンもサポートされ、並列実行できます。 メモリ最適化テーブルの場合、ヒープ スキャンは、行を保存するためのメモリ内ヒープ データ構造を利用し、テーブル内のすべての行をスキャンすることになります。 テーブルを完全にスキャンする場合、インデックスよりヒープ スキャンのほうが効率的です。

### <a name="transact-sql-improvements-for-memory-optimized-tables"></a>メモリ最適化テーブルに関係する Transact-SQL の改善点

いくつかの Transact-SQL 要素は、SQL Server 2014 のメモリ最適化テーブルではサポートされていなかったものの、SQL Server 2016 でサポートされるようになりました。


- UNIQUE 制約とインデックスがサポートされます。


- メモリ最適化テーブルどうしを参照する FOREIGN KEY がサポートされています。
  - これらの外部キーが参照できるのは、主キーのみで一意のキーは参照できません。


- CHECK 制約がサポートされています。

- 一意ではないインデックスは、そのキー内で NULL 値を許容できます。

- メモリ最適化テーブルで TRIGGER がサポートされています。
  - AFTER トリガーのみがサポートされます。 INSTEADOF トリガーはサポートされていません。
  - メモリ最適化テーブルのトリガーでは、WITH NATIVE_COMPILATION を使用する必要があります。

- SQL Server のすべてのコード ページを完全サポートし、メモリ最適化テーブルとネイティブ コンパイル T-SQL モジュールにあるインデックスやその他のアイテムと照合します。


- [メモリ最適化テーブルの変更](../relational-databases/in-memory-oltp/altering-memory-optimized-tables.md)をサポート:
  - ADD インデックスと DROP インデックス。 ハッシュ インデックスの bucket_count を変更します。
  - スキーマ変更: 列の追加/削除/変更、制約の追加/削除。

- 組み合わせた長さが 8,060 バイト ページの長さを超える複数の列をメモリ最適化テーブルに含めることができるようになりました。 例として、 `nvarchar(4000)`型の列が3 列が含まれているテーブルがあります。 そうした例では、行外に格納される列もあります。 列が行内と行外のどちらにあるかをクエリは意識しないで済みます。

- [LOB (ラージ オブジェクト) タイプ](../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md) `varbinary(max)`、`nvarchar(max)`、`varchar(max)` がメモリ最適化テーブルでサポートされるようになりました。


全般的な情報については、以下をご覧ください。

- [インメモリ OLTP でサポートされていない Transact-SQL の構造](../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)
- [インメモリ OLTP に対してサポートされていない SQL Server の機能](~/relational-databases/in-memory-oltp/unsupported-sql-server-features-for-in-memory-oltp.md)



### <a name="performance-and-scaling-improvements"></a>パフォーマンスとスケーリングの改善

- データ サイズに制限はありません。 「 [メモリ最適化テーブルのメモリ必要量の推定](~/relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md)」を参照してください。

- [メモリ最適化テーブルへの変更をディスクに保持](../relational-databases/in-memory-oltp/scalability.md)する複数の同時実行スレッドが提供されるようになりました。

- [解釈された Transact-SQL を使用したメモリ最適化テーブルへのアクセス](../relational-databases/in-memory-oltp/accessing-memory-optimized-tables-using-interpreted-transact-sql.md)の並列プランのサポート。


### <a name="enhancements-in-sql-server-management-studio"></a>SQL Server Management Studio の機能強化

- [テーブルまたはストアド プロシージャをインメモリ OLTP に移植する必要があるかどうかの確認](../relational-databases/in-memory-oltp/determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)を行うためにデータ コレクターまたは管理データ ウェアハウスを構成する必要はなくなりました。 レポートを実稼働データベースで直接実行できるようになりました。

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースで複数のオブジェクトの移行の適合性を評価するための、[移行評価用 PowerShell コマンドレット](../relational-databases/in-memory-oltp/powershell-cmdlet-for-migration-evaluation.md)。

- データベースを右クリックし、[タスク]、[インメモリ OLTP 移行チェックリストの生成] の順に選んで移行チェックリストを生成します。

### <a name="cross-feature-support"></a>相互機能サポート

- インメモリ OLTP で一時的なシステム バージョン管理を使用できるようになりました。 詳細については、「[メモリ最適化テーブルでのシステム バージョン管理されたテンポラル テーブル](../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)」を参照してください。

- インメモリ OLTP ワークロードからのネイティブ コンパイル コードでクエリ ストアがサポートされるようになりました。 詳細については、「 [インメモリ OLTP でのクエリ ストアの使用](../relational-databases/performance/using-the-query-store-with-in-memory-oltp.md)」を参照してください。

- [メモリ最適化テーブルの行レベルのセキュリティ](../relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables.md#rls)

- [複数のアクティブな結果セット &#40;MARS&#41; の使用](../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md)による接続で、メモリ最適化テーブルとネイティブ コンパイル ストアド プロシージャにアクセスできるようになりました。

- [Transparent Data Encryption (TDE)](../relational-databases/security/encryption/transparent-data-encryption.md) のサポート。 データベースが ENCRYPTION 用に構成されている場合、[メモリ最適化ファイル グループ](../relational-databases/in-memory-oltp/the-memory-optimized-filegroup.md)内のファイルも暗号化されるようになりました。

詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。


## <a name="query-optimizer"></a>クエリ オプティマイザー
### <a name="compatibility-level-guarantees"></a>互換性レベルの保証
データベースを SQL Server 2016 にアップグレードするとき、(120 や 110 など) 使用していた以前の互換性レベルに残っている場合、プランの変更は表示されません。 クエリ オプティマイザー関連の新しい機能や拡張は、最新の互換性レベルでのみ利用できます。 
### <a name="trace-flag-4199"></a>トレース フラグ 4199
一般に、Server 2016 ではトレース フラグ 4199 を使用する必要はありません。このトレース フラグで制御されるほとんどのクエリ オプティマイザーの動作が、Server 2016 では最新の互換性レベル (130) で無条件で有効になるためです。
### <a name="new-referential-integrity-operator"></a>参照整合性の新しい演算子
テーブルから、他のテーブルと列を最大 253 個まで外部キーとして参照 (発信参照) することができます。 [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] では、1 つのテーブル内の列を参照 (着信参照) できる他のテーブルと列の数が 253 から 10,000 までに限られています。 制限については、「 [Create Foreign Key Relationships](../relational-databases/tables/create-foreign-key-relationships.md)」を参照してください。 参照整合性の新しい演算子が導入されました (互換性レベル 130)。この演算子は参照整合性チェックをインプレースで実行します。 これにより、大量の着信参照が含まれるテーブルで、UPDATE 操作と UPDATE 操作のパフォーマンスが全体的に改善されます。そのため、大量の着信参照を使用することが実行可能となります。 詳細設定については、「 [Query Optimizer Additions in SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/05/23/query-optimizer-additions-in-sql-server/)」 (SQL Server 2016 のクエリ オプティマイザーの追加) を参照してください。
### <a name="parallel-update-of-sampled-statistics"></a>サンプリング統計の並列更新
データ サンプリングによる統計の作成が並列で実行できるようになりました (互換性レベル 130)。統計情報収集のパフォーマンスが上がります。 詳細については、「[Update Statistics](../t-sql/statements/update-statistics-transact-sql.md)」を参照してください。
### <a name="sublinear-threshold-for-update-of-statistics"></a>統計の更新の下位線形しきい値
大きなテーブルで統計を自動更新する際のパフォーマンスが上がりました (互換性レベル 130)。 SQL Server 2016 から、統計の自動更新をトリガーするしきい値は 20% となります。大きなテーブルの場合、テーブルの行の数が増えるため、このしきい値は下がります (パーセンテージ)。 しきい値を下げるためにトレース フラグ 2371 を設定する必要はなくなりました。 
### <a name="other-enhancements"></a>その他の機能強化
Insert select ステートメントで挿入では、マルチ スレッドは、または並列プランを持つことができます (互換性レベル 130)。 並列プランを取得するには、INSERT …SELECT ステートメントで TABLOCK ヒントを使用する必要があります。 詳細については、「 [Parallel Insert Select](https://blogs.msdn.microsoft.com/sqlcat/2016/07/06/sqlsweet16-episode-3-parallel-insert-select/)」 (並列 Insert Select) を参照してください。

## <a name="live-query-statistics"></a>ライブ クエリ統計
 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] では、アクティブ クエリのライブ実行プランを表示できます。 このライブ クエリ プランでは、クエリ プラン演算子間の制御フローとして、クエリ実行プロセスをリアルタイムで洞察できます。 詳細については、「 [Live Query Statistics](../relational-databases/performance/live-query-statistics.md)」を参照してください。

## <a name="query-store"></a>クエリ ストア
クエリ ストアは、クエリ プランの選択やパフォーマンスに関する洞察を DBA に提供する新しい機能です。 これにより、クエリ プランの変更によって生じるパフォーマンスの違いがすばやくわかるようになり、パフォーマンス上のトラブルシューティングを簡略化できます。 この機能により、クエリ、プラン、ランタイム統計情報の履歴が自動的にキャプチャされ、レビュー用に保持されます。 データは時間枠で区分されるため、データベースの使用パターンを表示して、サーバー上でクエリ プランが変わった時点を確認することができます。 クエリ ストアでは、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] のダイアログ ボックスを使用して情報を表示し、選択されたクエリ プランのいずれかにクエリを適用することができます。 詳細については、「[Monitoring Performance By Using the Query Store](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)」を参照してください。


## <a name="temporal-tables"></a>テンポラル テーブル
[!INCLUDE[ssSQL15](../includes/sssql15-md.md)] では、システム バージョン管理されたテンポラル テーブルがサポートされるようになりました。 テンポラル テーブルは新しい種類のテーブルです。このテーブルで、任意の時点でストアド ファクトに関する正しい情報が提供されます。 各テンポラル テーブルは実際には2 つのテーブルで構成されており、1 つは現在のデータ用で、もう1 つは履歴データ用です。 現在のデータを含むテーブルのデータが変更された場合、システムによって以前の値が履歴テーブルに格納されます。 クエリの構造は、この複雑さがユーザーにわからないようになっています。 詳細については、「 [Temporal Tables](../relational-databases/tables/temporal-tables.md)」を参照してください。

## <a name="backups"></a>バックアップ

### <a name="striped-backups-to-microsoft-azure-blob-storage"></a>Azure BLOB Storage へのストライプ バックアップ
[!INCLUDE[ssSQL15](../includes/sssql15-md.md)] では、Microsoft Azure Blob ストレージ サービスを使用した SQL Server Backup to URL がブロック BLOB によるストライプ バックアップ セットをサポートするようになり、最大バックアップ サイズ 12.8 TB をサポートするようになりました。 例については、「 [Code Examples](../relational-databases/backup-restore/sql-server-backup-to-url.md#Examples)」を参照してください。

### <a name="file-snapshot-backups-to-microsoft-azure-blob-storage"></a>Microsoft Azure BLOB Storage へのファイル スナップショット バックアップ
 [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]では、SQL Server Backup to URL で、Microsoft Azure BLOB ストレージ サービスによりすべてのデータベース ファイルが格納されたデータベースをバックアップする際に Azure スナップショットを使用できるようになりました。 詳細については、「 [Azure でのデータベース ファイルのファイル スナップショット バックアップ](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)」を参照してください。

### <a name="managed-backup"></a>管理対象のバックアップ
[!INCLUDE[ssSQL15](../includes/sssql15-md.md)] では、SQL Server Managed Backup to Microsoft Azure でバックアップ ファイルに新しいブロック BLOB ストレージが使用されます。 また、管理対象のバックアップはいくつかの点が変更され、機能が強化されています。

-   バックアップの自動とカスタムの両方のスケジューリングがサポートされます。

-   システム データベースのバックアップがサポートされます。

-   単純復旧モデルを使用するデータベースがサポートされます。

 詳細については、「 [SQL Server Managed Backup to Microsoft Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)」をご覧ください。

> [!NOTE]
>  [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] の場合、これらの新しい管理対象バックアップ機能では、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の対応する UI はまだサポートされていません。

## <a name="tempdb-database"></a>TempDB データベース
 以下のように、TempDB のいくつかの機能が強化されています。

-   tempdb ではトレース フラグ 1117 と 1118 は不要になりました。 複数の tempdb データベース ファイルがある場合は、すべてのファイルが拡張設定に応じて、同時に拡張されます。 さらに、tempdb 内のすべての割り当てでは単一エクステントが使用されます。

-   既定では、セットアップ時に、CPU 数と 8 のいずれか小さい方と同数の tempdb ファイルが追加されます。

-   セットアップ時に、tempdb データベース ファイルの数、初期サイズ、自動拡張およびディレクトリの位置を構成できます。その場合、SQL Server インストール ウィザードの "データベース エンジンの構成 - TempDB" セクションで新しい UI 入力コントロールを使用します。

-   既定の初期サイズは 8 MB で、既定の自動拡張は 64 MB です。

-   tempdb データベース ファイルに対して複数のボリュームを指定できます。 複数のディレクトリが指定されている場合、tempdb データ ファイルはラウンド ロビン形式でそのディレクトリにまたがるようになります。

## <a name="built-in-json-support"></a>組み込みの JSON サポート
SQL Server 2016 には、JSON のインポートとエクスポートと、JSON 文字列を処理するための組み込みサポートが追加されました。 この組み込みサポートには、次のステートメントおよび関数が含まれます。

-   **SELECT** ステートメントに **FOR JSON** 句を追加して、クエリの結果を JSON として書式設定するか、JSON をエクスポートします。 たとえば、**FOR JSON** 句を使用して、クライアント アプリケーションからの JSON 出力の書式設定を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に委任します。 詳細については、「[FOR JSON を使用してクエリ結果を JSON として書式設定する &#40;SQL Server&#41;](../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)」を参照してください。

-   **OPENJSON** 行セット プロバイダー関数を呼び出して、JSON データを行と列に変換するか、JSON をインポートします。 **OPENJSON** を使用して、JSON データを SQL Server にインポートしたり、現在 JSON を直接使用できないアプリやサービス用に JSON データを行と列に変換したりします。 詳細については、「[Convert JSON Data to Rows and Columns with OPENJSON &#40;SQL Server&#41; (OPENJSON を使用して JSON データを行と列に変換する (SQL Server))](../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md)」を参照してください。

-   **ISJSON** 関数は、文字列に有効な JSON が含まれているかどうかをテストします。 詳細については、「[ISJSON &#40;Transact-SQL&#41;](../t-sql/functions/isjson-transact-sql.md)」を参照してください。

-   **JSON_VALUE** 関数は、JSON 文字列からスカラー値を抽出します。詳細については、「[JSON_VALUE &#40;Transact-SQL&#41;](../t-sql/functions/json-value-transact-sql.md)」を参照してください。

-   **JSON_QUERY** 関数は、JSON 文字列からオブジェクトまたは配列を抽出します。 詳細については、「[JSON_QUERY &#40;Transact-SQL&#41;](../t-sql/functions/json-query-transact-sql.md)」を参照してください。

-   **JSON_MODIFY** 関数は、JSON 文字列内のプロパティの値を更新し、更新された JSON 文字列を返します。 詳細については、「[JSON_MODIFY &#40;Transact-SQL&#41;](../t-sql/functions/json-modify-transact-sql.md)」を参照してください。

## <a name="polybase"></a>PolyBase
 PolyBase では T-SQL ステートメントを使用して、Hadoop または Azure BLOB ストレージに格納されたデータにアクセスし、アドホック形式でクエリを実行することができます。 また、半構造化データにクエリを実行し、その結果を SQL Server に格納されているリレーショナル データ セットと結合することもできます。 PolyBase はデータ ウェアハウスのワークロード用に最適化されており、分析クエリ シナリオで使用するためのものです。

 詳細については、「[PolyBase Guide (PolyBase ガイド)](../relational-databases/polybase/polybase-guide.md)」を参照してください。

## <a name="stretch-database"></a>Stretch Database
 Stretch Database は、[!INCLUDE[ssSQL15](../includes/sssql15-md.md)] の新機能で、履歴データを透過的かつ安全に Microsoft Azure クラウドに移行します。 SQL Server のデータがオンプレミスにあろうと、クラウドに拡張されていようと、シームレスにアクセスできます。 データの格納場所を決定するポリシーはユーザーが設定し、データ移動は SQL Server によってバックグラウンドで処理されます。 テーブル全体が常にオンラインなので、いつでもクエリを実行できるほか、 Stretch Database では既存のクエリまたはアプリケーションに変更を加える必要がありません。データの場所は、アプリケーションに対して完全に透過的になっています。 詳細については、「 [Stretch Database](../sql-server/stretch-database/stretch-database.md)」を参照してください。
 
## <a name="support-for-utf-8"></a>UTF-8 のサポート
[bcp Utility](../tools/bcp-utility.md)、[BULK INSERT](../t-sql/statements/bulk-insert-transact-sql.md)、[OPENROWSET](../t-sql/functions/openrowset-transact-sql.md) で UTF-8 コード ページがサポートされるようになりました。 詳細については、それらの各トピックと「[フォーマット ファイルの作成 &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md)」を参照してください。

## <a name="new-default-database-size-and-autogrow-values"></a>新しい既定のデータベース サイズと自動拡張値
model データベースの新しい値および新しいデータベースの既定値 (model に基づく)。 データとログ ファイルの初期サイズが 8 MB になりました。 データとログ ファイルの既定の自動拡張は 64 MB になりました。


## <a name="transact-sql-enhancements"></a>Transact-SQL の機能強化
大幅な機能強化により、このトピックの他のセクションで説明されている機能がサポートされるようになりました。 追加された機能強化の内容は以下のとおりです。
- TRUNCATE TABLE ステートメントで、指定されたパーティションの切り捨てが許可されるようになりました。 詳細については、「[TRUNCATE TABLE &#40;Transact-SQL&#41;](../t-sql/statements/truncate-table-transact-sql.md)」を参照してください。
- [ALTER TABLE &#40;Transact-SQL&#41;](../t-sql/statements/alter-table-transact-sql.md) では、テーブルを使用可能な状態にしたままで、多くの列の変更アクションを実行できるようになりました。
- フルテキスト インデックス DMV の[sys.dm_fts_index_keywords_position_by_document &#40;Transact-SQL&#41;](../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-position-by-document-transact-sql.md) では、ドキュメント内のキーワードの位置が返されます。 この DMV は [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] SP2 と [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP1 でも追加されています。
- 新しいクエリ ヒントの **NO_PERFORMANCE_SPOOL** で、スプール演算子がクエリ プランに追加されないようにすることができます。 これにより、多くの同時実行クエリがスプール操作で実行されているときのパフォーマンスを向上させることができます。 詳細については、「[クエリ ヒント &#40;Transact-SQL&#41;](../t-sql/queries/hints-transact-sql-query.md)」を参照してください。
- [FORMATMESSAGE &#40;Transact-SQL&#41;](../t-sql/functions/formatmessage-transact-sql.md) ステートメントが強化され、msg_string 引数を受け入れるようになりました。
- 非クラスター化インデックスの最大インデックス キーのサイズが 1700 バイトに引き上げられました。
- AGGREGATE、ASSEMBLY、COLUMN、CONSTRAINT、DATABASE、DEFAULT、FUNCTION、INDEX、PROCEDURE、ROLE、RULE、SCHEMA、SECURITY POLICY、SEQUENCE、SYNONYM、TABLE、TRIGGER、TYPE、USER、VIEW に関連する DROP ステートメントに対して、新しい DROP IF 構文が追加されました。 構文については、個々の構文のトピックを参照してください。
- 並列処理の次数を指定するために、MAXDOP オプションが [DBCC CHECKTABLE &#40;Transact-SQL&#41;](../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)、[DBCC CHECKDB &#40;Transact-SQL&#41;](../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)、[DBCC CHECKFILEGROUP &#40;Transact-SQL&#41;](../t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql.md) に追加されました。
- SESSION_CONTEXT を設定できるようになりました。 これには、[SESSION_CONTEXT &#40;Transact-SQL&#41;](../t-sql/functions/session-context-transact-sql.md) 関数、[CURRENT_TRANSACTION_ID &#40;Transact-SQL&#41;](../t-sql/functions/current-transaction-id-transact-sql.md) 関数、[sp_set_session_context &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md) プロシージャが含まれます。
- Advanced Analytics Extensions により、R などのサポート対象言語で記述されたスクリプトの実行が可能になります。[!INCLUDE[tsql](../includes/tsql-md.md)] では、[sp_execute_external_script &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) ストアド プロシージャと、[external scripts enabled サーバー構成オプション](../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md) を導入することで R がサポートされます。 詳細については、「 [SQL Server R Services](../advanced-analytics/r-services/sql-server-r-services.md)」を参照してください。
- また、R をサポートするために、外部リソース プールを作成することができます。 詳細については、「[CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../t-sql/statements/create-external-resource-pool-transact-sql.md)」を参照してください。  新しいカタログ ビューおよび DMV ([sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md) および [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md))。 [sp_execute_external_script &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) および [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../t-sql/statements/create-workload-group-transact-sql.md) で使用できる引数が追加されました。 既存のリソース ガバナーのカタログ ビューおよび DMV のいくつかに列が追加されました。
- [CREATE USER](../t-sql/statements/create-user-transact-sql.md) 構文が ALLOW_ENCRYPTED_VALUE_MODIFICATIONS オプションで強化され、Always Encrypted 機能がサポートされるようになりました。 詳細については、「[Always Encrypted で保護された機微なデータの移行](../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md)」を参照してください。
- [COMPRESS &#40;Transact-SQL&#41;](../t-sql/functions/compress-transact-sql.md) 関数および [DECOMPRESS &#40;Transact-SQL&#41;](../t-sql/functions/decompress-transact-sql.md) 関数は、GZIP アルゴリズムに合わせて値を変換したり、変換解除したりします。
- 日付と時刻の相互作用をサポートするために、[DATEDIFF_BIG &#40;Transact-SQL&#41;](../t-sql/functions/datediff-big-transact-sql.md) 関数および [AT TIME ZONE &#40;Transact-SQL&#41;](../t-sql/queries/at-time-zone-transact-sql.md) 関数と [sys.time_zone_info &#40;Transact-SQL&#41;](../relational-databases/system-catalog-views/sys-time-zone-info-transact-sql.md) ビューが追加されました。
- (これまでのサーバー レベルの資格情報に加え) データベース レベルで資格情報を作成できるようになりました。 詳細については、「[CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../t-sql/statements/create-database-scoped-credential-transact-sql.md)」を参照してください。
- [SERVERPROPERTY &#40;Transact-SQL&#41;](../t-sql/functions/serverproperty-transact-sql.md) に新しい 8 つのプロパティ(InstanceDefaultDataPath、InstanceDefaultLogPath、ProductBuild、ProductBuildType、ProductMajorVersion、ProductMinorVersion、ProductUpdateLevel、ProductUpdateReference) が追加されました。
- [HASHBYTES &#40;Transact-SQL&#41;](../t-sql/functions/hashbytes-transact-sql.md) 関数に対する 8,000 バイトの入力長制限が削除されました。
- 新しい文字列関数 [STRING_SPLIT &#40;Transact-SQL&#41;](../t-sql/functions/string-split-transact-sql.md) および [STRING_ESCAPE &#40;Transact-SQL&#41;](../t-sql/functions/string-escape-transact-sql.md) が追加されました。
- 自動拡張オプション:トレース フラグ 1117 が ALTER DATABASE の AUTOGROW_SINGLE_FILE および AUTOGROW_ALL_FILES オプションに置き換えられ、トレース フラグ 1117 の効力はなくなりました。 詳細については、「[ALTER DATABASE の File および Filegroup オプション &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)」および [sys.filegroups &#40;Transact-SQL&#41;](../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md) の新しい is_autogrow_all_files 列をご覧ください。
- 混合エクステントの割り当て:ユーザー データベースの場合、オブジェクトの最初の 8 ページの既定の割り当てで、混合ページ エクステントではなく単一エクステントが使用されるようになります。 トレース フラグ 1118 は ALTER DATABASE の SET MIXED_PAGE_ALLOCATION オプションに置き換えられ、トレース フラグ 1118 の効力はなくなりました。 詳細については、「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-set-options.md)」および [sys.databases &#40;Transact-SQL&#41;](../relational-databases/system-catalog-views/sys-databases-transact-sql.md) の新しい `is_mixed_page_allocation_on` 列をご覧ください。

### <a name="transact-sql-improvements-for-natively-compiled-modules"></a>ネイティブ コンパイル モジュールに関係する Transact-SQL の改善点

いくつかの Transact-SQL 要素は SQL Server 2014 のネイティブ コンパイル モジュールではサポートされていなかったものの、SQL Server 2016 でサポートされるようになりました。


- クエリのコンストラクト:
  - UNION および UNION ALL
  - SELECT DISTINCT
  - OUTER JOIN
  - SELECT におけるサブクエリ


- INSERT、UPDATE、DELETE ステートメントに [OUTPUT 句](../t-sql/queries/output-clause-transact-sql.md)を含めることができるようになりました。

- ネイティブ プロシージャで LOB を次の方法で使用できるようになりました。
  - 変数の宣言。
  - 受信した入力パラメーター。
  - ネイティブ プロシージャにおいて文字列関数 (LTrim または Substring など) に渡されるパラメーター。


- インライン (つまり1 ステートメントの) テーブル値関数 (TVF) をネイティブ コンパイルできるようになりました。

- スカラーのユーザー定義関数 (UDF) をネイティブ コンパイルできるようになりました。

- ネイティブ プロシージャから以下を呼び出すサポートが強化されました。
  - 組み込み[セキュリティ関数](../t-sql/functions/security-functions-transact-sql.md)。
  - 組み込み[算術関数](../t-sql/functions/mathematical-functions-transact-sql.md)。
  - 組み込み関数 `@@SPID`。


- EXECUTE AS CALLER がサポートされるようになりました。つまり、ネイティブ コンパイルの T-SQL モジュールを作成するとき、EXECUTE AS 句が不要になりました。


全般的な情報については、以下をご覧ください。

- [ネイティブ コンパイル T-SQL モジュールでサポートされる機能](../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md)
- [Altering Natively Compiled T-SQL Modules](../relational-databases/in-memory-oltp/altering-natively-compiled-t-sql-modules.md)

## <a name="system-view-enhancements"></a>システム ビューの機能強化
- 2 つの新しいビューで、行レベルのセキュリティがサポートされるようになりました。 詳細については、「[sys.security_predicates &#40;Transact-SQL&#41;](../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)」および「[sys.security_policies &#40;Transact-SQL&#41;](../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)」を参照してください。
- 7 つの新しいビューではクエリ ストア機能がサポートされます。 詳細については、「[Query Store Catalog Views &#40;Transact-SQL&#41; (クエリのストアのカタログ ビュー (Transact-SQL))](../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)」を参照してください。
- [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md) に追加された 24 個の新しい列では、メモリ許可に関する情報が提供されます。
- メモリ許可を指定するための 2 つの新しいクエリ ヒント (MIN_GRANT_PERCENT および MAX_GRANT_PERCENT) が追加されました。 「[クエリ ヒント &#40;Transact-SQL&#41;](../t-sql/queries/hints-transact-sql-query.md)」を参照してください。
- [sys.dm_exec_session_wait_stats &#40;Transact-SQL&#41;](../relational-databases/system-dynamic-management-views/sys-dm-exec-session-wait-stats-transact-sql.md) では、サーバー全体の [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md) と似たようなセッションごとのレポートが提供されます。
- [sys.dm_exec_function_stats &#40;Transact-SQL&#41;](../relational-databases/system-dynamic-management-views/sys-dm-exec-function-stats-transact-sql.md) では、スカラー値関数に関する実行統計情報が提供されます。
- [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] 以降、[sys.dm_db_index_usage_stats &#40;Transact-SQL&#41;](../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md) のエントリは [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] より前の場合と同様に保持されます。
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに送信されたステートメントに関する情報は、新しい動的管理関数の [sys.dm_exec_input_buffer &#40;Transact-SQL&#41;](../relational-databases/system-dynamic-management-views/sys-dm-exec-input-buffer-transact-sql.md) で返すことができます。
- 2 つの新しいビューが [SQL Server R Services](../advanced-analytics/r-services/sql-server-r-services.md)をサポートします ( [sys.dm_external_script_requests](../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) および [sys.dm_external_script_execution_stats](../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md))。 


## <a name="security-enhancements"></a>セキュリティの強化

### <a name="row-level-security"></a>行レベルのセキュリティ
行レベルのセキュリティではアクセス制御に基づく述語が導入されています。 管理者が適切に決定したメタデータ (ラベルなど) や他の条件を考慮に入れることができる、柔軟で、集中管理された、述語ベースの評価を備えています。 述語は、ユーザーがその属性に基づいて適切にデータにアクセスできるかどうかを決定する条件として使用されます。 ラベルに基づくアクセス制御は、述語に基づくアクセス制御を使用して実装できます。 詳細については、「[行レベルのセキュリティ](../relational-databases/security/row-level-security.md)」を参照してください。


### <a name="always-encrypted"></a>Always Encrypted
Always Encrypted により、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は暗号化されたデータに対して操作を実行することができます。特筆すべき点は、暗号化キーが、サーバー上ではなく顧客の信頼できる環境内のアプリケーションと一緒にあることです。 Always Encrypted では顧客データがセキュリティで保護されるため、DBA はプレーン テキスト データにアクセスできません。 データの暗号化と暗号化解除はドライバー レベルで透過的に行われるため、既存のアプリケーションに加える必要が最小限に抑えられます。 詳細については、「[Always Encrypted &#40;データベース エンジン&#41;](../relational-databases/security/encryption/always-encrypted-database-engine.md)」を参照してください。


### <a name="dynamic-data-masking"></a>動的なデータ マスキング
動的データ マスクは、特権のないユーザーに対してデリケートなデータをマスクし、データの公開を制限します。 動的データ マスクでは、公開するデリケートなデータの量を指定することで、そのようなデータに対する未承認のアクセスを防ぎ、アプリケーション レイヤーへの影響が最小限に抑えられます。 これはポリシー ベースのセキュリティ機能です。これにより、データベース内のデータはそのままで、指定されたデータベース フィールドに対するクエリの結果セットで機微なデータを非表示にすることができます。 詳細については、「 [Dynamic Data Masking](../relational-databases/security/dynamic-data-masking.md)」を参照してください。


### <a name="new-permissions"></a>新しい権限
- **ALTER ANY SECURITY POLICY** 権限が、行レベルのセキュリティの実装の一部として使用できます。
- **ALTER ANY MASK** および **UNMASK** 権限は動的なデータ マスキングの実装の一部として使用できます。
- **ALTER ANY COLUMN ENCRYPTION KEY**、 **VIEW ANY COLUMN ENCRYPTION KEY**、 **ALTER ANY COLUMN MASTER KEY DEFINITION**、および **VIEW ANY COLUMN MASTER KEY DEFINITION** 権限は、Always Encrypted 機能の実装の一部として使用できます。
- **ALTER ANY EXTERNAL DATA SOURCE** および **ALTER ANY EXTERNAL FILE FORMAT** 権限は、[!INCLUDE[ssSQL15](../includes/sssql15-md.md)] で表示されますが、適用されるのは [!INCLUDE[ssAPS](../includes/ssaps-md.md)] ([!INCLUDE[ssDW](../includes/ssdw-md.md)]) に対してだけです。
- **EXECUTE ANY EXTERNAL SCRIPT** 権限は R スクリプトのサポートの一部として使用できます。
 - **ALTER ANY DATABASE SCOPED CONFIGURATION** 権限は [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) ステートメントの使用を承認するために使用できます。

### <a name="transparent-data-encryption"></a>透過的なデータ暗号化
- Transparent Data Encryption が強化され、暗号化の Intel AES-NI ハードウェア アクセラレータがサポートされるようになりました。 これにより、Transparent Data Encryption を有効にした場合の CPU のオーバーヘッドが低減されます。

### <a name="aes-encryption-for-endpoints"></a>エンドポイントの AES 暗号化
- エンドポイントの既定の暗号化が RC4 から AES に変更されました。

### <a name="new-credential-type"></a>新しい資格情報の種類
- (これまでのサーバー レベルの資格情報に加え) データベース レベルで資格情報を作成できるようになりました。 詳細については、「[CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../t-sql/statements/create-database-scoped-credential-transact-sql.md)」を参照してください。


## <a name="high-availability-enhancements"></a>高可用性に関する機能強化
SQL Server 2016 Standard Edition で、Always On の基本的な可用性グループがサポートされるようになりました。 基本的な可用性グループは、プライマリおよびセカンダリ レプリカのサポートを提供します。 この機能は、高可用性の廃止されたデータベース ミラーリング テクノロジに代わるものです。 基本および拡張可用性グループの違いの詳細については、「[Basic Availability Groups &#40;Always On Availability Groups&#41; (基本的な可用性グループ (Always On 可用性グループ))](../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md)」を参照してください。

読み取りを目的とした接続要求を一連の読み取り専用レプリカで負荷分散することがサポートされるようになりました。 以前の動作では常に、ルーティング リストで最初に使用可能な読み取り専用レプリカに直接接続されていました。 詳細については、「[読み取り専用レプリカ間の負荷分散の構成](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md#loadbalancing)」を参照してください。

 自動フェールオーバーをサポートするレプリカの数が 2 から 3 に増えました。

 Always On フェールオーバー クラスターでグループ管理サービス アカウントがサポートされるようになりました。 詳細については、「[グループの管理されたサービス アカウントの概要](https://technet.microsoft.com/library/hh831782.aspx)」を参照してください。 Windows Server 2012 R2 の場合は、パスワードの変更後の一時的なダウンタイムを回避するために更新プログラムが必要になります。 更新プログラムを取得する場合は、「 [gMSA ベースのサービスは、Windows Server 2012 R2 のドメインでパスワードを変更した後ログインできません](https://support.microsoft.com/kb/2998082/)」を参照してください。

 [!INCLUDE[ssHADR](../includes/sshadr-md.md)] では、Windows Server 2016 での分散トランザクションおよび DTC がサポートされます。 詳細については、「[Support for distributed transactions (分散トランザクションのサポート)](../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md#dtcsupport)」を参照してください。

 データベースがオフラインになったときにフェールオーバーするように [!INCLUDE[ssHADR](../includes/sshadr-md.md)] を構成できるようになりました。 この変更では、[CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../t-sql/statements/create-availability-group-transact-sql.md) ステートメントまたは [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../t-sql/statements/alter-availability-group-transact-sql.md) ステートメントで **DB_FAILOVER** オプションを **ON** に設定する必要があります。

Always On で、暗号化されたデータベースがサポートされるようになりました。 可用性グループ ウィザードでは、新しい可用性グループの作成時または既存の可用性グループへのデータベースやレプリカの追加時に、データベース マスター キーを含むデータベースのパスワードの入力を求められるようになりました。

2 つの別個の Windows Server フェールオーバー クラスター (WSFC) 内の 2 つの可用性グループを、1 つの分散可用性グループに結合できるようになりました。 詳細については、「[Distributed Availability Groups &#40;Always On Availability Groups&#41; (分散型可用性グループ (Always On 可用性グループ))](../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)」を参照してください。

直接シード処理で、セカンダリ レプリカをネットワーク経由で自動的にシード処理することができます (ターゲット データベースの物理バックアップをセカンダリで復元する必要がある手動によるシード処理ではない)。 直接シード処理は、[CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../t-sql/statements/create-availability-group-transact-sql.md) ステートメントまたは [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../t-sql/statements/alter-availability-group-transact-sql.md) ステートメントで **SEEDING_MODE=AUTOMATIC** を設定して指定します。 直接シード処理で使用される各セカンダリ レプリカに対し、**GRANT CREATE ANY DATABASE** に [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../t-sql/statements/alter-availability-group-transact-sql.md) を指定する必要もあります。

**パフォーマンスの向上** - 可用性グループの同期スループットが最大 10 倍向上しました。これは、プライマリ レプリカのログ ブロックの並列かつ高速な圧縮、最適化された同期プロトコル、セカンダリ レプリカのログ レコードの並列圧縮解除と再実行によります。 これにより、読み取り可能セカンダリの鮮度が向上し、フェールオーバーの場合のデータベースの復旧時間が短縮されます。 SQL Server 2016 ではメモリ最適化テーブルの再実行をまだ並列処理できないことにご注意ください。

## <a name="replication-enhancements"></a>レプリケーションの機能強化
- メモリ最適化テーブルのレプリケーションがサポートされるようになりました。 詳細については、「[メモリ最適化テーブル サブスクライバーへのレプリケーション](../relational-databases/replication/replication-to-memory-optimized-table-subscribers.md)」を参照してください。
- [!INCLUDE[ssSDSFull](../includes/sssdsfull-md.md)] へのレプリケーションがサポートされるようになりました。 詳細については、「 [Replication to SQL Database](../relational-databases/replication/replication-to-sql-database.md)」を参照してください。

## <a name="tools-enhancements"></a>ツールの機能強化

### <a name="management-studio"></a>Management Studio
最新の [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)をダウンロードしてください。

- [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] では、Microsoft Azure への接続用に開発中の Active Directory 認証ライブラリ (ADAL) がサポートされます。 これは、[!INCLUDE[ssSQL14](../includes/sssql14-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] で使用される証明書ベース認証に代わるものです。
- 新しいクエリ結果グリッド オプションでは、結果グリッドからのテキストのコピーまたは保存時に復帰/改行 (改行文字) を維持することができます。 [ツール] メニューの [オプション] からこのように設定します。
- SQL Server 管理ツールがメイン機能ツリーからインストールされなくなりました。詳細については、「 [SSMS を使用した SQL Server 管理ツールのインストール](https://msdn.microsoft.com/library/af68d59a-a04d-4f23-9967-ad4ee2e63381)」を参照してください。

### <a name="upgrade-advisor"></a>アップグレード アドバイザー
SQL Server 2016 Upgrade Advisor プレビューはスタンドアロン ツールです。これにより、以前のバージョンのユーザーは、SQL Server データベースに対して一連のアップグレード ルールを実行し、重大な動作変更や非推奨の機能を検出でき、Stretch Database などの新機能の採用に役立ちます。

 Upgrade Advisor プレビューは [ここ](https://docs.microsoft.com/sql/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades#how-to-install-and-run-upgrade-advisor) からダウンロードできます。また、Web Platform Installer を使用してインストールすることもできます。

## <a name="see-also"></a>参照
[SQL Server 2016 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)
 
[SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md) 
 
[SSMS を使用した SQL Server 管理ツールのインストール](https://msdn.microsoft.com/library/af68d59a-a04d-4f23-9967-ad4ee2e63381)
