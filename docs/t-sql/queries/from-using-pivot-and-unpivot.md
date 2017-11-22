---
title: "PIVOT および UNPIVOT を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: PIVOT_TSQL
helpviewer_keywords:
- FROM clause, UNPIVOT operator
- unpivoting tables
- table pivoting [SQL Server]
- UNPIVOT operator
- crosstab query
- PIVOT operator
- rotating table-valued expressions
- pivoting tables
- FROM clause, PIVOT operator
- rotating columns
ms.assetid: 24ba54fc-98f7-4d35-8881-b5158aac1d66
caps.latest.revision: "35"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 4555a892c55ae8ef40e8fd0c3658412e3641d973
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="from---using-pivot-and-unpivot"></a>PIVOT および UNPIVOT を使用して - から
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  使用することができます、`PIVOT`と`UNPIVOT`関係演算子を別のテーブルにテーブル値式を変更します。 `PIVOT`出力では、複数の列に式で 1 つの列から一意の値にすることによって、テーブル値式を回転し、最終的な出力で必要な残りの列値に必要で集計を実行します。 `UNPIVOT`列の値にテーブル値式の列を回転して PIVOT 演算子の逆を実行します。  
  
 構文`PIVOT`提供は簡単で、それ以外の場合、複雑な一連の指定できる構文よりも読みやすく`SELECT...CASE`ステートメントです。 構文の詳細については`PIVOT`を参照してください[(TRANSACT-SQL) から](../../t-sql/queries/from-transact-sql.md)です。  
  
## <a name="syntax"></a>構文  
 次の構文を使用する方法の概要を示します、`PIVOT`演算子。  
  
```  
SELECT <non-pivoted column>,  
    [first pivoted column] AS <column name>,  
    [second pivoted column] AS <column name>,  
    ...  
    [last pivoted column] AS <column name>  
FROM  
    (<SELECT query that produces the data>)   
    AS <alias for the source query>  
PIVOT  
(  
    <aggregation function>(<column being aggregated>)  
FOR   
[<column that contains the values that will become column headers>]   
    IN ( [first pivoted column], [second pivoted column],  
    ... [last pivoted column])  
) AS <alias for the pivot table>  
<optional ORDER BY clause>;  
```  

## <a name="remarks"></a>解説  
内の列識別子、`UNPIVOT`句がカタログ照合順序に従います。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]、照合順序は常に`SQL_Latin1_General_CP1_CI_AS`です。 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]部分的包含データベースの照合順序は常に`Latin1_General_100_CI_AS_KS_WS_SC`です。 他の列では、collate 句に列を組み合わせた場合 (`COLLATE DATABASE_DEFAULT`) 競合を回避するために必要なです。  

  
## <a name="basic-pivot-example"></a>PIVOT の基本的な例  
 次のコード例では、4 行、2 列で構成されるテーブルを生成します。  
  
```  
USE AdventureWorks2014 ;  
GO  
SELECT DaysToManufacture, AVG(StandardCost) AS AverageCost   
FROM Production.Product  
GROUP BY DaysToManufacture;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 DaysToManufacture AverageCost
 ----------------- -----------
 0                 5.0885
 1                 223.88
 2                 359.1082
 4                 949.4105
 ```
  
 3 つの製品が定義されていない`DaysToManufacture`です。  
  
 次のコードがピボットされる、同じ結果を表示できるように、`DaysToManufacture`値は、列見出しになります。 結果が `[3]` であっても、3 日目 `NULL` の列が表示されます。  
  
```  
-- Pivot table with one row and five columns  
SELECT 'AverageCost' AS Cost_Sorted_By_Production_Days,   
[0], [1], [2], [3], [4]  
FROM  
(SELECT DaysToManufacture, StandardCost   
    FROM Production.Product) AS SourceTable  
PIVOT  
(  
AVG(StandardCost)  
FOR DaysToManufacture IN ([0], [1], [2], [3], [4])  
) AS PivotTable;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
Cost_Sorted_By_Production_Days 0           1           2           3           4         
------------------------------ ----------- ----------- ----------- ----------- -----------
AverageCost                    5.0885      223.88      359.1082    NULL        949.4105
```
  
## <a name="complex-pivot-example"></a>PIVOT の複雑な例  
 一般的なシナリオで`PIVOT`役に立ちますはデータを集計するクロス集計レポートを生成するときにします。 たとえば、クエリを実行する、`PurchaseOrderHeader`テーブルに、`AdventureWorks2014`特定の従業員で注文書の数を決定するサンプル データベースが配置されます。 このレポートを仕入先別に返すクエリを次に示します。  
  
