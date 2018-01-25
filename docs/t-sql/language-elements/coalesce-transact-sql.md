---
title: "結合 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COALESCE
- COALESCE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- expressions [SQL Server], nonnull
- COALESCE function
- first nonnull expressions [SQL Server]
- nonnull expressions
ms.assetid: fafc0dba-f8a8-4aad-9b7f-908e34b74d88
caps.latest.revision: "52"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: fddb9a8535472c153adf036b5afed9584cfbd3d7
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="coalesce-transact-sql"></a>COALESCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

順序で引数を評価し、最初に評価されない最初の式の現在の値を返します`NULL`です。 たとえば、 `SELECT COALESCE(NULL, NULL, 'third_value', 'fourth_value');` 3 番目の値が null ではない最初の値であるために、3 番目の値を返します。 
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
COALESCE ( expression [ ,...n ] )   
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)任意の型。  
  
## <a name="return-types"></a>戻り値の型  
 データ型を返す*式*データ型の最も高い優先順位とします。 すべての式で NULL 値が許可されない場合、結果は NULL 値が許可されない型になります。  
  
## <a name="remarks"></a>解説  
 すべての引数が場合`NULL`、`COALESCE`返します`NULL`です。 型指定された null 値の少なくとも 1 つある必要があります`NULL`です。  
  
## <a name="comparing-coalesce-and-case"></a>COALESCE と CASE の比較  
 `COALESCE`式は、構文のショートカットを`CASE`式。  コードは、 `COALESCE`(*expression1*、*.. .n*) には、次のクエリ オプティマイザーによって書き換えられます`CASE`式。  
  
 ```sql  
 CASE  
 WHEN (expression1 IS NOT NULL) THEN expression1  
 WHEN (expression2 IS NOT NULL) THEN expression2  
 ...  
 ELSE expressionN  
 END  
 ```  
  
 つまり、入力値 (*expression1*、 *expression2*、 *expressionN*など) は、複数回評価されます。 また、SQL 標準に準拠して、サブクエリを含む値式は不明確な式と見なされ、サブクエリは 2 回評価されます。 どちらの場合も、最初の評価とその後の評価で返される結果が異なります。  
  
 たとえば、コード`COALESCE((subquery), 1)`が実行すると、サブクエリは 2 回評価されます。 その結果、クエリの分離レベルによっては、得られる結果が異なる場合があります。 たとえば、コードが返されます`NULL`下にある、`READ COMMITTED`マルチ ユーザー環境での分離レベル。 安定した結果が返されることを確認するを使用して、`SNAPSHOT ISOLATION`分離レベル、または置換`COALESCE`で、`ISNULL`関数。 また、次の例で示すように、サブクエリをサブセレクトにプッシュするクエリを書き直すことができます。  
  
```sql  
SELECT CASE WHEN x IS NOT NULL THEN x ELSE 1 END  
from  
(  
SELECT (SELECT Nullable FROM Demo WHERE SomeCol = 1) AS x  
) AS T;  
  
```  
  
## <a name="comparing-coalesce-and-isnull"></a>COALESCE と ISNULL の比較  
 `ISNULL`関数および`COALESCE`式と同様の目的が動作が異なることができます。  
  
1.  `ISNULL`関数は、1 回だけ評価されます。  前述のように、入力の値を`COALESCE`式を複数回評価されることができます。  
  
2.  結果式のデータ型の判定が異なります。 `ISNULL`最初のパラメーターのデータ型を使用して`COALESCE`に依存して、`CASE`式のルールし、優先順位が高い値のデータ型を返します。  
  
3.  結果式の null 値許容属性が異なる`ISNULL`と`COALESCE`です。 `ISNULL`返す値は常にないと見なされます (戻り値は null 非許容の 1 つを想定) NULLable 一方`COALESCE`null 以外のパラメーターであると見なされます`NULL`です。 したがって、式`ISNULL(NULL, 1)`と`COALESCE(NULL, 1)`それと同等ですが、異なる null 許容属性の値を持ちます。 これにより、相違点の計算列でこれらの式を使用して、キー制約を作成するか、次の例に示すように、インデックスことができるようにスカラー UDF の戻り値を決定論的に行う場合。  
  
    ```sql  
    USE tempdb;  
    GO  
    -- This statement fails because the PRIMARY KEY cannot accept NULL values  
    -- and the nullability of the COALESCE expression for col2   
    -- evaluates to NULL.  
    CREATE TABLE #Demo   
    (   
    col1 integer NULL,   
    col2 AS COALESCE(col1, 0) PRIMARY KEY,   
    col3 AS ISNULL(col1, 0)   
    );   
  
    -- This statement succeeds because the nullability of the   
    -- ISNULL function evaluates AS NOT NULL.  
  
    CREATE TABLE #Demo   
    (   
    col1 integer NULL,   
    col2 AS COALESCE(col1, 0),   
    col3 AS ISNULL(col1, 0) PRIMARY KEY   
    );  
    ```  
  
4.  妥当性検査`ISNULL`と`COALESCE`も異なります。 たとえば、`NULL`値`ISNULL`に変換されます**int**一方の`COALESCE`データ型を指定する必要があります。  
  
