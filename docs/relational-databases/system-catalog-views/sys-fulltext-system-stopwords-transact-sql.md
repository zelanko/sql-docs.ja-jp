---
title: sys.fulltext_system_stopwords (TRANSACT-SQL) |マイクロソフトのドキュメント
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
- sys.fulltext_system_stopwords_TSQL
- fulltext_system_stopwords
- fulltext_system_stopwords_TSQL
- sys.fulltext_system_stopwords
dev_langs:
- TSQL
helpviewer_keywords:
- stoplists [full-text search]
- sys.fulltext_system_stopwords catalog view
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 487de53f-c637-4d78-85f6-fef5e768cd0c
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 40ba819fcc6e488b76717c61c225180e91571473
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39542932"
---
# <a name="sysfulltextsystemstopwords-transact-sql"></a>sys.fulltext_system_stopwords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  システム ストップリストへのアクセスを提供します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**stopword**|**nvarchar(64)**|ストップ ワードと見なされる期間と一致します。|  
|**language_id**|**int**|言語のロケール識別子 (LCID) です。 この LCID は単語区切りに使用されます。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)   
 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)  
  
  