```  
USE AdventureWorks2014;  
GO  
SELECT VendorID, [250] AS Emp1, [251] AS Emp2, [256] AS Emp3, [257] AS Emp4, [260] AS Emp5  
FROM   
(SELECT PurchaseOrderID, EmployeeID, VendorID  
FROM Purchasing.PurchaseOrderHeader) p  
PIVOT  
(  
COUNT (PurchaseOrderID)  
FOR EmployeeID IN  
( [250], [251], [256], [257], [260] )  
) AS pvt  
ORDER BY pvt.VendorID;  
```  
  
 部分的な結果セットを次に示します。  
  
```
VendorID    Emp1        Emp2        Emp3        Emp4        Emp5  
----------- ----------- ----------- ----------- ----------- -----------
1492        2           5           4           4           4
1494        2           5           4           5           4
1496        2           4           4           5           5
1498        2           5           4           4           4
1500        3           4           4           5           4
```
  
 このサブセレクト ステートメントにより返される結果は `EmployeeID` 列でピボット処理されています。  
  
```  
SELECT PurchaseOrderID, EmployeeID, VendorID  
FROM PurchaseOrderHeader;  
```  
  
 つまり、によって返される一意の値、`EmployeeID`最終的な結果セット自体になる列のフィールドです。 各列があるため、 `EmployeeID` pivot 句で指定した数値: この case の従業員の`164`、 `198`、 `223`、`231`と`233`です。 `PurchaseOrderID` 列は、最終的な出力に返される列をグループ化する (この列をグループ化列といいます) のための値列です。 この例では、グループ化列を `COUNT` 関数で集計しています。 従業員ごとに `PurchaseOrderID` 関数を計算する際に `COUNT` 列に表示されている NULL 値を無視したことを示す警告メッセージが表示されます。  
  
> [!IMPORTANT]  
>  集計関数を使用するときに`PIVOT`集計を計算するときに、[値] 列で null 値の存在は考慮されません。  
  
 `UNPIVOT`ほぼ逆演算を実行`PIVOT`行に列を回転させるとします。 前の例としてデータベースに格納されているで作成されたテーブルと`pvt`、列の識別子を回転させると`Emp1`、 `Emp2`、 `Emp3`、 `Emp4`、および`Emp5`行に値を特定のベンダーに対応します。 そのためには、さらに 2 つの列を指定する必要があります。 回転する列の値を格納する列 (`Emp1`、 `Emp2`,...) が呼び出される`Employee`と呼び出される回転される列の下に現在格納されている値を保持する列`Orders`です。 これらの列に対応、 *pivot_column*と*value_column*をそれぞれで、[!INCLUDE[tsql](../../includes/tsql-md.md)]定義します。 クエリを次に示します。  
  
```  
-- Create the table and insert values as portrayed in the previous example.  
CREATE TABLE pvt (VendorID int, Emp1 int, Emp2 int,  
    Emp3 int, Emp4 int, Emp5 int);  
GO  
INSERT INTO pvt VALUES (1,4,3,5,4,4);  
INSERT INTO pvt VALUES (2,4,1,5,5,5);  
INSERT INTO pvt VALUES (3,4,3,5,4,4);  
INSERT INTO pvt VALUES (4,4,2,5,5,4);  
INSERT INTO pvt VALUES (5,5,1,5,5,5);  
GO  
-- Unpivot the table.  
SELECT VendorID, Employee, Orders  
FROM   
   (SELECT VendorID, Emp1, Emp2, Emp3, Emp4, Emp5  
   FROM pvt) p  
UNPIVOT  
   (Orders FOR Employee IN   
      (Emp1, Emp2, Emp3, Emp4, Emp5)  
)AS unpvt;  
GO  
```  
  
 部分的な結果セットを次に示します。  
  
```
VendorID    Employee    Orders
----------- ----------- ------
1            Emp1       4
1            Emp2       3 
1            Emp3       5
1            Emp4       4
1            Emp5       4
2            Emp1       4
2            Emp2       1
2            Emp3       5
2            Emp4       5
2            Emp5       5
...
```
  
 注意して`UNPIVOT`は正反対の`PIVOT`します。 `PIVOT`集計を実行し、そのため、マージ可能な複数の行出力内の単一行。 `UNPIVOT`行がマージされているため、元のテーブル値式の結果は再現しません。 入力内の値は null 以外にも、`UNPIVOT`が発生しました。 元の null 値の前に、入力、出力では、非表示になります、`PIVOT`操作します。  
  
 `Sales.vSalesPersonSalesByFiscalYears`で表示、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]サンプル データベースは`PIVOT`を各会計年度の各販売員の売上合計を返します。 ビューで、スクリプトを作成する[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、**オブジェクト エクスプ ローラー**、下にあるビューの検索、**ビュー**用のフォルダー、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。 ビュー名を右クリックし、**ビューをスクリプト**です。  
  
## <a name="see-also"></a>参照  
 [(TRANSACT-SQL) から](../../t-sql/queries/from-transact-sql.md)   
 [ケース (TRANSACT-SQL)](../../t-sql/language-elements/case-transact-sql.md)  
  
  
