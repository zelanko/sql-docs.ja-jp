---
title: "GROUPING_ID (TRANSACT-SQL) |Microsoft ドキュメント"
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
- GROUPING_ID_TSQL
- GROUPING_ID
dev_langs:
- TSQL
helpviewer_keywords:
- GROUP BY clause, GROUPING_ID
- GROUPING_ID function
ms.assetid: c1050658-b19f-42ee-9a05-ecd6a73b896c
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5cb5b4ba4925661797760e906e36ddcec1526747
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="groupingid-transact-sql"></a>GROUPING_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  グループ化のレベルを計算する関数を指定します。 GROUPING_ID は、選択でのみ使用できます\<選択 > リスト、HAVING、または GROUP BY が指定されている場合は、ORDER BY 句。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
GROUPING_ID ( <column_expression>[ ,...n ] )  
```  
  
## <a name="arguments"></a>引数  
 \<column_expression >  
 *Column_expression*で、 [GROUP BY](../../t-sql/queries/select-group-by-transact-sql.md)句。  
  
## <a name="return-type"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>解説  
 GROUPING_ID \<column_expression > GROUP BY リスト内の式と一致する必要があります。 たとえば、DATEPART でグループ化する場合 (yyyy, \<*列名*>)、GROUPING_ID を使用して (DATEPART (yyyy、 \<*列名*>));によってグループ化する場合、または\<*列名*>、GROUPING_ID を使用して (\<*列名*>)。  
  
## <a name="comparing-groupingid--to-grouping-"></a>GROUPING_ID () と GROUPING () の比較  
 GROUPING_ID (\<column_expression > [ **、**. *n*  ])、グループ化のと同等の入力 (\<column_expression >) 1 と 0 の文字列として各出力行では、その列リスト内の各列の戻り値。 GROUPING_ID は、その文字列を基数 2 の数値として解釈し、同等の整数を返します。 たとえば、次のステートメントについて考えてみます。`SELECT a, b, c, SUM(d),``GROUPING_ID(a,b,c)``FROM T GROUP BY <group by list>`です。 GROUPING_ID () の入力値と出力値を次の表に示します。  
  
|集計列|GROUPING_ID (a, b, c) の入力 = GROUPING(a) + GROUPING(b) + GROUPING(c)|GROUPING_ID () の出力|  
|------------------------|---------------------------------------------------------------------------------------|------------------------------|  
|`a`|`100`|`4`|  
|`b`|`010`|`2`|  
|`c`|`001`|`1`|  
|`ab`|`110`|`6`|  
|`ac`|`101`|`5`|  
|`bc`|`011`|`3`|  
|`abc`|`111`|`7`|  
  
## <a name="technical-definition-of-groupingid-"></a>GROUPING_ID () の技術的な定義  
 各 GROUPING_ID 引数は、GROUP BY リストの要素でなければなりません。 GROUPING_ID () を返します、**整数**ビットマップが最下位 N ビットが点灯している可能性があります。 点灯した**ビット**対応する引数が指定した出力行のグループ化列ではないことを示します。 最も順位が低い**ビット**N、および、N-1 引数に対応<sup>th</sup>下位**ビット**引数 1 に対応します。  
  
## <a name="groupingid--equivalents"></a>GROUPING_ID () の対応  
 単一グループ クエリの場合は、グループ化 (\<column_expression >) は GROUPING_ID (\<column_expression >)、し、両方は 0 を返します。  
  
 たとえば、次のステートメントは互いに対応しています。  
  
 ステートメント a:  
  
```  
SELECT GROUPING_ID(A,B)  
FROM T   
GROUP BY CUBE(A,B)   
```  
  
 ステートメント b:  
  
```  
SELECT 3 FROM T GROUP BY ()  
UNION ALL  
SELECT 1 FROM T GROUP BY A  
UNION ALL  
SELECT 2 FROM T GROUP BY B  
UNION ALL  
SELECT 0 FROM T GROUP BY A,B  
```  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-groupingid-to-identify-grouping-levels"></a>A. GROUPING_ID を使用してグループ化レベルを識別する  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースの `Name` と `Title` ごとの従業員数、`Name,` ごとの従業員数、および会社の合計従業員数が返されます。 `GROUPING_ID()`内の各行の値の作成に使用される、`Title`集計レベルを識別する列。  
  
```  
SELECT D.Name  
    ,CASE   
    WHEN GROUPING_ID(D.Name, E.JobTitle) = 0 THEN E.JobTitle  
    WHEN GROUPING_ID(D.Name, E.JobTitle) = 1 THEN N'Total: ' + D.Name   
    WHEN GROUPING_ID(D.Name, E.JobTitle) = 3 THEN N'Company Total:'  
        ELSE N'Unknown'  
    END AS N'Job Title'  
    ,COUNT(E.BusinessEntityID) AS N'Employee Count'  
