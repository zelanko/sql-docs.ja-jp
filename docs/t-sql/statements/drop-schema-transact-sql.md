---
title: "ドロップ スキーマ (TRANSACT-SQL) |Microsoft ドキュメント"
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
- DROP SCHEMA
- DROP_SCHEMA_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting schemas
- schemas [SQL Server], removing
- DROP SCHEMA statement
- dropping schemas
- removing schemas
ms.assetid: 874aa29e-c8ad-41e4-a672-900fdc58f1f6
caps.latest.revision: 51
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 584aea443e3263f44367ede24d7a59b8564e92c1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-schema-transact-sql"></a>DROP SCHEMA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベースからスキーマを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP SCHEMA  [ IF EXISTS ] schema_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP SCHEMA schema_name  
```  
  
## <a name="arguments"></a>引数  
 *場合に存在します。*  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
 条件付きでは既に存在する場合にのみ、スキーマを削除します。  
  
 *schema_name*  
 データベースで認識されるスキーマの名前を指定します。  
  
## <a name="remarks"></a>解説  
 削除するスキーマは、オブジェクトが含まれていないスキーマであることが必要です。 オブジェクトがスキーマに含まれている場合、DROP ステートメントは失敗します。  
  
 スキーマについての情報は、 [sys.schemas](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)カタログ ビューです。  
  
 **注意**[!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 スキーマに対する CONTROL 権限、またはデータベースに対する ALTER ANY SCHEMA 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、まず単一の `CREATE SCHEMA` ステートメントを実行し、 `Sprockets` が所有するスキーマ `Krishna` を作成します。次にテーブル `Sprockets.NineProngs` を作成した後、`SELECT` に対して `Anibal` 権限を許可し、`SELECT` に対して `Hung-Fu` 権限を拒否します。  
  
```  
CREATE SCHEMA Sprockets AUTHORIZATION Krishna   
    CREATE TABLE NineProngs (source int, cost int, partnumber int)  
    GRANT SELECT TO Anibal   
    DENY SELECT TO Hung-Fu;  
GO  
```  
  
 次のステートメントでは、このスキーマを削除します。 先に、スキーマに含まれるテーブルを削除する必要があることに注意してください。  
  
```  
DROP TABLE Sprockets.NineProngs;  
DROP SCHEMA Sprockets;  
GO  
```  
  
  
## <a name="see-also"></a>参照  
 [スキーマ &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-schema-transact-sql.md)   
 [ALTER SCHEMA &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-schema-transact-sql.md)   
 [スキーマ (TRANSACT-SQL) を削除します](../../t-sql/statements/drop-schema-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  

