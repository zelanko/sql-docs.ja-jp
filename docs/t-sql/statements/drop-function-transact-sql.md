---
title: "ドロップ関数 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/28/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_FUNCTION_TSQL
- DROP FUNCTION
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined functions [SQL Server], removing
- removing user-defined functions
- DROP FUNCTION statement
- dropping user-defined functions
- deleting user-defined functions
ms.assetid: ee5ad283-9e44-4109-902f-0ce12669ee11
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c0768b2a24a939bc2e646fb4cc7173762eae7679
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="drop-function-transact-sql"></a>DROP FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  1 つ以上のユーザー定義関数を現在のデータベースから削除します。 ユーザー定義関数を使用して作成される[CREATE FUNCTION](../../t-sql/statements/create-function-transact-sql.md)を使用して変更および[ALTER FUNCTION](../../t-sql/statements/alter-function-transact-sql.md)です。  
  
 ドロップ関数には、ネイティブ コンパイル、スカラー ユーザー定義関数がサポートしています。 詳細については、次を参照してください。 [scalar user-defined 関数は、インメモリ OLTP](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
 -- SQL Server, Azure SQL Database 

DROP FUNCTION [ IF EXISTS ] { [ schema_name. ] function_name } [ ,...n ]   
[;]
```

```  
 -- Azure SQL Data Warehouse, Parallel Data Warehouse 

DROP FUNCTION [ schema_name. ] function_name
[;] 
```  
   
  
## <a name="arguments"></a>引数  
 *場合に存在します。*    
 条件付きでは既に存在する場合にのみ、関数を削除します。 以降で利用可能[!INCLUDE[ssnoversion_md](../../includes/ssnoversion_md.md)]2016 し、[!INCLUDE[sssds_md](../../includes/sssds_md.md)]です。
  
 *schema_name*  
 ユーザー定義関数が属するスキーマの名前を指定します。  
  
 *function_name*  
 削除するユーザー定義関数の名前を指定します。 スキーマ名の指定は省略可能です。 サーバー名とデータベース名は指定できません。  
  
## <a name="remarks"></a>解説  
 データベース内に、この関数を参照し SCHEMABINDING を使って作成された [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数またはビューがある場合、または、この関数を参照する計算列、CHECK 制約、DEFAULT 制約がある場合、DROP FUNCTION は失敗します。  
  
 この関数を参照し、インデックスが作成された計算列がある場合、DROP FUNCTION は失敗します。  
  
## <a name="permissions"></a>Permissions  
 DROP FUNCTION を実行するには、少なくとも、関数が属するスキーマに対する ALTER 権限、または関数に対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-a-function"></a>A. 関数を削除する  
 次の例では削除、`fn_SalesByStore`からユーザー定義関数、`Sales`内のスキーマ、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]サンプル データベース。 この関数を作成するで例 B を参照してください。 [CREATE FUNCTION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-function-transact-sql.md).  
  
```  
DROP FUNCTION Sales.fn_SalesByStore;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-function-transact-sql.md)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)   
 [OBJECT_ID と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/object-id-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.parameters &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)  
  
  
