---
title: "sp_refreshview (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_refreshview
- sp_refreshview_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_refreshview
ms.assetid: 9ce1d07c-ee66-4a83-8c73-cd2cc104dd08
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7d5477bee5ddf5536f4a8ae838df354db3d7f72f
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sprefreshview-transact-sql"></a>sp_refreshview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定された非スキーマ バインド ビューのメタデータを更新します。 ビューの生成元であるオブジェクトを変更すると、ビューに固有のメタデータが古くなることがあります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_refreshview [ @viewname = ] 'viewname'   
```  
  
## <a name="arguments"></a>引数  
 [  **@viewname=** ] **'***viewname***'**  
 ビューの名前を指定します。 *viewname*は**nvarchar**、既定値はありません。 *viewname*マルチパートの識別子を指定できますが、現在のデータベース内のビューに参照できるのみです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 0 以外の数値 (失敗)  
  
## <a name="remarks"></a>解説  
 ビューがスキーマ バインドで作成されていない場合**sp_refreshview**ビューの定義に影響を与える、ビューを基になるオブジェクトが変更されたときに実行する必要があります。 この操作を行わないと、ビューのクエリ時に、予期しない結果が表示される可能性があります。  
  
## <a name="permissions"></a>Permissions  
 ビューに対する ALTER 権限と、共通言語ランタイム (CLR) ユーザー定義型およびビュー列で参照される XML スキーマ コレクションに対する REFERENCES 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-updating-the-metadata-of-a-view"></a>A. ビューのメタデータの更新  
 次の例では、ビュー `Sales.vIndividualCustomer` のメタデータを更新します。  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sp_refreshview N'Sales.vIndividualCustomer';  
```  
  
### <a name="b-creating-a-script-that-updates-all-views-that-have-dependencies-on-a-changed-object"></a>B. 変更されたオブジェクトに対する依存関係があるすべてのビューを更新するスクリプトの作成  
 テーブル `Person.Person` に対して作成された任意のビューの定義に影響を与える形で、このテーブルが変更されたとします。 次の例では、テーブル `Person.Person` に対する依存関係があるすべてのビューについて、メタデータを更新するスクリプトを作成しています。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT DISTINCT 'EXEC sp_refreshview ''' + name + ''''   
FROM sys.objects AS so   
INNER JOIN sys.sql_expression_dependencies AS sed   
    ON so.object_id = sed.referencing_id   
WHERE so.type = 'V' AND sed.referenced_id = OBJECT_ID('Person.Person');  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [sp_refreshsqlmodule &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-refreshsqlmodule-transact-sql.md)  
  
  
