---
title: sys.index_resumable_operations (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 07/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.index_resumable_operations_TSQL
- sys.indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.indexes
- sys.index_resumable_operations
ms.assetid: ''
caps.latest.revision: 1
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2017 || = sqlallproducts-allversions
ms.openlocfilehash: 0d68f6e0946f9b5fb781448b2973939831b6cab9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="indexresumableoperations-transact-sql"></a>index_resumable_operations (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]
**sys.index_resumable_operations**を監視して、再開可能なインデックスの再構築の現在の実行ステータスを確認するシステム ビューです。  
**適用されます**: SQL Server 2017 と Azure SQL Database 
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|このインデックスが所属する (null を許容しません)、オブジェクトの ID です。|  
|**index_id**|**int**|Null を許容しない) のインデックスの ID。 **index_id**オブジェクト内でのみ一意です。|
|**name**|**sysname**|インデックスの名前です。 **名前**オブジェクト内でのみ一意です。|  
|**sql_text**|**nvarchar(max)**|DDL T-SQL ステートメントのテキスト|
|**last_max_dop**|**smallint**|最後の使用の MAX_DOP (既定値 = 0)|
|**partition_number**|**int**|所有しているインデックスまたはヒープ内のパーティション番号。 非パーティション テーブルとパーティション インデックスや場合、すべてのパーティションはこの列の値を再構築は NULL をしています。|
|**状態**|**tinyint**|再開可能なインデックスの動作状態:<br /><br />0 = 実行中<br /><br />1 = 一時停止|
|**state_desc**|**nvarchar(60)**|再開可能なインデックス (実行中または一時停止) の操作状態の説明|  
|**start_time**|**datetime**|インデックス操作の開始時刻が null を許容しない)|
|**last_pause_time**|**datatime**| インデックス操作 (null 許容の) の最後の一時停止にします。 操作が実行されているとしない一時停止した場合は NULL です。|
|**total_execution_time**|**int**|開始時間 (分) (null を許容しません) からの実行時間の合計|
|**percent_complete**|**real**|% (Null を許容しないインデックス操作の進行状況の完了します。|
|**page_count**|**bigint**|マッピング インデックス (null を許容しないと、新しいインデックス構築操作によって割り当てられているインデックス ページの合計数。 

## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
   
## <a name="example"></a>例  
 一時停止状態にあるすべての再開可能なインデックス再構築操作の一覧を表示します。 
  
```  
SELECT * FROM  sys.index_resumable_operations WHERE STATE = 1;  
```  
  
## <a name="see-also"></a>参照 
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)    
 [カタログ ビュー &#40;TRANSACT-SQL&#41; ](catalog-views-transact-sql.md) [カタログ ビューのオブジェクト&#40;TRANSACT-SQL&#41; ](object-catalog-views-transact-sql.md) [sys.indexes &#40;TRANSACT-SQL&#41; ](sys-xml-indexes-transact-sql.md) [sys.index_columns &#40;TRANSACT-SQL&#41;](sys-index-columns-transact-sql.md)   
 [sys.xml_indexes &#40;Transact-SQL&#41;](sys-xml-indexes-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](sys-index-columns-transact-sql.md)   
 [sys.key_constraints &#40;TRANSACT-SQL&#41;](sys-key-constraints-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](sys-filegroups-transact-sql.md)   
 [sys.partition_schemes &#40;Transact-SQL&#41;](sys-partition-schemes-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](querying-the-sql-server-system-catalog-faq.md)   
  
