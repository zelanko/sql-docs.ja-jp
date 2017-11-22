---
title: "sys.resource_stats (Azure SQL データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/23/2016
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- resource_stats
- sys.resource_stats
- sys.resource_stats_TSQL
- resource_stats_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.resource_stats
- resource_stats
ms.assetid: 02379a1b-3622-4578-8c59-a1b8f1a17914
caps.latest.revision: "28"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dad039b91c30e4c8d89168dd90d549ec6507c750
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysresourcestats-azure-sql-database"></a>sys.resource_stats (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Azure SQL データベースの CPU 使用率とストレージのデータを返します。 データは、5 分間隔で収集と集計が実行されます。 ユーザー データベース別に、リソース消費量に変化があった 5 分間が報告され、1 つの行に表示されます。 これには CPU 使用率、ストレージ サイズの変化、データベース SKU の変更が含まれます。 変化のないアイドル状態のデータベースについては、5 分間隔で行が表示されるとは限りません。 履歴データは約 14 日間保持されます。  
  
 **Sys.resource_stats**ビューでは、データベースが関連付けられている Azure SQL データベース サーバーのバージョンによって異なる定義します。 新しいサーバー バージョンにアップグレードする際は、それら定義の違いとアプリケーションに必要な変更を考慮してください。  
  
 次の表は、v12 サーバーで使用できる列について説明しています。  
  
|列 (v12 サーバー)|データ型|Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|5 分間隔の報告の開始時刻を示す UTC 時刻。|  
|end_time|**datetime**|5 分間隔の報告の終了時刻を示す UTC 時刻。|  
|database_name|**varchar**|ユーザー データベースの名前。|  
|sku|**varchar**|データベースのサービス階層。 使用できる値を次に示します。<br /><br /> 基本<br /><br /> Standard<br /><br /> Premium|  
|storage_in_megabytes|**float**|一定期間の最大ストレージ サイズ (MB 単位)。これにはデータベースのデータ、インデックス、ストアド プロシージャ、およびメタデータが含まれます。|  
|avg_cpu_percent|**numeric**|サービス層の上限に対するパーセンテージで示した、平均コンピューティング使用率。|  
|avg_data_io_percent|**numeric**|サービス層の上限に基づくパーセンテージで示した、平均入出力使用率。|  
|avg_log_write_percent|**numeric**|サービス層の上限に対するパーセンテージで示した、平均書き込みリソース使用率。|  
|max_worker_percent|**decimal(5,2)**|データベースのサービス層の上限に基づくパーセンテージで最大同時実行ワーカー (要求)。<br /><br /> 最大値は、現在、同時実行ワーカーの数の 15 の 2 つ目のサンプルに基づいた、5 分間隔の計算されます。|  
|max_session_percent|**decimal(5,2)**|データベースのサービス層の上限に基づくパーセンテージで最大同時セッション数。<br /><br /> 現在、最大値は、同時セッション数の 15 の 2 つ目のサンプルに基づいた、5 分間隔の計算されます。|  
|dtu_limit|**int**|現在データベースの最大 DTU このデータベースの設定この間隔中にします。|  
  
> [!TIP]  
>  これらの制限とサービス層に関する詳細コンテキストは、トピックを参照して[サービス階層](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)と[サービス層の機能と制限](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)です。  
  
 次の表は、v11 サーバーで使用できる列について説明しています。  
  