FROM HumanResources.Employee E  
    INNER JOIN HumanResources.EmployeeDepartmentHistory DH  
        ON E.BusinessEntityID = DH.BusinessEntityID  
    INNER JOIN HumanResources.Department D  
        ON D.DepartmentID = DH.DepartmentID       
WHERE DH.EndDate IS NULL  
    AND D.DepartmentID IN (12,14)  
GROUP BY ROLLUP(D.Name, E.JobTitle);  
```  
  
### <a name="b-using-groupingid-to-filter-a-result-set"></a>B. GROUPING_ID を使用して結果セットをフィルター処理する  
  
#### <a name="simple-example"></a>簡単な例  
 役職ごとの従業員数が含まれた行のみを返すには、次のコードの [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースの `HAVING GROUPING_ID(D.Name, E.JobTitle); = 0` からコメント文字を削除します。 部門ごとの従業員数が含まれた行のみを返すには、`HAVING GROUPING_ID(D.Name, E.JobTitle) = 1;` からコメント文字を削除します。  
  
```  
SELECT D.Name  
    ,E.JobTitle  
    ,GROUPING_ID(D.Name, E.JobTitle) AS 'Grouping Level'  
    ,COUNT(E.BusinessEntityID) AS N'Employee Count'  
FROM HumanResources.Employee AS E  
    INNER JOIN HumanResources.EmployeeDepartmentHistory AS DH  
        ON E.BusinessEntityID = DH.BusinessEntityID  
    INNER JOIN HumanResources.Department AS D  
        ON D.DepartmentID = DH.DepartmentID       
WHERE DH.EndDate IS NULL  
    AND D.DepartmentID IN (12,14)  
