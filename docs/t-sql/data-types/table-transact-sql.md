---
title: "テーブル (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- table data type [SQL Server]
- table variables [SQL Server]
ms.assetid: 1ef0b60e-a64c-4e97-847b-67930e3973ef
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b22ecfa04f949af77df974abc3359b7bc5144a82
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="table-transact-sql"></a>table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

後で処理できるように結果セットを格納するために使用できる特別なデータ型です。 **テーブル**は主に、テーブル値関数の結果セットとして返される行のセットの一時的なストレージを使用します。 型である関数および変数を宣言できます**テーブル**です。 **テーブル**変数は、関数、ストアド プロシージャ、およびバッチで使用できます。 型の変数を宣言する**テーブル**を使用して[DECLARE @local_variable](../../t-sql/language-elements/declare-local-variable-transact-sql.md)です。
  

**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
table_type_definition ::=   
    TABLE ( { <column_definition> | <table_constraint> } [ ,...n ] )   
  
<column_definition> ::=   
    column_name scalar_data_type   
    [ COLLATE <collation_definition> ]   
    [ [ DEFAULT constant_expression ] | IDENTITY [ ( seed , increment ) ] ]   
    [ ROWGUIDCOL ]   
    [ column_constraint ] [ ...n ]   
  
 <column_constraint> ::=   
    { [ NULL | NOT NULL ]   
    | [ PRIMARY KEY | UNIQUE ]   
    | CHECK ( logical_expression )   
    }   
  
<table_constraint> ::=   
     { { PRIMARY KEY | UNIQUE } ( column_name [ ,...n ] )  
     | CHECK ( logical_expression )   
     }   
```  
  
## <a name="arguments"></a>引数  
*table_type_definition*  
CREATE TABLE でテーブルを定義するために使用する情報のサブセットと同じです。 テーブルの定義には、列の定義、名前、データ型、および制約が含まれます。 許可される制約の種類は、PRIMARY KEY、UNIQUE KEY、および NULL だけです。  
構文の詳細については、次を参照してください。 [CREATE TABLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-table-transact-sql.md)、[関数 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-function-transact-sql.md)、および[DECLARE @local_variable & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/declare-local-variable-transact-sql.md).
  
*collation_definition*  
構成されている列の照合順序、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ロケールと比較形式、Windows ロケールとバイナリ表記法または[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]照合順序。 場合*collation_definition*が指定されていない、現在のデータベースの照合順序が列に継承します。 または、列が共通言語ランタイム (CLR) ユーザー定義型として定義されている場合は、ユーザー定義型の照合順序が列に継承されます。
  
## <a name="remarks"></a>解説  
**テーブル**変数は、次の例に示すように、バッチの FROM 句での名前で参照できます。
  
```sql
SELECT Employee_ID, Department_ID FROM @MyTableVar;  
```  
  
FROM 句では、外部**テーブル**変数は、次の例で示すように、別名を使用して参照する必要があります。
  
```sql
SELECT EmployeeID, DepartmentID   
FROM @MyTableVar m  
JOIN Employee on (m.EmployeeID =Employee.EmployeeID AND  
   m.DepartmentID = Employee.DepartmentID);  
