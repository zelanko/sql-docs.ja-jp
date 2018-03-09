---
title: "GROUP BY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
- GROUP
- CUBE
- ROLLUP
- GROUPING_SETS_TSQL
- GROUP BY
- GROUPING SETS
- GROUP_BY_TSQL
- GROUP_TSQL
- CUBE_TSQL
- ROLLUP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GROUP BY clause, about GROUP BY clause
- dividing tables into groups
- GROUPING SETS
- GROUP BY clause
- table groups [SQL Server]
- groups [SQL Server], tables divided into groups
- summary values [SQL Server]
ms.assetid: 40075914-6385-4692-b4a5-62fe44ae6cb6
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5e99efe49620003de40659dd4bfd959dacef986c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="select---group-by--transact-sql"></a>SELECT - GROUP BY- Transact-SQL
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

クエリの結果をグループごとに 1 つまたは複数の集計を実行する目的では、通常、行のグループに分割する SELECT ステートメントの句。 SELECT ステートメントでは、グループごとに 1 行を返します。  
  
## <a name="syntax"></a>構文  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
```  
-- Syntax for SQL Server and Azure SQL Database   
-- ISO-Compliant Syntax  
  
GROUP BY {
      column-expression  
    | ROLLUP ( <group_by_expression> [ ,...n ] )  
    | CUBE ( <group_by_expression> [ ,...n ] )  
    | GROUPING SETS ( <grouping_set> [ ,...n ]  )  
    | () --calculates the grand total 
} [ ,...n ] 
 
<group_by_expression> ::=  
      column-expression  
    | ( column-expression [ ,...n ] )    
   
<grouping_set> ::=  
      () --calculates the grand total  
    | <grouping_set_item>  
    | ( <grouping_set_item> [ ,...n ] )  
  
<grouping_set_item> ::=  
      <group_by_expression>  
    | ROLLUP ( <group_by_expression> [ ,...n ] )  
    | CUBE ( <group_by_expression> [ ,...n ] )  
  

-- For backward compatibility only.
-- Non-ISO-Compliant Syntax for SQL Server and Azure SQL Database 
  
GROUP BY 
      [ ALL ] column-expression [ ,...n ] 
    | column-expression [ ,...n ] [ WITH { CUBE | ROLLUP } ]   

```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
GROUP BY {
      column-name [ WITH (DISTRIBUTED_AGG) ]  
    | column-expression
} [ ,...n ]

```  
  
## <a name="arguments"></a>引数 
 
### <a name="column-expression"></a>*column-expression*  
列の列または非集計計算を指定します。 この列は、テーブル、派生テーブル、またはビューに属することができます。 列は、SELECT ステートメントの FROM 句に表示する必要がありますが、選択リストに表示する必要はありません。 

有効な式は、次を参照してください。[式](~/t-sql/language-elements/expressions-transact-sql.md)です。    

列は、SELECT ステートメントの FROM 句に表示する必要がありますが、選択リストに表示する必要はありません。 ただし、各テーブルまたは内の非集計式で列を表示、\<選択 > ボックスの一覧は、GROUP BY リストに含める必要があります。  
  
次のようなステートメントは使用できます。  
  
    ```  
    SELECT ColumnA, ColumnB FROM T GROUP BY ColumnA, ColumnB;  
    SELECT ColumnA + ColumnB FROM T GROUP BY ColumnA, ColumnB;  
    SELECT ColumnA + ColumnB FROM T GROUP BY ColumnA + ColumnB;  
    SELECT ColumnA + ColumnB + constant FROM T GROUP BY ColumnA, ColumnB;  
    ```  
  
次のようなステートメントは使用できません。  
  
    ```  
    SELECT ColumnA, ColumnB FROM T GROUP BY ColumnA + ColumnB;  
    SELECT ColumnA + constant + ColumnB FROM T GROUP BY ColumnA + ColumnB;  
    ```  
列の式を含めることはできません。

- 選択リストで定義されている列の別名です。 FROM 句で定義されている派生テーブルの列の別名を使用できます。
- 型の列**テキスト**、 **ntext**、または**イメージ**です。 ただし、有効なデータ型の値を返す関数の引数として、text、ntext、または image の列を使用できます。 たとえば、式では、SUBSTRING() や CAST() を使用できます。 これは、HAVING 句内の式にも適用されます。
- xml データ型のメソッドです。 Xml データ型メソッドを使用するユーザー定義関数に含めることができます。 Xml データ型メソッドを使用する計算列に含めることができます。 
- サブクエリ。 エラー 144 が返されます。 
- インデックス付きビューの列。 
 
### <a name="group-by-column-expression--n-"></a>GROUP BY *column-expression* [ ,...n ] 

1 つまたは複数の列の式のリスト内の値に従って SELECT ステートメントの結果をグループ化します。 

たとえば、このクエリは、国、地域、および売上の列を Sales テーブルを作成します。 4 つの行を挿入し、国と地域の一致する値を持つ 2 つの行の。  

```
CREATE TABLE Sales ( Country varchar(50), Region varchar(50), Sales int );