5.  `ISNULL`一方、2 つのパラメーターを受け取る`COALESCE`可変個のパラメーターを受け取ります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-running-a-simple-example"></a>A. 簡単な例を実行する  
 例を次にどのように`COALESCE`を null 以外の値を持つ最初の列からデータを選択します。 この例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```sql  
SELECT Name, Class, Color, ProductNumber,  
COALESCE(Class, Color, ProductNumber) AS FirstNotNull  
FROM Production.Product;  
```  
  
### <a name="b-running-a-complex-example"></a>B. 複雑な例を実行する  
 次の例では、`wages` テーブルに、従業員の年俸に関する情報 (時給、給与、歩合) が含まれている 3 つの列を含めています。 ただし、1 人の従業員が受け取る給与の種類は 1 つだけです。 すべての従業員に支払額の合計を調べるには使用`COALESCE`については、null 以外の値のみを受信する`hourly_wage`、 `salary`、および`commission`です。  
  
```sql  
SET NOCOUNT ON;  
GO  
USE tempdb;  
IF OBJECT_ID('dbo.wages') IS NOT NULL  
    DROP TABLE wages;  
GO  
CREATE TABLE dbo.wages  
(  
    emp_id        tinyint   identity,  
    hourly_wage   decimal   NULL,  
    salary        decimal   NULL,  
    commission    decimal   NULL,  
    num_sales     tinyint   NULL  
);  
GO  
INSERT dbo.wages (hourly_wage, salary, commission, num_sales)  
VALUES  
    (10.00, NULL, NULL, NULL),  
    (20.00, NULL, NULL, NULL),  
    (30.00, NULL, NULL, NULL),  
    (40.00, NULL, NULL, NULL),  
    (NULL, 10000.00, NULL, NULL),  
    (NULL, 20000.00, NULL, NULL),  
    (NULL, 30000.00, NULL, NULL),  
    (NULL, 40000.00, NULL, NULL),  
    (NULL, NULL, 15000, 3),  
    (NULL, NULL, 25000, 2),  
    (NULL, NULL, 20000, 6),  
    (NULL, NULL, 14000, 4);  
GO  
SET NOCOUNT OFF;  
GO  
SELECT CAST(COALESCE(hourly_wage * 40 * 52,   
   salary,   
   commission * num_sales) AS money) AS 'Total Salary'   
FROM dbo.wages  
ORDER BY 'Total Salary';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```   
 Total Salary  
 ------------  
 10000.00  
 20000.00  
 20800.00  
 30000.00  
 40000.00  
 41600.00  
 45000.00  
 50000.00  
 56000.00  
 62400.00  
 83200.00  
 120000.00  
  
 (12 row(s) affected)
 ```  
  
### <a name="c-simple-example"></a>C: 簡単な例  
 次の例でどのように`COALESCE`null 以外の値を持つ最初の列からデータを選択します。 この例を想定する、`Products`テーブルには、このデータが含まれています。  
  
 ```  
 Name         Color      ProductNumber  
 ------------ ---------- -------------  
 Socks, Mens  NULL       PN1278  
 Socks, Mens  Blue       PN1965  
 NULL         White      PN9876
 ```  
  
 次の結合クエリを実行しています。  
  
```sql  
SELECT Name, Color, ProductNumber, COALESCE(Color, ProductNumber) AS FirstNotNull   
FROM Products ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 Name         Color      ProductNumber  FirstNotNull  
 ------------ ---------- -------------  ------------  
 Socks, Mens  NULL       PN1278         PN1278  
 Socks, Mens  Blue       PN1965         Blue  
 NULL         White      PN9876         White
 ```  
  
 最初の行のことに注意して、`FirstNotNull`値は`PN1278`ではなく、`Socks, Mens`です。 これは、ため、`Name`のパラメーターとして列が指定されませんでした`COALESCE`の例です。  
  
### <a name="d-complex-example"></a>D: 複雑な例  
 次の例では`COALESCE`を 3 つの列の値を比較し、この列に null 以外の値のみを返します。  
  
```sql  
CREATE TABLE dbo.wages  
(  
    emp_id        tinyint   NULL,  
    hourly_wage   decimal   NULL,  
    salary        decimal   NULL,  
    commission    decimal   NULL,  
    num_sales     tinyint   NULL  
);  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (1, 10.00, NULL, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (2, 20.00, NULL, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (3, 30.00, NULL, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (4, 40.00, NULL, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (5, NULL, 10000.00, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (6, NULL, 20000.00, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (7, NULL, 30000.00, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (8, NULL, 40000.00, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (9, NULL, NULL, 15000, 3);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (10,NULL, NULL, 25000, 2);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (11, NULL, NULL, 20000, 6);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (12, NULL, NULL, 14000, 4);  
  
SELECT CAST(COALESCE(hourly_wage * 40 * 52,   
   salary,   
   commission * num_sales) AS decimal(10,2)) AS TotalSalary   
FROM dbo.wages  
ORDER BY TotalSalary;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Total Salary  
 ------------  
 10000.00  
 20000.00  
 20800.00  
 30000.00  
 40000.00  
 41600.00  
 45000.00  
 50000.00  
 56000.00  
 62400.00  
 83200.00  
 120000.00
 ```  
  
## <a name="see-also"></a>参照  
 [ISNULL &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/isnull-transact-sql.md)   
 [CASE &#40;Transact-SQL&#41;](../../t-sql/language-elements/case-transact-sql.md)  
  
  
