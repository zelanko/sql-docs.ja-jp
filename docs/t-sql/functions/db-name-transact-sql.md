---
title: "DB_NAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/30/2017
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
- DB_NAME
- DB_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database names [SQL Server], DB_NAME
- names [SQL Server], databases
- viewing database names
- displaying database names
- DB_NAME function
ms.assetid: e21fb33a-a3ea-49b0-bb6b-8f789a675a0e
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c5743ccb1374640078a77d84a140e9e5d0fdaef0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dbname-transact-sql"></a>DB_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

データベース名を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DB_NAME ( [ database_id ] )  
```  
  
## <a name="arguments"></a>引数  
*database_id*  
名前が返されるデータベースの識別番号 (ID) を指定します。 *database_id*は**int**、既定値はありません。 ID の指定を省略すると、現在のデータベースの名前が返されます。
  
## <a name="return-types"></a>戻り値の型
**nvarchar (128)**
  
## <a name="permissions"></a>Permissions  
場合、呼び出し元の**DB_NAME**データベースの所有者ではないと、データベースが**マスター**または**tempdb**、対応する行を表示するために必要な最小限のアクセス許可は、ALTER ANY DATABASE または VIEW ANY DATABASE のサーバー レベル権限、または CREATE DATABASE 権限、**マスター**データベース。 呼び出し元が接続しているデータベースは常に **sys.databases**で確認できます。
  
> [!IMPORTANT]  
>  既定は、パブリックのロールは、データベースの情報を表示するすべてのログインを許可する、VIEW ANY DATABASE 権限を持っています。 データベースを検出する機能からのログインをブロックするには、パブリックから VIEW ANY DATABASE 権限を取り消すまたは個別のログインの VIEW ANY DATABASE 権限を拒否します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-the-current-database-name"></a>A. 現在のデータベース名を返す  
次の例では、現在のデータベース名を返します。
  
```sql
SELECT DB_NAME() AS [Current Database];  
GO  
```  
  
### <a name="b-returning-the-database-name-of-a-specified-database-id"></a>B. 指定したデータベース ID のデータベース名を返す  
次の例では、データベース ID が `3` のデータベース名を返します。
  
```sql
USE master;  
GO  
SELECT DB_NAME(3)AS [Database Name];  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-return-the-current-database-name"></a>C. 現在のデータベース名を返す  
  
```sql
SELECT DB_NAME() AS [Current Database];  
```  
  
### <a name="d-return-the-name-of-a-database-by-using-the-database-id"></a>D. データベース ID を使用して、データベースの名前を返す  
次の例では、各データベースの database_id とデータベースの名前を返します。
  
```sql
SELECT DB_NAME(database_id) AS [Database], database_id  
FROM sys.databases;  
```  
  
## <a name="see-also"></a>参照
[DB_ID と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/db-id-transact-sql.md)  
[メタデータ関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)  
[sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)
  
  