INSERT INTO sales VALUES (N'Canada', N'Alberta', 100);
INSERT INTO sales VALUES (N'Canada', N'British Columbia', 200);
INSERT INTO sales VALUES (N'Canada', N'British Columbia', 300);
INSERT INTO sales VALUES (N'United States', N'Montana', 100);
```
Sales テーブルには、これらの行が含まれています。

| Country | Region | 売上 |
|---------|--------|-------|
| Canada | Alberta | 100 |
| Canada | British Columbia | 200 |
| Canada | British Columbia | 300 |
| United States | モンタナ | 100 |

次のクエリでは、国と地域をグループ化し、値の組み合わせごとの集計合計を返します。  
 
``` 
SELECT Country, Region, SUM(sales) AS TotalSales
FROM Sales
GROUP BY Country, Region;
```
クエリ結果は、国と地域の値の 3 つの組み合わせがあるために、3 つの行を持ちます。 カナダおよび British Columbia TotalSales は、2 つの行の合計です。 

| Country | Region | [合計] |
|---------|--------|-------|
| Canada | Alberta | 100 |
| Canada | British Columbia | 500 |
| United States | モンタナ | 100 |

### <a name="group-by-rollup"></a>グループ ロールアップ化

列の式の組み合わせごとにグループを作成します。 さらに、その"にロール アップ"結果小計と総計を表示します。 これを行うには、右から左のグループと、aggregation(s) が作成される列の式の数を減らすに移動します。 

列の順序は、プログラムのロールアップの出力に影響して、結果セット内の行の数に影響を与えることができます。  

たとえば、`GROUP BY ROLLUP (col1, col2, col3, col4)`次の一覧に列の式の組み合わせごとにグループを作成します。  

- col1、col2、col3、col4 
- col1, col2, col3, NULL
- col1 と col2 に NULL の場合、NULL
- col1、NULL の場合、NULL の場合、NULL
- これは、総計、NULL、NULL、NULL NULL--

前の例からテーブルを使用して、このコードは、単純な GROUP BY の代わりに GROUP BY ROLLUP 操作を実行します。

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY ROLLUP (Country, Region);
```

クエリ結果は、単純な GROUP BY、ROLLUP せずとして同じ集計を持ちます。 さらに、国の値ごとの集計を作成します。 最後に、すべての行の総計を示します。 次のような結果が表示。

| Country | Region | [合計] |
| :------ | :----- | ---------: |
| Canada | Alberta | 100 |
| Canada | British Columbia | 500 |
| Canada | NULL | 600 |
| United States | モンタナ | 100 |
| United States | NULL | 100 |
| NULL | NULL | 700 |

### <a name="group-by-cube--"></a>GROUP BY CUBE)  

GROUP BY CUBE では、すべての列の組み合わせのグループを作成します。 GROUP BY CUBE (a、b) の結果が一意の値のグループ (a、b)、(NULL、b)、(、NULL の場合)、および (NULL, NULL)。

