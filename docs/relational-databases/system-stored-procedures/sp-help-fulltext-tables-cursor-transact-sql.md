---
title: "sp_help_fulltext_tables_cursor (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_tables_cursor
- sp_help_fulltext_tables_cursor_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_fulltext_tables_cursor
ms.assetid: 155791eb-8832-4596-8487-7fc70dfba5b9
caps.latest.revision: "25"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3e61a2db1bbfd1f631d3c438fc9cebab57ea0524
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpfulltexttablescursor-transact-sql"></a>sp_help_fulltext_tables_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  カーソルを使用して、フルテキスト インデックス作成用として登録されたテーブルの一覧を返します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して、新しい**sys.fulltext_indexes**カタログ ビューを代わりにします。 詳細については、次を参照してください。 [sys.fulltext_indexes &#40;です。TRANSACT-SQL と #41 です;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_fulltext_tables_cursor [ @cursor_return = ] @cursor_variable OUTPUT   
     [ , [ @fulltext_catalog_name = ] 'fulltext_catalog_name' ]   
     [ , [ @table_name = ] 'table_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@cursor_return=** ]  *@cursor_variable* 出力  
 型の output 変数は、**カーソル**です。 カーソルは読み取り専用で、スクロール可能な動的カーソルです。  
  
 [  **@fulltext_catalog_name=** ] **'***fulltext_catalog_name***'**  
 フルテキスト カタログの名前を指定します。 *fulltext_catalog_name*は**sysname**、既定値は NULL です。 場合*fulltext_catalog_name*を省略するか、NULL の場合は、データベースに関連付けられているすべてのフルテキスト インデックス付きのテーブルが返されます。 場合*fulltext_catalog_name*が指定されているが、 *table_name*を省略するか、NULL の場合は、このカタログに関連付けられているすべてのフルテキスト インデックス付きテーブルについて、フルテキスト インデックス情報を取得します。 両方*fulltext_catalog_name*と*table_name*を指定した場合は、行が返されます*table_name*に関連付けられている*fulltext_catalog_name。*;それ以外の場合、エラーが発生します。  
  
 [  **@table_name=**] **'***table_name***'**  
 フルテキスト メタデータを要求するテーブル名を指定します。この名前は 1 つまたは 2 つの要素で構成されます。 *table_name*は**nvarchar (517)**既定値は NULL です。 だけの場合*table_name*指定すると、関連する行のみ*table_name*が返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または (1) の失敗  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|テーブル所有者 テーブルを作成したデータベース ユーザーの名前です。|  
|**TABLE_NAME**|**sysname**|テーブル名です。|  
|**FULLTEXT_KEY_INDEX_NAME**|**sysname**|一意なキー列として指定された列に対して UNIQUE 制約を課すインデックス。|  
|**FULLTEXT_KEY_COLID**|**int**|FULLTEXT_KEY_NAME で指定された一意なインデックスの列 ID。|  
|**FULLTEXT_INDEX_ACTIVE**|**int**|このテーブルでフルテキスト インデックス作成のマークが付いている列がクエリに適しているかどうか。<br /><br /> 0 = 非アクティブ<br /><br /> 1 = アクティブ|  
|**FULLTEXT_CATALOG_NAME**|**sysname**|フルテキスト インデックス データが存在するフルテキスト カタログ。|  
  
## <a name="permissions"></a>Permissions  
 メンバーに権限は、既定の実行、**パブリック**ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、フルテキスト カタログ `Cat_Desc` に関連付けられた、フルテキスト インデックスが作成されているテーブルの名前を返します。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @mycursor CURSOR;  
EXEC sp_help_fulltext_tables_cursor @mycursor OUTPUT, 'Cat_Desc';  
FETCH NEXT FROM @mycursor;  
WHILE (@@FETCH_STATUS <> -1)  
   BEGIN  
      FETCH NEXT FROM @mycursor;  
   END;  
CLOSE @mycursor;  
DEALLOCATE @mycursor;  
GO   
```  
  
## <a name="see-also"></a>参照  
 [INDEXPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [sp_fulltext_table &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-fulltext-table-transact-sql.md)   
 [sp_help_fulltext_tables &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
