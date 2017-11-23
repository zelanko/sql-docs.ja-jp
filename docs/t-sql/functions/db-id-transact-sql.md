---
title: "Db_id 関数 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DB_ID_TSQL
- DB_ID
dev_langs: TSQL
helpviewer_keywords:
- viewing database ID numbers
- IDs [SQL Server], databases
- database IDs [SQL Server]
- identification numbers [SQL Server], databases
- displaying database ID numbers
- DB_ID function
ms.assetid: 7b3aef89-a6fd-4144-b468-bf87ebf381b8
caps.latest.revision: "39"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 152e471cf63efa09b0fc6dcb65acd28a191699b0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="dbid-transact-sql"></a>DB_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

データベースの識別 (ID) 番号を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DB_ID ( [ 'database_name' ] )   
```  
  
## <a name="arguments"></a>引数  
'*database_name*'  
対応するデータベース ID を返す基になるデータベースの名前です。 *database_name*は**sysname**です。 場合*database_name*は省略すると、現在のデータベース ID が返されます。
  
## <a name="return-types"></a>戻り値の型
**int**
  
## <a name="permissions"></a>Permissions  
場合、呼び出し元の**DB_ID**データベースの所有者ではないと、データベースが**マスター**または**tempdb**、対応する行を表示するために必要な最小限のアクセス許可は、ALTER ANY DATABASE または VIEW ANY DATABASE のサーバー レベル権限、または CREATE DATABASE 権限、**マスター**データベース。 呼び出し元が接続しているデータベースは常に **sys.databases**で確認できます。
  
> [!IMPORTANT]  
>  既定は、パブリックのロールは、データベースの情報を表示するすべてのログインを許可する、VIEW ANY DATABASE 権限を持っています。 データベースを検出する機能からのログインをブロックするには、パブリックから VIEW ANY DATABASE 権限を取り消すまたは個別のログインの VIEW ANY DATABASE 権限を拒否します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-the-database-id-of-the-current-database"></a>A. 現在のデータベースのデータベース ID を返す  
この例では、現在のデータベースのデータベース ID を返します。
  
```sql
SELECT DB_ID() AS [Database ID];  
GO  
```  
  
### <a name="b-returning-the-database-id-of-a-specified-database"></a>B. 指定したデータベースのデータベース ID を返す  
次の例、データベースの ID を返します、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。
  
```sql
SELECT DB_ID(N'AdventureWorks2008R2') AS [Database ID];  
GO  
```  
  
### <a name="c-using-dbid-to-specify-the-value-of-a-system-function-parameter"></a>C. DB_ID を使用してシステム関数パラメーターの値を指定する  
次の例で`DB_ID`のデータベース ID を返す、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]システム関数でデータベース`sys.dm_db_index_operational_stats`です。 この関数はデータベース ID を最初のパラメーターとしてとります。
  
```sql
DECLARE @db_id int;  
DECLARE @object_id int;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');  
IF @db_id IS NULL   
  BEGIN;  
    PRINT N'Invalid database';  
  END;  
ELSE IF @object_id IS NULL  
  BEGIN;  
    PRINT N'Invalid object';  
  END;  
ELSE  
  BEGIN;  
    SELECT * FROM sys.dm_db_index_operational_stats(@db_id, @object_id, NULL, NULL);  
  END;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-return-the-id-of-the-current-database"></a>D. 現在のデータベースの ID を返します  
この例では、現在のデータベースのデータベース ID を返します。
  
```sql
SELECT DB_ID();  
```  
  
### <a name="e-return-the-id-of-a-named-database"></a>E. 指定されたデータベースの ID を返します。  
次の例では、AdventureWorksDW2012 データベースのデータベース ID を返します。
  
```sql
SELECT DB_ID('AdventureWorksPDW2012');  
```  
  
## <a name="see-also"></a>参照
[DB_NAME &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/db-name-transact-sql.md)  
[メタデータ関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)  
[sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
[sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)
  
  