GROUP BY ROLLUP(D.Name, E.JobTitle)  
--HAVING GROUPING_ID(D.Name, E.JobTitle) = 0; --All titles  
--HAVING GROUPING_ID(D.Name, E.JobTitle) = 1; --Group by Name;  
```  
  
 フィルター処理していない結果セットは、次のようになります。  
  
|名前|Title|グループ化レベル|従業員数|名前|  
|----------|-----------|--------------------|--------------------|----------|  
|文書コントロール|コントロール スペシャリスト|0|2|文書コントロール|  
|文書コントロール|文書コントロール アシスタント|0|2|文書コントロール|  
|文書コントロール|文書コントロール マネージャー|0|1|文書コントロール|  
|文書コントロール|NULL|1|5|文書コントロール|  
|設備およびメンテナンス|設備管理アシスタント|0|1|設備およびメンテナンス|  
|設備およびメンテナンス|設備マネージャー|0|1|設備およびメンテナンス|  
|設備およびメンテナンス|管理人|0|4|設備およびメンテナンス|  
|設備およびメンテナンス|メンテナンス スーパーバイザー|0|1|設備およびメンテナンス|  
|設備およびメンテナンス|NULL|1|7|設備およびメンテナンス|  
|NULL|NULL|3|12|NULL|  
  
#### <a name="complex-example"></a>複雑な例  
 次の例では、`GROUPING_ID()` を使用して、複数のグループ化レベルが含まれた結果セットをグループ化レベルでフィルター処理します。 これと同様のコードを使用すると、複数のグループ化レベルがあるビューとストアド プロシージャを作成できます。このストアド プロシージャは、ビューをグループ化レベルでフィルター処理するパラメーターを渡すことによって、ビューを呼び出します。 この例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
DECLARE @Grouping nvarchar(50);  
DECLARE @GroupingLevel smallint;  
SET @Grouping = N'CountryRegionCode Total';  
  
SELECT @GroupingLevel = (  
    CASE @Grouping  
        WHEN N'Grand Total'             THEN 15  
        WHEN N'SalesPerson Total'       THEN 14  
        WHEN N'Store Total'             THEN 13  
        WHEN N'Store SalesPerson Total' THEN 12  
        WHEN N'CountryRegionCode Total' THEN 11  
        WHEN N'Group Total'             THEN 7  
        ELSE N'Unknown'  
    END);  
  
SELECT   
    T.[Group]  
    ,T.CountryRegionCode  
    ,S.Name AS N'Store'  
    ,(SELECT P.FirstName + ' ' + P.LastName   
        FROM Person.Person AS P   
        WHERE P.BusinessEntityID = H.SalesPersonID)  
        AS N'Sales Person'  
    ,SUM(TotalDue)AS N'TotalSold'  
    ,CAST(GROUPING(T.[Group])AS char(1)) +   
        CAST(GROUPING(T.CountryRegionCode)AS char(1)) +   
        CAST(GROUPING(S.Name)AS char(1)) +   
        CAST(GROUPING(H.SalesPersonID)AS char(1))   
        AS N'GROUPING base-2'  
    ,GROUPING_ID((T.[Group])  
        ,(T.CountryRegionCode),(S.Name),(H.SalesPersonID)  
        ) AS N'GROUPING_ID'  
    ,CASE   
        WHEN GROUPING_ID(  
            (T.[Group]),(T.CountryRegionCode)  
            ,(S.Name),(H.SalesPersonID)  
            ) = 15 THEN N'Grand Total'  
        WHEN GROUPING_ID(  
            (T.[Group]),(T.CountryRegionCode)  
            ,(S.Name),(H.SalesPersonID)  
            ) = 14 THEN N'SalesPerson Total'  
        WHEN GROUPING_ID(  
            (T.[Group]),(T.CountryRegionCode)  
            ,(S.Name),(H.SalesPersonID)  
            ) = 13 THEN N'Store Total'  
        WHEN GROUPING_ID(  
            (T.[Group]),(T.CountryRegionCode)  
            ,(S.Name),(H.SalesPersonID)  
            ) = 12 THEN N'Store SalesPerson Total'  
        WHEN GROUPING_ID(  
            (T.[Group]),(T.CountryRegionCode)  
            ,(S.Name),(H.SalesPersonID)  
            ) = 11 THEN N'CountryRegionCode Total'  
        WHEN GROUPING_ID(  
            (T.[Group]),(T.CountryRegionCode)  
            ,(S.Name),(H.SalesPersonID)  
            ) =  7 THEN N'Group Total'  
        ELSE N'Error'  
        END AS N'Level'  
FROM Sales.Customer AS C  
    INNER JOIN Sales.Store AS S  
        ON C.StoreID  = S.BusinessEntityID   
    INNER JOIN Sales.SalesTerritory AS T  
        ON C.TerritoryID  = T.TerritoryID   
    INNER JOIN Sales.SalesOrderHeader AS H  
        ON C.CustomerID = H.CustomerID  
GROUP BY GROUPING SETS ((S.Name,H.SalesPersonID)  
    ,(H.SalesPersonID),(S.Name)  
    ,(T.[Group]),(T.CountryRegionCode),()  
    )  
HAVING GROUPING_ID(  
    (T.[Group]),(T.CountryRegionCode),(S.Name),(H.SalesPersonID)  
    ) = @GroupingLevel  
ORDER BY   
    GROUPING_ID(S.Name,H.SalesPersonID),GROUPING_ID((T.[Group])  
    ,(T.CountryRegionCode)  
    ,(S.Name)  
    ,(H.SalesPersonID))ASC;  
```  
  
### <a name="c-using-groupingid--with-rollup-and-cube-to-identify-grouping-levels"></a>C. GROUPING_ID () を ROLLUP および CUBE と共に使用してグループ化レベルを識別する  
 コードの次の例を使用して表示する`GROUPING()`を計算する、`Bit Vector(base-2)`列です。 `GROUPING_ID()`対応する計算に使用`Integer Equivalent`列です。 `GROUPING_ID()` 関数の列順序は、`GROUPING()` 関数によって連結された列の列順序の逆になります。  
  
 これらの例で`GROUPING_ID()`内の各行の値の作成に使用される、`Grouping Level`列をグループ化レベルを識別します。 常に 1 (0 1、2、... で始まる整数の連続する一覧がグループ化レベルではありません。*n*).  
  
