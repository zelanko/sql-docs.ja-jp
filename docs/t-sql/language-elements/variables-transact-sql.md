---
title: "変数 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f372ae86-a003-40af-92de-fa52e3eea13f
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c77c323f8e9dbb2abc010c3fbc9e6d2b349c8ae1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="variables-transact-sql"></a>変数 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

TRANSACT-SQL のローカル変数は、特定の種類の 1 つのデータ値を保持できるオブジェクトです。 バッチ内の変数とスクリプトは、通常、次の場合に使用されます。 

* ループの実行回数をカウントしたり、制御するカウンターとして使用する場合。
* 流れ制御ステートメントによって検査されるデータ値を保持する場合。
* ストアド プロシージャのリターン コードや関数の戻り値によって返されるデータ値を保存する場合。

> [!NOTE]
> 一部の TRANSACT-SQL システム関数名の先頭に 2 つ*で*マーク (@ @)。 以前のバージョンのでは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、@@functions呼びますにグローバル変数、として変数ではない、変数と同じ動作にはありません。 @@functionsシステム関数であり、構文の用法関数の規則に従います。

次のスクリプトは小さなテスト テーブルを作成し、そのテーブルに 26 行を設定する例です。 このスクリプトでは変数を使用して次の 3 つのことを行います。 

* ループの実行回数を管理して、挿入する行数を制御します。
* 整数列に挿入する値を供給します。
* 文字列に挿入する文字を生成する式の一部として機能させます。
```
-- Create the table.
CREATE TABLE TestTable (cola int, colb char(3));
GO
SET NOCOUNT ON;
GO
-- Declare the variable to be used.
DECLARE @MyCounter int;

-- Initialize the variable.
SET @MyCounter = 0;

-- Test the variable to see if the loop is finished.
WHILE (@MyCounter < 26)
BEGIN;
   -- Insert a row into the table.
   INSERT INTO TestTable VALUES
       -- Use the variable to provide the integer value
       -- for cola. Also use it to generate a unique letter
       -- for each row. Use the ASCII function to get the
       -- integer value of 'a'. Add @MyCounter. Use CHAR to
       -- convert the sum back to the character @MyCounter
       -- characters after 'a'.
       (@MyCounter,
        CHAR( ( @MyCounter + ASCII('a') ) )
       );
   -- Increment the variable to count this iteration
   -- of the loop.
   SET @MyCounter = @MyCounter + 1;
END;
GO
SET NOCOUNT OFF;
GO
-- View the data.
SELECT cola, colb
FROM TestTable;
GO
DROP TABLE TestTable;
GO
```

## <a name="declaring-a-transact-sql-variable"></a>Transact-SQL 変数の宣言
DECLARE ステートメントでは、TRANSACT-SQL 変数を初期化します。 
* 名前を割り当てます。 名前は 1 つの @ で始まる必要があります。
* システム提供のデータ型またはユーザー定義データ型と長さを割り当てます。 数値変数の場合は、有効桁数と小数点以下桁数も割り当てます。 XML 型の変数の場合は、省略可能なスキーマ コレクションを割り当てることができます。
* 値を NULL に設定します。

たとえば、次**DECLARE**ステートメントがという名前のローカル変数を作成 **@mycounter**  int データ型を持つ。
```
DECLARE @MyCounter int;
```
複数のローカル変数を宣言するには、最初のローカル変数を定義した後にコンマを付け、次のローカル変数名とデータ型を指定します。

たとえば、次**DECLARE**という 3 つのローカル変数を作成するステートメント **@LastName** 、  **@FirstName** と **@StateProvince** 、し、それぞれを NULL に初期化します。
```
DECLARE @LastName nvarchar(30), @FirstName nvarchar(20), @StateProvince nchar(2);
```

