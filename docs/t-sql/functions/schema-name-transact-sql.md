---
title: "SCHEMA_NAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SCHEMA_NAME
- SCHEMA_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SCHEMA_NAME function
- schemas [SQL Server], names
ms.assetid: 20071b77-2b6e-4ce7-a8e3-fa71480baf73
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e507e5a406cb78645489adbab13d16cf513b2448
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="schemaname-transact-sql"></a>SCHEMA_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  スキーマ ID に関連付けられているスキーマ名を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
SCHEMA_NAME ( [ schema_id ] )  
```  
  
## <a name="arguments"></a>引数  
  
|項目|定義|  
|----------|----------------|  
|*schema_id*|スキーマの ID を指定します。 *schema_id*は、 **int**です。場合*schema_id*が定義されていない、SCHEMA_NAME は、呼び出し元の既定のスキーマの名前が返すされます。|  
  
## <a name="return-types"></a>戻り値の型  
 **sysname**  
  
 ときに、NULL を返します*schema_id*有効な ID ではありません  
  
## <a name="remarks"></a>解説  
 SCHEMA_NAME は、システム スキーマとユーザー定義スキーマの名前を返します。 SCHEMA_NAME は、選択リストの中、WHERE 句の中、また、式を使える所であればどこでも呼び出すことができます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-the-name-of-the-default-schema-of-the-caller"></a>A. 呼び出し元の既定のスキーマ名を返す  
  
```  
SELECT SCHEMA_NAME();  
GO  
```  
  
### <a name="b-returning-the-name-of-a-schema-by-using-an-id"></a>B. ID を使用してスキーマの名前を返す  
  
```  
USE AdventureWorks2012;  
GO  
SELECT SCHEMA_NAME(5);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-the-name-of-the-default-schema-of-the-caller"></a>C. 呼び出し元の既定のスキーマ名を返す  
  
```  
SELECT SCHEMA_NAME();  
```  
  
### <a name="d-returning-the-name-of-a-schema-by-using-an-id"></a>D. ID を使用してスキーマの名前を返す  
  
```  
SELECT SCHEMA_NAME(1);  
```  
  
## <a name="see-also"></a>参照  
 [式 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SCHEMA_ID & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/schema-id-transact-sql.md)   
 [sys.schemas & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [メタデータ関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [ここで & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)  
  
  


