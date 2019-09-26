---
title: データベース エンジンの新機能 - SQL Server 2017 | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
ms.assetid: 42f45b23-6509-45e8-8ee7-76a78f99a920
author: rothja
ms.author: jroth
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 6c0889349631a543e970b11eff9bb24a6f2da208
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874455"
---
# <a name="whats-new-in-database-engine---sql-server-2017"></a>データベース エンジンの新機能 - SQL Server 2017
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

このトピックでは、[!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)] の [!INCLUDE[ssdenoversion-md](../includes/ssdenoversion-md.md)]で導入された強化機能について説明します。 各項目の詳細については、リンクをクリックしてください。

> [!NOTE]  
> SQL Server 2017 には、SQL Server 2016 サービス パックに追加された機能も含まれています。 それらの項目については、「[SQL Server 2016 (データベース エンジン) の新機能](../database-engine/configure-windows/what-s-new-in-sql-server-2016-database-engine.md)」を参照してください。

**機能強化**  

- CLR では、セキュリティ境界としてサポートされなくなった、.NET Framework のコード アクセス セキュリティ (CAS) が使用されます。 `PERMISSION_SET = SAFE` で作成された CLR アセンブリが、外部のシステム リソースにアクセスし、非管理対象コードを呼び出し、sysadmin 特権を取得できる場合があります。 [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)] 以降、CLR アセンブリのセキュリティを強化するために `clr strict security` という `sp_configure` オプションが導入されました。 `clr strict security` は既定で有効になり、`SAFE` および `EXTERNAL_ACCESS` アセンブリを `UNSAFE` とマークされている場合と同様に扱います。 `clr strict security` オプションは、旧バージョンとの互換性のために無効にできますが、これは推奨されません。 Microsoft では、master データベースで `UNSAFE ASSEMBLY` アクセス許可が付与されている対応するログインを含む証明書または非対称キーで、すべてのアセンブリに署名することをお勧めします。 `clr strict security` 機能の回避策として、CLR アセンブリを許可リストに追加できます。 信頼できるアセンブリの許可リストをサポートするために、[sp_add_trusted_assembly](../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md)、[sp_drop_trusted_assembly](../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md)、および [sys.trusted_asssemblies](../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md) が追加されました。 詳しくは、「[CLR の厳密なセキュリティ](configure-windows/clr-strict-security.md)」をご覧ください。  
- 新しい DMF [sys.dm_db_log_stats](../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md) は、トランザクション ログの正常性の監視に役立つ、トランザクション ログ ファイルに関する概要レベルの属性と情報を公開するために、導入されました。  
- 再開可能なオンライン インデックス リビルド。 再開可能なオンライン インデックス リビルドを使用すると、障害 (レプリカへのフェールオーバーや、ディスク領域不足など) 発生後、停止した場所からオンライン インデックス リビルド操作を再開できます。 また、一時停止し、オンライン インデックス リビルド操作を後で再開することもできます。 たとえば、利用できるメンテナンス期間が大規模なテーブルには短すぎる場合、別のメンテナンス期間に優先度の高いタスクを実行したり、インデックスのリビルドを完了したりするために、システム リソースの解放が必要になる場合があります。 最終的に、再開可能なオンライン インデックス リビルドでは大量のログ領域は必要ないため、再開可能なリビルド操作の実行中に、ログの切り捨てを実行できます。 「[ALTER INDEX](../t-sql/statements/alter-index-transact-sql.md)」と「[オンライン インデックス操作のガイドライン](../relational-databases/indexes/guidelines-for-online-index-operations.md)」を参照してください。
- **ALTER DATABASE SCOPED CONFIGURATION の IDENTITY_CACHE オプション**。 `ALTER DATABASE SCOPED CONFIGURATION` T-SQL ステートメントに追加された新しい IDENTITY_CACHE オプションです。 このオプションを `OFF` に設定すると、サーバーが予期せず再起動したときやセカンダリ サーバーにフェールオーバーしたときに、データベースが ID 列の値のギャップを回避できます。 「[ALTER DATABASE SCOPED CONFIGURATION (ALTER データベース スコープ ベースの構成)](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)」を参照してください。   
-  [!INCLUDE[ssnoversion](../includes/ssnoversion-md.md)] には、より意味のあるリレーションシップ指向データをモデリングできるグラフ データベース機能が追加されました。 これには、ノードとエッジ テーブルを作成するための新しい [CREATE TABLE](../t-sql/statements/create-table-sql-graph.md) 構文と、クエリ用の [MATCH](../t-sql/queries/match-sql-graph.md) キーワードが含まれています。 詳細については、[SQL Server 2017 でのグラフ処理](../relational-databases/graphs/sql-graph-overview.md)に関するページをご覧ください。   
- 新世代のクエリ処理では、最適化戦略がアプリケーション ワークロードの実行時条件に適用される点が改善されています。 **アダプティブ クエリ処理**機能ファミリのこの最初のバージョンでは、3 つの新しい改善点があります。**バッチ モード適応型結合**、**バッチ モード メモリ許可フィードバック**、そして複数ステートメントのテーブル値関数の**インターリーブ実行**です。  「[SQL データベースでのインテリジェントなクエリ処理](../relational-databases/performance/intelligent-query-processing.md)」を参照してください。
- 自動チューニングは、潜在的なクエリ パフォーマンスの問題に関する洞察を提供し、解決策を推奨して、特定された問題を自動的に解決するデータベース機能です。 潜在的なパフォーマンスの問題が検出されると必ず、[!INCLUDE[ssnoversion](../includes/ssnoversion-md.md)] の自動チューニングにより通知されます。また、修正措置を適用したり、[!INCLUDE[ssde-md](../includes/ssde-md.md)]でパフォーマンスの問題を自動修復したりすることも可能です。 詳しくは、「[自動調整](../relational-databases/automatic-tuning/automatic-tuning.md)」をご覧ください。
- メモリ最適化テーブルでの非クラスター化インデックス ビルドのパフォーマンス向上。 データベース復旧中の MEMORY_OPTIMIZED テーブルにおける bwtree (非クラスター化) インデックス リビルドのパフォーマンスが大幅に最適化されました。 この機能強化により、非クラスター化インデックス使用時のデータベースの復旧時間が大幅に短縮されます。  
- [sys.dm_os_sys_info](../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md) には、socket_count、cores_per_socket、numa_node_count の 3 つの新しい列があります。 過度の NUMA はホストの過剰な介入につながり、最終的にパフォーマンスの問題に変わる可能性があるため、これは VM でサーバーを実行する場合に便利です。
- 新しい列 modified_extent_page_count\, は、データベースの各データベース ファイルの差分変更を追跡するために [sys.dm_db_file_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md) に導入されました。 新しい列 modified_extent_page_count を使用すると、スマート バックアップ ソリューションをビルドできます。このソリューションは、データベース内の変更されたページの割合がしきい値 (たとえば、70 ～ 80%) を下回る場合は差分バックアップを実行し、それ以外の場合はデータベースの完全バックアップを実行します。
- SELECT INTO ...ON FileGroup - [SELECT INTO](../t-sql/queries/select-into-clause-transact-sql.md) で、SELECT INTO TSQL 構文に追加された **ON** キーワードのサポートにより、ユーザーの既定のファイル グループ以外のファイル グループにテーブルを読み込むことができるようになりました。
- Tempdb セットアップの機能強化 - セットアップ時に、ファイルあたり **256 GB** (262,144 MB) までの初期 tempdb ファイル サイズを指定できるようになりました。ファイル サイズが 1 GB より大きい値に設定されている場合、IFI が有効になっていないと、警告が顧客に表示されます。 指定されたtempdb データ ファイルの初期サイズによっては、セットアップ時間が指数関数的に長くなる可能性がある状況で、ファイルの瞬時初期化 (IFI) を有効にしない場合の影響を理解しておくことが重要です。 IFI はトランザクション ログ サイズには適用されないため、トランザクション ログに大きな値を指定すると、SQL Server サービス アカウントの IFI 設定に関係なく、セットアップ時に tempdb を起動中、セットアップ時間が必ず長くなります。
- データベースごとのバージョン ストアの使用状況を追跡するために、dmv [sys.dm_tran_version_store_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-space-usage.md) が新たに導入されました。 この新しい dmv は、tempdb でバージョン ストアの使用状況を監視するときに便利で、tempdb サイズ変更を、運用サーバーでのパフォーマンスの低下やオーバーヘッドなしで、各データベースのバージョン ストア使用要件に基づいて事前に計画できます。
- DBCC LOGINFO と似た VLF 情報を公開し、VLF の数やサイズが原因で発生する可能性があるトランザクション ログの問題や、顧客の shrinkfile に関する問題を監視、警告、および回避するために、DMF [sys.dm_db_log_info](../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md) が新しく導入されました。
- ハイエンド サーバーにおける小規模データベースのバックアップ パフォーマンスが向上 - SQL Server でデータベースをバックアップをするとき、バックアップ プロセスでは、バッファー プールを複数回繰り返すことで、継続的 I/O をドレインする必要があります。 このため、バックアップ時間は、データベース サイズだけでなく、アクティブなバッファー プール サイズにも関連します。 SQL Server 2017 では、バックアップが最適化され、バッファー プールの繰り返しが回避されるため、小規模から中規模データベースのバックアップ パフォーマンスが大幅に向上します。 バックアップするページが増加してデータベースのサイズが大きくなり、バッファー プールを繰り返す場合と比べ、バックアップ IO の時間が長くなると、バッファー プールのパフォーマンスの向上の幅が小さくなります。  
- クエリ ストアが、待機統計概要情報を追跡するようになりました。 クエリ ストアの各クエリの待機統計情報カテゴリを追跡すると、パフォーマンス トラブルシューティング エクスペリエンスのレベルが上がり、クエリ ストアの主要メリットを維持しながら、ワークロードのパフォーマンスとそのボトルネックをさらに細かく把握できます。  
- システムのバージョン管理されたテンポラル テーブルが、CASCADE DELETE と CASCADE UPDATE をサポートするようになりました。  
- 間接チェックポイントのパフォーマンスが強化されました。
- クラスターレス可用性グループのサポートが追加されました。
- ミニマム レプリカ コミット可用性グループの設定が追加されました。
- Windows と Linux 間で可用性グループが利用できるようになり、OS 間での移行とテストができるようになりました。
- テンポラル表の保持ポリシーのサポートが追加されました。
- DMV SYS.DM_DB_STATS_HISTOGRAM が新しくなりました。
- 非クラスター化列ストア インデックスのオンライン ビルドおよびリビルドのサポートが追加されました。
- 統計情報を確認するための[sys.dm_db_stats_histogram (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) が追加されました。
- SQL Server Management Studio バージョン 16.4 とともにリリースされた データベース チューニング アドバイザー (DTA) には、SQL Server 2016 以降を分析する際の追加のオプションがあります。    
   - 向上したパフォーマンス。 詳細については、「[Performance Improvements using Database Engine Tuning Advisor (DTA) recommendations (データベース エンジン チューニング アドバイザー (DTA) の推奨事項を使用したパフォーマンスの強化)](../relational-databases/performance/performance-improvements-using-dta-recommendations.md)」を参照してください。
   - 列ストア インデックスの推奨事項を許可する `-fc` オプション。 詳細については、「[dta ユーティリティ](../tools/dta/dta-utility.md)」、および「[Columnstore index recommendations in Database Engine Tuning Advisor (DTA) (データベース エンジン チューニング アドバイザー (DTA) での列ストア インデックス推奨事項)](../relational-databases/performance/columnstore-index-recommendations-in-database-engine-tuning-advisor-dta.md)」を参照してください。  
   - DTA を許可してクエリ ストアのワークロードをレビューする `-iq` オプション。 詳細については、「 [Tuning Database Using Workload from Query Store (クエリ ストアのワークロードを使用してデータベースをチューニングする)](../relational-databases/performance/tuning-database-using-workload-from-query-store.md)」を参照してください。  
- インメモリ機能については、メモリ最適化テーブルおよびネイティブにコンパイルされた関数の追加の強化機能を利用できます。 こうした強化機能を示すコード サンプルについては、「[インメモリ OLTP を使用した JSON の処理の最適化](../relational-databases/json/optimize-json-processing-with-in-memory-oltp.md)」を参照してください。
    - 計算列のインデックスなど、メモリ最適化テーブルの計算列のサポート。
    - ネイティブ コンパイル モジュールと CHECK 制約の JSON 関数の完全サポート。  
    - ネイティブ コンパイル モジュールの`CROSS APPLY` 演算子。   
- 新しい文字列関数 [CONCAT_WS](../t-sql/functions/concat-ws-transact-sql.md)、[TRANSLATE](../t-sql/functions/translate-transact-sql.md)、および[TRIM](../t-sql/functions/trim-transact-sql.md) が追加されました。   
- [STRING_AGG](../t-sql/functions/string-agg-transact-sql.md) 関数で `WITHIN GROUP` 句がサポートされました。
- 2 つの新しい日本語の照合順序ファミリ (Japanese_Bushu_Kakusu_140 and Japanese_XJIS_140) が追加され、これらの新しい日本語の照合順序用に、照合順序オプション Variation-selector-sensitive (_VSS) が追加されました。 また、すべての新しい照合順序では、_SC オプションを指定する必要がなく、自動的に補助文字をサポートします。 詳細については、「 [照合順序と Unicode のサポート](../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。   
- 新しい一括アクセス オプション ([BULK INSERT](../t-sql/statements/bulk-insert-transact-sql.md) と [OPENROWSET(BULK...)](../t-sql/functions/openrowset-transact-sql.md)) を使用すると、[EXTERNAL DATA SOURCE](../t-sql/statements/create-external-data-source-transact-sql.md) の新しい `BLOB_STORAGE` オプションで、CSV 形式で指定したファイルまたは Azure BLOB 記憶域に格納されているファイルから直接データにアクセスできます。
- データベース **COMPATIBILITY_LEVEL** 140 が追加されました。   このレベルで実行しているお客様には、最新の言語機能とクエリ オプティマイザー動作が与えられます。 これには、Microsoft 製品の各リリース前バージョンの変更が含まれています。
- 増分統計更新の方法が改善され、しきい値が計算されます (140 互換モード必須)。
- [sys.dm_exec_query_statistics_xml](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md) が追加されます。
- メモリ最適化オブジェクトにパフォーマンスと言語の拡張機能を複数追加しました。
    - `sp_spaceused` が、メモリ最適化テーブルでサポートされるようになりました。
    - `sp_rename` が、メモリ最適化テーブルおよびネイティブ コンパイル T-SQL モジュールでサポートされるようになりました。
    - `CASE` 式が、ネイティブ コンパイル T-SQL モジュールでサポートされるようになりました。
    - メモリ最適化テーブルの 8 個のインデックス制限がなくなりました。
    - `TOP (N) WITH TIES` が、ネイティブ コンパイル T-SQL モジュールでサポートされるようになりました。
    - 通常は、メモリ最適化テーブルに対する `ALTER TABLE` が大幅に高速になります。
    - メモリ最適化テーブルのトランザクション ログの再実行が並列で行われるようになりました。 これにより復旧時間が短縮され、AlwaysOn 可用性グループ構成の持続スループットが大幅に向上します。
    - メモリ最適化ファイル グループのファイルを Azure Storage に保存できるようになりました。 Azure Storage でメモリ最適化ファイルをバックアップ/復元することもできます。
- クラスター化された列ストア インデックスが LOB 列 (nvarchar(max)、varchar(max)、varbinary(max)) 対応になりました。
- [STRING_AGG](../t-sql/functions/string-agg-transact-sql.md) 集計関数が追加されました。  
- 新しい権限: `DATABASE SCOPED CREDENTIAL` クラスがセキュリティ保護可能となり、 `CONTROL`、 `ALTER`、 `REFERENCES`、 `TAKE OWNERSHIP`、および `VIEW DEFINITION` の各権限がサポートされるようになりました。 SQL Database に限られていた `ADMINISTER DATABASE BULK OPERATIONS` が `sys.fn_builtin_permissions` で表示されるようになりました。   
- [sys.dm_os_host_info](../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md) DMV が追加され、Windows と Linux の両方のオペレーティング システム情報を提供します。   
- データベース ロールが R サービスで作成され、パッケージに関連付けられているアクセス許可を管理します。 詳細については、[SQL Server の R パッケージ管理](../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md)に関するページを参照してください。