```  
  
**テーブル**変数は、クエリ プランが変化せず、再コンパイルの影響が大きい場合がある小規模のクエリに対して、次の利点を提供します。
-   A**テーブル**変数がローカル変数のように動作します。 この変数には適切に定義されたスコープがあります。 スコープは、それが宣言されている関数、ストアド プロシージャ、またはバッチです。  
     そのスコープ内で、**テーブル**変数は、通常のテーブルのように使用できます。 また、SELECT、INSERT、UPDATE、および DELETE の各ステートメントで、テーブルまたはテーブル式が使用されている任意の場所で適用できます。 ただし、**テーブル**次のステートメントでは使用できません。  
  
```sql
SELECT select_list INTO table_variable;
```
  
**テーブル**変数が関数、ストアド プロシージャ、または定義されているバッチの最後に自動的にクリーンアップします。
  
-   **テーブル**ストアド プロシージャで使用される変数が、ストアド プロシージャのコンパイルのパフォーマンスに影響を与えるコストベースの選択肢がない場合に一時テーブルを使用する場合よりも少ない。  
-   使用するトランザクション**テーブル**変数が最後の更新の間にのみ、**テーブル**変数。 したがって、**テーブル**変数が小さいロックとログ記録のリソースを必要とします。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項
**テーブル**変数には、分布統計情報はありません、それらは再コンパイルがトリガーされません。 したがって、多くの場合、オプティマイザーはテーブル変数に行がないことを前提としてクエリ プランを構築します。 このため、多数の行 (100 行を超える行) を使用する可能性がある場合は、テーブル変数を慎重に使用する必要があります。 このような場合、一時テーブルによって問題が解決することがあります。 また、他のテーブルとテーブル変数を結合するクエリでは、オプティマイザーがテーブル変数の適切な基数を使用すると、再コンパイルのヒントを使用します。
  
**テーブル**では、変数はサポートされていない、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オプティマイザーのコストベースの推論モデル。 したがって、効果的なクエリ プランを実現するためにコストベースの選択が必要な場合は、使用しないでください。 コストベースの選択が必要な場合は、一時テーブルが推奨されます。 これには、通常、結合、並列処理の決定、およびインデックス選択を含むクエリが含まれます。
  
変更するクエリ**テーブル**変数は、並列クエリ実行プランを生成しません。 パフォーマンスに影響が非常に大きいとき**テーブル**変数、または**テーブル**、複雑なクエリで変数を変更します。 このような場合は、代わりに一時テーブルを使用することを検討してください。 詳細については、「[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)」を参照してください。 読み取るクエリは**テーブル**変数を変更せずの並列処理を実行できます。
  
インデックスが明示的に作成することはできません**テーブル**変数、および統計情報はありませんが上に保持されます**テーブル**変数。 場合によっては、インデックスと統計をサポートする一時テーブルを使用した方がパフォーマンスが向上する場合があります。 一時テーブルの詳細については、次を参照してください。 [CREATE TABLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-table-transact-sql.md).
  
CHECK 制約、既定値、および計算列、**テーブル**型の宣言は、ユーザー定義関数を呼び出すことはできません。
  
間における代入操作**テーブル**変数はサポートされていません。
  
**テーブル**変数がスコープに制限されているし、永続的なデータベースの一部ではない、トランザクションのロールバックは影響ありません。
  
table 変数は、作成後に変更できません。
  
## <a name="examples"></a>使用例  
  
### <a name="a-declaring-a-variable-of-type-table"></a>A. table 型の変数を宣言する  
次の例では、UPDATE ステートメントの OUTPUT 句で指定される値を格納する `table` 変数を作成します。 この後に、`SELECT` 内の値、および `@MyTableVar` テーブルの更新操作の結果を返す 2 つの `Employee` ステートメントが続きます。 なおで結果、`INSERTED.ModifiedDate`列の値と異なる、`ModifiedDate`内の列、`Employee`テーブル。 これは、`AFTER UPDATE` の値を現在の日付に更新する `ModifiedDate` トリガーが、`Employee` テーブルで定義されるためです。 ただし、`OUTPUT` が返す列には、トリガーが起動される前の値が反映されています。 詳細については、次を参照してください。 [OUTPUT 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/output-clause-transact-sql.md).
  
```sql
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table(  
    EmpID int NOT NULL,  
    OldVacationHours int,  
    NewVacationHours int,  
    ModifiedDate datetime);  
UPDATE TOP (10) HumanResources.Employee  
SET VacationHours = VacationHours * 1.25   
OUTPUT INSERTED.BusinessEntityID,  
       DELETED.VacationHours,  
       INSERTED.VacationHours,  
       INSERTED.ModifiedDate  
INTO @MyTableVar;  
--Display the result set of the table variable.  
SELECT EmpID, OldVacationHours, NewVacationHours, ModifiedDate  
FROM @MyTableVar;  
GO  
--Display the result set of the table.  
--Note that ModifiedDate reflects the value generated by an  
--AFTER UPDATE trigger.  
SELECT TOP (10) BusinessEntityID, VacationHours, ModifiedDate  
FROM HumanResources.Employee;  
GO  
```  
  
### <a name="b-creating-an-inline-table-valued-function"></a>B. インライン テーブル値関数を作成する  
次の例では、インライン テーブル値関数を返します。 次の 3 つの列を返します`ProductID`、`Name`店舗別合計を年度累計の集計`YTD Total`ストアに販売された製品ごとです。
  
```sql
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'Sales.ufn_SalesByStore', N'IF') IS NOT NULL  
    DROP FUNCTION Sales.ufn_SalesByStore;  
GO  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
GO  
```  
  
関数を呼び出すには、次のクエリを実行します。
  
```sql
SELECT * FROM Sales.ufn_SalesByStore (602);  
```  
  
## <a name="see-also"></a>参照
[COLLATE & #40 です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)  
[ユーザー定義関数](../../relational-databases/user-defined-functions/user-defined-functions.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[使用してテーブル値パラメーター (&) #40; データベース エンジン"&"#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)  
[クエリ ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md)
  
  

