---
title: 動的管理ビュー (Dmv) - SQL Server Machine Learning を使用して R と Python スクリプトの実行を監視します。
description: 動的管理ビュー (Dmv) を使用すると、SQL Server Machine Learning Services での R と Python の外部スクリプト実行を監視できます。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 8d701d9e8595eee3a583e913baabc2148af214fe
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67681621"
---
# <a name="monitor-sql-server-machine-learning-services-using-dynamic-management-views-dmvs"></a>SQL Server Machine Learning Services の動的管理ビュー (Dmv) を使用した監視します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

動的管理ビュー (Dmv) 外部の実行を監視するスクリプトを使用すると、(R および Python) のリソースを使用して、問題を診断し、SQL Server Machine Learning Services でのパフォーマンスを調整します。

この記事では、SQL Server Machine Learning Services の固有の Dmv を紹介します。 表示するクエリの例も表示されます。

+ 設定と machine learning 用の構成オプション
+ 外部の R または Python スクリプトを実行しているアクティブなセッション
+ 外部 R と Python のランタイム実行統計
+ 外部スクリプトのパフォーマンス カウンター
+ OS、SQL Server、および外部リソース プールのメモリ使用量
+ SQL Server と外部リソース プールのメモリの構成
+ 外部リソース プールを含めて、リソース ガバナー リソース プール
+ R と Python のインストール済みパッケージ

Dmv の概要については、次を参照してください。[システム動的管理ビュー](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)します。

> [!TIP]
> SQL Server Machine Learning サービスを監視するのにカスタム レポートを使用することもできます。 詳細については、次を参照してください。 [Management Studio でカスタム レポートを使用して機械学習の監視](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md)します。

## <a name="dynamic-management-views"></a>動的管理ビュー

SQL server machine learning ワークロードを監視する場合、次の動的管理ビューを使用できます。 Dmv を照会する必要があります`VIEW SERVER STATE`インスタンスに対する権限。

| 動的管理ビュー | 型 | 説明 |
|-------------------------|------|-------------|
| [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) | 実行 | 外部スクリプトを実行しているアクティブなワーカー アカウントごとに行を返します。 |
| [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) | 実行 | 外部スクリプト要求の種類ごとに 1 つの行を返します。 |
| [sys.dm_os_performance_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md) | 実行 | サーバーで管理されているパフォーマンス カウンターごとに 1 行のデータを返します。 検索条件を使用する場合`WHERE object_name LIKE '%External Scripts%'`、この情報を使用するには、スクリプトの数は実行を確認する認証モード、または数の R を使用してスクリプトが実行されたか、インスタンス全体で Python の呼び出しが発行されました。 |
| [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) | [リソース ガバナー] | リソース ガバナーで、リソース プール、およびリソース プール統計の現在の構成、現在の外部リソース プールの状態に関する情報を返します。 |
| [sys.dm_resource_governor_external_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md) | [リソース ガバナー] | リソース ガバナーにおける外部リソース プールの現在の構成について、CPU アフィニティ情報を返します。 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] のスケジューラごとに 1 行のデータを返します。各スケジューラは個別のプロセッサにマップされています。 このビューは、スケジューラの状況の監視やランナウェイ タスクの特定に使用できます。 |

監視について[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]インスタンスを参照してください[カタログ ビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)と[リソース ガバナー関連の動的管理ビュー](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)します。

## <a name="settings-and-configuration"></a>設定と構成

Machine Learning サービスのインストールの設定と構成オプションを表示します。

![設定および構成のクエリからの出力](media/dmv-settings-and-configuration.png "設定および構成のクエリからの出力")

この出力を取得する次のクエリを実行します。 ビューおよび関数の使用の詳細については、次を参照してください。 [sys.dm_server_registry](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)、 [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)、および[SERVERPROPERTY](../../t-sql/functions/serverproperty-transact-sql.md)します。

```sql
SELECT CAST(SERVERPROPERTY('IsAdvancedAnalyticsInstalled') AS INT) AS IsMLServicesInstalled
    , CAST(value_in_use AS INT) AS ExternalScriptsEnabled
    , COALESCE(SIGN(SUSER_ID(CONCAT (
                    CAST(SERVERPROPERTY('MachineName') AS NVARCHAR(128))
                    , '\SQLRUserGroup'
                    , CAST(serverproperty('InstanceName') AS NVARCHAR(128))
                    ))), 0) AS ImpliedAuthenticationEnabled
    , COALESCE((
            SELECT CAST(r.value_data AS INT)
            FROM sys.dm_server_registry AS r
            WHERE r.registry_key LIKE 'HKLM\Software\Microsoft\Microsoft SQL Server\%\SuperSocketNetLib\Tcp'
            AND r.value_name = 'Enabled'
            ), - 1) AS IsTcpEnabled
FROM sys.configurations
WHERE name = 'external scripts enabled';
```

