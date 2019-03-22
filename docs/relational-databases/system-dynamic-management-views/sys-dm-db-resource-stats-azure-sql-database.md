---
title: sys.dm_db_resource_stats (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/21/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_resource_stats
- sys.dm_db_resource_stats_TSQL
- dm_db_resource_stats
- dm_db_resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_resource_stats
- dm_db_resource_stats
ms.assetid: 6e76b39f-236e-4bbf-b0b5-38be190d81e8
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: f3b8defbb43cd07afe38915c6a0c14cb226fbf2c
ms.sourcegitcommit: 1c1ed8d6aa2fb9fceb6a00c39597578442f7f4e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2019
ms.locfileid: "58325505"
---
# <a name="sysdmdbresourcestats-azure-sql-database"></a>sys.dm_db_resource_stats (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  CPU、I/O、およびメモリの消費量を返す、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]データベース。 データベースのアクティビティがない場合でも、15 秒ごとに 1 つの行が存在します。 履歴データは 1 時間保持されます。  
  
|[列]|データ型|説明|  
|-------------|---------------|-----------------|  
|end_time|**datetime**|UTC 時刻では、現在のレポート間隔の終了を示します。|  
|avg_cpu_percent|**10 進数 (5,2)**|サービス層の制限の割合で表した平均コンピューティング使用率。|  
|avg_data_io_percent|**10 進数 (5,2)**|データ サービス層の制限の割合での I/O 使用率は平均です。|  
|avg_log_write_percent|**10 進数 (5,2)**|平均は、I/O スループットの使用率のサービス層の上限に対するパーセンテージとしてを記述します。|  
|avg_memory_usage_percent|**10 進数 (5,2)**|サービス層の制限の割合の平均メモリ使用率。<br /><br /> これには、バッファー プール ページと、インメモリ OLTP オブジェクトのストレージに使用されるメモリが含まれます。|  
|xtp_storage_percent|**10 進数 (5,2)**|記憶域使用率、インメモリ OLTP のサービス層の制限の割合で (レポートの期間の最後)。 これには、次のインメモリ OLTP オブジェクトの記憶域として使用されるメモリが含まれます。 メモリ最適化テーブル、インデックス、およびテーブル変数。 ALTER TABLE 操作を処理するために使用されるメモリも含まれています。<br /><br /> データベースでインメモリ OLTP を使用しない場合は、0 を返します。|  
|max_worker_percent|**10 進数 (5,2)**|データベースのサービス層の制限の割合で表した最大同時実行ワーカー (要求)。|  
|max_session_percent|**10 進数 (5,2)**|データベースのサービス層の制限の割合で表した最大同時セッション数。|  
|dtu_limit|**int**|現在データベースの最大 DTU このデータベースの設定この間隔中にします。 仮想コアベースのモデルを使用してデータベースでは、この列は NULL です。|
|cpu_limit|**10 進数 (5,2)**|この間隔中にこのデータベースの仮想コアの数。 データベースが DTU に基づくモデルを使用して、この列は NULL です。|
|||
  
> [!TIP]  
>  これらの制限とサービス レベルに関する詳細なコンテキスト、トピックを参照してください。[サービス階層](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)と[サービス層の機能と制限](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)します。  
  
## <a name="permissions"></a>アクセス許可  
 このビューには、VIEW DATABASE STATE 権限が必要です。  
  
## <a name="remarks"></a>コメント  
 によって返されるデータ**sys.dm_db_resource_stats**実行しているサービス階層/パフォーマンス レベルの制限が許容される最大の割合として表されます。
 
 データベースは、過去 60 分以内の別のサーバーにフェールオーバーしたが、ビューはそのフェールオーバー以降、プライマリ データベースがされた時間のデータを返すだけです。  
  
 このデータの詳細度の低いビューは、使用**sys.resource_stats**カタログ ビューで、**マスター**データベース。 このビューでは、5 分ごとにデータをキャプチャし、履歴データを 14 日間保持します。  詳細については、次を参照してください。 [sys.resource_stats &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)します。  
  
 データベースがエラスティック プールのメンバーである場合は、割合の値として表示されるリソース統計は、エラスティック プールの構成で設定されているデータベースの最大制限の割合として表されます。  
  
## <a name="example"></a>例  
  
次の例では、現在接続されているデータベースの最新の時間によって並べ替えられてリソース使用率データを返します。  
  
```  
SELECT * FROM sys.dm_db_resource_stats ORDER BY end_time DESC;  
  
```  
  
 次の例では、過去 1 時間のユーザー データベースのパフォーマンス レベルで許可される最大の DTU の上限の割合の観点から、平均 DTU 消費を識別します。 一貫性のあるごとに 100% 近くには、この割合として、パフォーマンス レベルを増やすことを検討します。  
  
```  
SELECT end_time,   
  (SELECT Max(v)    
   FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS    
   value(v)) AS [avg_DTU_percent]   
FROM sys.dm_db_resource_stats;  
  
```  
  
 次の例では、過去 1 時間のメモリ消費量と CPU の割合、データおよびログ、I/O の平均と最大値を返します。  
  
```  
SELECT    
    AVG(avg_cpu_percent) AS 'Average CPU Utilization In Percent',   
    MAX(avg_cpu_percent) AS 'Maximum CPU Utilization In Percent',   
    AVG(avg_data_io_percent) AS 'Average Data IO In Percent',   
    MAX(avg_data_io_percent) AS 'Maximum Data IO In Percent',   
    AVG(avg_log_write_percent) AS 'Average Log Write I/O Throughput Utilization In Percent',   
    MAX(avg_log_write_percent) AS 'Maximum Log Write I/O Throughput Utilization In Percent',   
    AVG(avg_memory_usage_percent) AS 'Average Memory Usage In Percent',   
    MAX(avg_memory_usage_percent) AS 'Maximum Memory Usage In Percent'   
FROM sys.dm_db_resource_stats;  
  
```  
  
## <a name="see-also"></a>参照  
 [sys.resource_stats &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [サービス レベル](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [サービス層の機能と制限](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
