---
title: "LEN (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/03/2015
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
- LEN
- LEN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- LEN function
- characters [SQL Server], number of
- number of characters
ms.assetid: fa20fee4-884d-4301-891a-c03e901345ae
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4f81bca5986279d53ea1fce44c50ab400ad03d50
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="len-transact-sql"></a>LEN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定された文字列式の、末尾の空白を除いた文字数を返します。  
  
> [!NOTE]  
>  式を表すために使用するバイト数を返すを使用して、 [DATALENGTH](../../t-sql/functions/datalength-transact-sql.md)関数。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
LEN ( string_expression )  
```  
  
## <a name="arguments"></a>引数  
 *string_expression*  
 文字列は、[式](../../t-sql/language-elements/expressions-transact-sql.md)に評価されます。 *string_expression*定数、変数、または文字またはバイナリ データのいずれかの列を指定できます。  
  
## <a name="return-types"></a>戻り値の型  
 **bigint**場合*式*は、 **varchar (max)**、 **nvarchar (max)**または**varbinary (max)**データ型です。それ以外の場合、 **int**です。  
  
 SC の照合順序を使用する場合、返される整数値では、UTF-16 サロゲート ペアが 1 文字としてカウントされます。 詳細については、「 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 Len 関数は、末尾の空白を除外します。 問題がある場合は、使用を検討して、 [DATALENGTH (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/datalength-transact-sql.md)を切り捨てるはありません、文字列関数。 Unicode 文字列を処理するには、DATALENGTH は文字の 2 倍の数を返します。 次の例では、末尾のスペースを持つ LEN および DATALENGTH を示します。  
  
```  
DECLARE @v1 varchar(40),  
    @v2 nvarchar(40);  
SELECT   
@v1 = 'Test of 22 characters ',   
@v2 = 'Test of 22 characters ';  
SELECT LEN(@v1) AS [varchar LEN] , DATALENGTH(@v1) AS [varchar DATALENGTH];  
SELECT LEN(@v2) AS [nvarchar LEN], DATALENGTH(@v2) AS [nvarchar DATALENGTH];  
  
```  
  
## <a name="examples"></a>使用例  
 次の例では、`FirstName` に居住する人の `Australia` の文字数とデータを選択します。 この例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
SELECT LEN(FirstName) AS Length, FirstName, LastName   
FROM Sales.vIndividualCustomer  
WHERE CountryRegionName = 'Australia';  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例は、列の文字の数を返します`FirstName`あり内にある従業員の姓と名`Australia`です。  
  
```  
-- Uses AdventureWorks  
  
SELECT DISTINCT LEN(FirstName) AS FNameLength, FirstName, LastName   
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.DimGeography AS g   
    ON e.SalesTerritoryKey = g.SalesTerritoryKey   
WHERE EnglishCountryRegionName = 'Australia';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
FNameLength  FirstName  LastName  
-----------  ---------  ---------------  
4            Lynn       Tsoflias
```  
  
## <a name="see-also"></a>参照  
 [DATALENGTH &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/datalength-transact-sql.md)   
 [Charindex 関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/charindex-transact-sql.md)  
 [PATINDEX &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/patindex-transact-sql.md)  
 [左と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/left-transact-sql.md)   
 [右 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/right-transact-sql.md)  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [文字列関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)   
  
  