前の例とテーブルを使用して、このコードは、国と地域に GROUP BY CUBE 操作を実行します。 

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY CUBE (Country, Region);
```

クエリの結果が (国、地域) の一意の値について、グループ (NULL、地域)、(国、NULL)、および (NULL, NULL)。 結果は、次のようになります。

| Country | Region | [合計] |
|---------|--------|-------|
| Canada | Alberta | 100 |
| NULL | Alberta | 100 |
| Canada | British Columbia | 500 |
| NULL | British Columbia | 500 |
| United States | モンタナ | 100 |
| NULL | モンタナ | 100 |
| NULL | NULL | 700
| Canada | NULL | 600 |
| United States | NULL | 100 |
   
 ### <a name="group-by-grouping-sets--"></a>グループ化セット () をグループ化  
 
GROUPING SETS オプションを使用すると、複数の GROUP BY 句を GROUP BY 句を 1 つに統合できます。 結果は、指定したグループの UNION ALL と同じになります。 

たとえば、`GROUP BY ROLLUP (Country, Region)`と`GROUP BY GROUPING SETS ( ROLLUP (Country, Region) )`同じ結果を返します。 

GROUPING SETS に 2 つ以上の要素がある場合、結果は、要素の和集合になります。 この例では、国と地域を ROLLUP および CUBE の結果の和集合を返します。

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY GROUPING SETS ( ROLLUP (Country, Region), CUBE (Country, Region) );
```

