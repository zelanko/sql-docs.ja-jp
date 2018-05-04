---
title: sys.dm_db_xtp_index_stats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_xtp_index_stats
- dm_db_xtp_index_stats
- sys.dm_db_xtp_index_stats_TSQL
- dm_db_xtp_index_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_index_stats dynamic management view
ms.assetid: 8d0a50b8-2015-4576-930f-e3307dfc888e
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: ee4858c2ea314529398950623221735fc2d4e911
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmdbxtpindexstats-transact-sql"></a>sys.dm_db_xtp_index_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  前回データベースが再起動されてから収集された統計が含まれます。  
  
 詳細については、次を参照してください。 [、インメモリ OLTP&#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)と[を使用してメモリ最適化テーブルのインデックスのガイドライン](http://msdn.microsoft.com/library/16ef63a4-367a-46ac-917d-9eebc81ab29b)です。  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|object_id|**bigint**|インデックスが属しているオブジェクトの ID。|  
|xtp_object_id|**bigint**|オブジェクトの現在のバージョンに対応する内部の ID。<br /><br /> 注: 対象[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。|  
|index_id|**bigint**|インデックスの ID。 index_id は、オブジェクト内でのみ一意です。|  
|scans_started|**bigint**|実行されたインメモリ OLTP のインデックス スキャンの回数。 選択、挿入、更新、または削除を実行するたびに、インデックス スキャンが必要になります。|  
|scans_retries|**bigint**|再試行する必要のあるインデックス スキャンの回数。|  
|rows_returned|**bigint**|テーブルが作成された後に返される行またはの開始の累積数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|rows_touched|**bigint**|テーブルが作成された後にアクセスする行の累積数またはの開始[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|rows_expiring|**bigint**|内部使用のみです。|  
|rows_expired|**bigint**|内部使用のみです。|  
|rows_expired_removed|**bigint**|内部使用のみです。|  
|phantom_scans_started|**bigint**|内部使用のみです。|  
|phatom_scans_retries|**bigint**|内部使用のみです。|  
|phantom_rows_touched|**bigint**|内部使用のみです。|  
|phantom_expiring_rows_encountered|**bigint**|内部使用のみです。|  
|phantom_expired_rows_encountered|**bigint**|内部使用のみです。|  
|phantom_expired_removed_rows_encountered|**bigint**|内部使用のみです。|  
|phantom_expired_rows_removed|**bigint**|内部使用のみです。|  
|object_address|**varbinary(8)**|内部使用のみです。|  
  
## <a name="permissions"></a>権限  
 現在のデータベースに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [メモリ最適化テーブルの動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
