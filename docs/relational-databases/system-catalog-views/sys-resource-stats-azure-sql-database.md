---
title: sys.resource_stats (Azure SQL データベース) |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/06/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- resource_stats
- sys.resource_stats
- sys.resource_stats_TSQL
- resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_stats
- resource_stats
ms.assetid: 02379a1b-3622-4578-8c59-a1b8f1a17914
caps.latest.revision: 28
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 7b8087839e5ea151d69a18cdf46d19fa5c917e66
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysresourcestats-azure-sql-database"></a>sys.resource_stats (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Azure SQL データベースの CPU 使用率とストレージのデータを返します。 データは、5 分間隔で収集と集計が実行されます。 ユーザー データベース別に、リソース消費量に変化があった 5 分間が報告され、1 つの行に表示されます。 返されるデータには、CPU 使用率、ストレージ サイズの変更、またはデータベース SKU の変更が含まれています。 変化のないアイドル状態のデータベースでは、5 分おきに行をことはできません。 履歴データは約 14 日間保持されます。  
  
 **Sys.resource_stats**ビューでは、データベースが関連付けられている Azure SQL データベース サーバーのバージョンによって異なる定義します。 新しいサーバー バージョンにアップグレードする際は、それら定義の違いとアプリケーションに必要な変更を考慮してください。  
  
 次の表は、v12 サーバーで使用できる列について説明しています。  
  
|列|データ型|Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|5 分間のレポート間隔の開始を示す UTC 時刻です。|  
|end_time|**datetime**|5 分間のレポート間隔の終了を示す UTC 時刻です。|  
|database_name|**varchar**|ユーザー データベースの名前。|  
|sku|**varchar**|データベースのサービス階層。 使用できる値を次に示します。<br /><br /> 基本<br /><br /> Standard<br /><br /> Premium<br /><br />一般的な用途<br /><br />ビジネス上重要|  
|storage_in_megabytes|**float**|データベースのデータ、インデックス、ストアド プロシージャ、およびメタデータを含む、期間のメガバイト単位でストレージの最大サイズ。|  
|avg_cpu_percent|**numeric**|サービス層の上限に対するパーセンテージで示した、平均コンピューティング使用率。|  
|avg_data_io_percent|**numeric**|サービス層の上限に基づくパーセンテージで示した、平均入出力使用率。|  
|avg_log_write_percent|**numeric**|サービス層の上限に対するパーセンテージで示した、平均書き込みリソース使用率。|  
|max_worker_percent|**decimal(5,2)**|データベースのサービス層の上限に基づくパーセンテージで最大同時実行ワーカー (要求)。<br /><br /> 現在、最大値は同時実行ワーカーの数の 15 秒サンプルに基づいた、5 分間隔の計算されます。|  
|max_session_percent|**decimal(5,2)**|データベースのサービス層の上限に基づくパーセンテージで最大同時セッション数。<br /><br /> 最大値は現在、同時セッション数の 15 秒のサンプルに基づいた、5 分間隔の計算されます。|  
|dtu_limit|**int**|現在データベースの最大 DTU このデータベースの設定この間隔中にします。 |  
  
> [!TIP]  
>  これらの制限とサービス層に関する詳細コンテキストは、トピックを参照して[サービス階層](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)です。  
    
## <a name="permissions"></a>権限  
 このビューは、仮想に接続する権限を持つすべてのユーザー ロールに利用可能な**マスター**データベース。  
  
## <a name="remarks"></a>解説  
 によって返されるデータ**sys.resource_stats**は許可されている制限を実行しているサービス階層/パフォーマンス レベルの最大のパーセンテージで表されます。  
  
 データベースが弾力性プールのメンバーである、パーセントの値として表されるリソースの統計情報は、弾力性プールの構成で設定されているデータベースの最大の制限の割合として表されます。  
  
 このデータのより詳細なビューを使用して**sys.dm_db_resource_stats**ユーザー データベースでの動的管理ビュー。 このビューは、15 秒ごとにデータをキャプチャし、1 時間の履歴データを保持します。  詳細については、次を参照してください。 [sys.dm_db_resource_stats &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md)です。  

## <a name="examples"></a>使用例  
 次の例では、過去 1 週間で平均してコンピューティング使用率が 80% 以上になっているすべてのデータベースが返されます。  
  
```sql  
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
    
## <a name="see-also"></a>参照  
 [サービス層](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [サービス層の機能および制限](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
