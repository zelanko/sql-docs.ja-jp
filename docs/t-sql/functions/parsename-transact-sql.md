---
title: "PARSENAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PARSENAME_TSQL
- PARSENAME
dev_langs:
- TSQL
helpviewer_keywords:
- PARSENAME function
- parsing [SQL Server], PARSENAME function
- names [SQL Server], objects
- objects [SQL Server], names
- part of object names [SQL Server]
ms.assetid: abf34f99-9ee9-460b-85b2-930ca5c4b5ae
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 5664c0a98663897f1d0a3cfa46e8dabab0d6ef7a
ms.contentlocale: ja-jp
ms.lasthandoff: 10/17/2017

---
# <a name="parsename-transact-sql"></a>PARSENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  オブジェクト名の指定した部分を返します。 取得できるオブジェクト名の部分は、オブジェクト名、所有者名、データベース名、およびサーバー名です。  
  
> [!NOTE]  
>  PARSENAME 関数では、指定した名前のオブジェクトが存在するかどうかは示されず、 指定したオブジェクト名の指定した部分が返されるだけです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
PARSENAME ( 'object_name' , object_piece )   
```  
  
## <a name="arguments"></a>引数  
 '*object_name*'  
 取得対象となるオブジェクトの名前を指定します。 *object_name*は**sysname**です。 このパラメーターには、オブジェクトの部分的な修飾名を指定します (省略可能)。 オブジェクト名のすべての部分が修飾される場合、この名前には、サーバー名、データベース名、所有者名、オブジェクト名の 4 つの部分を指定可能です。  
  
 *object_piece*  
 返すオブジェクトの部分を指定します。 *object_piece*の種類は**int**、これらの値を持つことができます。  
  
 1 = オブジェクト名  
  
 2 = スキーマ名  
  
 3 = データベース名  
  
 4 = サーバー名  
  
## <a name="return-types"></a>戻り値の型  
 **nchar**  
  
## <a name="remarks"></a>解説  
 PARSENAME では、次のいずれかの条件が真の場合に NULL が返されます。  
  
-   いずれか*object_name*または*object_piece*は NULL です。  
  
-   構文エラーがある。  
  
 要求されたオブジェクトの部分が長さ 0 のであり、有効な[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子。 オブジェクト名の長さが 0 の場合、修飾名全体が無効になります。  
  
## <a name="examples"></a>使用例  
 次の例で`PARSENAME`情報を返す、`Person`テーブルに、`AdventureWorks2012`データベース。  
  
```  
-- Uses AdventureWorks  
  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 1) AS 'Object Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 2) AS 'Schema Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 3) AS 'Database Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 4) AS 'Server Name';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
```
Object Name
------------------------------
DimCustomer

(1 row(s) affected)

Schema Name
------------------------------
dbo

(1 row(s) affected)

Database Name
------------------------------
AdventureWorksPDW2012

(1 row(s) affected)

Server Name
------------------------------
(null)

(1 row(s) affected)
```
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [システム関数 & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  


