---
title: sys.dm_fts_index_keywords (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_fts_index_keywords
- sys.dm_fts_index_keywords
- sys.dm_fts_index_keywords_TSQL
- dm_fts_index_keywords_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_index_keywords dynamic management function
- full-text search [SQL Server], viewing keywords
- troubleshooting [SQL Server], full-text search
ms.assetid: fce7b2a1-7e74-4769-86a8-c77c7628decd
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 86fcb1729835cb834491bd3ce20716f82b6feb9a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmftsindexkeywords-transact-sql"></a>sys.dm_fts_index_keywords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたテーブルのフルテキスト インデックスのコンテンツに関する情報を返します。  
  
 **sys.dm_fts_index_keywords**動的管理関数です。  
  
> [!NOTE]  
>  表示するには下位レベルのフルテキスト インデックス情報を使用して、 [sys.dm_fts_index_keywords_by_document](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)ドキュメント レベルでの動的管理関数です。  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.dm_fts_index_keywords( DB_ID('database_name'), OBJECT_ID('table_name') )  
```  
  
## <a name="arguments"></a>引数  
 db_id('*database_name*')  
 呼び出し、 [DB_ID()](../../t-sql/functions/db-id-transact-sql.md)関数。 この関数は、データベースの名前を受け付けますをデータベース ID を返しますこれ**sys.dm_fts_index_keywords**を使用して、指定されたデータベースを検索します。 場合 *database_name* は省略すると、現在のデータベース ID が返されます。  
  
 object_id('*table_name*')  
 呼び出し、 [OBJECT_ID()](../../t-sql/functions/object-id-transact-sql.md)関数。 この関数はテーブル名を受け取り、調べるフルテキスト インデックスが含まれているテーブルのテーブル ID を返します。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**keyword**|**nvarchar (4000)**|フルテキスト インデックスの内部に格納されているキーワードの 16 進数表現です。<br /><br /> 注: 0 Xff は、ファイルまたはデータセットの終了を示す特殊文字を表します。|  
|**display_term**|**nvarchar (4000)**|人間が判読できる形式のキーワードです。 この形式は、16 進数形式から派生します。<br /><br /> 注: **display_term**値 0 Xff は「のファイルの終了」です。|  
|**column_id**|**int**|現在のキーワードのフルテキスト インデックスが作成された列の ID です。|  
|**document_count**|**int**|現在の用語を含むドキュメントまたは行の数です。|  
  
## <a name="remarks"></a>解説  
 によって返される情報**sys.dm_fts_index_keywords**は特に、次を検索するために便利です。  
  
-   キーワードがフルテキスト インデックスの一部であるかどうか。  
  
-   特定のキーワードを含むドキュメントまたは行の数。  
  
-   フルテキスト インデックスで最も一般的なキーワード。  
  
    -   **document_count**各*keyword_value*合計と比較して**document_count**、0 xff のドキュメント数。  
  
    -   通常、一般的なキーワードは、ストップワードとして宣言するのに適している可能性が高いと考えられます。  
  
> [!NOTE]  
>  **Document_count**によって返される**sys.dm_fts_index_keywords**によって返されるカウントよりも特定のドキュメントの不正確になる可能性があります**sys.dm_fts_index_keywords_by_document**または**CONTAINS**クエリ。 このように不正確になる可能性は、1% 未満であると推定されます。 に、この状況が発生することが、 **document_id**インデックス フラグメントで、または同じ行で複数回表示される 2 つ以上の行にわたって続いてときに 2 回カウントされることがあります。 特定のドキュメントの正確なカウントを取得するには使用**sys.dm_fts_index_keywords_by_document**または**CONTAINS**クエリ。  
  
## <a name="permissions"></a>権限  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-displaying-high-level-full-text-index-content"></a>A. 上位レベルのフルテキスト インデックス コンテンツの表示  
 次の例で、フルテキスト インデックスの上位レベルのコンテンツに関する情報を表示する、`HumanResources.JobCandidate`テーブル。  
  
```  
SELECT * FROM sys.dm_fts_index_keywords(db_id('AdventureWorks2012'), object_id('HumanResources.JobCandidate'))  
GO  
```  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索とセマンティック検索の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [フル テキスト検索](../../relational-databases/search/full-text-search.md)   
 [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
