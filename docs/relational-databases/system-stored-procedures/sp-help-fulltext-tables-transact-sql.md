---
title: "sp_help_fulltext_tables (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_help_fulltext_tables
- sp_help_fulltext_tables_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_fulltext_tables
ms.assetid: 86e24a5f-a869-43f6-b83e-c52b7b01b5ff
caps.latest.revision: "21"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d021a6f59bd85cdc8c163d2dfb35eab90efa349b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sphelpfulltexttables-transact-sql"></a>sp_help_fulltext_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  フルテキスト インデックス作成用に登録されたテーブルの一覧を返します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して**sys.fulltext_indexes**カタログ ビューを代わりにします。 詳細については、次を参照してください。 [sys.fulltext_indexes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md).  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)、 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_fulltext_tables [ [ @fulltext_catalog_name = ] 'fulltext_catalog_name' ]   
     [ , [ @table_name = ] 'table_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@fulltext_catalog_name=**] **'***fulltext_catalog_name***'**  
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
EXEC sp_help_fulltext_tables 'Cat_Desc';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [INDEXPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [sp_fulltext_table &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-fulltext-table-transact-sql.md)   
 [sp_help_fulltext_tables_cursor &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-cursor-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
