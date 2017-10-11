---
title: "NTILE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NTILE_TSQL
- NTILE
dev_langs:
- TSQL
helpviewer_keywords:
- distributing rows
- groups [SQL Server], row distribution
- row distribution [SQL Server]
- NTILE function
ms.assetid: 1c364511-d72a-4789-8efa-3cf2a1f6b791
caps.latest.revision: 63
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7cb3ab21f1707c1af1c689e438e9d6ead291dcc4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="ntile-transact-sql"></a>NTILE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  順序付けられたパーティションの行を、指定した数のグループに分散します。 グループには、1 から始まる番号が付けられます。 行ごとに、NTILE はその行が属しているグループの番号を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
NTILE (integer_expression) OVER ( [ <partition_by_clause> ] < order_by_clause > )  
```  
  
## <a name="arguments"></a>引数  
 *integer_expression*  
 各パーティションを分割するグループの数を表す正の整数定数式を指定します。 *あれば、任意*型でも**int**、または**bigint**です。  
  
 \<partition_by_clause >  
 によって生成される結果セットに分割、 [FROM](../../t-sql/queries/from-transact-sql.md)句のパーティション関数が適用されます。 PARTITION BY の構文を参照してください。 [OVER 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
 \<order_by_clause >  
 NTILE 値がパーティション内の行に割り当てられる順序を決定します。 整数は、列を表すことができないときに、 \<order_by_clause > は、順位付け関数で使用します。  
  
## <a name="return-types"></a>戻り値の型  
 **bigint**  
  
## <a name="remarks"></a>解説  
 パーティション内の行の数がで割り切れるかどうか*であれば、任意*、2 つのサイズが異なる 1 つのメンバーによってグループが生成されます。 OVER 句で指定される順序では、大きいグループが小さいグループよりも前になります。 たとえば、行の総数が 53 でグループの数が 5 の場合、最初の 3 つのグループに 11 行が割り当てられ、残りの 2 つのグループにはそれぞれ 10 行が割り当てられます。 一方、行の総数がグループの数で割り切れる場合、行はそれらのグループに均等に割り当てられます。 たとえば、行の総数が 50 で、5 つのグループがある場合、各グループに 10 行ずつ割り当てられます。  
  
 NTILE は非決定的です。 詳細については、「 [決定的関数と非決定的関数](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dividing-rows-into-groups"></a>A. 行をグループに分割する  
 次の例では、年度累計の売上高に基づいて、行を 4 つの従業員グループに分割します。 行の総数がグループの数で割り切れないため、最初の 2 つのグループに 4 つの行が割り当てられ、残りのグループにはそれぞれ 3 つの行が割り当てられます。  
  
```  
USE AdventureWorks2012;   
GO  
SELECT p.FirstName, p.LastName  
    ,NTILE(4) OVER(ORDER BY SalesYTD DESC) AS Quartile  
    ,CONVERT(nvarchar(20),s.SalesYTD,1) AS SalesYTD  
    , a.PostalCode  
FROM Sales.SalesPerson AS s   
INNER JOIN Person.Person AS p   
    ON s.BusinessEntityID = p.BusinessEntityID  
INNER JOIN Person.Address AS a   
    ON a.AddressID = p.BusinessEntityID  
WHERE TerritoryID IS NOT NULL   
    AND SalesYTD <> 0;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
FirstName      LastName              Quartile  SalesYTD       PostalCode  
-------------  --------------------- --------- -------------- ----------  
Linda          Mitchell              1         4,251,368.55   98027  
Jae            Pak                   1         4,116,871.23   98055  
Michael        Blythe                1         3,763,178.18   98027  
Jillian        Carson                1         3,189,418.37   98027  
Ranjit         Varkey Chudukatil     2         3,121,616.32   98055  
José           Saraiva               2         2,604,540.72   98055  
Shu            Ito                   2         2,458,535.62   98055  
Tsvi           Reiter                2         2,315,185.61   98027  
Rachel         Valdez                3         1,827,066.71   98055  
Tete           Mensa-Annan           3         1,576,562.20   98055  
David          Campbell              3         1,573,012.94   98055  
Garrett        Vargas                4         1,453,719.47   98027  
Lynn           Tsoflias              4         1,421,810.92   98055  
Pamela         Ansman-Wolfe          4         1,352,577.13   98027  