> [!NOTE]  
>  GROUPING と GROUPING_ID は、結果セットをフィルター処理するために HAVING 句で使用できます。  
  
#### <a name="rollup-example"></a>ROLLUP の例  
 この例では、すべてのグループ化レベルが次の CUBE 例の場合と同様に表示されるわけではありません。 `ROLLUP` リストの列の順序が変更された場合は、`Grouping Level` 列のレベル値も変更する必要があります。 この例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
SELECT DATEPART(yyyy,OrderDate) AS N'Year'  
    ,DATEPART(mm,OrderDate) AS N'Month'  
    ,DATEPART(dd,OrderDate) AS N'Day'  
    ,SUM(TotalDue) AS N'Total Due'  
    ,CAST(GROUPING(DATEPART(dd,OrderDate))AS char(1)) +   
        CAST(GROUPING(DATEPART(mm,OrderDate))AS char(1)) +   
        CAST(GROUPING(DATEPART(yyyy,OrderDate))AS char(1))   
     AS N'Bit Vector(base-2)'  
    ,GROUPING_ID(DATEPART(yyyy,OrderDate)  
        ,DATEPART(mm,OrderDate)  
        ,DATEPART(dd,OrderDate))   
        AS N'Integer Equivalent'  
    ,CASE  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 0 THEN N'Year Month Day'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 1 THEN N'Year Month'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 2 THEN N'not used'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 3 THEN N'Year'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 4 THEN N'not used'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 5 THEN N'not used'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 6 THEN N'not used'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 7 THEN N'Grand Total'  
    ELSE N'Error'  
    END AS N'Grouping Level'  
FROM Sales.SalesOrderHeader  
WHERE DATEPART(yyyy,OrderDate) IN(N'2007',N'2008')  
    AND DATEPART(mm,OrderDate) IN(1,2)  
    AND DATEPART(dd,OrderDate) IN(1,2)  
GROUP BY ROLLUP(DATEPART(yyyy,OrderDate)  
        ,DATEPART(mm,OrderDate)  
        ,DATEPART(dd,OrderDate))  
ORDER BY GROUPING_ID(DATEPART(mm,OrderDate)  
    ,DATEPART(yyyy,OrderDate)  
    ,DATEPART(dd,OrderDate)  
    )  
    ,DATEPART(yyyy,OrderDate)  
    ,DATEPART(mm,OrderDate)  
    ,DATEPART(dd,OrderDate);  
```  
  
 部分的な結果セットを次に示します。  
  
|年|Month|日|精算額|ビット ベクター (基数 2)|等価の整数|グループ化レベル|  
|----------|-----------|---------|---------------|----------------------------|------------------------|--------------------|  
|2007|1|1|1497452.6066|000|0|年月日|  
|2007|1|2|21772.3494|000|0|年月日|  
|2007|2|1|2705653.5913|000|0|年月日|  
|2007|2|2|21684.4068|000|0|年月日|  
|2008|1|1|1908122.0967|000|0|年月日|  
|2008|1|2|46458.0691|000|0|年月日|  
|2008|2|1|3108771.9729|000|0|年月日|  
|2008|2|2|54598.5488|000|0|年月日|  
|2007|1|NULL|1519224.956|100|1|年月|  
|2007|2|NULL|2727337.9981|100|1|年月|  
|2008|1|NULL|1954580.1658|100|1|年月|  
|2008|2|NULL|3163370.5217|100|1|年月|  
|2007|NULL|NULL|4246562.9541|110|3|年|  
|2008|NULL|NULL|5117950.6875|110|3|年|  
|NULL|NULL|NULL|9364513.6416|111|7|総計|  
  
#### <a name="cube-example"></a>CUBE の例  
 この例では、`GROUPING_ID()` 関数を使用して、グループ化レベルを識別する値を `Grouping Level` 列の各行に対して作成します。  
  
 異なり`ROLLUP`前の例では、`CUBE`すべてのグループ化レベルを出力します。 `CUBE` リストの列の順序が変更された場合は、`Grouping Level` 列のレベル値も変更する必要があります。 この例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース  
  
```  
SELECT DATEPART(yyyy,OrderDate) AS N'Year'  
    ,DATEPART(mm,OrderDate) AS N'Month'  
    ,DATEPART(dd,OrderDate) AS N'Day'  
    ,SUM(TotalDue) AS N'Total Due'  
    ,CAST(GROUPING(DATEPART(dd,OrderDate))AS char(1)) +   
        CAST(GROUPING(DATEPART(mm,OrderDate))AS char(1)) +   
        CAST(GROUPING(DATEPART(yyyy,OrderDate))AS char(1))   
        AS N'Bit Vector(base-2)'  
    ,GROUPING_ID(DATEPART(yyyy,OrderDate)  
        ,DATEPART(mm,OrderDate)  
        ,DATEPART(dd,OrderDate))   
        AS N'Integer Equivalent'  
    ,CASE  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)  
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 0 THEN N'Year Month Day'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)   
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 1 THEN N'Year Month'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)   
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 2 THEN N'Year Day'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)   
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 3 THEN N'Year'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)   
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 4 THEN N'Month Day'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)   
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 5 THEN N'Month'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)   
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 6 THEN N'Day'  
        WHEN GROUPING_ID(DATEPART(yyyy,OrderDate)   
            ,DATEPART(mm,OrderDate),DATEPART(dd,OrderDate)  
            ) = 7 THEN N'Grand Total'  
    ELSE N'Error'  
    END AS N'Grouping Level'  