このクエリでは、次の列を返します。

| [列] | 説明 |
|--------|-------------|
| IsMLServicesInstalled | インスタンスの SQL Server Machine Learning サービスがインストールされている場合は、1 を返します。 それ以外の場合、0 を返します。 |
| ExternalScriptsEnabled | インスタンスの外部のスクリプトが有効になっている場合は、1 を返します。 それ以外の場合、0 を返します。 |
| ImpliedAuthenticationEnabled | 暗黙の認証の場合は 1 になっています。 それ以外の場合、0 を返します。 SQLRUserGroup のログインが存在するかどうかを確認し、暗黙の認証の構成がチェックされます。 |
| IsTcpEnabled | インスタンスの TCP/IP プロトコルが有効になっている場合は、1 を返します。 それ以外の場合、0 を返します。 詳細については、次を参照してください。 [SQL サーバー ネットワーク プロトコルの構成を既定の](../../database-engine/configure-windows/default-sql-server-network-protocol-configuration.md)します。 |

## <a name="active-sessions"></a>Active sessions

外部スクリプトを実行しているアクティブなセッションを表示します。

![アクティブな設定のクエリからの出力](media/dmv-active-sessions.png "アクティブな設定のクエリからの出力")

この出力を取得する次のクエリを実行します。 使用する動的管理ビューの詳細については、次を参照してください。 [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)、 [sys.dm_external_script_requests](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)、および[sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)します。

```sql
SELECT r.session_id, r.blocking_session_id, r.status, DB_NAME(s.database_id) AS database_name
    , s.login_name, r.wait_time, r.wait_type, r.last_wait_type, r.total_elapsed_time, r.cpu_time
    , r.reads, r.logical_reads, r.writes, er.language, er.degree_of_parallelism, er.external_user_name
FROM sys.dm_exec_requests AS r
INNER JOIN sys.dm_external_script_requests AS er
ON r.external_script_request_id = er.external_script_request_id
INNER JOIN sys.dm_exec_sessions AS s
ON s.session_id = r.session_id;
```

このクエリでは、次の列を返します。

| [列] | 説明 |
|--------|-------------|
| session_id | アクティブな各プライマリ接続に関連付けられたセッションの識別子。 |
| blocking_session_id | 要求をブロックしているセッションの ID。 この列が NULL の場合は、要求がブロックされていないか、ブロックしているセッションのセッション情報が使用または識別できません。 |
| status | 要求の状態です。 |
| database_name | 各セッションの現在のデータベースの名前。 |
| login_name | セッションが現在実行されている SQL Server ログインの名前。 |
| wait_time | 要求が現在ブロックされている場合の現時点での待機時間 (ミリ秒単位)。 NULL 値は許可されません。 |
| wait_type | 要求が現在ブロックされている場合の待機の種類。 待機の種類については、次を参照してください。 [sys.dm_os_wait_stats](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)します。 |
| last_wait_type | 要求がブロックされていた場合の最後の待機の種類。 |
| total_elapsed_time | 要求を受信してから経過した総時間 (ミリ秒単位)。 |
| cpu_time | 要求で使用される CPU 時間 (ミリ秒単位)。 |
| reads | 要求で実行された読み取りの数。 |
| logical_reads | 要求で実行された論理読み取りの数。 |
| writes | 要求で実行された書き込みの数。 |
| language | サポートされているスクリプト言語を表すキーワードです。 |
| degree_of_parallelism | 作成された並列処理の数を示す数値です。 この値は、要求された並列処理の数と異なる場合があります。 |
| external_user_name | スクリプトが実行されたときの Windows ワーカー アカウント。 |

## <a name="execution-statistics"></a>実行の統計

R と Python の外部のランタイム実行の統計を表示します。 RevoScaleR、revoscalepy、または microsoftml パッケージ関数の統計情報のみが現在使用できません。

![実行の統計情報のクエリからの出力](media/dmv-execution-statistics.png "実行の統計情報のクエリからの出力")

この出力を取得する次のクエリを実行します。 使用する動的管理ビューの詳細については、次を参照してください。 [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)します。 クエリは、複数回実行された関数のみを返します。

```sql
SELECT language, counter_name, counter_value
FROM sys.dm_external_script_execution_stats
WHERE counter_value > 0
ORDER BY language, counter_name;
```

