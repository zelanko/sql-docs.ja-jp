---
title: "照会する (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_columns
- sp_help_fulltext_columns_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_fulltext_columns
ms.assetid: 92c8656b-f7fd-4904-9796-acc9ffed4106
caps.latest.revision: "25"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e1cb2b03611ed1208716008e7178ce139e7d9c61
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sphelpfulltextcolumns-transact-sql"></a>sp_help_fulltext_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  フルテキスト インデックス作成用として指定された列を返します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して、 [sys.fulltext_index_columns](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)カタログ ビューを代わりにします。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)、 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_fulltext_columns [ [ @table_name = ] 'table_name' ] ]   
     [ , [ @column_name = ] 'column_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@table_name=**] **'***table_name***'**  
 フルテキスト インデックス情報を要求するテーブル名を指定します。この名前は 1 つまたは 2 つの要素で構成されます。 *table_name*は**nvarchar (517)**既定値は NULL です。 場合*table_name*を省略すると、すべてのフルテキスト インデックス付きテーブルのフルテキスト インデックス列情報を取得します。  
  
 [  **@column_name=**] **'***column_name***'**  
 フルテキスト インデックスのメタデータを要求する対象の列の名前です。 *column_name*は**sysname**既定値は NULL です。 場合*column_name*を省略するか、NULL の場合は、すべてのフルテキスト インデックス付き列のフルテキスト列情報が返されます*table_name*です。 場合*table_name*はも省略するか、NULL の場合、データベース内のすべてのテーブルのすべてのフルテキスト インデックス付き列のフルテキスト インデックス列情報が返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または (1) の失敗  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|テーブル所有者 テーブルを作成したデータベース ユーザーの名前です。|  
|**TABLE_ID**|**int**|テーブルの ID を指定します。|  
|**TABLE_NAME**|**sysname**|テーブルの名前。|  
|**FULLTEXT_COLUMN_NAME**|**sysname**|フルテキスト インデックスが作成されたテーブル内にある、インデックス作成用に指定された列。|  
|**FULLTEXT_COLID**|**int**|フルテキスト インデックスが作成された列の列 ID。|  
|**FULLTEXT_BLOBTP_COLNAME**|**sysname**|フルテキスト インデックスが作成されたテーブル内の列で、フルテキスト インデックス列のドキュメントの種類を指定する列。 この値は、フルテキスト インデックス列がときにのみ適用、 **varbinary (max)**または**イメージ**列です。|  
|**FULLTEXT_BLOBTP_COLID**|**int**|ドキュメント型列の列 ID。 この値は、フルテキスト インデックス列がときにのみ適用、 **varbinary (max)**または**イメージ**列です。|  
|**FULLTEXT_LANGUAGE**|**sysname**|列のフルテキスト検索に使用される言語。|  
  
## <a name="permissions"></a>Permissions  
 メンバーに権限は、既定の実行、**パブリック**ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、`Document` テーブルでフルテキスト インデックス作成用に指定された列に関する情報を返します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_help_fulltext_columns 'Production.Document';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [COLUMNPROPERTY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/columnproperty-transact-sql.md)   
 [sp_fulltext_column &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-fulltext-column-transact-sql.md)   
 [sp_help_fulltext_columns_cursor &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-cursor-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
