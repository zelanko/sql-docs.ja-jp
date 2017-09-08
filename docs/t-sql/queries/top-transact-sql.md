---
title: "上部 (TRANSACT-SQL) |Microsoft ドキュメント"
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
- TOP_TSQL
- TOP
dev_langs:
- TSQL
helpviewer_keywords:
- TOP clause
- first set of query result rows [SQL Server]
- TOP clause, about TOP clause
- queries [SQL Server], results
ms.assetid: da983c0a-06c5-4cf8-a6a4-7f9d66f34f2c
caps.latest.revision: 60
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9e360ecdae24cbe93b0ed75215819ad4bb9e6bff
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="top-transact-sql"></a>TOP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  クエリの結果で返される行の制限が指定数の行または内の行の割合に設定[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。 ORDER BY 句と共に TOP を使用すると、結果セットは、最初に制限されます*N*最初を返します、順序付けられた行の番号。 それ以外の場合、 *N*が任意の順序で行の数。 SELECT ステートメントから返される行、または INSERT、UPDATE、MERGE、DELETE ステートメントで処理する行の数を指定するには、この句を使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
[   
    TOP (expression) [PERCENT]  
    [ WITH TIES ]  
]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
[   
    TOP ( expression )   
    [ WITH TIES ]  
]  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 返す行数を指定する数式を指定します。 *式*暗黙的に変換されます、 **float** % は、それ以外の指定した場合の値に変換されます**bigint**です。  
  
 PERCENT  
 クエリが最初のメッセージだけを返すことを示します*式*結果セットから行の比率。 小数値は整数値に切り上げられます。  
  
 WITH TIES  
 限定された結果セットの最下位を分け合う複数の行を返す場合に使用します。 使用する必要があります、 **ORDER BY**句。 **WITH TIES**で指定された値よりも返される行数が増えますが発生する可能性があります*式*です。 たとえば場合、*式*5 が 2 に設定されている追加の行の値に一致、 **ORDER BY** 7 行が行 5 の場合、結果セット内の列に格納されます。  
  
 TOP...WITH TIES は SELECT ステートメントでのみ使用でき、ORDER BY 句が指定されている必要があります。 同順位のレコードが返される順序は任意です。 ORDER BY はこの規則に影響しません。  
  
## <a name="best-practices"></a>ベスト プラクティス  
 SELECT ステートメントでは、必ず ORDER BY 句と TOP 句を使用してください。 これは、TOP の処理対象の行を指定するための唯一の方法です。  
  
 クエリ ページング ソリューションを実装するには、TOP 句ではなく ORDER BY 句で OFFSET と FETCH を使用します。 OFFSET 句と FETCH 句を使用した方が、ページング ソリューション (データのチャンクまたは "ページ" をクライアントに送信するソリューション) を容易に実装できます。 詳細については、「[ORDER BY 句 (Transact-SQL)](../../t-sql/queries/select-order-by-clause-transact-sql.md)」を参照してください。  
  
 返される行の数を制限するには、SET ROWCOUNT ではなく TOP (または OFFSET と FETCH) を使用します。 SET ROWCOUNT の代わりにこれらのメソッドを使用することをお勧めする理由は、以下のとおりです。  
  
-   、SELECT ステートメントの一部として、クエリ オプティマイザーがの値を認識できます*式*、TOP 句または FETCH 句クエリの最適化中にします。 SET ROWCOUNT はクエリを実行するステートメントの外部で使用されるので、その値をクエリ プランで認識することはできません。  
  
## <a name="compatibility-support"></a>互換性サポート  
 旧バージョンとの互換性のために、SELECT ステートメントではかっこが省略可能になっています。 かっこが必須となっている INSERT、UPDATE、MERGE、および DELETE ステートメントとの一貫性を保つために、SELECT ステートメント内の TOP でもかっこを常に使用することをお勧めします。  
  
## <a name="interoperability"></a>相互運用性  
 TOP 式は、トリガーが起動されたときに実行されるステートメントには影響しません。 **挿入**と**削除**トリガー内のテーブルには、INSERT、UPDATE、MERGE、または DELETE ステートメントによって実際に影響を受けた行のみが返されます。 たとえば、TOP 句が含まれる INSERT ステートメントの結果として INSERT TRIGGER が起動された場合、  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ビューを介して行を更新をできます。 TOP 句はビュー定義に含めることができるため、行が TOP 式の要件を満たさなくなると、更新したときに特定の行がビューから削除される場合があります。  
  
 MERGE ステートメントで指定すると、TOP 句が適用される*後*ソース テーブル全体と対象テーブル全体が参加しているし、insert、update、または削除操作の対象とならない結合された行が削除されます。 TOP 句を使用すると、結合された行の数が指定の値まで減少し、挿入、更新、または削除操作が残りの結合された行に順序付けなしで適用されます。 つまり、WHEN 句で定義された各操作に行を割り当てる順序に決まりはありません。 たとえば、TOP (10) と指定すると 10 行に影響し、そのうち 7 行が更新されて 3 行が挿入されたり、1 行が削除され、5 行が更新され、4 行が挿入されたりします。 MERGE ステートメントはソース テーブルと対象テーブルの両方のフル テーブル スキャンを実行するので、TOP 句を使用し、複数のバッチを作成して大きなテーブルを変更すると、I/O パフォーマンスが影響を受ける場合があります。 この場合は、一連のすべてのバッチが新しい行を対象としていることを確認してください。  
  
 UNION、UNION ALL、EXCEPT、または INTERSECT 演算子を含む TOP 句をクエリで指定する場合は注意が必要です。 これらの演算子を選択操作で使用するとき、TOP 句および ORDER BY 句が論理的に処理される順序は必ずしも直感的ではないため、記述したクエリによって予期しない結果が返される場合があります。 たとえば、次のテーブルとデータがある場合に、最も安価な赤色の自動車と青色の自動車 (つまり赤色のセダンと青色のバン) を取得する必要があるとします。  
  
```  
CREATE TABLE dbo.Cars(Model varchar(15), Price money, Color varchar(10));  
INSERT dbo.Cars VALUES  
    ('sedan', 10000, 'red'), ('convertible', 15000, 'blue'),   
    ('coupe', 20000, 'red'), ('van', 8000, 'blue');  
```  
  
 これらの結果を得るためには、次のクエリを記述します。  
  
```  
SELECT TOP(1) Model, Color, Price  
FROM dbo.Cars  
WHERE Color = 'red'  
UNION ALL  
SELECT TOP(1) Model, Color, Price  
FROM dbo.Cars  
WHERE Color = 'blue'  
ORDER BY Price ASC;  
```  
  
 以下に結果セットを示します。  
  
 `Model         Color      Price`  
  
 `------------- ---------- -------`  
  
 `sedan         red        10000.00`  
  
 `convertible   blue       15000.00`  
  
 TOP 句は論理的には ORDER BY 句の前に実行され、演算子 (この場合は UNION ALL) の結果が並べ替えられるため、予期しない結果が返されます。 したがって、前のクエリは任意の赤色の自動車と青色の自動車を 1 つずつ返し、その和集合の結果を価格で並べ替えます。 目的の結果を得るための正しいクエリの例を次に示します。  
  
```  
SELECT Model, Color, Price  
FROM (SELECT TOP(1) Model, Color, Price  
      FROM dbo.Cars  
      WHERE Color = 'red'  
      ORDER BY Price ASC) AS a  
UNION ALL  
SELECT Model, Color, Price  
FROM (SELECT TOP(1) Model, Color, Price  
      FROM dbo.Cars  
      WHERE Color = 'blue'  
      ORDER BY Price ASC) AS b;  
```  
  
 TOP と ORDER BY をサブセレクト操作で使用することにより、ORDER BY 句の結果が TOP 句に適用され、UNION 操作の結果の並べ替えには使用されなくなります。  
  
 以下に結果セットを示します。  
  
 `Model         Color      Price`  
  
 `------------- ---------- -------`  
  
 `sedan         red        10000.00`  
  
 `van           blue        8000.00`  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 TOP を INSERT、UPDATE、MERGE、または DELETE と共に使用する場合、参照される行は任意の順序に並べられません。また、これらのステートメントで、ORDER BY 句を直接指定することはできません。 TOP を使用して意味のある順序で行を挿入、削除、変更する必要がある場合は、サブセレクト ステートメントで ORDER BY 句を指定して TOP を使用する必要があります。 例については、後の「例」のセクションを参照してください。  
  
 パーティション ビューでは、UPDATE および DELETE ステートメントで TOP を使用することはできません。  
  
 (同じクエリ スコープ内の) 同じクエリ式で TOP を OFFSET および FETCH と組み合わせて使用することはできません。 詳細については、「[ORDER BY 句 (Transact-SQL)](../../t-sql/queries/select-order-by-clause-transact-sql.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
|カテゴリ|主な構文要素|  
|--------------|------------------------------|  
|[基本構文](#BasicSyntax)|TOP および PERCENT|  
|[同順位の値を含む](#tie)|WITH TIES|  
|[DELETE、INSERT、または UPDATE によって影響を受ける行数を制限します。](#DML)|DELETE、INSERT、UPDATE|  
  
###  <a name="BasicSyntax"></a>基本構文  
 このセクションの例では、最低限必要な構文を使用して ORDER BY 句の基本機能を示します。  
  
#### <a name="a-using-top-with-a-constant-value"></a>A. 定数値を指定して TOP を使用する  
 次の例では、クエリの結果セットで返される従業員の数を、定数値を使用して指定します。 最初の例では、ORDER BY 句が使用されていないため、先頭の 10 行が任意の順序で返されます。 2 番目の例では、ORDER BY 句が使用されているため、新規採用者が新しい方から 10 名返されます。  
  
```  
USE AdventureWorks2012;  
GO  
-- Select the first 10 random employees.  
SELECT TOP(10)JobTitle, HireDate  
FROM HumanResources.Employee;  
GO  
-- Select the first 10 employees hired most recently.  
SELECT TOP(10)JobTitle, HireDate  
FROM HumanResources.Employee  
ORDER BY HireDate DESC;  
  
```  
  
#### <a name="b-using-top-with-a-variable"></a>B. 変数を指定して TOP を使用する  
 次の例では、クエリの結果セットで返される従業員の数を、変数を使用して指定します。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @p AS int = 10;  
SELECT TOP(@p)JobTitle, HireDate, VacationHours  
FROM HumanResources.Employee  
ORDER BY VacationHours DESC  
GO  
  
```  
  
#### <a name="c-specifying-a-percentage"></a>C. 割合を指定する  
 次の例では、クエリの結果セットで返される従業員の数を、PERCENT を使用して指定します。 290 の従業員がある、`HumanResources.Employee`テーブル。 290 の 5% は小数を含む値なので、整数に切り上げられます。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT TOP(5)PERCENT JobTitle, HireDate  
FROM HumanResources.Employee  
ORDER BY HireDate DESC;  
  
```  
  
###  <a name="tie"></a>同順位の値を含む  
  
#### <a name="a-using-with-ties-to-include-rows-that-match-the-values-in-the-last-row"></a>A. WITH TIES を使用して、最後の行の値と一致する行を含める  
 次の例は、先頭を取得`10`パーセントのすべての従業員を最高レベルの給与とに従って、給与の降順で順序を返します。 指定する`WITH TIES`(最後の行) が返された一番低い給与と同じ給与をされている任意の従業員が、結果セットにも含まれていることを確認は、これを超える場合でも`10`従業員の比率。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT TOP(10)WITH TIES  
pp.FirstName, pp.LastName, e.JobTitle, e.Gender, r.Rate  
FROM Person.Person AS pp   
    INNER JOIN HumanResources.Employee AS e  
        ON pp.BusinessEntityID = e.BusinessEntityID  
    INNER JOIN HumanResources.EmployeePayHistory AS r  
        ON r.BusinessEntityID = e.BusinessEntityID  
ORDER BY Rate DESC;  
  
```  
  
###  <a name="DML"></a>DELETE、INSERT、または UPDATE によって影響を受ける行数を制限します。  
  
#### <a name="a-using-top-to-limit-the-number-of-rows-deleted"></a>A. TOP を使用して削除する行数を制限する  
 ときに、TOP (*n*) 句を DELETE と共に使用の未定義の選択で、削除操作が実行される *n* 行の数。 DELETE ステートメントがいずれかを選択するは、(*n*) WHERE 句で定義された条件を満たす行の数。 次の例削除`20`からの行、`PurchaseOrderDetail`期限のあるテーブルは、2002 年 7 月 1 日より前の日付。  
  
```  
USE AdventureWorks2012;  
GO  
DELETE TOP (20)   
FROM Purchasing.PurchaseOrderDetail  
WHERE DueDate < '20020701';  
GO  
  
```  
  
 TOP を使用して、意味のある順序で行を削除する必要がある場合は、サブセレクト ステートメントで ORDER BY を指定して TOP を使用する必要があります。 次のクエリでは、納期が早いものから 10 行を `PurchaseOrderDetail` テーブルから削除します。 10 行だけを確実に削除するために、サブセレクト ステートメントではテーブルの主キーの列 (`PurchaseOrderID`) を指定しています。 サブセレクト ステートメントで非キー列を指定すると、指定した列に重複する値が含まれる場合、10 行以上の行が削除される可能性があります。  
  
```  
USE AdventureWorks2012;  
GO  
DELETE FROM Purchasing.PurchaseOrderDetail  
WHERE PurchaseOrderDetailID IN  
   (SELECT TOP 10 PurchaseOrderDetailID   
    FROM Purchasing.PurchaseOrderDetail   
    ORDER BY DueDate ASC);  
GO  
```  
  
#### <a name="b-using-top-to-limit-the-number-of-rows-inserted"></a>B. TOP を使用して挿入する行数を制限する  
 次の例では、`EmployeeSales` テーブルを作成し、上位 5 人の従業員の名前と年度累計売り上げデータを `HumanResources.Employee` テーブルから挿入します。 INSERT ステートメントは、`SELECT` ステートメントで返された、WHERE 句で定義した条件を満たす任意の 5 行を選択します。  OUTPUT 句に挿入される行を表示する、`EmployeeSales`テーブル。 上位 5 人の従業員を特定するために SELECT ステートメントの ORDER BY 句を使用することはありません。  
  
```  
USE AdventureWorks2012 ;  
GO  
IF OBJECT_ID ('dbo.EmployeeSales', 'U') IS NOT NULL  
    DROP TABLE dbo.EmployeeSales;  
GO  
CREATE TABLE dbo.EmployeeSales  
( EmployeeID   nvarchar(11) NOT NULL,  
  LastName     nvarchar(20) NOT NULL,  
  FirstName    nvarchar(20) NOT NULL,  
  YearlySales  money NOT NULL  
 );  
GO  
INSERT TOP(5)INTO dbo.EmployeeSales  
    OUTPUT inserted.EmployeeID, inserted.FirstName, inserted.LastName, inserted.YearlySales  
    SELECT sp.BusinessEntityID, c.LastName, c.FirstName, sp.SalesYTD   
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.SalesYTD > 250000.00  
    ORDER BY sp.SalesYTD DESC;  
  
```  
  
 TOP を使用して意味のある順序で行を挿入する必要がある場合は、次の例に示すように、サブセレクト ステートメントで ORDER BY を指定して TOP を使用する必要があります。 OUTPUT 句に挿入される行を表示する、`EmployeeSales`テーブル。 未定義の行の代わりに、ORDER BY 句の結果に基づいて、上位 5 人の従業員が挿入されます。  
  
```  
INSERT INTO dbo.EmployeeSales  
    OUTPUT inserted.EmployeeID, inserted.FirstName, inserted.LastName, inserted.YearlySales  
    SELECT TOP (5) sp.BusinessEntityID, c.LastName, c.FirstName, sp.SalesYTD   
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.SalesYTD > 250000.00  
    ORDER BY sp.SalesYTD DESC;  
  
```  
  
#### <a name="c-using-top-to-limit-the-number-of-rows-updated"></a>C. TOP を使用して更新する行数を制限する  
 次の例では、TOP 句を使用してテーブルの行を更新します。 ときに、TOP (*n*) UPDATE 句を使用、任意の数の行に対して更新操作を実行します。 つまり、いずれかの選択、UPDATE ステートメント (*n*) WHERE 句で定義された条件を満たす行の数。 次の例では、ある販売員の顧客から 10 人を抽出して別の販売員に割り当てています。  
  
```  
USE AdventureWorks2012;  
UPDATE TOP (10) Sales.Store  
SET SalesPersonID = 276  
WHERE SalesPersonID = 275;  
GO  
```  
  
 TOP を使用して意味のある日時順での更新を適用する場合は、サブセレクト ステートメントで ORDER BY TOP を使用する必要があります。 次の例では、採用日の古い従業員上位 10 人の休暇時間を更新します。  
  
```  
UPDATE HumanResources.Employee  
SET VacationHours = VacationHours + 8  
FROM (SELECT TOP 10 BusinessEntityID FROM HumanResources.Employee  
     ORDER BY HireDate ASC) AS th  
WHERE HumanResources.Employee.BusinessEntityID = th.BusinessEntityID;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、クエリ条件に一致する最上位の 31 行を返します。 **ORDER BY**句を使用して、31 の行は、最初の 31 のアルファベット順の順序に基づいて行が返されるように、`LastName`列です。  
  
 使用して**上部**ties を指定せずします。  
  
```  
SELECT TOP (31) FirstName, LastName   
FROM DimEmployee ORDER BY LastName;  
```  
  
 結果: 31 行が返されます。  
  
 WITH TIES を指定する、TOP を使用しています。  
  
```  
SELECT TOP (31) WITH TIES FirstName, LastName   
FROM DimEmployee ORDER BY LastName;  
```  
  
 結果: 33 行が返されます、31 の行の 3 つの従業員が Brown をという名前を分け合うため。  
  
## <a name="see-also"></a>参照  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [ORDER BY 句 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-order-by-clause-transact-sql.md)   
 [SET ROWCOUNT と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-rowcount-transact-sql.md)   
 [MERGE &#40;Transact-SQL&#41;](../../t-sql/statements/merge-transact-sql.md)  
  
  


