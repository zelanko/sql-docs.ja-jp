---
title: "FULLTEXT STOPLIST (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STOPLIST_TSQL
- FULLTEXT STOPLIST
- STOPLIST
- FULLTEXT_STOPLIST_TSQL
- CREATE FULLTEXT STOPLIST
- CREATE_FULLTEXT_STOPLIST_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- stoplists [full-text search]
- CREATE FULLTEXT STOPLIST statement
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 0669b1d0-46cc-4fac-8df7-5f7fa7af5db4
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c6877dccd56d4f90a5600b095b1294ec1ccd6eb3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-fulltext-stoplist-transact-sql"></a>CREATE FULLTEXT STOPLIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベースに新しいフルテキスト ストップリストを作成します。  
  
 ストップ ワードと呼ばれるオブジェクトを使用して、データベースで管理*ストップ リスト*です。 ストップリストは、フルテキスト インデックスに関連付けられている場合、そのインデックスのフルテキスト クエリに適用されるストップワードの一覧です。 詳細については、「 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)」を参照してください。  
  
> [!IMPORTANT]  
>  CREATE FULLTEXT STOPLIST、ALTER FULLTEXT STOPLIST、および DROP FULLTEXT STOPLIST は、互換性レベル 100 でのみサポートされています。 互換性レベルが 80 および 90 の場合、これらのステートメントはサポートされません。 ただし、システム ストップリストは、どの互換性レベルでも自動的に新しいフルテキスト インデックスに関連付けられます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE FULLTEXT STOPLIST stoplist_name  
[ FROM { [ database_name.]source_stoplist_name } | SYSTEM STOPLIST ]  
[ AUTHORIZATION owner_name ]  
;  
```  
  
## <a name="arguments"></a>引数  
 *stoplist_name*  
 ストップリストの名前です。 *stoplist_name*最大 128 文字まで指定できます。 *stoplist_name*現在のデータベース内のすべてのストップ リストで一意になるし、識別子の規則に準拠している必要があります。  
  
 *stoplist_name*フルテキスト インデックスが作成されるときに使用されます。  
  
 *database_name*  
 ストップ リストがで指定されたデータベースの名前を指定*source_stoplist_name*が配置されています。 指定しない場合、 *database_name*既定値は、現在のデータベースです。  
  
 *source_stoplist_name*  
 既存のストップリストをコピーして新しいストップリストを作成するように指定します。 場合*source_stoplist_name*が存在しないデータベース ユーザーには、適切なアクセス許可はありません。 または、CREATE FULLTEXT STOPLIST がエラーで失敗します。 ソース ストップリストのストップワードに指定された言語が現在のデータベースに登録されていない場合、CREATE FULLTEXT STOPLIST は成功しますが、警告が表示され、対応するストップワードは追加されません。  
  
 SYSTEM STOPLIST  
 既定で存在するストップ リストから新しいストップ リストが作成されたことを指定します、 [Resource データベース](../../relational-databases/databases/resource-database.md)です。  
  
 承認*owner_name*  
 ストップリストの所有者となるデータベース プリンシパルの名前を指定します。 *owner_name*うち、現在のユーザーがメンバー、または現在のユーザーでは、に対する IMPERSONATE 権限が必要、プリンシパルの名前を指定するかする必要*owner_name*です。 このオプションを指定しない場合は、所有権は現在のユーザーに与えられます。  
  
## <a name="remarks"></a>解説  
 ストップリストの作成者はその所有者になります。  
  
## <a name="permissions"></a>Permissions  
 STOPLIST を作成するには、CREATE FULLTEXT CATALOG 権限が必要です。 ストップリストの所有者は、ストップリストに対して明示的に CONTROL 権限を付与することで、ユーザーによるワードの追加と削除、およびストップリストの削除を許可できます。  
  
> [!NOTE]  
>  フルテキスト インデックスが関連付けられたストップリストを使用するには、REFERENCE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-new-full-text-stoplist"></a>A. 新しいフルテキスト ストップリストを作成する  
 次の例では、`myStoplist` という名前の新しいフルテキスト ストップリストを作成しています。  
  
```  
CREATE FULLTEXT STOPLIST myStoplist;  
GO  
```  
  
### <a name="b-copying-a-full-text-stoplist-from-an-existing-full-text-stoplist"></a>B. 既存のフルテキスト ストップリストからフルテキスト ストップリストをコピーする  
 次の例では、`myStoplist2` という名前の既存の AdventureWorks ストップリストをコピーして、`Customers.otherStoplist` という名前の新しいフルテキスト ストップリストを作成しています。  
  
```  
CREATE FULLTEXT STOPLIST myStoplist2 FROM AdventureWorks.otherStoplist;  
GO  
```  
  
### <a name="c-copying-a-full-text-stoplist-from-the-system-full-text-stoplist"></a>C. システムのフルテキスト ストップリストからフルテキスト ストップリストをコピーする  
 次の例では、システム ストップリストをコピーして、`myStoplist3` という名前の新しいフルテキスト ストップリストを作成しています。  
  
```  
CREATE FULLTEXT STOPLIST myStoplist3 FROM SYSTEM STOPLIST;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER FULLTEXT STOPLIST & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)   
 [DROP FULLTEXT STOPLIST & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-fulltext-stoplist-transact-sql.md)   
 [構成およびストップ ワードとストップ リストをフルテキスト検索の管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [sys.fulltext_stoplists & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_stopwords & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)   
 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)  
  
  