|列 (v11 サーバー)|データ型|Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|5 分間隔の報告の開始時刻を示す UTC 時刻。|  
|end_time|**datetime**|5 分間隔の報告の終了時刻を示す UTC 時刻。|  
|database_name|**nvarchar**|データベースの名前です。|  
|sku|**nvarchar**|データベースのサービス階層。 使用できる値を次に示します。<br /><br /> Web<br /><br /> ビジネス<br /><br /> 基本<br /><br /> Standard<br /><br /> Premium|  
|usage_in_seconds|**int**|*注: この列は v11 推奨されていませんし、その値は常に 0 に設定します。*<br /><br /> 最後に測定が行われてから使用された CPU 時間。<br /><br /> CPU の測定をお勧めを使用すること、 **avg_cpu_cores_used**この列ではなく列です。|  
|storage_in_megabytes|**decimal**|一定期間の最大ストレージ サイズ (MB 単位)。これにはデータベースのデータ、インデックス、ストアド プロシージャ、およびメタデータが含まれます。|  
|avg_cpu_cores_used|**decimal**|*注: この列は v11 推奨されていませんし、その値は常に 0 に設定します。*<br /><br /> この間隔で使用された CPU コアの平均数。|  
|avg_physical_read_iops|**decimal**|*注: この列は v11 推奨されていませんし、その値は常に 0 に設定します。*<br /><br /> この間隔の読み取り IOP の平均数。|  
|avg_physical_write_iops|**decimal**|*注: この列は v11 推奨されていませんし、その値は常に 0 に設定します。*<br /><br /> この間隔の書き込み IOP の平均数。|  
|active_memory_used_kb|**bigint**|*注: この列は v11 推奨されていませんし、その値は常に 0 に設定します。*<br /><br /> この間隔の終了に使用されているアクティブなメモリの数。|  
|active_session_count|**int**|この間隔の終了時点でアクティブなセッションの数。|  
|active_worker_count|**int**|この間隔の終了時点でアクティブなワーカーの数。|  
|avg_cpu_percent|**decimal**|サービス層の上限に対するパーセンテージで示した、平均コンピューティング使用率。|  
|avg_physical_data_read_percent|**decimal**|サービス層の上限に基づくパーセンテージで示した、平均入出力使用率。|  
|avg_log_write_percent|**decimal**|サービス層の上限に対するパーセンテージで示した、平均書き込みリソース使用率。|  
  
## <a name="permissions"></a>Permissions  
 このビューは、仮想に接続する権限を持つすべてのユーザー ロールに利用可能な**マスター**データベース。  
  
## <a name="remarks"></a>解説  
 によって返されるデータ**sys.resource_stats**は Basic、Standard、および Premium データベースを実行しているサービス階層/パフォーマンス レベルの DTU の制限を許可される最大のパーセンテージで表されます。  Web およびビジネス層では、これらの数字は Standard S2 パフォーマンス層に関するパーセンテージを示しています。  たとえば、Web データベースに対して実行する際に、avg_cpu_percent が 70% を返す場合、S2 層の限度の 70% を示しています。 さらに、Web およびビジネス層では、パーセンテージが 100% を超えた数値を反映している場合があります。これも、S2 層の限度に基づいています。  
  
 データベースが、柔軟なプールのメンバーである場合は、割合の値として表されるリソースの統計情報は、柔軟なプールの構成で設定されているデータベースの最大の DTU 制限の割合として表されます。  
  
 このデータのより詳細なビューを使用して**sys.dm_db_resource_stats**ユーザー データベースでの動的管理ビュー。 このビューはデータを 15 秒ごとにキャプチャし、履歴データを 1 時間保持します。  詳細については、次を参照してください。 [sys.dm_db_resource_stats &#40;です。Azure SQL データベース &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md).  

## <a name="examples"></a>使用例  
 次の例では、過去 1 週間で平均してコンピューティング使用率が 80% 以上になっているすべてのデータベースが返されます。  
  
```  
DECLARE @s datetime;  
DECLARE @e datetime;  
SET @s= DateAdd(d,-7,GetUTCDate());  
SET @e= GETUTCDATE();  
SELECT database_name, AVG(avg_cpu_percent) AS Average_Compute_Utilization   
FROM sys.resource_stats   
WHERE start_time BETWEEN @s AND @e  
GROUP BY database_name  
HAVING AVG(avg_cpu_percent) >= 80  
```  
  
 以下の例では、あるデータベースでの平均 DTU パーセンテージ消費量を計算します。 (このクエリは、v11 サーバーに対して実行する場合のみ機能します。)  
  
```  
SELECT start_time, end_time,      
  (SELECT Max(v)      
   FROM (VALUES (avg_cpu_percent), (avg_physical_data_read_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]    
FROM sys.resource_stats   
WHERE database_name = '<your db name>'   
ORDER BY end_time DESC;  
  
```  
  
## <a name="see-also"></a>参照  
 [サービス層](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [サービス層の機能および制限](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
