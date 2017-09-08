---
title: "検索プロパティ リスト (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SEARCH_PROPERTY_LIST_TSQL
- CREATE SEARCH
- CREATE_SEARCH_TSQL
- CREATE_SEARCH_PROPERTY_TSQL
- CREATE SEARCH PROPERTY
- CREATE SEARCH PROPERTY LIST
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search property lists [SQL Server], creating
- CREATE SEARCH PROPERTY LIST statement
ms.assetid: 5440cbb8-3403-4d27-a2f9-8e1f5a1bc12b
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b055be4f948b62553ddbabb40613971a0e5619d8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-search-property-list-transact-sql"></a>CREATE SEARCH PROPERTY LIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  新しい検索プロパティ リストを作成します。 検索プロパティ リストは、フルテキスト インデックスに含める 1 つまたは複数の検索プロパティを指定するために使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE SEARCH PROPERTY LIST new_list_name  
   [ FROM [ database_name. ] source_list_name ]  
   [ AUTHORIZATION owner_name ]  
;  
```  
  
## <a name="arguments"></a>引数  
 *new_list_name*  
 新しい検索プロパティ リストの名前を指定します。 *new_list_name*最大 128 文字の識別子です。 *new_list_name*現在のデータベース内のすべてのプロパティ リストで一意になるし、識別子の規則に準拠している必要があります。 *new_list_name*フルテキスト インデックスが作成されるときに使用されます。  
  
 *database_name*  
 プロパティ リストが指定されたデータベースの名前を指定*source_list_name*が配置されています。 指定しない場合、 *database_name*既定値は、現在のデータベースです。  
  
 *database_name*既存のデータベースの名前を指定する必要があります。 現在の接続のログインがで指定されたデータベース内の既存のユーザー ID を関連付ける必要がある*database_name*です。 必要な必要もあります[権限](#Permissions)データベースでします。  
  
 *source_list_name*  
 既存のプロパティ リストをコピーして、新しいプロパティ リストを作成するように指定*database_name*です。 場合*source_list_name*が存在しない CREATE SEARCH PROPERTY LIST がエラーで失敗します。 検索プロパティは、 *source_list_name*によって継承される*new_list_name*です。  
  
 承認*owner_name*  
 プロパティ リストを所有するユーザーまたはロールの名前を指定します。 *owner_name*うち、現在のユーザーがメンバー、または現在のユーザーでは、に対する IMPERSONATE 権限が必要なロールの名前を指定するかする必要*owner_name*です。 このオプションを指定しない場合は、所有権は現在のユーザーに与えられます。  
  
> [!NOTE]  
>  使用して、所有者を変更することができます、 [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]  
>  を一般に、リスト プロパティについてを参照してください[検索プロパティ リストとドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)です。  
  
 既定では、新しい検索プロパティ リストは空であるため、1 つまたは複数の検索プロパティを手動で追加する必要があります。 また、既存の検索プロパティ リストをコピーすることもできます。 その場合、コピー元の検索プロパティが新しいリストに継承されます。検索プロパティを追加または削除することによって、新しいリストに変更を加えることができます。 フルテキスト インデックスには、すべてのカタログを次回作成するときの検索プロパティ リスト内にあるプロパティが含まれます。  
  
 CREATE SEARCH PROPERTY LIST ステートメントは、次のような状況で失敗します。  
  
-   データベースを指定して場合*database_name*存在しません。  
  
-   一覧を指定して場合*source_list_name*存在しません。  
  
-   正しい権限がない場合。  
  
 **追加または一覧からプロパティを削除するには**  
  
-   [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/alter-search-property-list-transact-sql.md)  
  
-   **プロパティ リストを削除するには**  
  
-   [DROP SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/drop-search-property-list-transact-sql.md)  
  
##  <a name="Permissions"></a> アクセス許可  
 現在のデータベースには CREATE FULLTEXT CATALOG 権限が必要であり、ソース プロパティ リストのコピー元のデータベースには REFERENCES 権限が必要です。  
  
> [!NOTE]  
>  リストとフルテキスト インデックスを関連付けるには、REFERENCE 権限が必要です。 プロパティを追加または削除するか、リストを削除するには、CONTROL 権限が必要です。 プロパティ リストの REFERENCE 権限または CONTROL 権限は、そのプロパティ リストの所有者が許可できます。 CONTROL 権限を持つユーザーは、他のユーザーに REFERENCES 権限を与えることができます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-an-empty-property-list-and-associating-it-with-an-index"></a>A. 空のプロパティ リストを作成し、インデックスに関連付ける  
 次の例では、という名前の新しい検索プロパティ リスト`DocumentPropertyList`です。 使用して、 [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md)ステートメントに、新しいプロパティ リストのフルテキスト インデックスに関連付ける、`Production.Document`テーブルに、`AdventureWorks`データベースの作成を開始することがなく、します。  
  
> [!NOTE]  
>  例ではいくつかの定義済みで既知の検索プロパティをこの検索プロパティ リストに追加する場合は、次を参照してください。 [ALTER SEARCH PROPERTY LIST & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-search-property-list-transact-sql.md). 検索プロパティをリストに追加した後、データベース管理者は、START FULL POPULATION 句を指定して別の ALTER FULLTEXT INDEX ステートメントを使用する必要があります。  
  
```  
CREATE SEARCH PROPERTY LIST DocumentPropertyList;  
GO  
USE AdventureWorks2012;  
ALTER FULLTEXT INDEX ON Production.Document   
   SET SEARCH PROPERTY LIST DocumentPropertyList  
   WITH NO POPULATION;   
GO   
```  
  
### <a name="b-creating-a-property-list-from-an-existing-one"></a>B. 既存のプロパティ リストからプロパティ リストを作成する  
 次の例では、`JobCandidateProperties` データベースのフルテキスト インデックスに関連付けられた、例 A で作成したリスト `DocumentPropertyList` から、新しい検索プロパティ リスト `AdventureWorks2012` を作成します。 使用して ALTER FULLTEXT INDEX ステートメントに、新しいプロパティ リストのフルテキスト インデックスに関連付ける、`HumanResources.JobCandidate`テーブルに、`AdventureWorks2012`データベース。 この ALTER FULLTEXT INDEX ステートメントにより、完全作成が開始されます。これは、SET SEARCH PROPERTY LIST 句の既定の動作です。  
  
```  
CREATE SEARCH PROPERTY LIST JobCandidateProperties 
FROM AdventureWorks2012.DocumentPropertyList;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate   
   SET SEARCH PROPERTY LIST JobCandidateProperties;  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [ALTER SEARCH PROPERTY LIST & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-search-property-list-transact-sql.md)   
 [DROP SEARCH PROPERTY LIST & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-search-property-list-transact-sql.md)   
 [sys.registered_search_properties & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [sys.registered_search_property_lists & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [sys.dm_fts_index_keywords_by_property & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)   
 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [検索プロパティのプロパティ セット GUID およびプロパティ整数 ID の取得](../../relational-databases/search/find-property-set-guids-and-property-integer-ids-for-search-properties.md)  
  
  