FROM Sales.SalesOrderHeader  
WHERE DATEPART(yyyy,OrderDate) IN(N'2007',N'2008')  
    AND DATEPART(mm,OrderDate) IN(1,2)  
    AND DATEPART(dd,OrderDate) IN(1,2)  
GROUP BY CUBE(DATEPART(yyyy,OrderDate)  
    ,DATEPART(mm,OrderDate)  
    ,DATEPART(dd,OrderDate))  
ORDER BY GROUPING_ID(DATEPART(yyyy,OrderDate)  
    ,DATEPART(mm,OrderDate)  
    ,DATEPART(dd,OrderDate)  
    )  
    ,DATEPART(yyyy,OrderDate)  
    ,DATEPART(mm,OrderDate)  
    ,DATEPART(dd,OrderDate);  
```  
  
 部分的な結果セットを次に示します。  
  
|年|Month|日|精算額|ビット ベクター (基数 2)|等価の整数|グループ化レベル|  
|----------|-----------|---------|---------------|----------------------------|------------------------|--------------------|  
|2007|1|1|1497452.6066|000|0|年月日|  
|2007|1|2|21772.3494|000|0|年月日|  
|2007|2|1|2705653.5913|000|0|年月日|  
|2007|2|2|21684.4068|000|0|年月日|  
|2008|1|1|1908122.0967|000|0|年月日|  
|2008|1|2|46458.0691|000|0|年月日|  
|2008|2|1|3108771.9729|000|0|年月日|  
|2008|2|2|54598.5488|000|0|年月日|  
|2007|1|NULL|1519224.956|100|1|年月|  
|2007|2|NULL|2727337.9981|100|1|年月|  
|2008|1|NULL|1954580.1658|100|1|年月|  
|2008|2|NULL|3163370.5217|100|1|年月|  
|2007|NULL|1|4203106.1979|010|2|年日|  
|2007|NULL|2|43456.7562|010|2|年日|  
|2008|NULL|1|5016894.0696|010|2|年日|  
|2008|NULL|2|101056.6179|010|2|年日|  
|2007|NULL|NULL|4246562.9541|110|3|年|  
|2008|NULL|NULL|5117950.6875|110|3|年|  
|NULL|1|1|3405574.7033|001|4|月日|  
|NULL|1|2|68230.4185|001|4|月日|  
|NULL|2|1|5814425.5642|001|4|月日|  
|NULL|2|2|76282.9556|001|4|月日|  
|NULL|1|NULL|3473805.1218|101|5|Month|  
|NULL|2|NULL|5890708.5198|101|5|Month|  
|NULL|NULL|1|9220000.2675|011|6|日|  
|NULL|NULL|2|144513.3741|011|6|日|  
|NULL|NULL|NULL|9364513.6416|111|7|総計|  
  
## <a name="see-also"></a>参照  
 [グループ化と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/grouping-transact-sql.md)   
 [GROUP BY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-group-by-transact-sql.md)  
  
  
