---
title: "COMMON_TABLE_EXPRESSION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WITH common_table_expression
- WITH_TSQL
- WITH
- common table expression
dev_langs:
- TSQL
helpviewer_keywords:
- WITH common_table_expression clause
- CTEs
- hierarchical queries [SQL Server], WITH common_table_expression
- recursive CTEs [SQL Server]
- recursive queries [SQL Server]
- common table expressions
- MAXRECURSION hint
- clauses [SQL Server], WITH common_table_expression
ms.assetid: 27cfb819-3e8d-4274-8bbe-cbbe4d9c2e23
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 8c77e9c97fd3d31b63e6e3938cbdab134554dd1c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="with-commontableexpression-transact-sql"></a>WITH common_table_expression (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  共通テーブル式 (CTE) と呼ばれる一時的な名前付き結果セットを指定します。 共通テーブル式は単純なクエリから派生し、単一の SELECT、INSERT、UPDATE、または DELETE ステートメントの実行スコープ内で定義されます。 CTE は、CREATE VIEW ステートメントの中で、ビューの SELECT ステートメントの定義の一部として指定することもできます。 共通テーブル式には、自己参照を含めることができます。 これは再帰共通テーブル式と呼ばれます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
[ WITH <common_table_expression> [ ,...n ] ]  
  
<common_table_expression>::=  
    expression_name [ ( column_name [ ,...n ] ) ]  
    AS  
    ( CTE_query_definition )  
```  
  
## <a name="arguments"></a>引数  
 *expression_name*  
共通テーブル式の有効な識別子です。 *expression_name* 、他の共通テーブル式の同一の WITH で定義されている名前と異なる必要があります\<common_table_expression > 句が*expression_name*の名前と同じであることができます、ベース テーブルまたはビュー。 参照*expression_name*では、クエリで共通テーブル式とベース オブジェクトではありません。
  
 *column_name*  
 共通テーブル式の列名を指定します。 1 つの CTE 定義の中で、列名の重複は許可されません。 指定した列名の数がの結果セット内の列の数に一致する必要があります、 *CTE_query_definition*です。 クエリ定義内で、結果セットのすべての列に対して異なる列名が指定されている場合にのみ、列名リストをオプションで使用できます。  
  
 *CTE_query_definition*  
 共通テーブル式を設定した結果セットを持つ SELECT ステートメントを指定します。 SELECT ステートメントの*CTE_query_definition* CTE が別の CTE を定義することはできません以外に、ビューを作成する場合と同じ要件を満たす必要があります。 詳細については、「解説」セクションを参照してください。 および[CREATE VIEW &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-view-transact-sql.md).  
  
 複数ある場合*CTE_query_definition*が定義されている、クエリの定義が参加しているこれらのいずれかで set 演算子: UNION ALL、UNION、EXCEPT、または INTERSECT です。  
  
## <a name="remarks"></a>解説  
  
## <a name="guidelines-for-creating-and-using-common-table-expressions"></a>共通テーブル式の作成および使用に関するガイドライン  
 非再帰共通テーブル式には、次のガイドラインが適用されます。 再帰共通テーブル式に適用されるガイドラインについては、後述の「再帰共通テーブル式の定義および使用に関するガイドライン」を参照してください。  
  
-   CTE の後には、その CTE 列の一部または全部を参照する単一の SELECT、INSERT、UPDATE、または DELETE ステートメントを指定する必要があります。 CTE は、ビューの定義の SELECT ステートメントの一部として、CREATE VIEW ステートメントでも指定することができます。  
  
-   非再帰 CTE では、複数の CTE クエリを定義できます。 定義は、set 演算子 UNION ALL、UNION、INTERSECT、または EXCEPT のいずれかによって結合する必要があります。  
  
-   CTE は、自分自身および同一の WITH 句内で先に定義された CTE を参照できます。 前方参照は許可されません。  
  
-   1 つの CTE の中で複数の WITH 句を指定することはできません。 たとえば場合、 *CTE_query_definition*サブクエリを含むそのサブクエリは、別の CTE を定義する句を使用して、入れ子になった含めることはできません。  
  
-   次の句は使用できません、 *CTE_query_definition*:  
  
    -   ORDER BY (TOP 句が指定されている場合は除く)  
  
    -   INTO  
  
    -   クエリ ヒントを含む OPTION 句  
  
    -   FOR BROWSE  
  
-   バッチの一部となるステートメント内で CTE が使用される場合、この句の前のステートメントの末尾にセミコロンを記述する必要があります。  
  
-   CTE を参照するクエリは、カーソル定義に使用できます。  
  
-   リモート サーバー上のテーブルは、CTE 内で参照できます。  
  
-   CTE を実行するときには、クエリ内のビューを参照するヒントと同様に、CTE を参照するヒントと基になるテーブルに CTE がアクセスした際に発見されたその他のヒントとの間で、競合が発生する可能性があります。 この競合が発生すると、クエリはエラーを返します。  
  
## <a name="guidelines-for-defining-and-using-recursive-common-table-expressions"></a>再帰共通テーブル式の定義および使用に関するガイドライン  
 再帰共通テーブル式の定義には、次のガイドラインが適用されます。  
  
-   再帰 CTE の定義には、少なくとも 2 つの CTE クエリ定義を含める必要があります。1 つはアンカー メンバーで、もう 1 つは再帰メンバーです。 アンカー メンバーと再帰メンバーは複数定義できます。ただし、すべてのアンカー メンバーの定義は、最初の再帰メンバーの定義よりも前に記述する必要があります。 CTE 自体を参照しない CTE クエリ定義はすべてアンカー メンバーとなります。  
  
-   アンカー メンバーは、set 演算子 UNION ALL、UNION、INTERSECT、または EXCEPT のいずれかによって結合する必要があります。 UNION ALL は、最後のアンカー メンバーと最初の再帰メンバーを連結する場合、および複数の再帰メンバーを連結する場合に使用できる唯一の set 演算子です。  
  
-   アンカー メンバーの列数と再帰メンバーの列数は、同じである必要があります。  
  
-   再帰メンバーの列のデータ型は、アンカー メンバーの対応する列のデータ型と同じである必要があります。  
  
-   再帰メンバーの FROM 句は、CTE に対する 1 回だけを参照する必要があります*expression_name*です。  
  
-   次の項目は使用できません、 *CTE_query_definition*再帰メンバーの。  
  
    -   SELECT DISTINCT  
  
    -   GROUP BY  
  
    -   PIVOT (データベース互換性レベルが 110 以上の場合。 参照してください[SQL Server 2016 におけるデータベース エンジン機能の重大な変更](../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md))。  
  
    -   HAVING  
  
    -   スカラー集計  
  
    -   先頭に戻る  
  
    -   LEFT、RIGHT、OUTER JOIN (INNER JOIN は使用できます)  
  
    -   サブクエリ  
  
    -   内の CTE に対する再帰参照に適用されるヒント、 *CTE_query_definition*です。  
  
 再帰共通テーブル式の使用には、次のガイドラインが適用されます。  
  
-   再帰 CTE に含まれる SELECT ステートメントが返す列で NULL 値が許容されるかどうかにかかわらず、再帰 CTE が返すすべての列で NULL 値が許可されます。  
  
-   再帰 CTE が適切に構成されていない場合、無限ループが発生する可能性があります。 たとえば、再帰メンバーのクエリ定義が親列と子列に対して同じ値を返す場合、無限ループが生成されます。 無限ループを防ぐには、MAXRECURSION ヒントを使用したり、INSERT、UPDATE、DELETE、または SELECT ステートメントの OPTION 句に 0 ～ 32,767 の値を指定したりすることにより、特定のステートメントに許可される再帰レベルの数を制限します。 これにより、無限ループの原因となったコードの問題が解決されるまで、ステートメントの実行を制御できます。 サーバー全体での既定値は 100 です。 0 を指定した場合、制限は適用されません。 MAXRECURSION の値は 1 つのステートメントに 1 つだけ指定できます。 詳細については、「[クエリ ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md)」を参照してください。  
  
-   再帰共通テーブル式を含むビューを使用してデータを更新することはできません。  
  
-   CTE を使用するクエリにカーソルを定義できます。 CTE は、 *select_statement*カーソルの結果セットを定義する引数。 再帰 CTE では、高速順方向専用および静的 (スナップショット) カーソルのみ使用できます。 他の種類のカーソルを再帰 CTE で指定した場合、カーソルの種類は静的に変換されます。  
  
-   リモート サーバー上のテーブルは、CTE 内で参照できます。 CTE の再帰メンバーがリモート サーバーを参照する場合、各リモート テーブルごとにスプールが作成されます。そのため、ローカルからそのテーブルに繰り返しアクセスできます。 CTE クエリの場合、クエリ プランに Index Spool/Lazy Spool が表示され、WITH STACK 述語が付加されます。 これは、適切な再帰を確認する方法の 1 つです。  
  
-   CTE の再帰部分の分析関数と集計関数は、CTE のセットではなく、現在の再帰レベルのセットに適用されます。 ROW_NUMBER などの関数は、現在の再帰レベルによって渡されたデータのサブセットでのみ機能し、CTE の再帰部分に渡されたデータのセット全体では機能しません。 詳細については、例 k. を使用してで分析関数に続く CTE の再帰的なを参照してください。  
  
## <a name="features-and-limitations-of-common-table-expressions-in-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>テーブル内の式の共通の機能と制限[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 内の Cte の現在の実装[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]以下の機能と制限事項があります。  
  
-   CTE を指定することができます、**選択**ステートメントです。  
  
-   CTE を指定することができます、 **CREATE VIEW**ステートメントです。  
  
-   CTE を指定することができます、 **CREATE TABLE AS SELECT** (CTAS) ステートメントです。  
  
-   CTE を指定することができます、 **CREATE リモート TABLE AS SELECT** (CRTAS) ステートメントです。  
  
-   CTE を指定することができます、 **CREATE EXTERNAL TABLE AS SELECT** (CETAS) ステートメントです。  
  
-   リモート テーブルは、CTE から参照できます。  
  
-   外部テーブルは、CTE から参照できます。  
  
-   複数の CTE クエリ定義は、CTE を定義できます。  
  
-   CTE は、1 つが続かなければなりません**選択**ステートメントです。 **挿入**、**更新**、**削除**、および**マージ**ステートメントはサポートされていません。  
  
-   (再帰共通テーブル式) 自体への参照が含まれる共通テーブル式がサポートされていません。  
  
-   複数のいずれかを示す**WITH** CTE の句は許可されていません。 たとえば、CTE_query_definition にサブクエリが含まれている場合そのサブクエリは使用できません、入れ子になった**WITH**別の CTE を定義する句。  
  
-   **ORDER BY**場合を除き、CTE_query_definition で句は使用できません、**上部**句を指定します。  
  
-   バッチの一部となるステートメント内で CTE が使用される場合、この句の前のステートメントの末尾にセミコロンを記述する必要があります。  
  
-   ステートメントを準備するために使用すると**sp_prepare**、Cte は、同様の動作方法とその他の**選択**PDW 内のステートメント。 ただし、CETAS を準備するための一部として Cte を使用するかどうかは**sp_prepare**から動作を延期できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]な方向バインディングのためには、その他の PDW ステートメントは実装と**sp_prepare**です。 場合**選択**参照 CTE を使用している、CTE に存在していない誤った列、 **sp_prepare**中にスローされますが、エラー、エラーを検出せずに渡されます**sp_execute**代わりにします。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-simple-common-table-expression"></a>A. 単純な共通テーブル式を作成する  
 次の例では、年度ごとの販売注文の合計数を示しますにおける各販売員の[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]します。  
  
```  
  
-- Define the CTE expression name and column list.  
WITH Sales_CTE (SalesPersonID, SalesOrderID, SalesYear)  
AS  
-- Define the CTE query.  
(  
    SELECT SalesPersonID, SalesOrderID, YEAR(OrderDate) AS SalesYear  
    FROM Sales.SalesOrderHeader  
    WHERE SalesPersonID IS NOT NULL  
)  
-- Define the outer query referencing the CTE name.  
SELECT SalesPersonID, COUNT(SalesOrderID) AS TotalSales, SalesYear  
FROM Sales_CTE  
GROUP BY SalesYear, SalesPersonID  
ORDER BY SalesPersonID, SalesYear;  
GO  
  
```  
  
### <a name="b-using-a-common-table-expression-to-limit-counts-and-report-averages"></a>B. 共通テーブル式を使用して、回数を制限し、平均数をレポートする  
 次の例は、販売員のすべての年度の販売注文数の平均を示しています。  
  
```  
WITH Sales_CTE (SalesPersonID, NumberOfOrders)  
AS  
(  
    SELECT SalesPersonID, COUNT(*)  
    FROM Sales.SalesOrderHeader  
    WHERE SalesPersonID IS NOT NULL  
    GROUP BY SalesPersonID  
)  
SELECT AVG(NumberOfOrders) AS "Average Sales Per Person"  
FROM Sales_CTE;  
GO  
```  
  
### <a name="c-using-multiple-cte-definitions-in-a-single-query"></a>C. 単一のクエリでの複数の CTE の定義  
 次の例は、単一のクエリで複数の CTE を定義する方法を示しています。 CTE クエリ定義を区切るために、コンマを使用することに注意してください。 通貨書式で金額を表示する FORMAT 関数は、SQL Server 2012 以降で利用できます。  
  
```  
  
WITH Sales_CTE (SalesPersonID, TotalSales, SalesYear)  
AS  
-- Define the first CTE query.  
(  
    SELECT SalesPersonID, SUM(TotalDue) AS TotalSales, YEAR(OrderDate) AS SalesYear  
    FROM Sales.SalesOrderHeader  
    WHERE SalesPersonID IS NOT NULL  
       GROUP BY SalesPersonID, YEAR(OrderDate)  
  
)  
,   -- Use a comma to separate multiple CTE definitions.  
  
-- Define the second CTE query, which returns sales quota data by year for each sales person.  
Sales_Quota_CTE (BusinessEntityID, SalesQuota, SalesQuotaYear)  
AS  
(  
       SELECT BusinessEntityID, SUM(SalesQuota)AS SalesQuota, YEAR(QuotaDate) AS SalesQuotaYear  
       FROM Sales.SalesPersonQuotaHistory  
       GROUP BY BusinessEntityID, YEAR(QuotaDate)  
)  
  
-- Define the outer query by referencing columns from both CTEs.  
SELECT SalesPersonID  
  , SalesYear  
  , FORMAT(TotalSales,'C','en-us') AS TotalSales  
  , SalesQuotaYear  
  , FORMAT (SalesQuota,'C','en-us') AS SalesQuota  
  , FORMAT (TotalSales -SalesQuota, 'C','en-us') AS Amt_Above_or_Below_Quota  
FROM Sales_CTE  
JOIN Sales_Quota_CTE ON Sales_Quota_CTE.BusinessEntityID = Sales_CTE.SalesPersonID  
                    AND Sales_CTE.SalesYear = Sales_Quota_CTE.SalesQuotaYear  
ORDER BY SalesPersonID, SalesYear;  
GO  
  
```  
  
 部分的な結果セットを次に示します。  
  
```  
  
SalesPersonID SalesYear   TotalSales    SalesQuotaYear SalesQuota  Amt_Above_or_Below_Quota  
------------- ---------   -----------   -------------- ---------- ----------------------------------   
  
274           2005        $32,567.92    2005           $35,000.00  ($2,432.08)  
274           2006        $406,620.07   2006           $455,000.00 ($48,379.93)  
274           2007        $515,622.91   2007           $544,000.00 ($28,377.09)  
274           2008        $281,123.55   2008           $271,000.00  $10,123.55  
  
```  
  
### <a name="d-using-a-recursive-common-table-expression-to-display-multiple-levels-of-recursion"></a>D. 再帰共通テーブル式を使用して、複数の再帰レベルを表示する  
 次の例は、マネージャーおよびマネージャーにレポートする従業員の階層リストを示しています。 最初に、`dbo.MyEmployees` テーブルを作成して値を設定します。  
  
```  
-- Create an Employee table.  
CREATE TABLE dbo.MyEmployees  
(  
EmployeeID smallint NOT NULL,  
FirstName nvarchar(30)  NOT NULL,  
LastName  nvarchar(40) NOT NULL,  
Title nvarchar(50) NOT NULL,  
DeptID smallint NOT NULL,  
ManagerID int NULL,  
 CONSTRAINT PK_EmployeeID PRIMARY KEY CLUSTERED (EmployeeID ASC)   
);  
-- Populate the table with values.  
INSERT INTO dbo.MyEmployees VALUES   
 (1, N'Ken', N'Sánchez', N'Chief Executive Officer',16,NULL)  
,(273, N'Brian', N'Welcker', N'Vice President of Sales',3,1)  
,(274, N'Stephen', N'Jiang', N'North American Sales Manager',3,273)  
,(275, N'Michael', N'Blythe', N'Sales Representative',3,274)  
,(276, N'Linda', N'Mitchell', N'Sales Representative',3,274)  
,(285, N'Syed', N'Abbas', N'Pacific Sales Manager',3,273)  
,(286, N'Lynn', N'Tsoflias', N'Sales Representative',3,285)  
,(16,  N'David',N'Bradley', N'Marketing Manager', 4, 273)  
,(23,  N'Mary', N'Gibson', N'Marketing Specialist', 4, 16);  
```  
  
```  
USE AdventureWorks2012;  
GO  
WITH DirectReports(ManagerID, EmployeeID, Title, EmployeeLevel) AS   
(  
    SELECT ManagerID, EmployeeID, Title, 0 AS EmployeeLevel  
    FROM dbo.MyEmployees   
    WHERE ManagerID IS NULL  
    UNION ALL  
    SELECT e.ManagerID, e.EmployeeID, e.Title, EmployeeLevel + 1  
    FROM dbo.MyEmployees AS e  
        INNER JOIN DirectReports AS d  
        ON e.ManagerID = d.EmployeeID   
)  
SELECT ManagerID, EmployeeID, Title, EmployeeLevel   
FROM DirectReports  
ORDER BY ManagerID;  
GO  
```  
  
### <a name="e-using-a-recursive-common-table-expression-to-display-two-levels-of-recursion"></a>E. 再帰共通テーブル式を使用して、2 つの再帰レベルを表示する  
 次の例は、マネージャーおよびマネージャーにレポートする従業員を示しています。 返されるレベルの数は 2 つに制限されます。  
  
```  
USE AdventureWorks2012;  
GO  
WITH DirectReports(ManagerID, EmployeeID, Title, EmployeeLevel) AS   
(  
    SELECT ManagerID, EmployeeID, Title, 0 AS EmployeeLevel  
    FROM dbo.MyEmployees   
    WHERE ManagerID IS NULL  
    UNION ALL  
    SELECT e.ManagerID, e.EmployeeID, e.Title, EmployeeLevel + 1  
    FROM dbo.MyEmployees AS e  
        INNER JOIN DirectReports AS d  
        ON e.ManagerID = d.EmployeeID   
)  
SELECT ManagerID, EmployeeID, Title, EmployeeLevel   
FROM DirectReports  
WHERE EmployeeLevel <= 2 ;  
GO  
  
```  
  
### <a name="f-using-a-recursive-common-table-expression-to-display-a-hierarchical-list"></a>F. 再帰共通テーブル式を使用して、階層リストを表示する  
 次の例は、例 D にマネージャーと従業員の名前および各自の役職を追加したものです。 各レベルをインデントすることにより、マネージャーおよび従業員の階層をさらに強調しています。  
  
```  
USE AdventureWorks2012;  
GO  
WITH DirectReports(Name, Title, EmployeeID, EmployeeLevel, Sort)  
AS (SELECT CONVERT(varchar(255), e.FirstName + ' ' + e.LastName),  
        e.Title,  
        e.EmployeeID,  
        1,  
        CONVERT(varchar(255), e.FirstName + ' ' + e.LastName)  
    FROM dbo.MyEmployees AS e  
    WHERE e.ManagerID IS NULL  
    UNION ALL  
    SELECT CONVERT(varchar(255), REPLICATE ('|    ' , EmployeeLevel) +  
        e.FirstName + ' ' + e.LastName),  
        e.Title,  
        e.EmployeeID,  
        EmployeeLevel + 1,  
        CONVERT (varchar(255), RTRIM(Sort) + '|    ' + FirstName + ' ' +   
                 LastName)  
    FROM dbo.MyEmployees AS e  
    JOIN DirectReports AS d ON e.ManagerID = d.EmployeeID  
    )  
SELECT EmployeeID, Name, Title, EmployeeLevel  
FROM DirectReports   
ORDER BY Sort;  
GO  
```  
  
### <a name="g-using-maxrecursion-to-cancel-a-statement"></a>G. MAXRECURSION を使用して、ステートメントを取り消す  
 `MAXRECURSION` を使用すると、不適切に作成された再帰 CTE による無限ループの発生を防ぐことができます。 次の例は意図的に無限ループを作成しを使用して、`MAXRECURSION`を 2 つの再帰レベルの数を制限するためのヒント。  
  
```  
USE AdventureWorks2012;  
GO  
--Creates an infinite loop  
WITH cte (EmployeeID, ManagerID, Title) as  
(  
    SELECT EmployeeID, ManagerID, Title  
    FROM dbo.MyEmployees  
    WHERE ManagerID IS NOT NULL  
  UNION ALL  
    SELECT cte.EmployeeID, cte.ManagerID, cte.Title  
    FROM cte   
    JOIN  dbo.MyEmployees AS e   
        ON cte.ManagerID = e.EmployeeID  
)  
--Uses MAXRECURSION to limit the recursive levels to 2  
SELECT EmployeeID, ManagerID, Title  
FROM cte  
OPTION (MAXRECURSION 2);  
GO  
```  
  
 コードのエラーが訂正されると、MAXRECURSION は不要になります。 次の例は、訂正されたコードを示しています。  
  
```  
USE AdventureWorks2012;  
GO  
WITH cte (EmployeeID, ManagerID, Title)  
AS  
(  
    SELECT EmployeeID, ManagerID, Title  
    FROM dbo.MyEmployees  
    WHERE ManagerID IS NOT NULL  
  UNION ALL  
    SELECT  e.EmployeeID, e.ManagerID, e.Title  
    FROM dbo.MyEmployees AS e  
    JOIN cte ON e.ManagerID = cte.EmployeeID  
)  
SELECT EmployeeID, ManagerID, Title  
FROM cte;  
GO  
```  
  
### <a name="h-using-a-common-table-expression-to-selectively-step-through-a-recursive-relationship-in-a-select-statement"></a>H. 共通テーブル式を使用して、SELECT ステートメント内の再帰リレーションシップを選択的にステップ スルーする  
 次の例では、製品アセンブリと自転車を組み立てるに必要なコンポーネントの階層`ProductAssemblyID = 800`です。  
  
```  
USE AdventureWorks2012;  
GO  
WITH Parts(AssemblyID, ComponentID, PerAssemblyQty, EndDate, ComponentLevel) AS  
(  
    SELECT b.ProductAssemblyID, b.ComponentID, b.PerAssemblyQty,  
        b.EndDate, 0 AS ComponentLevel  
    FROM Production.BillOfMaterials AS b  
    WHERE b.ProductAssemblyID = 800  
          AND b.EndDate IS NULL  
    UNION ALL  
    SELECT bom.ProductAssemblyID, bom.ComponentID, p.PerAssemblyQty,  
        bom.EndDate, ComponentLevel + 1  
    FROM Production.BillOfMaterials AS bom   
        INNER JOIN Parts AS p  
        ON bom.ProductAssemblyID = p.ComponentID  
        AND bom.EndDate IS NULL  
)  
SELECT AssemblyID, ComponentID, Name, PerAssemblyQty, EndDate,  
        ComponentLevel   
FROM Parts AS p  
    INNER JOIN Production.Product AS pr  
    ON p.ComponentID = pr.ProductID  
ORDER BY ComponentLevel, AssemblyID, ComponentID;  
GO  
```  
  
### <a name="i-using-a-recursive-cte-in-an-update-statement"></a>I. UPDATE ステートメントで再帰 CTE を使用する  
 次の例の更新プログラム、 `PerAssemblyQty` "ROAD-W 550 Yellow, 44"製品をビルドするために使用されるすべての部分の値`(ProductAssemblyID``800`)。 共通テーブル式は、`ProductAssemblyID 800` の製造に使用される部品およびこれらの部品の製造に使用されるコンポーネントの階層リストを返します。 共通テーブル式が返した行のみが変更されます。  
  
```  
USE AdventureWorks2012;  
GO  
WITH Parts(AssemblyID, ComponentID, PerAssemblyQty, EndDate, ComponentLevel) AS  
(  
    SELECT b.ProductAssemblyID, b.ComponentID, b.PerAssemblyQty,  
        b.EndDate, 0 AS ComponentLevel  
    FROM Production.BillOfMaterials AS b  
    WHERE b.ProductAssemblyID = 800  
          AND b.EndDate IS NULL  
    UNION ALL  
    SELECT bom.ProductAssemblyID, bom.ComponentID, p.PerAssemblyQty,  
        bom.EndDate, ComponentLevel + 1  
    FROM Production.BillOfMaterials AS bom   
        INNER JOIN Parts AS p  
        ON bom.ProductAssemblyID = p.ComponentID  
        AND bom.EndDate IS NULL  
)  
UPDATE Production.BillOfMaterials  
SET PerAssemblyQty = c.PerAssemblyQty * 2  
FROM Production.BillOfMaterials AS c  
JOIN Parts AS d ON c.ProductAssemblyID = d.AssemblyID  
WHERE d.ComponentLevel = 0;  
```  
  
### <a name="j-using-multiple-anchor-and-recursive-members"></a>J. 複数のアンカー メンバーと再帰メンバーを使用する  
 次の例では、複数のアンカー メンバーと再帰メンバーを使用して、指定された個人のすべての先祖を返します。 テーブルが 1 つ作成され、値が挿入されます。このテーブルは、再帰 CTE が返す家系図になります。  
  
```  
-- Genealogy table  
IF OBJECT_ID('dbo.Person','U') IS NOT NULL DROP TABLE dbo.Person;  
GO  
CREATE TABLE dbo.Person(ID int, Name varchar(30), Mother int, Father int);  
GO  
INSERT dbo.Person   
VALUES(1, 'Sue', NULL, NULL)  
      ,(2, 'Ed', NULL, NULL)  
      ,(3, 'Emma', 1, 2)  
      ,(4, 'Jack', 1, 2)  
      ,(5, 'Jane', NULL, NULL)  
      ,(6, 'Bonnie', 5, 4)  
      ,(7, 'Bill', 5, 4);  
GO  
-- Create the recursive CTE to find all of Bonnie's ancestors.  
WITH Generation (ID) AS  
(  
-- First anchor member returns Bonnie's mother.  
    SELECT Mother   
    FROM dbo.Person  
    WHERE Name = 'Bonnie'  
UNION  
-- Second anchor member returns Bonnie's father.  
    SELECT Father   
    FROM dbo.Person  
    WHERE Name = 'Bonnie'  
UNION ALL  
-- First recursive member returns male ancestors of the previous generation.  
    SELECT Person.Father  
    FROM Generation, Person  
    WHERE Generation.ID=Person.ID  
UNION ALL  
-- Second recursive member returns female ancestors of the previous generation.  
    SELECT Person.Mother  
    FROM Generation, dbo.Person  
    WHERE Generation.ID=Person.ID  
)  
SELECT Person.ID, Person.Name, Person.Mother, Person.Father  
FROM Generation, dbo.Person  
WHERE Generation.ID = Person.ID;  
GO  
```  
  
###  <a name="bkmkUsingAnalyticalFunctionsInARecursiveCTE"></a> K. 再帰 CTE で分析関数を使用する  
 次の例は、CTE の再帰部分で分析関数または集計関数を使用するときに生じる可能性がある落とし穴を示しています。  
  
```  
DECLARE @t1 TABLE (itmID int, itmIDComp int);  
INSERT @t1 VALUES (1,10), (2,10);   
  
DECLARE @t2 TABLE (itmID int, itmIDComp int);   
INSERT @t2 VALUES (3,10), (4,10);   
  
WITH vw AS  
 (  
    SELECT itmIDComp, itmID  
    FROM @t1  
  
    UNION ALL  
  
    SELECT itmIDComp, itmID  
    FROM @t2  
)   
,r AS  
 (  
    SELECT t.itmID AS itmIDComp  
           , NULL AS itmID  
           ,CAST(0 AS bigint) AS N  
           ,1 AS Lvl  
    FROM (SELECT 1 UNION ALL SELECT 2 UNION ALL SELECT 3 UNION ALL SELECT 4) AS t (itmID)   
  
UNION ALL  
  
SELECT t.itmIDComp  
    , t.itmID  
    , ROW_NUMBER() OVER(PARTITION BY t.itmIDComp ORDER BY t.itmIDComp, t.itmID) AS N  
    , Lvl + 1  
FROM r   
    JOIN vw AS t ON t.itmID = r.itmIDComp  
)   
  
SELECT Lvl, N FROM r;  
```  
  
 次の結果は、クエリの予想結果です。  
  
```  
Lvl  N  
1    0  
1    0  
1    0  
1    0  
2    4  
2    3  
2    2  
2    1  
```  
  
 次の結果は、クエリの実際の結果です。  
  
```  
Lvl  N  
1    0  
1    0  
1    0  
1    0  
2    1  
2    1  
2    1  
2    1  
```  
  
 `N`その再帰レベルのデータのサブセットのみが渡されるため、CTE の再帰部分のパスごとに 1 を返します`ROWNUMBER`です。 クエリの再帰部分の反復処理ごとに、1 行だけが渡される`ROWNUMBER`です。  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="l-using-a-common-table-expression-within-a-ctas-statement"></a>L. CTAS ステートメント内で共通テーブル式を使用します。  
 次の例にある各営業担当者の年度ごとの販売注文の合計数を含む新しいテーブルを作成する[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]です。  
  
```  
-- Uses AdventureWorks  
  
CREATE TABLE SalesOrdersPerYear  
WITH  
(  
    DISTRIBUTION = HASH(SalesPersonID)  
)  
AS  
    -- Define the CTE expression name and column list.  
    WITH Sales_CTE (SalesPersonID, SalesOrderID, SalesYear)  
    AS  
    -- Define the CTE query.  
    (  
        SELECT SalesPersonID, SalesOrderID, YEAR(OrderDate) AS SalesYear  
        FROM Sales.SalesOrderHeader  
        WHERE SalesPersonID IS NOT NULL  
    )  
    -- Define the outer query referencing the CTE name.  
    SELECT SalesPersonID, COUNT(SalesOrderID) AS TotalSales, SalesYear  
    FROM Sales_CTE  
    GROUP BY SalesYear, SalesPersonID  
    ORDER BY SalesPersonID, SalesYear;  
GO  
```  
  
### <a name="m-using-a-common-table-expression-within-a-cetas-statement"></a>M. CETAS ステートメント内で共通テーブル式を使用します。  
 次の例で各販売担当者の年度ごとの販売注文の合計数を格納する新しい外部テーブルを作成する[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]です。  
  
```  
-- Uses AdventureWorks  
  
CREATE EXTERNAL TABLE SalesOrdersPerYear  
WITH  
(  
    LOCATION = 'hdfs://xxx.xxx.xxx.xxx:5000/files/Customer',  
    FORMAT_OPTIONS ( FIELD_TERMINATOR = '|' )   
)  
AS  
    -- Define the CTE expression name and column list.  
    WITH Sales_CTE (SalesPersonID, SalesOrderID, SalesYear)  
    AS  
    -- Define the CTE query.  
    (  
        SELECT SalesPersonID, SalesOrderID, YEAR(OrderDate) AS SalesYear  
        FROM Sales.SalesOrderHeader  
        WHERE SalesPersonID IS NOT NULL  
    )  
    -- Define the outer query referencing the CTE name.  
    SELECT SalesPersonID, COUNT(SalesOrderID) AS TotalSales, SalesYear  
    FROM Sales_CTE  
    GROUP BY SalesYear, SalesPersonID  
    ORDER BY SalesPersonID, SalesYear;  
GO  
```  
  
### <a name="n-using-multiple-comma-separated-ctes-in-a-statement"></a>N. ステートメントで Cte を区切られた複数のコンマを使用します。  
 次の例では、単一のステートメントで 2 つの Cte を含むを示します。 Cte をすることはできません (再帰なし) を入れ子にします。  
  
```  
WITH   
 CountDate (TotalCount, TableName) AS  
    (  
     SELECT COUNT(datekey), 'DimDate' FROM DimDate  
    ) ,  
 CountCustomer (TotalAvg, TableName) AS  
    (  
     SELECT COUNT(CustomerKey), 'DimCustomer' FROM DimCustomer  
    )  
SELECT TableName, TotalCount FROM CountDate  
UNION ALL  
SELECT TableName, TotalAvg FROM CountCustomer;  
```  
  
## <a name="see-also"></a>参照  
 [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [除くおよび INTERSECT と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/set-operators-except-and-intersect-transact-sql.md)   
 [挿入 &#40; です。Transact SQL と &#41; です。](../../t-sql/statements/insert-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  
  
  
