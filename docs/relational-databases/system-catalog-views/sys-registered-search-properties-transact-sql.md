---
title: sys.registered_search_properties (Transact SQL) |マイクロソフトのドキュメント
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
- sys.registered_search_properties
- registered_search_properties
- sys.registered_search_properties_TSQL
- registered_search_properties_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search properties [SQL Server]
- property searching [SQL Server], viewing registered properties
- search property lists [SQL Server], viewing registered properties
- sys.registered_search_properties catalog view
ms.assetid: 1b9a7a5c-8c05-4819-83c3-7487dd08fcf7
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 8a174f95ef4c6519c88002ca7393c0d5b1123e4a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39541572"
---
# <a name="sysregisteredsearchproperties-transact-sql"></a>sys.registered_search_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベースの任意の検索プロパティ リストに含まれている検索プロパティごとに 1 行のデータを格納します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**property_list_id**|**int**|このプロパティが属する検索プロパティ リストの ID。|  
|**property_set_guid**|**uniqueidentifier**|検索プロパティが属するプロパティ セットを識別するグローバル一意識別子 GUID。|  
|**property_int_id**|**int**|プロパティ セット内でこの検索プロパティを識別する整数。 **property_int_id**プロパティ セット内で一意です。|  
|**property_name**|**nvarchar(64)**|検索プロパティ リスト内のこの検索プロパティを一意に識別する名前。<br /><br /> 注: のプロパティを検索するにでは、このプロパティ名を指定します[含む](../../t-sql/queries/contains-transact-sql.md)述語です。|  
|**property_description**|**nvarchar(512)**|プロパティの説明。|  
|**property_id**|**int**|検索プロパティで指定された検索プロパティ リスト内のプロパティの内部 ID、 **property_list_id**の値です。<br /><br /> 特定のプロパティが特定の検索プロパティ リストに追加されると、Full-Text Engine は、プロパティを登録し、このプロパティ リストに固有の内部プロパティ ID を、そのプロパティに割り当てます。 内部プロパティ ID は、特定の検索プロパティ リストに固有の整数です。 特定のプロパティを複数の検索プロパティ リストに登録した場合、検索プロパティ リストごとに異なる内部プロパティ ID が割り当てられる可能性があります。<br /><br /> 注: 内部プロパティ ID は、検索プロパティ リストにプロパティを追加するときに指定されるプロパティ整数識別子とは異なります。 詳細については、「 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)」を参照してください。<br /><br /> フルテキスト インデックスのプロパティに関連するコンテンツを参照してください。 <br />                  [sys.dm_fts_index_keywords_by_property &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)|  
  
## <a name="remarks"></a>コメント  
 検索プロパティ リストについて詳しくは、「[検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)」をご覧ください。  
  
## <a name="permissions"></a>アクセス許可  
 検索プロパティのメタデータの表示は、自分が所有しているかまたは REFERENCE 権限が与えられている検索プロパティ リストに含まれている検索プロパティに限定されます。  
  
> [!NOTE]  
>  検索プロパティ リストの REFERENCE 権限または CONTROL 権限は、その検索プロパティ リストの所有者が許可できます。 CONTROL 権限を持つユーザーは、他のユーザーに REFERENCE 権限を与えることができます。  
  
## <a name="examples"></a>使用例  
 次の例は、登録されている検索プロパティのすべてのメタデータを表示します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.registered_search_properties;   
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [sys.fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)   
 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
