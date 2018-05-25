---
title: sys.dm_fts_active_catalogs (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_active_catalogs_TSQL
- dm_fts_active_catalogs
- dm_fts_active_catalogs_TSQL
- sys.dm_fts_active_catalogs
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_active_catalogs dynamic management view
ms.assetid: 40ab5453-040c-4d2e-bb49-e340cf90c3ee
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 564f66e6207ebc79b7545a77af8da8f156faf673
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmftsactivecatalogs-transact-sql"></a>sys.dm_fts_active_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  サーバーで作成操作が進行中のフルテキスト カタログに関する情報を返します。  
  
> [!NOTE]  
>  次の列は、の将来のバージョンで削除される予定[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: is_paused、previous_status、previous_status_description、row_count_in_thousands、状態、status_description、および worker_count します。 新しい開発作業では、これらの列の使用は避け、現在これらの列のいずれかを使用しているアプリケーションは修正するようにしてください。  
  
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|アクティブなフルテキスト カタログを含むデータベースの ID。|  
|**catalog_id**|**int**|アクティブなフルテキスト カタログの ID。|  
|**memory_address**|**varbinary(8)**|フルテキスト カタログに関係する作成操作に割り当てられているメモリ バッファーのアドレス。|  
|**name**|**nvarchar(128)**|アクティブなフルテキスト カタログの名前。|  
|**is_paused**|**bit**|アクティブなフルテキスト カタログの作成が一時停止されているかどうかを示します。|  
|**ステータス**|**int**|フルテキスト カタログの現在の状態。 次のいずれかです。<br /><br /> 0 = 初期化中<br /><br /> 1 = 準備完了<br /><br /> 2 = 一時停止<br /><br /> 3 = 一時エラー<br /><br /> 4 = 再マウントが必要<br /><br /> 5 = シャットダウン<br /><br /> 6 = バックアップのための休止<br /><br /> 7 = カタログからのバックアップ完了<br /><br /> 8 = カタログ破損|  
|**status_description**|**nvarchar(120)**|アクティブなフルテキスト カタログの現在の状態に関する説明。|  
|**previous_status**|**int**|フルテキスト カタログの以前の状態。 次のいずれかです。<br /><br /> 0 = 初期化中<br /><br /> 1 = 準備完了<br /><br /> 2 = 一時停止<br /><br /> 3 = 一時エラー<br /><br /> 4 = 再マウントが必要<br /><br /> 5 = シャットダウン<br /><br /> 6 = バックアップのための休止<br /><br /> 7 = カタログからのバックアップ完了<br /><br /> 8 = カタログ破損|  
|**previous_status_description**|**nvarchar(120)**|アクティブなフルテキスト カタログの以前の状態に関する説明。|  
|**worker_count**|**int**|フルテキスト カタログで現在実行されているスレッドの数。|  
|**active_fts_index_count**|**int**|作成されるフルテキスト インデックスの数。|  
|**auto_population_count**|**int**|フルテキスト カタログに対して自動作成が進行中のテーブルの数。|  
|**manual_population_count**|**int**|フルテキスト カタログに対して手動の作成が進行中のテーブルの数。|  
|**full_incremental_population_count**|**int**|フルテキスト カタログに対して完全作成または増分作成が進行中のテーブルの数。|  
|**row_count_in_thousands**|**int**|フルテキスト カタログ内にあるすべてのフルテキスト インデックス行の概数 (1,000 行単位)。|  
|**is_importing**|**bit**|フルテキスト カタログがインポートされているかどうかを示します。<br /><br /> 1 = カタログがインポートされています。<br /><br /> 2 = カタログがインポートされていません。|  
  
## <a name="remarks"></a>解説  
 Is_importing 列はで新しく[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]です。  
  
## <a name="permissions"></a>権限  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   
   
## <a name="physical-joins"></a>物理結合  
 ![この動的管理ビューの重要な結合](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-active-catalogs-1.gif "この動的管理ビューの重要な結合")  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|dm_fts_active_catalogs.database_id|dm_fts_index_population.database_id|一対一|  
|dm_fts_active_catalogs.catalog_id|dm_fts_index_population.catalog_id|一対一|  
  
## <a name="examples"></a>使用例  
 次の例では、現在のデータベースのアクティブなフルテキスト カタログに関する情報を返します。  
  
```  
SELECT catalog.name, catalog.is_importing, catalog.auto_population_count,  
  OBJECT_NAME(population.table_id) AS table_name,  
  population.population_type_description, population.is_clustered_index_scan,  
  population.status_description, population.completion_type_description,  
  population.queued_population_type_description, population.start_time,  
  population.range_count   
FROM sys.dm_fts_active_catalogs catalog   
CROSS JOIN sys.dm_fts_index_population population   
WHERE catalog.database_id = population.database_id   
AND catalog.catalog_id = population.catalog_id   
AND catalog.database_id = (SELECT dbid FROM sys.sysdatabases WHERE name = DB_NAME());  
GO  
```  
  
## <a name="see-also"></a>参照  
 
 [フルテキスト検索とセマンティック検索の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  
