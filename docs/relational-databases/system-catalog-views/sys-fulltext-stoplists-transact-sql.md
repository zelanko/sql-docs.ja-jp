---
title: sys.fulltext_stoplists (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.fulltext_stoplists
- sys.fulltext_stoplists_TSQL
- fulltext_stoplists_TSQL
- fulltext_stoplists
dev_langs:
- TSQL
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- sys.fulltext_stoplists catalog view
- stopwords [full-text search]
ms.assetid: eb69fb8f-f6d9-446e-83c0-67afd05dfba0
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 2ab58541738654f6ffd8aedada56b31f9817cc1b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysfulltextstoplists-transact-sql"></a>sys.fulltext_stoplists (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベース内のフルテキスト ストップリストごとに 1 行のデータを格納します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**stoplist_id**|**int**|ストップリストの ID。データベースで一意の値です。|  
|**name**|**sysname**|ストップリストの名前。|  
|**create_date**|**datetime**|ストップリストが作成された日付。|  
|**modify_date**|**datetime**|ALTER ステートメントを使用してストップリストが最後に変更された日付。|  
|**principal_id**|**int**|ストップリストを所有するデータベース プリンシパルの ID。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.fulltext_system_stopwords &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-system-stopwords-transact-sql.md)   
 [sys.fulltext_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)   
 [構成およびストップ ワードとストップ リストをフルテキスト検索の管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [FULLTEXT STOPLIST & #40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [ALTER FULLTEXT STOPLIST & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)   
 [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/drop-fulltext-stoplist-transact-sql.md)  
  
  
