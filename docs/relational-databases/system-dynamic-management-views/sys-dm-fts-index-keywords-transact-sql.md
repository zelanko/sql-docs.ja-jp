---
title: sys.dm_fts_index_keywords (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 86a4aa126ef72425aa2e3c284a3762517d31222d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47790030"
---
# <a name="sysdmftsindexkeywords-transact-sql"></a>sys.dm_fts_index_keywords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたテーブルのフルテキスト インデックスのコンテンツに関する情報を返します。  
  
 **sys.dm_fts_index_keywords**は動的管理関数です。  
  
> [!NOTE]  
>  下位レベルのフルテキスト インデックス情報を表示するには、使用、 [sys.dm_fts_index_keywords_by_document](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)ドキュメント レベルでの動的管理関数。  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.dm_fts_index_keywords( DB_ID('database_name'), OBJECT_ID('table_name') )  
```  
  
## <a name="arguments"></a>引数  
 db_id('*database_name*')  
 呼び出し、 [DB_ID()](../../t-sql/functions/db-id-transact-sql.md)関数。 この関数は、データベースの名前を受け付けますをデータベースの ID を返しますが**sys.dm_fts_index_keywords**を使用して、指定されたデータベースを検索します。 場合 *database_name* は省略すると、現在のデータベース ID が返されます。  
  
 object_id('*table_name*')  
 呼び出し、 [OBJECT_ID()](../../t-sql/functions/object-id-transact-sql.md)関数。 この関数はテーブル名を受け取り、調べるフルテキスト インデックスが含まれているテーブルのテーブル ID を返します。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**keyword**|**nvarchar (4000)**|フルテキスト インデックス内で格納されているキーワードの 16 進数表現。<br /><br /> 注: 0 Xff は、ファイルまたはデータセットの終了位置を示す特殊文字を表します。|  
|**display_term**|**nvarchar (4000)**|人間が判読できる形式のキーワードです。 この形式は、16 進数形式から派生します。<br /><br /> 注: **display_term**値 0 Xff は"END OF FILE"です。|  
|**column_id**|**int**|現在のキーワードのフルテキスト インデックスが作成された列の ID です。|  
|**document_count**|**int**|現在の用語を含むドキュメントまたは行の数です。|  
  
## <a name="remarks"></a>コメント  
 によって返される情報**sys.dm_fts_index_keywords**は特に、次を検索するために便利です。  
  
-   キーワードがフルテキスト インデックスの一部であるかどうか。  
  
-   特定のキーワードを含むドキュメントまたは行の数。  
  
-   フルテキスト インデックスで最も一般的なキーワード。  
  
    -   **document_count**それぞれの*keyword_value*合計と比較**document_count**、0 xff のドキュメント数。  
  
    -   通常、一般的なキーワードは、ストップワードとして宣言するのに適している可能性が高いと考えられます。  
  
> [!NOTE]  
>  **Document_count**によって返される**sys.dm_fts_index_keywords**によって返されるカウントよりも特定のドキュメントの不正確になる可能性があります**sys.dm_fts_index_keywords_by_document**または**CONTAINS**クエリ。 このように不正確になる可能性は、1% 未満であると推定されます。 に、この状況が発生することが、 **document_id** 1 つ以上の行インデックス フラグメントで、または同じ行が複数回にわたってときに 2 回カウントされる可能性があります。 特定のドキュメントの正確なカウントを取得するを使用して**sys.dm_fts_index_keywords_by_document**または**CONTAINS**クエリ。  
  
## <a name="permissions"></a>アクセス許可  
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
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)   
 [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
