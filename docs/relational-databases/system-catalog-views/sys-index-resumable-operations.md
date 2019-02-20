---
title: sys.index_resumable_operations (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/14/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 780cffa17f6ee1af70d942545632c98c9d6dc1e7
ms.sourcegitcommit: ad3b2133585bc14fc6ef8be91f8b74ee2f498b64
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2019
ms.locfileid: "56425777"
---
# <a name="indexresumableoperations-transact-sql"></a>index_resumable_operations (TRANSACT-SQL)

[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]
**sys.index_resumable_operations**システム ビューを監視し、再開可能なインデックス再構築の現在の実行状態を確認します。  
**適用対象**:SQL Server 2017 と Azure SQL Database
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|このインデックスが属する (いない null 許容の) オブジェクトの ID。|  
|**index_id**|**int**|(非 null 許容) のインデックスの ID。 **index_id**オブジェクト内でのみ一意です。|
|**name**|**sysname**|インデックスの名前です。 **名前**オブジェクト内でのみ一意です。|  
|**sql_text**|**nvarchar(max)**|DDL の T-SQL ステートメントのテキスト|
|**last_max_dop**|**smallint**|最後の使用の MAX_DOP (既定 = 0)|
|**partition_number**|**int**|所有しているインデックスまたはヒープ内のパーティション番号。 非パーティション テーブルとパーティション インデックスの場合またはこの列の値を再構築が NULL のすべてのパーティションがされています。|
|**state**|**tinyint**|再開可能なインデックスの動作状態:<br /><br />0 = 実行中<br /><br />1 = 一時停止|
|**state_desc**|**nvarchar(60)**|再開可能なインデックス (実行中または一時停止) の操作状態の説明|  
|**start_time**|**datetime**|インデックス操作の開始時刻が (いない null 許容の)|
|**last_pause_time**|**datatime**| インデックス操作 (null 許容の) 最後の一時停止時間。 操作が実行されているとしない一時停止した場合は NULL です。|
|**total_execution_time**|**int**|開始時間 (分) (null 許容のない) からの合計実行時間|
|**percent_complete**|**real**|% (Null を許容しません) でインデックス操作の進行状況の完了。|
|**page_count**|**bigint**|新しいインデックス構築操作とのマッピング インデックス (null を許容しません) によって割り当てられたインデックス ページの合計数。

## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  

## <a name="example"></a>例

 一時停止状態にあるすべての再開可能なインデックス再構築操作を一覧表示します。

```sql
SELECT * FROM  sys.index_resumable_operations WHERE STATE = 1;  
```

## <a name="see-also"></a>参照

- [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)
- [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)
- [カタログ ビュー](catalog-views-transact-sql.md)
- [オブジェクト カタログ ビュー](object-catalog-views-transact-sql.md)
- [sys.indexes](sys-xml-indexes-transact-sql.md)
- [sys.index_columns](sys-index-columns-transact-sql.md)
- [sys.xml_indexes](sys-xml-indexes-transact-sql.md)
- [sys.objects](sys-index-columns-transact-sql.md)
- [sys.key_constraints](sys-key-constraints-transact-sql.md)
- [sys.filegroups](sys-filegroups-transact-sql.md)
- [sys.partition_schemes](sys-partition-schemes-transact-sql.md)
- [SQL Server システム カタログに対するクエリに関してよくあるご質問](querying-the-sql-server-system-catalog-faq.md)
