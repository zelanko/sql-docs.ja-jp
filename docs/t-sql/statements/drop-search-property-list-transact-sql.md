---
title: "DROP SEARCH PROPERTY LIST (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_SEARCH_PROPERTY_LIST_TSQL
- DROP SEARCH PROPERTY LIST
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- DROP SEARCH PROPERTY LIST statement
- search property lists [SQL Server], dropping
- search property lists [SQL Server], deleting
ms.assetid: 7c7ce52a-6b77-4a1c-9abf-d5feb664bea8
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 970fd636239f6de212d667ef6ec22edfa182859c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-search-property-list-transact-sql"></a>DROP SEARCH PROPERTY LIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  検索プロパティ リストがデータベース内のフルテキスト インデックスに現在関連付けられていない場合に、現在のデータベースからプロパティ リストを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP SEARCH PROPERTY LIST property_list_name  
;  
```  
  
## <a name="arguments"></a>引数  
 *property_list_name*  
 削除する検索プロパティ リストの名前を指定します。 *property_list_name*識別子です。  
  
 表示するには既存のプロパティ リストの名前を使用して、 [sys.registered_search_property_lists](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)カタログ ビューを次のようにします。  
  
```  
SELECT name FROM sys.registered_search_property_lists;  
```  
  
## <a name="remarks"></a>解説  
 リストがいずれかのフルテキスト インデックスに関連付けられている場合は、データベースから検索プロパティ リストを削除できません。削除しようとすると失敗します。 特定のフルテキスト インデックスから検索プロパティ リストを削除する、使用、 [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md)ステートメントでは、off、SET SEARCH PROPERTY LIST 句を指定するか、別の名前を検索プロパティ リスト。  
  
 **サーバー インスタンス上に一覧表示、プロパティを表示するには**  
  
-   [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
  
 **プロパティ リストを表示するには、フルテキスト インデックスに関連します。**  
  
-   [sys.fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)  
  
 **フルテキスト インデックスからプロパティ リストを削除するには**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
##  <a name="Permissions"></a> アクセス許可  
 検索プロパティ リストに対する CONTROL 権限が必要です。  
  
> [!NOTE]  
>  プロパティ リストの CONTROL 権限はそのリストの所有者が許可できます。 既定では、検索プロパティ リストを作成したユーザーが所有者になります。 使用して、所有者を変更することができます、 [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。  
  
## <a name="examples"></a>使用例  
 次の例では削除、`JobCandidateProperties`からプロパティ リスト、`AdventureWorks2012`データベース。  
  
```  
DROP SEARCH PROPERTY LIST JobCandidateProperties;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER SEARCH PROPERTY LIST & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-search-property-list-transact-sql.md)   
 [SEARCH PROPERTY LIST &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-search-property-list-transact-sql.md)   
 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.registered_search_properties & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [sys.registered_search_property_lists & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
  
  

