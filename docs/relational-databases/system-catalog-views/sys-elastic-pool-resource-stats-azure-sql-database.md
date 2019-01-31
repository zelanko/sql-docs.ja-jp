---
title: sys.elastic_pool_resource_stats (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 01/28/2019
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: reference
f1_keywords:
- sys.elastic_pool_resource_stats catalog view
helpviewer_keywords:
- sys.elastic_pool_resource_stats_TSQL
- sys.elastic_pool_resource_stats
- elastic_pool_resource_stats_TSQL
- elastic_pool_resource_stats
ms.assetid: f242c1bd-3cc8-4c8b-8aaf-c79b6a8a0329
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: bc5059682e3b909fee2ce730e7496333b9d4d861
ms.sourcegitcommit: 97340deee7e17288b5eec2fa275b01128f28e1b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "55421119"
---
# <a name="syselasticpoolresourcestats-azure-sql-database"></a>sys.elastic_pool_resource_stats (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  SQL Database サーバー内のすべてのエラスティック プールのリソース使用状況の統計を返します。 エラスティック プールごとには、レポート ウィンドウ (1 分あたり 4 つの行) 15 秒ごとに 1 つの行があります。 プール内のすべてのデータベースで CPU、IO、ログ、ストレージの使用量、および同時実行の要求またはセッションの使用率が含まれます。 このデータは 14 日間保持されます。 
  
||  
|-|  
|**適用対象**:[!INCLUDE[ssSDS](../../includes/sssds-md.md)] V12 します。|  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**start_time**|**datetime2**|15 秒のレポート間隔の開始を示す UTC 時刻。|  
|**end_time**|**datetime2**|レポート間隔である 15 秒の終わりを示す UTC 時刻。|  
|**elastic_pool_name**|**nvarchar(128)**|柔軟なデータベースのプールの名前。|  
|**avg_cpu_percent**|**decimal(5,2)**|プールの制限の割合で表した平均コンピューティング使用率。|  
|**avg_data_io_percent**|**decimal(5,2)**|平均 I/O の使用率 (%) のプールの上限に基づきます。|  
|**avg_log_write_percent**|**decimal(5,2)**|平均書き込みリソース使用率、プールの制限の割合。|  
|**avg_storage_percent**|**decimal(5,2)**|プールの記憶域の制限の割合で記憶域使用率を平均します。|  
|**max_worker_percent**|**decimal(5,2)**|プールの上限に基づく割合の最大同時実行ワーカー (要求)。|  
|**max_session_percent**|**decimal(5,2)**|プールの上限に基づくパーセンテージで最大同時セッション数です。|  
|**elastic_pool_dtu_limit**|**int**|最大の柔軟なプール DTU の現在の設定この柔軟なプールこの時間内にします。|  
|**elastic_pool_storage_limit_mb**|**bigint**|現在の最大の柔軟なプール記憶域制限がこの時間内に、メガバイト単位で柔軟なこのプールの設定です。|
|**avg_allocated_storage_percent**|**decimal(5,2)**|エラスティック プール内のすべてのデータベースで割り当てられているデータ領域の割合。  これは、エラスティック プールの最大サイズのデータに割り当てられているデータ領域の比率です。  詳細について参照してください。[SQL DB でのファイル領域の管理](https://docs.microsoft.com/azure/sql-database/sql-database-file-space-management)|  
  
## <a name="remarks"></a>コメント

 このビューは、SQL Database サーバーの master データベースに存在します。 クエリに、master データベースに接続する必要がある必要があります**sys.elastic_pool_resource_stats**します。  
  
## <a name="permissions"></a>アクセス許可

 メンバーシップが必要です、 **dbmanager**ロール。  
  
## <a name="examples"></a>使用例

 次の例では、現在の SQL Database サーバー内のすべてのエラスティック データベース プールの最新の時間によって並べ替えられてリソース使用率データを返します。  
  
```sql
SELECT * FROM sys.elastic_pool_resource_stats
ORDER BY end_time DESC;  
```

 次の例では、指定のプールの平均の DTU 割合使用量を計算します。  

```sql
SELECT start_time, end_time,
  (SELECT Max(v)
FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]
FROM sys.elastic_pool_resource_stats
WHERE elastic_pool_name = '<your pool name>'
ORDER BY end_time DESC;  
```

## <a name="see-also"></a>参照

 [エラスティック データベースで爆発的な増加を緩和して](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)   
 [作成し、管理、SQL Database エラスティック データベース プール (プレビュー)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)   
 [sys.resource_stats &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [sys.dm_db_resource_stats &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md)  
  
  
