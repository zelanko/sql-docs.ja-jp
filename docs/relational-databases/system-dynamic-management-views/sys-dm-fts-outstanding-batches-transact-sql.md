---
title: sys.dm_fts_outstanding_batches (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/29/2017
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
- dm_fts_outstanding_batches
- dm_fts_outstanding_batches_TSQL
- sys.dm_fts_outstanding_batches_TSQL
- sys.dm_fts_outstanding_batches
dev_langs:
- TSQL
helpviewer_keywords:
- troubleshooting [SQL Server], full-text search
- sys.dm_fts_outstanding_batches dynamic management view
ms.assetid: c4d697ed-c906-4c28-b137-036a25e13c84
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: fc924c085044b92deadca30b13f693b041fa39d7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmftsoutstandingbatches-transact-sql"></a>sys.dm_fts_outstanding_batches (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  各フルテキスト インデックス バッチに関する情報を返します。  
  
  |列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|データベースの ID。|  
|catalog_id|**int**|フルテキスト カタログの ID|  
|table_id|**int**|フルテキスト インデックスを含むテーブル ID の ID。|  
|batch_id|**int**|バッチ ID。|  
|memory_address|**varbinary(8)**|バッチ オブジェクトのメモリ アドレス。|  
|crawl_memory_address|**varbinary(8)**|クロール オブジェクトのメモリ アドレス (親オブジェクト)。|  
|memregion_memory_address|**varbinary(8)**|フィルター デーモン ホスト (fdhost.exe) の送信共有メモリのメモリ領域メモリ アドレス。|  
|hr_batch|**int**|バッチの最新のエラー コード。|  
|is_retry_batch|**bit**|再試行バッチかどうかを示します。<br /><br /> 0 = いいえ<br /><br /> 1 = はい|  
|retry_hints|**int**|バッチに必要な再試行の種類。<br /><br /> 0 = 再試行なし<br /><br /> 1 = マルチスレッドでの再試行<br /><br /> 2 = シングルスレッドでの再試行<br /><br /> 3 = シングルスレッドおよびマルチスレッドでの再試行<br /><br /> 5 = マルチスレッドでの最終再試行<br /><br /> 6 = シングルスレッドでの最終再試行<br /><br /> 7 = シングルスレッドおよびマルチスレッドでの最終再試行|  
|retry_hints_description|**nvarchar(120)**|必要な再試行の種類の説明。<br /><br /> NO RETRY<br /><br /> MULTI THREAD RETRY<br /><br /> SINGLE THREAD RETRY<br /><br /> SINGLE AND MULTI THREAD RETRY<br /><br /> MULTI THREAD FINAL RETRY<br /><br /> SINGLE THREAD FINAL RETRY<br /><br /> SINGLE AND MULTI THREAD FINAL RETRY|  
|doc_failed|**bigint**|バッチ内の失敗したドキュメントの数。|  
|batch_timestamp|**timestamp**|バッチの作成時に取得されたタイムスタンプ値。|  
  
## <a name="permissions"></a>権限  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   
  
## <a name="examples"></a>使用例  
 次の例では、サーバー インスタンス内の各テーブルで現在処理されているバッチの数を調べます。  
  
```  
SELECT database_id, table_id, COUNT(*) AS batch_count FROM sys.dm_fts_outstanding_batches GROUP BY database_id, table_id ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索とセマンティック検索の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)  
  
  
