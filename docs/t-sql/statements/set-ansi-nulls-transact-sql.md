---
title: "[SET ANSI_NULLS] (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/04/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_ANSI_NULLS_TSQL
- ANSI_NULLS
- SET ANSI_NULLS
- ANSI_NULLS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET ANSI_NULLS statement
- not equal to operator (<>)
- ANSI_NULLS option
- equals operator (=)
- null values [SQL Server], comparison operators
- comparison operators [SQL Server], null values
ms.assetid: aae263ef-a3c7-4dae-80c2-cc901e48c755
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: a6ef51bb13ae7372175a390a3d8c5509550a3ad1
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="set-ansinulls-transact-sql"></a>SET ANSI_NULLS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で = (等号) 比較演算子と <> (不等号) 比較演算子を NULL 値に対して使用した場合の ISO 準拠動作を指定します。  
  
> [!IMPORTANT]  
>  将来のバージョンで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ANSI_NULLS になり、オプションを OFF に明示的に設定するアプリケーションでエラーが発生します。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

## <a name="syntax"></a>構文

```
-- Syntax for SQL Server

SET ANSI_NULLS { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse

SET ANSI_NULLS ON
```

## <a name="remarks"></a>解説  
 SET ANSI_NULLS が ON、WHERE を使用する SELECT ステートメントの場合*column_name* = **NULL**内の null 値がある場合でもゼロ行を返します*column_name*です。 WHERE を使用する SELECT ステートメント*column_name* <> **NULL**で null 以外の値がある場合でもゼロ行を返します*column_name*です。  
  
 SET ANSI_NULLS が OFF の場合は、= (等号) 比較演算および <> (不等号) 比較演算の実行結果に、ISO 標準が適用されません。 WHERE を使用する SELECT ステートメント*column_name* = **NULL**に null 値を持つ行が返されます*column_name*です。 WHERE を使用する SELECT ステートメント*column_name* <> **NULL**を列に null 以外の値を持つ行を返します。 WHERE を使用する SELECT ステートメントも、 *column_name* <> *XYZ_value*れていないすべての行を返します*XYZ_value*が NULL でないとします。  
  
 SET ANSI_NULLS が ON に設定されていると、NULL 値に対するすべての比較は UNKNOWN に評価されます。 SET ANSI_NULLS が OFF に設定されていて、データ値が NULL の場合は、NULL 値に対するすべてのデータ比較は TRUE に評価されます。 SET ANSI_NULLS が指定されていない場合は、現在のデータベースの ANSI_NULLS オプションの設定が適用されます。 ANSI_NULLS データベース オプションの詳細については、次を参照してください。 [ALTER DATABASE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql.md)  
  
 比較のオペランドの 1 つが NULL またはリテラル NULL のいずれかの変数であるとき、SET ANSI_NULLS が ON の場合のみ比較に影響します。 比較の両側が列または複合式の場合は、この設定は比較に影響しません。  
  
 スクリプトが意図どおりに動作するようにするには、ANSI_NULLS データベース オプションや SET ANSI_NULLS の設定とは無関係に、NULL 値を含む可能性のある比較で、IS NULL と IS NOT NULL を使用するようにしてください。  
  
 分散クエリを実行する際には、SET ANSI_NULLS を ON に設定してください。  
  
 計算列やインデックス付きビューのインデックスを作成または変更するときには、SET ANSI_NULLS を ON に設定する必要があります。 SET ANSI_NULLS が OFF の場合、計算列にインデックスが設定されているテーブルやインデックス付きビューにおける CREATE、UPDATE、INSERT、および DELETE のステートメントはいずれも失敗します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]必要な値に違反しているすべての SET オプションの一覧を示すエラーを返します。 また、実行すると、SELECT ステートメントでは、SET ANSI_NULLS を OFF 場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]計算列やビュー上のインデックス値を無視し、テーブルまたはビューには、そのようなインデックスが存在しなかった場合、select 操作を解決します。  
  
> [!NOTE]  
>  ANSI_NULLS は、計算列およびインデックス付きビューにおいてインデックスを操作するときに、指定された値に設定する必要がある 7 つの SET オプションの中の 1 つです。 オプションの ANSI_PADDING、ANSI_WARNINGS、ARITHABORT、QUOTED_IDENTIFIER、および CONCAT_NULL_YIELDS_NULL も ON に設定する必要があります。また、NUMERIC_ROUNDABORT は OFF に設定する必要があります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB Provider for[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続するときに、ON に ANSI_NULLS を自動的に設定します。 この設定は、ODBC データ ソースまたは ODBC 接続属性で構成でき、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する前にアプリケーションの内部で設定される OLE DB 接続プロパティでも構成できます。 SET ANSI_NULLS の既定値は OFF です。  
  
 SET ANSI_DEFAULTS が ON の場合には、SET ANSI_NULLS は有効 (ON) になります。  
  
 SET ANSI_NULLS は、解析時ではなく実行時に設定されます。  
  
 この設定の現在の設定を表示するには、次のクエリを実行します。
  
```  
DECLARE @ANSI_NULLS VARCHAR(3) = 'OFF';  
IF ( (32 & @@OPTIONS) = 32 ) SET @ANSI_NULLS = 'ON';  
SELECT @ANSI_NULLS AS ANSI_NULLS;  
  
```  
  
## <a name="permissions"></a>Permissions  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、等号 (`=`) と不等号 (`<>`) と比較する比較演算子`NULL`と、テーブル内の null 以外の値。 例では、ことも示しています`IS NULL`は影響しません、`SET ANSI_NULLS`設定します。  
  
```  
-- Create table t1 and insert values.  
CREATE TABLE dbo.t1 (a INT NULL);  
INSERT INTO dbo.t1 values (NULL),(0),(1);  
GO  
  
-- Print message and perform SELECT statements.  
PRINT 'Testing default setting';  
DECLARE @varname int;   
SET @varname = NULL;  
  
SELECT a  
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- SET ANSI_NULLS to ON and test.  
PRINT 'Testing ANSI_NULLS ON';  
SET ANSI_NULLS ON;  
GO  
DECLARE @varname int;  
SET @varname = NULL  
  
SELECT a   
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- SET ANSI_NULLS to OFF and test.  
PRINT 'Testing SET ANSI_NULLS OFF';  
SET ANSI_NULLS OFF;  
GO  
DECLARE @varname int;  
SET @varname = NULL;  
SELECT a   
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- Drop table t1.  
DROP TABLE dbo.t1;  
  
```  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/sessionproperty-transact-sql.md)   
 [= (& a) #40 です。等しい &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/equals-transact-sql.md)   
 [もし。。。ELSE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/if-else-transact-sql.md)   
 [(& m); 60 &#62;。&#40;です。等しい &#41; されません。&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/not-equal-to-transact-sql-traditional.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [[SET ansi_defaults] &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [ここで &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)   
 [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  
  
  