このクエリでは、次の列を返します。

| [列] | 説明 |
|--------|-------------|
| language | 登録されている外部スクリプト言語の名前です。 |
| counter_name | 登録されている外部スクリプト関数の名前です。 |
| counter_value | 登録されている外部スクリプト関数がサーバーで呼び出されたインスタンスの合計数です。 この値は、機能がインスタンスにインストールされてからの累積値で、リセットすることはできません。 |

## <a name="performance-counters"></a>パフォーマンス カウンター

外部スクリプトの実行に関連するパフォーマンス カウンターを表示します。

![出力、パフォーマンスからカウンター クエリ](media/dmv-performance-counters.png "出力、パフォーマンスからカウンターのクエリ")

この出力を取得する次のクエリを実行します。 使用する動的管理ビューの詳細については、次を参照してください。 [sys.dm_os_performance_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)します。

```sql
SELECT counter_name, cntr_value
FROM sys.dm_os_performance_counters 
WHERE object_name LIKE '%External Scripts%'
```

**sys.dm_os_performance_counters**外部スクリプトの次のパフォーマンス カウンターを出力します。

| カウンター | 説明 |
|---------|-------------|
| Total Executions | ローカルまたはリモートの呼び出しによって開始された外部のプロセスの数。 |
| Parallel Executions | スクリプトが含まれている回数、 _@parallel_ 仕様と[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]生成し、並列クエリ プランを使用することができました。 |
| Streaming Executions | ストリーミングの機能が呼び出された回数。 |
| SQL CC Executions | 外部スクリプトの呼び出しがリモートでインスタンス化、および SQL Server の実行の数は、計算コンテキストとして使用されました。 |
| Implied Auth.Login | 暗黙の認証を使用して ODBC ループバック呼び出しが行われた回数つまり、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]スクリプト要求を送信するユーザーの代理呼び出しを実行します。 |
| Total Execution Time (ms) | 呼び出しと呼び出しの完了までの経過時間。 |
| Execution Errors | スクリプトにエラーが報告された回数。 この数には、R または Python のエラーは含まれません。 |

## <a name="memory-usage"></a>メモリ使用量

OS、SQL Server、および外部プールによって使用されるメモリについての情報を表示します。

![メモリの使用状況クエリからの出力](media/dmv-memory-usage.png "メモリの使用状況クエリからの出力")

この出力を取得する次のクエリを実行します。 使用する動的管理ビューの詳細については、次を参照してください。 [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md)と[sys.dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)します。

```sql
SELECT physical_memory_kb, committed_kb
    , (SELECT SUM(peak_memory_kb)
        FROM sys.dm_resource_governor_external_resource_pools AS ep
        ) AS external_pool_peak_memory_kb
FROM sys.dm_os_sys_info;
```

このクエリでは、次の列を返します。

| [列] | 説明 |
|--------|-------------|
| physical_memory_kb | コンピューターの物理メモリの総量。 |
| committed_kb | メモリ マネージャーでは、キロバイト (KB) でコミットされたメモリ。 メモリ マネージャー内の予約済みメモリは含まれません。 |
| external_pool_peak_memory_kb | 最大メモリ量の合計使用、キロバイト単位ですべての外部リソース プール。 |

## <a name="memory-configuration"></a>メモリ構成

SQL Server と外部リソース プールの割合の最大メモリ構成に関する情報を表示します。 既定値は、SQL Server が実行されているかどうかは`max server memory (MB)`、OS メモリの 100% としてと見なされます。

![メモリ構成のクエリからの出力](media/dmv-memory-configuration.png "メモリ構成のクエリからの出力")

この出力を取得する次のクエリを実行します。 ビューの使用の詳細については、次を参照してください。 [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)と[sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md)します。

```sql
SELECT 'SQL Server' AS name
    , CASE CAST(c.value AS BIGINT)
        WHEN 2147483647 THEN 100
        ELSE (SELECT CAST(c.value AS BIGINT) / (physical_memory_kb / 1024.0) * 100 FROM sys.dm_os_sys_info)
        END AS max_memory_percent
FROM sys.configurations AS c
WHERE c.name LIKE 'max server memory (MB)'
UNION ALL
SELECT CONCAT ('External Pool - ', ep.name) AS pool_name, ep.max_memory_percent
FROM sys.dm_resource_governor_external_resource_pools AS ep;
```

このクエリでは、次の列を返します。

| [列] | 説明 |
|--------|-------------|
| NAME | 外部リソース プールまたは SQL Server の名前。 |
| max_memory_percent | SQL Server または外部リソース プールが使用できる最大のメモリ。 |

