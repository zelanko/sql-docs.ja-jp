---
title: sys.fulltext_stopwords (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fulltext_stopwords_TSQL
- fulltext_stopwords
- sys.fulltext_stopwords
- sys.fulltext_stopwords_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stopwords
- sys.fulltext_stopwords catalog view
- stopwords [full-text search]
ms.assetid: 79787bb7-d729-448e-b56a-0a467bbb304f
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 01a61adac50845def8a54b4b311008c06e01b98e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysfulltextstopwords-transact-sql"></a>sys.fulltext_stopwords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベース内のすべてのストップリストでストップワードごとに 1 行のデータを格納します。  
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**stoplist_id**|**int**|**stopword** が属しているストップリストの ID です。 この ID はデータベース内で一意です。|  
|**stopword**|**nvarchar(64)**|ストップワードの照合で考慮される用語です。|  
|**言語**|**sysname**|内の別名のいずれかの値は、 [sys.fulltext_languages](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)ロケール識別子の値に対応する (**LCID**)、または LCID の数値の文字列表現。|  
|**language_id**|**int**|単語区切りに使用される LCID です。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [構成およびストップ ワードとストップ リストをフルテキスト検索の管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_system_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-system-stopwords-transact-sql.md)  
  
  