結果は、この 2 つの GROUP BY ステートメントの和集合を返すクエリと同じです。

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY ROLLUP (Country, Region)
UNION ALL
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY CUBE (Country, Region)
;
```

SQL では、GROUPING SETS リストに対して生成される重複したグループは統合しません。 たとえば、 `GROUP BY ( (), CUBE (Country, Region) )`、両方の要素は、総計の行を返すし、両方の行を結果に表示されます。 

 ### <a name="group-by-"></a>GROUP BY ()  
総計を生成する空のグループを指定します。 これは、グループ化セットの要素の 1 つとして役立ちます。 たとえば、このステートメント各国の売上合計を提供し、総計 - すべての国のします。

```
SELECT Country, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY GROUPING SETS ( Country, () );
```

### <a name="group-by--all--column-expression--n-"></a>GROUP BY [ ALL ] column-expression [ ,...n ] 

適用されます SQL Server と Azure SQL Database。

注: この構文は、旧バージョンと互換性のためだけに提供されます。 将来のバージョンで削除されます。 新しい開発作業でこの構文の使用を避けるため、現在この構文を使用しているアプリケーションの変更を検討してください。

WHERE 句内の検索条件を満たしているかどうかに関係なく、結果にすべてのグループを含めることを指定します。 検索条件を満たしていないグループでは、集計の NULL があります。 

すべてのグループ。
- ある場合、WHERE 句、クエリでリモート テーブルにアクセスするクエリではサポートされません。
- FILESTREAM 属性を持つ列に対しては失敗します。
  
### <a name="with-distributedagg"></a>(DISTRIBUTED_AGG) と
対象: Azure SQL Data Warehouse と並列データ ウェアハウス

DISTRIBUTED_AGG クエリ ヒントは、集計を実行する前に、テーブルの特定の列を再配布する膨大な並列処理 (MPP) システムを強制します。 GROUP BY 句で 1 つだけの列には、DISTRIBUTED_AGG クエリ ヒントを持つことができます。 クエリが完了したら、再配布されるテーブルは削除されます。 元のテーブルは変更されません。  

注: DISTRIBUTED_AGG クエリ ヒントは説明を旧バージョンと並列データ ウェアハウスの以前のバージョンとの互換性とほとんどのクエリのパフォーマンスは向上しません。 既定では、MPP は集計のパフォーマンスを向上させるために必要に応じて、データを既に再分配します。 
  
## <a name="general-remarks"></a>全般的な解説

### <a name="how-group-by-interacts-with-the-select-statement"></a>GROUP BY とやり取りする方法、SELECT ステートメント
選択リストは:
- ベクター集計値。 場合は、選択リストでは、集計関数が含まれている、GROUP BY は、各グループの集計値を計算します。 これらはベクター集計値と呼ばれます。 
- Distinct 集計します。 AVG 集計 (DISTINCT *column_name*)、COUNT (DISTINCT *column_name*)、および SUM (DISTINCT *column_name*) は ROLLUP、CUBE、および GROUPING SETS でサポートされています。
  
WHERE 句:
- SQL では、任意のグループ化操作が実行される前に、WHERE 句で条件を満たしていない行を削除します。  
  
HAVING 句:
- SQL は having 句、結果セット内のフィルター グループにします。 
  
ORDER BY 句:
- 結果セットを並べ替えるには、ORDER BY 句を使用します。 GROUP BY 句では、結果セットの並べ替えが行われません。 
  
NULL 値は:
- グループ化列に NULL 値が含まれている場合は、すべての NULL 値が等しいと見なされます、単一のグループに収集されします。   
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項

適用されます SQL Server (2008 以降) および Azure SQL Data Warehouse。

### <a name="maximum-capacity"></a>最大容量

GROUP BY 句の ROLLUP、CUBE、または GROUPING SETS を使用する、式の最大数には 32 です。 グループの最大数は 4096 (2<sup>12</sup>)。 次の例は、GROUP BY 句に 4096 個を超えるグループがあるために失敗します。  
 
-   次の例では、4097 (2<sup>12</sup> + 1) のセットをグループ化とは失敗します。  
  
    ```  
    GROUP BY GROUPING SETS( CUBE(a1, ..., a12), b )  
    ```  
  
-   次の例では、4097 (2<sup>12</sup> + 1) グループ化し、失敗します。 `CUBE ()` と `()` の両方のグループ化セットで総計行が生成され、重複したグループ化セットは削除されません。  
  
    ```  
    GROUP BY GROUPING SETS( CUBE(a1, ..., a12), ())  
    ```  

-   この例では、旧バージョンと互換性のある構文で使用します。 8192 が生成されます (2<sup>13</sup>) のセットをグループ化とは失敗します。  
  
    ```  
    GROUP BY CUBE (a1, ..., a13)   
    GROUP BY a1, ..., a13 WITH CUBE   
    ```    
    下位互換性を GROUP BY 句の CUBE または ROLLUP を含まない、group by item の数が、GROUP BY 列のサイズ、集計の列で制限され、集計値がクエリに関係します。 この数制限は、クエリの中間結果を保持するために中間作業テーブル上に必要な 8,060 バイトを基本にしています。 CUBE または ROLLUP を指定している場合は、最大 12 個のグループ化式を使用できます。

### <a name="support-for-iso-and-ansi-sql-2006-group-by-features"></a>ISO および ANSI SQL-2006 の GROUP BY 機能のサポート

GROUP BY 句には、次の構文の例外、sql-2006 標準規格に含まれているすべてのグループ化機能がサポートされています。  
  
-   GROUP BY 句では、明示的な GROUPING SETS リストに含まれていないグループ化セットは使用できません。 たとえば、 `GROUP BY Column1, (Column2, ...ColumnN`) により、TRANSACT-SQL ではなく、標準では許可します。  Transact SQL をサポートしている`GROUP BY C1, GROUPING SETS ((Column2, ...ColumnN))`と`GROUP BY Column1, Column2, ... ColumnN`、意味的に同等であります。 これらは、前と同じ意味`GROUP BY`例です。 これは、可能性を回避するを`GROUP BY Column1, (Column2, ...ColumnN`) として誤って解釈される可能性があります`GROUP BY C1, GROUPING SETS ((Column2, ...ColumnN))`と同じ意味はありません。  
  
-   グループ化セット内でグループ化セットを使用することはできません。 たとえば、 `GROUP BY GROUPING SETS (A1, A2,…An, GROUPING SETS (C1, C2, ...Cn))` TRANSACT-SQL ではなく、sql-2006 標準規格では許可します。 により、TRANSACT-SQL`GROUP BY GROUPING SETS( A1, A2,...An, C1, C2, ...Cn )`または`GROUP BY GROUPING SETS( (A1), (A2), ... (An), (C1), (C2), ... (Cn) )`は最初の GROUP BY の例と同じ意味と構文をより明確になっています。  
  
-   GROUP BY [ALL/DISTINCT] のみでは許可単純な GROUP BY 句を含む列の式。 GROUPING SETS、ROLLUP、CUBE、WITH CUBE または WITH ROLLUP のコンストラクトでは許可されません。 ALL は既定値であり暗黙的です。 旧バージョンと互換性のある構文ものみ許可されます。
  
### <a name="comparison-of-supported-group-by-features"></a>サポートされる GROUP BY 機能の比較  
 次の表では、SQL のバージョンとデータベースの互換性レベルに基づいてサポートされている GROUP BY 機能について説明します。  
  
|機能|SQL Server Integration Services|SQL Server 互換性レベル 100 以上|SQL Server 2008 以降で互換性レベル 90|  
|-------------|-------------------------------------|--------------------------------------------------|-----------------------------------------------------------|  
|DISTINCT 集計|WITH CUBE および WITH ROLLUP ではサポートされていません。|WITH CUBE、WITH ROLLUP、GROUPING SETS、CUBE、および ROLLUP でサポートされています。|互換性レベル 100 と同じです。|  
|GROUP BY 句内の、CUBE または ROLLUP の名前を持つユーザー定義関数|ユーザー定義関数**dbo.cube (***arg1***、***.. .argN***)**または**dbo.rollup (***arg1***、**.*argN * * *)** で GROUP BY 句は許可します。<br /><br /> 例: `SELECT SUM (x) FROM T  GROUP BY dbo.cube(y);`|ユーザー定義関数**dbo.cube (***arg1***、**.. .argN**)**または**dbo.rollup (**arg1**、***.. .argN***)**で GROUP BY 句は許可されません。<br /><br /> 例: `SELECT SUM (x) FROM T  GROUP BY dbo.cube(y);`<br /><br /> 次のエラー メッセージが返されます"キーワード 'cube' &#124; 付近に構文が正しくない '。プログラムのロールアップ '."<br /><br /> この問題を避けるためには、置換`dbo.cube`で`[dbo].[cube]`または`dbo.rollup`で`[dbo].[rollup]`です。<br /><br /> 次の例は使用できます。`SELECT SUM (x) FROM T  GROUP BY [dbo].[cube](y);`|ユーザー定義関数 **dbo.cube (***arg1***、* * *.. .argN*) または**dbo.rollup (***arg1***、***.. .argN***)**で GROUP BY 句は許可<br /><br /> 例: `SELECT SUM (x) FROM T  GROUP BY dbo.cube(y);`|  
|GROUPING SETS|サポートされていません|Supported|Supported|  
|CUBE|サポートされていません|Supported|サポートされていません|  
|ROLLUP|サポートされていません|Supported|サポートされていません|  
|GROUP BY () などの総計|サポートされていません|Supported|Supported|  
|GROUPING_ID 関数|サポートされていません|Supported|Supported|  
|GROUPING 関数|Supported|Supported|Supported|  
|WITH CUBE|Supported|Supported|Supported|  
|WITH ROLLUP|サポートされている|Supported|Supported|  
|WITH CUBE または WITH ROLLUP の重複したグループ化の削除|Supported|Supported|Supported| 
 
  
## <a name="examples"></a>使用例  
  
### <a name="a-use-a-simple-group-by-clause"></a>A. 単純な GROUP BY 句を使用します。  
 次の例では、`SalesOrderID` テーブルから `SalesOrderDetail` ごとの合計を取得します。 この例では、AdventureWorks で使用します。  
  
```  
SELECT SalesOrderID, SUM(LineTotal) AS SubTotal  
FROM Sales.SalesOrderDetail AS sod  
GROUP BY SalesOrderID  
ORDER BY SalesOrderID;  
```  
  
### <a name="b-use-a-group-by-clause-with-multiple-tables"></a>B. GROUP BY 句を使用して、複数のテーブル  
 次の例では、`City` テーブルと `Address` テーブルを結合したものから、`EmployeeAddress` ごとに従業員の数を取得します。 この例では、AdventureWorks で使用します。 
  
```  
SELECT a.City, COUNT(bea.AddressID) EmployeeCount  
FROM Person.BusinessEntityAddress AS bea   
    INNER JOIN Person.Address AS a  
        ON bea.AddressID = a.AddressID  
GROUP BY a.City  
ORDER BY a.City;  
```  
  
### <a name="c-use-a-group-by-clause-with-an-expression"></a>C. 式で GROUP BY 句を使用します。  
 次の例では、各年の売上合計を取得を使用して、`DATEPART`関数。 同じ式の両方に存在する必要があります、`SELECT`リストと`GROUP BY`句。  
  
```  
SELECT DATEPART(yyyy,OrderDate) AS N'Year'  
    ,SUM(TotalDue) AS N'Total Order Amount'  
FROM Sales.SalesOrderHeader  
GROUP BY DATEPART(yyyy,OrderDate)  
ORDER BY DATEPART(yyyy,OrderDate);  
```  
  
### <a name="d-use-a-group-by-clause-with-a-having-clause"></a>D. HAVING 句と共に GROUP BY 句を使用します。  
 次の例では、`HAVING` 句で生成されたグループのうち結果セットに含めるグループを、`GROUP BY` 句を使用して指定します。  
  
```  
SELECT DATEPART(yyyy,OrderDate) AS N'Year'  
    ,SUM(TotalDue) AS N'Total Order Amount'  
FROM Sales.SalesOrderHeader  
GROUP BY DATEPART(yyyy,OrderDate)  
HAVING DATEPART(yyyy,OrderDate) >= N'2003'  
ORDER BY DATEPART(yyyy,OrderDate);  
```  
  
## <a name="examples-sql-data-warehouse-and-parallel-data-warehouse"></a>例: SQL データ ウェアハウスと並列データ ウェアハウス  
  
### <a name="e-basic-use-of-the-group-by-clause"></a>E. GROUP BY 句の基本的な使用  
 次の例では、各日に、すべての売上の合計金額を検索します。 すべての売上合計を含む 1 つの行には、各日が返されます。  
  
```  
-- Uses AdventureWorksDW  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales FROM FactInternetSales  
GROUP BY OrderDateKey ORDER BY OrderDateKey;  
```  
  
### <a name="f-basic-use-of-the-distributedagg-hint"></a>F. DISTRIBUTED_AGG ヒントの基本的な使用  
 この例では、DISTRIBUTED_AGG クエリ ヒントを使用して、強制的に、アプライアンス上の表に、ランダム再生を`CustomerKey`集計を実行する前に列です。  
  
```  
-- Uses AdventureWorksDW  
  
SELECT CustomerKey, SUM(SalesAmount) AS sas  
FROM FactInternetSales  
GROUP BY CustomerKey WITH (DISTRIBUTED_AGG)  
ORDER BY CustomerKey DESC;  
```  
  
### <a name="g-syntax-variations-for-group-by"></a>G. GROUP BY の構文の違い  
 選択リストには、集計がない、GROUP BY リストで、選択リスト内の各列を含める必要があります。 選択リスト内の計算列は、表示することができますが、GROUP BY リストで、必須ではありません。 次の構文が有効な SELECT ステートメントの例に示します。  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, FirstName FROM DimCustomer GROUP BY LastName, FirstName;  
SELECT NumberCarsOwned FROM DimCustomer GROUP BY YearlyIncome, NumberCarsOwned;  
SELECT (SalesAmount + TaxAmt + Freight) AS TotalCost FROM FactInternetSales GROUP BY SalesAmount, TaxAmt, Freight;  
SELECT SalesAmount, SalesAmount*1.10 SalesTax FROM FactInternetSales GROUP BY SalesAmount;  
SELECT SalesAmount FROM FactInternetSales GROUP BY SalesAmount, SalesAmount*1.10;  
```  
  
### <a name="h-using-a-group-by-with-multiple-group-by-expressions"></a>H. 複数の GROUP BY 式で GROUP BY の使用  
 次の例は、複数を使用して結果をグループ化`GROUP BY`条件。 各内にいる場合、`OrderDateKey`グループのサブグループで区別することができますがある`DueDateKey`、結果セットに新しいグループが定義されます。  
  
```  
-- Uses AdventureWorks  
  
SELECT OrderDateKey, DueDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSalesGROUP BY OrderDateKey, DueDateKey   
ORDER BY OrderDateKey;  
```  
  
### <a name="i-using-a-group-by-clause-with-a-having-clause"></a>I. GROUP BY 句を HAVING 句と共に使用する  
 次の例では、`HAVING`句で生成されるグループを指定、`GROUP BY`句を結果セットに含める必要があります。 2004 以降での注文の日付のグループのみが結果に含まれます。  
  
```  
-- Uses AdventureWorks  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSales  
GROUP BY OrderDateKey   
HAVING OrderDateKey > 20040000   
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>参照  
 [GROUPING_ID &#40;です。TRANSACT-SQL と #41 です。](~/t-sql/functions/grouping-id-transact-sql.md)   
 [グループ化と #40 です。TRANSACT-SQL と #41 です。](~/t-sql/functions/grouping-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](~/t-sql/queries/select-transact-sql.md)   
 [SELECT 句 &#40;です。TRANSACT-SQL と #41 です。](~/t-sql/queries/select-clause-transact-sql.md)  
  
  