変数のスコープは、変数を参照できる範囲の TRANSACT-SQL ステートメントです。 変数のスコープは、その変数が宣言された時点で始まり、変数が宣言されたバッチやストアド プロシージャが終了した時点で終了します。 たとえば、次のスクリプトでは変数が宣言されたバッチと変数を参照するバッチが異なるため、構文エラーが発生します。
```
USE AdventureWorks2014;
GO
DECLARE @MyVariable int;
SET @MyVariable = 1;
-- Terminate the batch by using the GO keyword.
GO 
-- @MyVariable has gone out of scope and no longer exists.

-- This SELECT statement generates a syntax error because it is
-- no longer legal to reference @MyVariable.
SELECT BusinessEntityID, NationalIDNumber, JobTitle
FROM HumanResources.Employee
WHERE BusinessEntityID = @MyVariable;
```

変数にはローカル スコープがあり、その変数が定義されたバッチまたはプロシージャ内でのみ参照されます。 次の例では、sp_executesql の実行のために作成された入れ子になったスコープでは、より上位のスコープで宣言された変数にはアクセスできないので、エラーが返されます。

```
DECLARE @MyVariable int;
SET @MyVariable = 1;
EXECUTE sp_executesql N'SELECT @MyVariable'; -- this produces an error
```

## <a name="setting-a-value-in-a-transact-sql-variable"></a>Transact-SQL 変数内での値の設定

変数を初めて宣言したときは値が NULL に設定されます。 変数に値を代入するには、SET ステートメントを使用します。 変数に値を代入する場合は、この方法を使用することをお勧めします。 SELECT ステートメントの選択リストの中で変数を参照して、変数に値を代入することもできます。

SET ステートメントを使用して変数に値を代入するには、変数名とその変数に代入する値を含めます。 変数に値を代入する場合は、この方法を使用することをお勧めします。 次のバッチの例では、2 つの変数を宣言し、それぞれに値を代入し、`WHERE` ステートメントの `SELECT` 句でその値を使用しています。

```
USE AdventureWorks2014;
GO
-- Declare two variables.
DECLARE @FirstNameVariable nvarchar(50),
   @PostalCodeVariable nvarchar(15);

-- Set their values.
SET @FirstNameVariable = N'Amy';
SET @PostalCodeVariable = N'BA5 3HX';

-- Use them in the WHERE clause of a SELECT statement.
SELECT LastName, FirstName, JobTitle, City, StateProvinceName, CountryRegionName
FROM HumanResources.vEmployee
WHERE FirstName = @FirstNameVariable
   OR PostalCode = @PostalCodeVariable;
GO
```

選択リストの中で変数を参照して、変数に値を代入することもできます。 選択リストの中で変数を参照する場合は、スカラー値を代入することをお勧めします。スカラー値を代入しないと、SELECT ステートメントからは 1 行しか返されません。 例:

```
USE AdventureWorks2014;
GO
DECLARE @EmpIDVariable int;

SELECT @EmpIDVariable = MAX(EmployeeID)
FROM HumanResources.Employee;
GO
```

> [!WARNING]
> 1 つの SELECT ステートメントに複数の代入句がある場合、SQL Server では式の評価順序が保証されません。 複数の代入の間に参照がある場合のみ、その影響を確認できることに注意してください。

SELECT ステートメントは複数の行を返し、変数参照、非スカラー式場合、変数は、結果セットの最後の行に式の戻り値に設定されます。 たとえば、次のバッチで **@EmpIDVariable** に設定されている、 **BusinessEntityID** 1 である最後の行の値が返されます。

```
USE AdventureWorks2014;
GO
DECLARE @EmpIDVariable int;

SELECT @EmpIDVariable = BusinessEntityID
FROM HumanResources.Employee
ORDER BY BusinessEntityID DESC;

SELECT @EmpIDVariable;
GO
```

## <a name="see-also"></a>参照  
 [宣言@local_variable](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
  
 [SET @local_variable](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
  
 [選択します。@local_variable](../../t-sql/language-elements/select-local-variable-transact-sql.md)  
  
  
