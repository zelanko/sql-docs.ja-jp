---
title: fulltext_stoplists (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
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
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 88f4354a343e9748e1111d26c3ce8c248431b1be
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68133769"
---
# <a name="sysfulltext_stoplists-transact-sql"></a>sys.fulltext_stoplists (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベース内のフルテキスト ストップリストごとに 1 行のデータを格納します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**stoplist_id**|**int**|ストップリストの ID。データベースで一意の値です。|  
|**name**|**sysname**|ストップリストの名前。|  
|**create_date**|**DATETIME**|ストップリストが作成された日付。|  
|**modify_date**|**DATETIME**|ストップリストが ALTER ステートメントを使用して最後に変更された日付。|  
|**Principal_id**|**int**|ストップリストを所有するデータベースプリンシパルの ID。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [fulltext_system_stopwords &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-fulltext-system-stopwords-transact-sql.md)   
 [fulltext_stopwords &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)   
 [フルテキスト検索のためのストップワードとストップリストの構成と管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Transact-sql&#41;&#40;のフルテキストストップリストの作成](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [Transact-sql&#41;&#40;フルテキストストップリストの変更](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)   
 [Transact-sql&#41;&#40;のフルテキストストップリストの削除](../../t-sql/statements/drop-fulltext-stoplist-transact-sql.md)  
  
  
