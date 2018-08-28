---
title: DROP SCHEMA (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 77f9c7a7ea923e2c713e76e1051e8209a3c80794
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43074164"
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
 *IF EXISTS*  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
 条件付きでは既に存在する場合にのみ、スキーマを削除します。  
  
 *schema_name*  
 データベースで認識されるスキーマの名前を指定します。  
  
## <a name="remarks"></a>Remarks  
 削除するスキーマは、オブジェクトが含まれていないスキーマであることが必要です。 オブジェクトがスキーマに含まれている場合、DROP ステートメントは失敗します。  
  
 スキーマに関する情報は、[sys.schemas](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md) カタログ ビューで確認できます。  
  
 **注意** [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>アクセス許可  
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
 [CREATE SCHEMA &#40;Transact-SQL&#41;](../../t-sql/statements/create-schema-transact-sql.md)   
 [ALTER SCHEMA &#40;Transact-SQL&#41;](../../t-sql/statements/alter-schema-transact-sql.md)   
 [DROP SCHEMA (Transact-SQL)](../../t-sql/statements/drop-schema-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
