---
title: sys.registered_search_property_lists (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- registered_search_property_lists_TSQL
- sys.registered_search_property_lists
- registered_search_property_lists
- sys.registered_search_property_lists_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- sys.registered_search_property_lists catalog view
- search property lists [SQL Server], viewing
ms.assetid: 630d4caa-9bea-4cd3-a5b1-01098b0855fc
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a3581b5af74c6b9d23157e3806c68bfbd0db1854
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysregisteredsearchpropertylists-transact-sql"></a>sys.registered_search_property_lists (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースの検索プロパティ リストごとに 1 行のデータを格納します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**property_list_id**|**int**|プロパティ リストの ID。|  
|**name**|**sysname**|プロパティ リストの名前。|  
|**create_date**|**datetime**|プロパティ リストが作成された日付。|  
|**modify_date**|**datetime**|ALTER ステートメントによってプロパティ リストが最後に変更された日付。|  
|**principal_id**|**int**|プロパティ リストの所有者。|  
  
## <a name="remarks"></a>解説  
 詳細については、「 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)」を参照してください。  
  
## <a name="permissions"></a>権限  
 検索プロパティ リスト内のメタデータの表示は、自分が所有している、または REFERENCE 権限が与えられている検索プロパティ リストに限定されます。  
  
> [!NOTE]  
>  検索プロパティ リストの REFERENCE 権限または CONTROL 権限は、その検索プロパティ リストの所有者が許可できます。 CONTROL 権限を持つユーザーは、他のユーザーに REFERENCE 権限を与えることができます。  
  
## <a name="examples"></a>使用例  
 次の例では、検索プロパティ リストの名前と ID の表示、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT property_list_id, name FROM sys.registered_search_property_lists;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [sys.fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)  
  
  
