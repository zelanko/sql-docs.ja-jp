---
title: "ドロップ プロシージャ (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP PROCEDURE
- DROP_PROCEDURE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing stored procedures
- dropping procedure groups
- deleting stored procedures
- deleting procedure groups
- DROP PROCEDURE statement
- dropping stored procedures
- stored procedures [SQL Server], removing
- removing procedure groups
ms.assetid: 1c2d7235-7b9b-4336-8f17-429e7d82c2c3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: aef67c09e34bf23fa1185cc10b12ff3fb88e6a6c
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="drop-procedure-transact-sql"></a>DROP PROCEDURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  1 つ以上のストアド プロシージャまたはプロシージャ グループを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の現在のデータベースから削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP { PROC | PROCEDURE } [ IF EXISTS ] { [ schema_name. ] procedure } [ ,...n ]  
```  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP { PROC | PROCEDURE } { [ schema_name. ] procedure_name }  
```  
  
## <a name="arguments"></a>引数  
 *場合に存在します。*  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
 条件付きでは既に存在する場合にのみ、プロシージャを削除します。  
  
 *schema_name*  
 プロシージャが属するスキーマの名前を指定します。 サーバー名またはデータベース名は指定できません。  
  
 *プロシージャ*  
 削除するストアド プロシージャまたはストアド プロシージャ グループの名前です。 番号の付いたプロシージャ グループ内の個々のプロシージャは削除できません。プロシージャ グループ全体が削除されます。  
  
## <a name="best-practices"></a>ベスト プラクティス  
 ストアド プロシージャを削除する前に、依存オブジェクトを確認し、それらのオブジェクトを適切に修正します。 ストアド プロシージャを削除すると、依存オブジェクトとスクリプトが更新されていない場合、それらのオブジェクトがエラーになることがあります。 詳細については、次を参照してください[ストアド プロシージャの依存関係の表示。](../../relational-databases/stored-procedures/view-the-dependencies-of-a-stored-procedure.md)  
  
## <a name="metadata"></a>メタデータ  
 既存のプロシージャの一覧を表示するクエリ、 **sys.objects**カタログ ビューです。 プロシージャの定義を表示するには、クエリ、 **sys.sql_modules**カタログ ビューです。  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 必要があります**コントロール**、プロシージャに対する権限または**ALTER**メンバーシップまたは、プロシージャが所属するスキーマに対する権限、 **db_ddladmin**固定サーバー ロール.  
  
## <a name="examples"></a>使用例  
 次の例では、削除、`dbo.uspMyProc`ストアド プロシージャを現在のデータベースでします。  
  
```  
DROP PROCEDURE dbo.uspMyProc;  
GO  
```  
  
 次の例では、現在のデータベースからいくつかのストアド プロシージャを削除します。  
  
```  
DROP PROCEDURE dbo.uspGetSalesbyMonth, dbo.uspUpdateSalesQuotes, dbo.uspGetSalesByYear;  
```  
  
 次の例では、削除、`dbo.uspMyProc`ストアド プロシージャが存在するは、プロシージャが存在しない場合、エラーは発生しません。 この構文はで新しい[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。  
  
```  
DROP PROCEDURE IF EXISTS dbo.uspMyProc;  
GO  
```  
  
  
## <a name="see-also"></a>参照  
 [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [ストアド プロシージャの削除](../../relational-databases/stored-procedures/delete-a-stored-procedure.md)  
  
  