(14 row(s) affected)  
```  
  
### <a name="b-dividing-the-result-set-by-using-partition-by"></a>B. PARTITION BY を使用して結果セットを分割する  
 次の例では追加、`PARTITION BY`例 A のコードに渡す引数行が最初にパーティション分割`PostalCode`ごとに 4 つのグループに分割し、`PostalCode`です。 この例では、変数もを宣言`@NTILE_Var`の値を指定する変数を使用して、*であれば、任意*パラメーター。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @NTILE_Var int = 4;  
  
SELECT p.FirstName, p.LastName  
    ,NTILE(@NTILE_Var) OVER(PARTITION BY PostalCode ORDER BY SalesYTD DESC) AS Quartile  
    ,CONVERT(nvarchar(20),s.SalesYTD,1) AS SalesYTD  
    ,a.PostalCode  
FROM Sales.SalesPerson AS s   
INNER JOIN Person.Person AS p   
    ON s.BusinessEntityID = p.BusinessEntityID  
INNER JOIN Person.Address AS a   
    ON a.AddressID = p.BusinessEntityID  
WHERE TerritoryID IS NOT NULL   
    AND SalesYTD <> 0;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
FirstName    LastName             Quartile SalesYTD      PostalCode  
------------ -------------------- -------- ------------  ----------  
Linda        Mitchell             1        4,251,368.55  98027  
Michael      Blythe               1        3,763,178.18  98027  
Jillian      Carson               2        3,189,418.37  98027  
Tsvi         Reiter               2        2,315,185.61  98027  
Garrett      Vargas               3        1,453,719.47  98027  
Pamela       Ansman-Wolfe         4        1,352,577.13  98027  
Jae          Pak                  1        4,116,871.23  98055  
Ranjit       Varkey Chudukatil    1        3,121,616.32  98055  
José         Saraiva              2        2,604,540.72  98055  
Shu          Ito                  2        2,458,535.62  98055  
Rachel       Valdez               3        1,827,066.71  98055  
Tete         Mensa-Annan          3        1,576,562.20  98055  
David        Campbell             4        1,573,012.94  98055  
Lynn         Tsoflias             4        1,421,810.92  98055  
  
(14 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-dividing-rows-into-groups"></a>C. 行をグループに分割する  
 次の例では、NTILE 関数を使用して、次の 4 つのグループごとに、割り当てられている販売ノルマ 2003 年の販売員のセットを分割します。 行の総数がグループの数で割り切れるにないため、最初のグループの 5 行あり、残りのグループを持っている 4 つの行。  
  
```  
-- Uses AdventureWorks  
  
SELECT e.LastName, NTILE(4) OVER(ORDER BY SUM(SalesAmountQuota) DESC) AS Quartile,  
       CONVERT (varchar(13), SUM(SalesAmountQuota), 1) AS SalesQuota  
FROM dbo.DimEmployee AS e   
INNER JOIN dbo.FactSalesQuota AS sq   
    ON e.EmployeeKey = sq.EmployeeKey  
WHERE sq.CalendarYear = 2003  
    AND SalesTerritoryKey IS NOT NULL AND SalesAmountQuota <> 0  
GROUP BY e.LastName  
ORDER BY Quartile, e.LastName;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
LastName          Quartile SalesYTD  
----------------- -------- ------------`  
Blythe            1        4,716,000.00  
Carson            1        4,350,000.00  
Mitchell          1        4,682,000.00  
Pak               1        5,142,000.00  
Varkey Chudukatil 1        2,940,000.00  
Ito               2        2,644,000.00  
Saraiva           2        2,293,000.00  
Vargas            2        1,617,000.00  
Ansman-Wolfe      3        1,183,000.00  
Campbell          3        1,438,000.00  
Mensa-Annan       3        1,481,000.00  
Valdez            3        1,294,000.00  
Abbas             4          172,000.00  
Albert            4          651,000.00  
Jiang             4          544,000.00  
Tsoflias          4          867,000.00
```  
  
### <a name="d-dividing-the-result-set-by-using-partition-by"></a>D. PARTITION BY を使用して結果セットを分割する  
 次の例は、例 A のコードに PARTITION BY 引数を追加します。行が最初にパーティション分割`SalesTerritoryCountry`ごとに 2 つのグループに分割し、`SalesTerritoryCountry`です。 OVER 句内の ORDER BY、NTILE を orders、ORDER BY、SELECT ステートメントの結果セットを並べ替えますことを確認します。  
  
```  
-- Uses AdventureWorks  
  
SELECT e.LastName, NTILE(2) OVER(PARTITION BY e.SalesTerritoryKey ORDER BY SUM(SalesAmountQuota) DESC) AS Quartile,  
       CONVERT (varchar(13), SUM(SalesAmountQuota), 1) AS SalesQuota  
   ,st.SalesTerritoryCountry  
FROM dbo.DimEmployee AS e   
INNER JOIN dbo.FactSalesQuota AS sq   
    ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory AS st  
    ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE sq.CalendarYear = 2003  
GROUP BY e.LastName,e.SalesTerritoryKey,st.SalesTerritoryCountry  
ORDER BY st.SalesTerritoryCountry, Quartile;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
LastName          Quartile SalesYTD       SalesTerritoryCountry  
----------------- -------- -------------- ------------------  
Tsoflias          1         867,000.00     Australia  
Saraiva           1        2,293,000.00    Canada  
Varkey Chudukatil 1        2,940,000.00    France  
Valdez            1        1,294,000.00    Germany  
Alberts           1          651,000.00    NA  
Jiang             1          544,000.00    NA  
Pak               1        5,142,000.00    United Kingdom  
Mensa-Annan       1        1,481,000.00    United States  
Campbell          1        1,438,000.00    United States  
Reiter            1        2,768,000.00    United States  
Blythe            1        4,716,000.00    United States  
Carson            1        4,350,000.00     United States  
Mitchell          1        4,682,000.00     United States  
Vargas            2        1,617,000.00     Canada  
Abbas             2          172,000.00     NA  
Ito               2        2,644,000.00     United States  
Ansman-Wolfe      2        1,183,000.00     United States
```  
  
## <a name="see-also"></a>参照  
 [ランクと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/rank-transact-sql.md)   
 [DENSE_RANK & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/dense-rank-transact-sql.md)   
 [ROW_NUMBER & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/row-number-transact-sql.md)   
 [順位付け関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/ranking-functions-transact-sql.md)   
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
  



