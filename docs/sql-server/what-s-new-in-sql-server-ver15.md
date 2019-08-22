---
title: SQL Server 2019 の新機能 | Microsoft Docs
ms.date: 07/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2ded17c5baf35949b16c173236f94f8d0d3dd299
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028910"
---
# <a name="whats-new-in-includesql-server-2019includessssqlv15-mdmd"></a>[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] の新機能

[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

以前のリリースを基にして構築された [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では、開発言語、データ型、オンプレミスまたはクラウド、オペレーティング システムを選択できるプラットフォームとしての SQL Server がいっそう成長しています。

この記事では、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] の新機能と拡張機能について要約します。

詳細および既知の問題については、「[[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] リリース ノート](sql-server-ver15-release-notes.md)」 をご覧ください。

**[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] で最良のエクスペリエンスを得るには、[最新のツール](what-s-new-in-sql-server-ver15-prerelease.md#tools)を使用してください。**

## <a name="ctp-32-july-2019"></a>CTP 3.2、2019 年 7 月

Community Technology Preview (CTP) 3.2 は、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] の最新のパブリック リリースです。 このリリースには、以前の CTP リリースのバグを修正し、セキュリティを強化し、パフォーマンスを最適化する機能強化が含まれています。 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 3.2 より前の各 CTP リリースで導入または強化された機能の一覧については、「[[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP announcement archive](what-s-new-in-sql-server-ver15-prerelease.md)」 (CTP アナウンス アーカイブ) を参照してください。

### <a name="new-in-big-data-clusters"></a>ビッグ データ クラスターの新機能

|新機能または更新 | 詳細 |
|:---|:---|
|パブリック プレビュー |CTP 3.2 より前の SQL Server ビッグ データ クラスターは、登録した早期導入者に提供されていました。 このリリースでは、あらゆるユーザーが SQL Server ビッグ データ クラスターの機能を操作できるようにします。 <br/><br/> 「[SQL Server ビッグ データ クラスターの概要](../big-data-cluster/deploy-get-started.md)」を参照してください。|
|`azdata` |CTP 3.2 での `azdata` の導入 - Python で作成されたコマンドライン ユーティリティを使用して、クラスター管理者が REST API 経由でビッグ データ クラスターをブートストラップし、管理できるようにします。 `mssqlctl` が `azdata` に置き換えられます。 [`azdata` のインストール](../big-data-cluster/deploy-install-azdata.md)に関するページを参照してください。 |
|PolyBase |外部テーブルの列名は、SQL Server、Oracle、Teradata、MongoDB、ODBC データ ソースに対してクエリを実行するために使用されるようになりました。 以前の CTP リリースでは、列は変換先の序数に基づいてのみバインドされ、外部テーブルの定義の列名は使用されませんでした。|
|HDFS の階層の更新 |リモート データの最新のスナップショットに対して既存のマウントを更新できるように、HDFS の階層に対して更新機能を導入しました。 [HDFS の階層](../big-data-cluster/hdfs-tiering.md)に関するページを参照してください。 |
|Notebook ベースのトラブルシューティング |CTP 3.2 では、Jupyter Notebook が導入されており、SQL Server ビッグ データ クラスター内のコンポーネントの[配置](../big-data-cluster/deploy-notebooks.md)と[検出、診断、トラブルシューティング](../big-data-cluster/manage-notebooks.md)の支援が行われます。 |
| &nbsp; | &nbsp; |

### <a name="new-in-analysis-services"></a>Analysis Services の新機能

| 新機能または更新 | 詳細 |
|:---|:---| 
| Power BI キャッシュに対するガバナンス設定の更新  | Power BI サービスは、Live Connect レポートの初期読み込みのダッシュボード タイル データとレポート データをキャッシュします。これにより、大量のキャッシュ クエリが SSAS に送信され、極端な場合はサーバーが過負荷になります。 このリリースでは、**ClientCacheRefreshPolicy** プロパティが導入されています。 このプロパティによって、サーバー レベルでこの動作をオーバーライドすることが許可されます。 詳細については、「[全般プロパティ](https://docs.microsoft.com/analysis-services/server-properties/general-properties)」を参照してください。 |
| オンラインのアタッチ  | この機能を使用すると、表形式モデルをオンライン操作としてアタッチすることができます。 オンラインのアタッチは、オンプレミスのクエリ スケールアウト環境で読み取り専用レプリカを同期するために使用できます。 詳細については、[オンラインのアタッチ](what-s-new-in-sql-server-ver15-prerelease.md#online-attach-ctp32)に関するページを参照してください。 |
| &nbsp; | &nbsp; |

### <a name="new-in-language-extensions"></a>言語拡張の新機能

|新機能または更新 | 詳細 |
|:---|:---|
| 新しい既定の Java Runtime  | SQL Server には、製品全体で Java サポート用に埋め込まれた Azul System のズールー語が含まれるようになりました。 詳細については、「[Free supported Java in SQL Server 2019 is now available](https://cloudblogs.microsoft.com/sqlserver/2019/07/24/free-supported-java-in-sql-server-2019-is-now-available/)」 (SQL Server 2019 で無料でサポートされる Java が利用可能になりました) を参照してください。 |

### <a name="new-in-sql-server-on-linux"></a>SQL Server on Linux の新機能

|新機能または更新 | 詳細 |
|:---|:---|
| 変更データ キャプチャ (CDC) のサポート | SQL Server 2019 では、変更データ キャプチャ (CDC) が Linux でサポートされるようになりました。 |

## <a name="includesql-server-2019includessssqlv15-mdmd-features-by-component"></a>コンポーネント別の [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] の機能

次のセクションでは、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] の以前のリリースで拡張された新しいコンポーネントと機能について説明します。

## <a name="big-data-clusters"></a>ビッグ データ クラスター

| 新機能または更新 | 詳細 |
|:---|:---|
| スケーラブルなビッグ データ ソリューション | Kubernetes で実行している SQL Server、Spark、HDFS コンテナーの[スケーラブルなクラスターを配置する](../big-data-cluster/deploy-get-started.md) <br/><br/> Transact-SQL または Spark からビッグ データの読み取り、書き込み、処理を行う<br/><br/> 大量のビッグ データを使用して、価値の高いリレーショナル データを簡単に組み合わせて分析する<br/><br/>外部データ ソースを照会する<br/><br/>SQL Server によって管理される HDFS にビッグ データを格納する<br/><br/>クラスターを介して複数の外部データ ソースからデータを照会する<br/><br/> AI、機械学習、その他の分析タスクにデータを使用する<br/><br/> ビッグデータクラスターでのアプリケーションのデプロイと実行 <br/>|
| &nbsp; | &nbsp; |

詳細については、「[SQL Server ビッグ データ クラスターとは](../big-data-cluster/big-data-cluster-overview.md)」を参照してください。

[[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] (CTP) アナウンス アーカイブ](what-s-new-in-sql-server-ver15-prerelease.md)には、この機能の以前のすべての CTP リリースで発表および変更された機能の一覧が含まれています。

## <a name="database-engine"></a>データベース エンジン

### <a name="security"></a>セキュリティ

|新機能または更新 | 詳細 |
|:---|:---|
|暗号化された列のインデックス付け|ランダム化された暗号化およびエンクレーブ対応のキーを使用して暗号化された列のインデックスを作成し、リッチなクエリのパフォーマンスを向上させます (`LIKE` と比較演算子を使用)。 「[セキュリティで保護されたエンクレーブが設定された Always Encrypted](../relational-databases/security/encryption/always-encrypted-enclaves.md)」をご覧ください。
|Transparent Data Encryption (TDE) に対する初期スキャンの一時停止および再開|[Transparent Data Encryption (TDE) スキャンの一時停止と再開](../relational-databases/security/encryption/transparent-data-encryption.md#scan-suspend-resume)に関するページを参照してください。|
|SQL Server 構成マネージャーでの証明書管理|[証明書の管理 (SQL Server 構成マネージャー)](../database-engine/configure-windows/manage-certificates.md)に関するページを参照してください。
| &nbsp; | &nbsp; |


### <a name="graph"></a>グラフ

|新機能または更新 | 詳細 |
|:---|:---|
|エッジ制約のカスケード削除アクション |グラフ データベースでのエッジ制約で連鎖削除操作を定義します。 [エッジ制約](../relational-databases/tables/graph-edge-constraints.md)に関するページを参照してください。 |
|新しいグラフ関数 - `SHORTEST_PATH` | `MATCH` 内で `SHORTEST_PATH` を使用し、グラフ内の任意の 2 ノード間の最短パスを検索するか、任意の長さのトラバーサルを実行します。|
|パーティション テーブルとパーティション インデックス| パーティション テーブルとパーティション インデックスのデータは、グラフ データベース内の複数のファイル グループに分散できるように、複数の単位に分割されます。 |
|グラフ一致クエリで派生テーブルまたはビューの別名を使用する |[グラフ エッジ制約](../relational-databases/tables/graph-edge-constraints.md)に関するページを参照してください。 |
| &nbsp; | &nbsp; |

### <a name="indexes"></a>インデックス

|新機能または更新 | 詳細 |
|:---|:---|
|`OPTIMIZE_FOR_SEQUENTIAL_KEY`|インデックスへの高コンカレンシーの挿入のスループット向上に役立つ、データベース エンジン内での最適化を有効にします。 このオプションは、最終ページ挿入の競合が起きやすいインデックスを対象としています。これは、一般に、ID 列、シーケンス、または日付/時刻列などの連続したキーを持つインデックスでよく見られます。 詳しくは、「[CREATE INDEX](../t-sql/statements/create-index-transact-sql.md#sequential-keys)」をご覧ください。|
|オンラインでのクラスター化列ストア インデックスのビルドとリビルド | [オンラインでのインデックス操作の実行](../relational-databases/indexes/perform-index-operations-online.md)に関するページを参照してください。 |
| &nbsp; | &nbsp; |

### <a name="in-memory-databases"></a>メモリ内のデータベース

|新機能または更新 | 詳細 |
|:---|:---|
|ハイブリッド バッファー プールの DDL コントロール |[ハイブリッド バッファー プール](../database-engine/configure-windows/hybrid-buffer-pool.md)を使用すると、永続的なメモリ (PMEM) デバイス上に置かれたデータベース ファイル上のデータベース ページが必要に応じて直接アクセスされます。|
|メモリ最適化 tempdb メタデータ|「[メモリ最適化 tempdb メタデータ](../relational-databases/databases/tempdb-database.md#memory-optimized-tempdb-metadata)」を参照してください。|
| &nbsp; | &nbsp; |

### <a name="linked-servers"></a>リンク サーバー

|新機能または更新 | 詳細 |
|:---|:---|
|リンク サーバーでは UTF-8 文字エンコードがサポートされます。 |[照合順序と Unicode のサポート](../relational-databases/collations/collation-and-unicode-support.md) |
| &nbsp; | &nbsp; |

### <a name="polybase"></a>PolyBase

|新機能または更新 | 詳細 |
|:---|:---|
|PolyBase |外部テーブルの列名は、SQL Server、Oracle、Teradata、MongoDB および ODBC データ ソースのクエリに使用されるようになりました。 |
| &nbsp; | &nbsp; |

### <a name="collation"></a>照合順序

|新機能または更新 | 詳細 |
|:---|:---|
|UTF-8 文字エンコードのサポート |BIN2 照合順序 (`Latin1_General_100_BIN2_UTF8`) に対して有効になりました。 [照合順序と Unicode のサポート](../relational-databases/collations/collation-and-unicode-support.md)に関するページを参照してください。 |
|設定中に既定値として UTF-8 照合順序を選択 | [照合順序と Unicode のサポート](../relational-databases/collations/collation-and-unicode-support.md#ctp23)に関するページを参照してください。 |
| &nbsp; | &nbsp; |

### <a name="server-settings"></a>サーバーの設定

|新機能または更新 | 詳細 |
|:---|:---|
|セットアップ時に `MIN` と `MAX` のサーバー メモリ値を設定する |セットアップの間に、サーバー メモリの値を設定できます。 **推奨される**オプションである[サーバー メモリのサーバー構成オプション](../database-engine/configure-windows/server-memory-server-configuration-options.md#setting-the-memory-options-manually)を選択した後、既定値、計算された推奨値、または独自の値の手動指定を使用します。|
|SQL Server セットアップで MAXDOP 設定を有効にする |新しい推奨事項は、ドキュメントに記載されている [max degree of parallelism サーバーの構成オプションの構成](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines)に関するガイドラインに従います。|
|ハイブリッド バッファー プール| 永続的なメモリ (PMEM) デバイス上に置かれたデータベース ファイル上のデータベース ページが必要に応じて直接アクセスされるという、SQL Server データベース エンジンの新しい機能です。 [ハイブリッド バッファー プール](../database-engine/configure-windows/hybrid-buffer-pool.md)に関するページを参照してください。|
| &nbsp; | &nbsp; |

### <a name="performance-monitoring"></a>パフォーマンスの監視

|新機能または更新 | 詳細 |
|:---|:---|
|スカラー UDF のインライン化 |スカラー ユーザー定義関数 (UDF) が関係式に自動的に変換され、それらが呼び出し元の SQL クエリに埋め込まれます。 [スカラー UDF のインライン化](../relational-databases/user-defined-functions/scalar-udf-inlining.md)に関するページを参照してください。 |
| `command` 列の `sys.dm_exec_requests` | クエリの実行を続行する前に `SELECT` が、統計更新の同期操作の完了を待機している場合は、`SELECT (STATMAN)` が表示されます。 [`sys.dm_exec_requests`](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)に関するページを参照してください。|
|`WAIT_ON_SYNC_STATISTICS_REFRESH` | `sys.dm_os_wait_stats` 動的管理ビューの新しい待機の種類。 これには、統計更新の同期操作に費やされたインスタンス レベルの累積時間が表示されます。 [`sys.dm_os_wait_stats`](../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)に関するページを参照してください。|
|クエリ ストア用のカスタム キャプチャ ポリシー|有効にすると、新しいクエリ ストアのキャプチャ ポリシーの設定で、特定のサーバーでのデータ収集を微調整するための追加のクエリ ストアを使用できるようになります。 詳しくは、「[ALTER DATABASE SET オプション](../t-sql/statements/alter-database-transact-sql-set-options.md)」をご覧ください。|
|`sys.dm_exec_query_plan_stats` |新しい DMF では、ほとんどのクエリについて最後の既知の実際の実行プランと同等のものが返されます。 [sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md) に関するページを参照してください。|
|`LAST_QUERY_PLAN_STATS` | `sys.dm_exec_query_plan_stats` を有効にする新しいデータベース スコープの構成。 「[ALTER DATABASE SCOPED CONFIGURATION (ALTER データベース スコープ ベースの構成)](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)」を参照してください。|
|`LIGHTWEIGHT_QUERY_PROFILING`|新しいデータベース スコープの構成。 「[`LIGHTWEIGHT_QUERY_PROFILING`](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#lqp)」を参照してください。 |
|`query_post_execution_plan_profile` | 拡張イベントでは、標準プロファイリングを使用する `query_post_execution_showplan` とは異なり、軽量プロファイリングに基づいて、実際の実行プランと同等のものを収集します。 [クエリ プロファイリング インフラストラクチャ](../relational-databases/performance/query-profiling-infrastructure.md)に関するページを参照してください。|
|行モード メモリ許可フィードバック |[行モード メモリ許可フィードバック](../relational-databases/performance/intelligent-query-processing.md#row-mode-memory-grant-feedback) |
|テーブル変数の遅延コンパイル|[テーブル変数の遅延コンパイル](../relational-databases/performance/intelligent-query-processing.md#table-variable-deferred-compilation) |
|概算 `COUNT DISTINCT`|[概数クエリ処理](../relational-databases/performance/intelligent-query-processing.md#approximate-query-processing)|
|行ストアでのバッチ モード|[行ストアでのバッチ モード](../relational-databases/performance/intelligent-query-processing.md#batch-mode-on-rowstore) |

### <a name="language-extensions"></a>言語拡張機能

|新機能または更新 | 詳細 |
|:---|:---|
|新しい Java 言語 SDK | SQL Server から実行できる Java プログラムの開発を簡略化します。 「[What's new in SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md)」 (SQL Server Machine Learning Services の新機能) を参照してください。 |
|SQL Server 言語拡張機能 - [Java 言語拡張機能](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview)|[Microsoft SQL Server 用の Microsoft Extensibility SDK for Java](https://docs.microsoft.com/sql/language-extensions/how-to/extensibility-sdk-java-sql-server) がオープン ソース化され、[GitHub で入手可能](https://github.com/microsoft/sql-server-language-extensions)になりました。|
|外部言語を登録する|新しい DDL `CREATE EXTERNAL LANGUAGE` では、Java などの外部の言語を SQL Server に登録します。 [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md) に関するページを参照してください。 |
|Java データ型のサポート|[Java のデータ型](../language-extensions/how-to/java-to-sql-data-types.md)に関するページを参照してください。|

### <a name="spatial"></a>空間インデックス

|新機能または更新 | 詳細 |
|:---|:---|
| 新しい Spatial Reference Identifier (SRID) |[Australian GDA2020](http://www.ga.gov.au/scientific-topics/positioning-navigation/geodesy/datums-projections/gda2020) により、全地球測位システム (GPS) に対しさらに緊密に配置された、より堅牢で正確な測量基準点が提供されます。 新しい SRID は次のとおりです。<br/><br/> - 7843 - 地理 2D<br/> - 7844 - 地理 3D <br/><br/>[sys.spatial_reference_systems](../relational-databases/system-catalog-views/sys-spatial-reference-systems-transact-sql.md) ビューには、新しい SRID の定義が含まれています。 |
| &nbsp; | &nbsp; |

### <a name="performance"></a>パフォーマンス

|新機能または更新 | 詳細 |
|:---|:---|
|高速データベース復旧 | データベースごとに高速データベース復旧を有効にする [高速データベース復旧](../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#adr)に関するページを参照してください。|
|高速順方向カーソルと静的カーソルを強制する | 高速順方向カーソルと静的カーソルのサポートを強制するクエリ ストア プラン [高速順方向カーソルと静的カーソルのサポートを強制するプラン](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md#ctp23)に関するページを参照してください。|
|ワークロードの再コンパイルの削減| 複数のスコープを超えて一時テーブルを使用して改善します。 [ワークロードの再コンパイルの削減](../relational-databases/tables/tables.md#ctp23)に関するページを参照してください。 |
|間接チェックポイントのスケーラビリティ |[間接チェックポイントのスケーラビリティの向上](../relational-databases/logs/database-checkpoints-sql-server.md#ctp23)に関するページを参照してください。|
| &nbsp; | &nbsp; |

### <a name="availability-groups"></a>可用性グループ

|新機能または更新 | 詳細 |
|:---|:---|
|最大 5 つの同期レプリカ|[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では 3 つであった同期レプリカの最大数が、[!INCLUDE[ssSQL17](../includes/sssql17-md.md)] では 5 つに増加します。 この 5 つのレプリカのグループを、グループ内で自動フェールオーバーするように構成できます。 1 つのプライマリ レプリカと、4 つの同期セカンダリ レプリカがあります。|
|セカンダリからプライマリ レプリカへの接続のリダイレクト| 接続文字列に指定されたターゲット サーバーに関係なく、クライアント アプリケーションの接続先をプライマリ レプリカにすることができます。 詳しくは、「[セカンダリからプライマリ レプリカへの読み取り/書き込み接続のリダイレクト (Always On 可用性グループ)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md)」をご覧ください。|
| &nbsp; | &nbsp; |

### <a name="error-messages"></a>エラー メッセージ

|新機能または更新 | 詳細 |
|:---|:---|
|詳細な切り捨ての警告 | 切り捨てエラー メッセージに、テーブル名および列名と切り捨てられた値が既定で含まれます。 [VERBOSE_TRUNCATION_WARNINGS](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#verbose-truncation)に関するページを参照してください。|
| &nbsp; | &nbsp; |

## <a name="sql-server-on-linux"></a>Linux 上の SQL Server

| 新機能または更新 | 詳細 |
|:-----|:-----|
|新しいコンテナー レジストリ|[Docker で SQL Server のコンテナーの使用を開始する](../linux/quickstart-install-connect-docker.md) |
|Kubernetes を使用する Docker コンテナー上の Always On 可用性グループ |[コンテナー用の Always On 可用性グループ](../linux/sql-server-ag-kubernetes.md) |
|レプリケーションのサポート |[Linux での SQL Server のレプリケーション](../linux/sql-server-linux-replication.md)
|Microsoft 分散トランザクション コーディネーター (MSDTC) のサポート |[Linux で MSDTC を構成する方法](../linux/sql-server-linux-configure-msdtc.md) |
|サード パーティの AD プロバイダーに対する OpenLDAP のサポート |[チュートリアル: SQL Server on Linux で Active Directory 認証を使用する](../linux/sql-server-linux-active-directory-authentication.md) |
|Linux 上の Machine Learning |[Linux に Machine Learning を構成する](../linux/sql-server-linux-setup-machine-learning.md) |
|tempdb の強化機能 | 既定では、Linux 上に SQL Server を新しくインストールすると、論理コアの数に基づいて複数の tempdb データ ファイルが作成されます(最大で 8 個のデータ ファイル)。 これは、マイナー バージョンまたはメジャー バージョンのインプレース アップグレードには適用されません。 各 tempdb ファイルは 8 MB で、64 MB まで自動拡張します。 この動作は、Windows への SQL Server の既定のインストールに似ています。 |
| Linux での PolyBase | 非 Hadoop コネクタ向けに Linux に [PolyBase をインストール](../relational-databases/polybase/polybase-linux-setup.md)します。<br/><br/>[PolyBase 型のマッピング](../relational-databases/polybase/polybase-type-mapping.md) |
| &nbsp; | &nbsp; |

## <a id="ml"></a> SQL Server Machine Learning Services

|新機能または更新 | 詳細 |
|:---|:---|
|パーティション ベースのモデリング|`sp_execute_external_script` に追加された新しいパラメーターを使用し、データのパーティションごとに外部スクリプトが処理されます。 この機能は、1 つの大きいモデルではなく、多数の小さいモデル (データのパーティションごとに 1 つのモデル) のトレーニングをサポートします。 [パーティション ベースのモデルの作成](../advanced-analytics/tutorials/r-tutorial-create-models-per-partition.md)に関するページを参照してください。|
|Windows Server フェールオーバー クラスター| Windows Server フェールオーバー クラスター上の Machine Learning Services に高可用性を構成します。|
| &nbsp; | &nbsp; |

## [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]

| 新機能または更新 | 詳細 |
|:---|:---|
|Azure SQL Database Managed Instance データベースのサポート。| マネージド インスタンス上で [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] をホストします。 [[!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] のインストールと構成](../master-data-services/master-data-services-installation-and-configuration.md#SetUpWeb)に関するページを参照してください。|
|新しい HTML コントロール| HTML コントロールでは、以前の Silverlight コンポーネントがすべて置き換えられます。 Silverlight の依存関係が削除されました。|
| &nbsp; | &nbsp; |

## <a name="analysis-services"></a>Analysis Services

| 新機能または更新 | 詳細 |
|:---|:---|
|表形式モデルでの計算グループ| [テーブル モデルでの計算グループ](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24) |
|計算グループを使用した表形式モデルに対する MDX クエリのサポート | [計算グループ](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24)に関するページを参照してください。 |
|計算グループを使用したメジャーの動的な書式設定 |この機能を使用すると、[計算グループ](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24)を使用してメジャーの書式設定文字列を条件付きで変更できます。 たとえば、通貨換算を使用すると、さまざまな外貨形式を使ってメジャーを表示することができます。|
|表形式モデルでの多対多リレーションシップ|[表形式モデルでの多対多リレーションシップ](what-s-new-in-sql-server-ver15-prerelease.md#many-to-many-ctp24)|
|リソース ガバナンス用のプロパティ設定|[リソース ガバナンス用のプロパティ設定](what-s-new-in-sql-server-ver15-prerelease.md#property-ctp24)|
| &nbsp; | &nbsp; |

[!INCLUDE[ctp-support-exclusion](../includes/ctp-support-exclusion.md)]

サポートから除外される特定の機能については、[リリース ノート](sql-server-ver15-release-notes.md)を参照してください。

また、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 3.2 では、次の機能が追加または強化されています。

## <a name="see-also"></a>参照

- [`SqlServer` PowerShell モジュール](https://www.powershellgallery.com/packages/Sqlserver)
- [SQL Server PowerShell ドキュメント](../powershell/sql-server-powershell.md)

## <a name="next-steps"></a>次の手順

- [[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] リリース ノート](sql-server-ver15-release-notes.md)

- [Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]:テクニカル ホワイト ペーパー](http://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />2018 年 9 月に公開されました。 Windows、Linux、Docker コンテナー向けの Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.0 に適用されます。

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
