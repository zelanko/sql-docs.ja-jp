---
title: "DROP VIEW (Transact SQL) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_VIEW_TSQL
- DROP VIEW
dev_langs:
- TSQL
helpviewer_keywords:
- dropping views
- DROP VIEW statement
- deleting views
- indexed views [SQL Server], removing
- views [SQL Server], removing
- removing views
ms.assetid: 03cea355-e39c-46e1-b7db-8832038669dd
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8dedeff21f56659d0cc55eef2d133a1ecbe0f63e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-view-transact-sql"></a>DROP VIEW (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  1 つ以上のビューを現在のデータベースから削除します。 DROP VIEW は、インデックス付きビューに対して実行できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP VIEW [ IF EXISTS ] [ schema_name . ] view_name [ ...,n ] [ ; ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP VIEW [ schema_name . ] view_name   
[;]  
```  
  
## <a name="arguments"></a>引数  
 *場合に存在します。*  
 **適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)、 [!INCLUDE[sssds](../../includes/sssds-md.md)]). |  
  
 条件付きでは既に存在する場合にのみ、ビューを削除します。  
  
 *schema_name*  
 ビューが所属するスキーマの名前を指定します。  
  
 *view_name*  
 削除するビューの名前を指定します。  
  
## <a name="remarks"></a>解説  
 ビューを削除すると、ビューの定義やビューに関するその他の情報がシステム カタログから削除されます。 ビューに対する権限もすべて削除されます。  
  
 DROP TABLE を使用して削除されたテーブルのすべてのビューは、DROP VIEW を使用して明示的に削除する必要があります。  
  
 DROP VIEW をインデックス付きビューに対して実行すると、ビューのすべてのインデックスが自動的に削除されます。 ビューのすべてのインデックスを表示する使用[sp_helpindex](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md)です。  
  
 ビューからクエリを実行すると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では、ステートメントで参照されているデータベース オブジェクトがすべて存在すること、データベース オブジェクトがステートメントのコンテキストで有効であること、およびデータ変更ステートメントがデータの整合性規則に違反していないことが確認されます。 確認に失敗すると、エラー メッセージが返されます。 確認に成功すると、指定した動作が、基になるテーブルに対する動作に変換されます。 ビューが作成された後で基になるテーブルやビューが変更された場合は、ビューを削除して再作成することが適切な場合があります。  
  
 特定のビューの依存関係の確認の詳細については、次を参照してください。 [sys.sql_dependencies & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md).  
  
 ビューのテキストを表示する方法の詳細については、次を参照してください。 [sp_helptext & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 必要があります**コントロール**、ビューに対する権限**ALTER**ビュー、またはメンバーシップが含まれているスキーマに対する権限、 **db_ddladmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-drop-a-view"></a>A. ビューを削除します。  
 次の例では、削除、ビュー`Reorder`です。  
  
```  
DROP VIEW dbo.Reorder ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/alter-view-transact-sql.md)   
 [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.objects & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [使用 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/use-transact-sql.md)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
 

