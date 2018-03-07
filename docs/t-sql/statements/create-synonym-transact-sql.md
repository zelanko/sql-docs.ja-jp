---
title: "CREATE SYNONYM (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SYNONYM_TSQL
- SYNONYM_TSQL
- SYNONYM
- CREATE SYNONYM
dev_langs:
- TSQL
helpviewer_keywords:
- alternate names [SQL Server]
- names [SQL Server], synonyms
- CREATE SYNONYM statement
- synonyms [SQL Server], creating
ms.assetid: 41313809-e970-449c-bc35-85da2ef96e48
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5dd9893a3832a2fc1bd40d56b119096718b2cf42
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="create-synonym-transact-sql"></a>CREATE SYNONYM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  新しいシノニムを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- SQL Server Syntax  
  
CREATE SYNONYM [ schema_name_1. ] synonym_name FOR <object>  
  
<object> :: =  
{  
    [ server_name.[ database_name ] . [ schema_name_2 ]. object_name   
  | database_name . [ schema_name_2 ].| schema_name_2. ] object_name  
}  
```  
  
```  
-- Azure SQL Database Syntax  
  
CREATE SYNONYM [ schema_name_1. ] synonym_name FOR < object >  
  
< object > :: =  
{  
    [database_name. [ schema_name_2 ].| schema_name_2. ] object_name  
}  
```  
  
## <a name="arguments"></a>引数  
 *schema_name_1*  
 シノニムを作成するスキーマを指定します。 場合*スキーマ*が指定されていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]現在のユーザーの既定のスキーマを使用します。  
  
 *synonym_name*  
 新しいシノニムの名前です。  
  
 *サーバー名*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ベース オブジェクトがあるサーバーの名前です。  
  
 *database_name*  
 ベース オブジェクトがあるデータベースの名前です。 場合*database_name*が指定されていない、現在のデータベースの名前を使用します。  
  
 *schema_name_2*  
 ベース オブジェクトのスキーマの名前です。 場合*schema_name*が指定されていない、現在のユーザーの既定のスキーマが使用されます。  
  
 *object_name*  
 シノニムが参照するベース オブジェクトの名前です。  
  
 Windows Azure SQL データベースでは、database_name が現在のデータベースの場合、または database_name が tempdb で、object_name が # で始まる場合に、3 つの要素で構成された名前形式 database_name.[schema_name].object_name をサポートします。  
  
## <a name="remarks"></a>解説  
 シノニムの作成時にベース オブジェクトが存在している必要はありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、ベース オブジェクトが存在することを実行時に確認します。  
  
 次の種類のオブジェクトに対してシノニムを作成することができます。  
  
|||  
|-|-|  
|アセンブリ (CLR) ストアド プロシージャ|アセンブリ (CLR) テーブル値関数|  
|アセンブリ (CLR) スカラー関数|アセンブリ集計 (CLR) 集計関数|  
|レプリケーション フィルター プロシージャ|拡張ストアド プロシージャ|  
|SQL スカラー関数|SQL テーブル値関数|  
|SQL インラインテーブル値関数|SQL ストアド プロシージャ|  
|表示|テーブル<sup>1</sup> (ユーザー定義)|  
  
 <sup>1 には、ローカルおよびグローバル一時テーブルが含まれています。</sup>  
  
 4 部構成の関数ベース オブジェクト名はサポートされません。  
  
 シノニムは、動的な SQL で作成、削除、および参照できます。  
  
## <a name="permissions"></a>Permissions  
 ユーザーが特定のスキーマ内にシノニムを作成するには、CREATE SYNONYM 権限が必要であり、さらにスキーマを所有しているか ALTER SCHEMA 権限が与えられている必要があります。  
  
 CREATE SYNONYM 権限は、譲与可能な権限です。  
  
> [!NOTE]  
>  ベース オブジェクトに対する権限のチェックはすべて実行時まで延期されるため、ベース オブジェクトに対する権限を持っていなくても、CREATE SYNONYM ステートメントは正常にコンパイルされます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-synonym-for-a-local-object"></a>A. ローカル オブジェクトに対してシノニムを作成する  
 次の例では、まず `Product` データベース中のベース オブジェクト `AdventureWorks2012` に対してシノニムを作成し、次にシノニムに対してクエリを実行します。  
  
```  
-- Create a synonym for the Product table in AdventureWorks2012.  
CREATE SYNONYM MyProduct  
FOR AdventureWorks2012.Production.Product;  
GO  
  
-- Query the Product table by using the synonym.  
SELECT ProductID, Name   
FROM MyProduct  
WHERE ProductID < 5;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ----------------------- 
 ProductID   Name 
 ----------- -------------------------- 
 1           Adjustable Race 
 2           Bearing Ball 
 3           BB Ball Bearing 
 4           Headset Ball Bearings 

 (4 row(s) affected)
``` 
  
### <a name="b-creating-a-synonym-to-remote-object"></a>B. リモート オブジェクトに対してシノニムを作成する  
 次の例では、ベース オブジェクト`Contact`、という名前のリモート サーバー上にある`Server_Remote`です。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
EXEC sp_addlinkedserver Server_Remote;  
GO  
USE tempdb;  
GO  
CREATE SYNONYM MyEmployee FOR Server_Remote.AdventureWorks2012.HumanResources.Employee;  
GO  
```  
  
### <a name="c-creating-a-synonym-for-a-user-defined-function"></a>C. ユーザー定義関数に対してシノニムを作成する  
 次の例は、という名前の関数を作成`dbo.OrderDozen`ちょうど 1 ダース単位に注文の金額を増加します。 次に、シノニム `dbo.CorrectOrder` を `dbo.OrderDozen` 関数に対して作成します。  
  
```  
-- Creating the dbo.OrderDozen function  
CREATE FUNCTION dbo.OrderDozen (@OrderAmt int)  
RETURNS int  
WITH EXECUTE AS CALLER  
AS  
BEGIN  
IF @OrderAmt % 12 <> 0  
BEGIN  
    SET @OrderAmt +=  12 - (@OrderAmt % 12)  
END  
RETURN(@OrderAmt);  
END;  
GO  
  
-- Using the dbo.OrderDozen function  
DECLARE @Amt int;  
SET @Amt = 15;  
SELECT @Amt AS OriginalOrder, dbo.OrderDozen(@Amt) AS ModifiedOrder;  
  
-- Create a synonym dbo.CorrectOrder for the dbo.OrderDozen function.  
CREATE SYNONYM dbo.CorrectOrder  
FOR dbo.OrderDozen;  
GO  
  
-- Using the dbo.CorrectOrder synonym.  
DECLARE @Amt int;  
SET @Amt = 15;  
SELECT @Amt AS OriginalOrder, dbo.CorrectOrder(@Amt) AS ModifiedOrder;  
```  
  
## <a name="see-also"></a>参照  
 [DROP SYNONYM &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-synonym-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
