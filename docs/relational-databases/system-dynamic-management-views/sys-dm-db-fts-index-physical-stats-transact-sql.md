---
title: sys.dm_db_fts_index_physical_stats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_fts_index_physical_stats_TSQL
- dm_db_fts_index_physical_stats
- dm_db_fts_index_physical_stats_TSQL
- sys.dm_db_fts_index_physical_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_fts_index_physical_stats dynamic management view
ms.assetid: 997c3278-3630-47f6-ada3-190b6c16ce0e
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 87496b0041b356f76bca28cd30cefa459f2c4f98
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmdbftsindexphysicalstats-transact-sql"></a>sys.dm_db_fts_index_physical_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  フルテキスト インデックスまたはセマンティック インデックスを関連付けられている各テーブル内のフルテキスト インデックスまたはセマンティック インデックスごとに 1 行のデータを返します。  
  
||||  
|-|-|-|  
|**列名**|**型**|**Description**|  
|**object_id**|int|インデックスを含むテーブルのオブジェクト ID。|  
|**fulltext_index_page_count**|**bigint**|インデックス ページの数で表された、抽出の論理サイズ。|  
|**keyphrase_index_page_count**|**bigint**|インデックス ページの数で表された、抽出の論理サイズ。|  
|**similarity_index_page_count**|**bigint**|インデックス ページの数で表された、抽出の論理サイズ。|  
  
## <a name="general-remarks"></a>全般的な解説  
 詳細については、次を参照してください。[モニター セマンティック検索の管理と](../../relational-databases/search/manage-and-monitor-semantic-search.md)です。  
  
## <a name="metadata"></a>メタデータ  
 セマンティック インデックス作成の状態の詳細については、次の動的管理ビューに対してクエリを実行してください。  
  
-   [sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)  
  
-   [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)  
  
## <a name="permissions"></a>権限

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   

## <a name="examples"></a>使用例  
 次の例では、フルテキスト インデックスまたはセマンティック インデックスを関連付けられているすべてのテーブル内の各フルテキスト インデックスまたはセマンティック インデックスの論理サイズについてクエリを実行する方法を示しています。  
  
```  
SELECT * FROM sys.dm_db_fts_index_physical_stats;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セマンティクス検索の管理および監視](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