## <a name="resource-pools"></a>[リソース プール]

[SQL Server リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)、[リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)インスタンスの物理リソースのサブセットを表します。 CPU、物理 IO、および外部のスクリプトの実行など、アプリケーションの受信要求がリソース プール内で使用できることをメモリの量に制限を指定できます。 SQL Server と外部のスクリプトを使用するリソース プールを表示します。

![クエリ プールのリソースからの出力](media/dmv-resource-pools.png "クエリ プールのリソースからの出力")

この出力を取得する次のクエリを実行します。 使用する動的管理ビューの詳細については、次を参照してください。 [sys.dm_resource_governor_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)と[sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md)します。

```sql
SELECT CONCAT ('SQL Server - ', p.name) AS pool_name
    , p.total_cpu_usage_ms, p.read_io_completed_total, p.write_io_completed_total
FROM sys.dm_resource_governor_resource_pools AS p
UNION ALL
SELECT CONCAT ('External Pool - ', ep.name) AS pool_name
    , ep.total_cpu_user_ms, ep.read_io_count, ep.write_io_count
FROM sys.dm_resource_governor_external_resource_pools AS ep;
```

このクエリでは、次の列を返します。

| [列] | 説明 |
|--------|-------------|
| pool_name | リソース プールの名前。 SQL Server リソース プールが付いて`SQL Server`外部リソース プールがというプレフィックスが付いた`External Pool`します。
| total_cpu_usage_hours | リソース ガバナー統計がリセットされた後のミリ秒単位で累積の CPU 使用率。 |
| read_io_completed_total | リソース ガバナー統計がリセットされた後に完了した読み取り IO の合計。 |
| write_io_completed_total | リソース ガバナー統計がリセットされた後に完了した書き込み IO の合計。 |

## <a name="installed-packages"></a>インストールされているパッケージ

これらを出力する R または Python スクリプトを実行することによって、SQL Server Machine Learning Services でインストールされている R と Python のパッケージを表示することができます。

### <a name="installed-packages-for-r"></a>R のパッケージをインストールします。

SQL Server Machine Learning Services でインストールされている R パッケージを表示します。

![クエリの R のインストールされているパッケージからの出力](media/dmv-installed-packages-r.png "R クエリにインストールされているパッケージからの出力")

この出力を取得する次のクエリを実行します。 クエリの使用状況を R パッケージを特定の R スクリプトは、SQL Server と共にインストールします。

```sql
EXEC sp_execute_external_script @language = N'R'
, @script = N'
OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
WITH result sets((Package NVARCHAR(255), Version NVARCHAR(100), Depends NVARCHAR(4000)
    , License NVARCHAR(1000), LibPath NVARCHAR(2000)));
```

返される列は次のとおりです。

| [列] | 説明 |
|--------|-------------|
| [パッケージ] | インストールされているパッケージの名前です。 |
| バージョン | パッケージのバージョンです。 |
| 依存 | インストールされているパッケージが依存するパッケージを一覧表示します。 |
| ライセンス | インストールされているパッケージのライセンス。 |
| LibPath | ディレクトリは、パッケージを見つけることができます。 |

### <a name="installed-packages-for-python"></a>Python 用のパッケージのインストール

SQL Server Machine Learning Services でインストールされた Python パッケージを表示します。

![クエリの Python のインストールされているパッケージからの出力](media/dmv-installed-packages-python.png "Python クエリにインストールされているパッケージからの出力")

この出力を取得する次のクエリを実行します。 クエリでは、Python スクリプトを使用を SQL Server と共にインストールされる Python パッケージを特定します。

```sql
EXEC sp_execute_external_script @language = N'Python'
, @script = N'
import pip
OutputDataSet = pandas.DataFrame([(i.key, i.version, i.location) for i in pip.get_installed_distributions()])'
WITH result sets((Package NVARCHAR(128), Version NVARCHAR(128), Location NVARCHAR(1000)));
```

返される列は次のとおりです。

| [列] | 説明 |
|--------|-------------|
| [パッケージ] | インストールされているパッケージの名前です。 |
| バージョン | パッケージのバージョンです。 |
| 場所 | ディレクトリは、パッケージを見つけることができます。 |

## <a name="next-steps"></a>次の手順

+ [Machine Learning ソリューションの管理と監視](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)
+ [Machine learning の拡張イベント](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md)
+ [リソース ガバナー関連の動的管理ビュー](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)
+ [システム動的管理ビュー](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
+ [Management Studio でカスタム レポートを使用して機械学習を監視します。](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md)