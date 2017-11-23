---
title: "ケース (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/28/2017
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
- CASE_TSQL
- CASE
dev_langs: TSQL
helpviewer_keywords:
- CASE expression [Transact-SQL]
- simple CASE expression
- comparing expressions
- searched CASE expression
ms.assetid: 658039ec-8dc2-4251-bc82-30ea23708cee
caps.latest.revision: "59"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 4d5241ddc65de92d7588e4c8d1ddb7c2e6b08528
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="case-transact-sql"></a>CASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  一連の条件を評価して、考えられる結果式のうちの 1 つを返します。  
  
 CASE 式には 2 つの形式があります。  
  
-   単純 CASE 式では、1 つの式を一連の単純式と比較して結果を決定します。  
  
-   検索 CASE 式では、一連のブール式を評価して結果を判定します。  
  
 どちらの形式も、ELSE 引数 (省略可) をサポートしています。  
  
 CASE は、有効な式を使用できる任意のステートメントや句で使用できます。 たとえば、SELECT、UPDATE、DELETE、SET などのステートメントや、select_list、IN、WHERE、ORDER BY、HAVING などの句で使用できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
Simple CASE expression:   
CASE input_expression   
     WHEN when_expression THEN result_expression [ ...n ]   
     [ ELSE else_result_expression ]   
END   
Searched CASE expression:  
CASE  
     WHEN Boolean_expression THEN result_expression [ ...n ]   
     [ ELSE else_result_expression ]   
END  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CASE  
     WHEN when_expression THEN result_expression [ ...n ]   
     [ ELSE else_result_expression ]   
END  
```  
  
## <a name="arguments"></a>引数  
 *input_expression*  
 単純 CASE 形式を使用した場合に評価される式です。 *input_expression*は任意の有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)です。  
  
 ときに*when_expression*  
 単純な式は、 *input_expression*単純 CASE 形式を使用する場合と比較されます。 *when_expression*有効な式です。 データ型*input_expression*とは、それぞれ*when_expression*同じである必要がありますか、暗黙的な変換をする必要があります。  
  
 *Result_expression*  
 返される式の場合に*input_expression* equals *when_expression*を TRUE に評価または*Boolean_expression*を TRUE に評価します。 *式の結果*は任意の有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)です。  
  
 ELSE*戻り値*  
 比較操作の評価がいずれも TRUE でなかった場合に返される式です。 この引数を省略し、比較操作のいずれも TRUE でなかった場合、CASE は NULL を返します。 *戻り値*有効な式です。 データ型*戻り値*と任意*result_expression*同じである必要がありますか、暗黙的な変換をする必要があります。  
  
 ときに*Boolean_expression*  
 検索 CASE 形式で評価するブール式です。 *Boolean_expression*有効なブール式です。  
  
## <a name="return-types"></a>戻り値の型  
 型のセットから最高の優先順位の型を返します*result_expressions*と、省略可能な*戻り値*です。 詳細については、「[データ型の優先順位 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)」を参照してください。  
  
### <a name="return-values"></a>戻り値  
 **単純 CASE 式:**  
  
 単純 CASE 式では、最初の式が各 WHEN 句の式と比較されて、等しいかどうかが確認されます。 等しかった場合は、THEN 句の式が返されます。  
  
-   実行できるのは、等しいかどうかのチェックだけです。  
  
-   指定された順序で評価 input_expression when_expression 各 WHEN 句を = です。  
  
-   返します、 *result_expression*最初の*input_expression* = *when_expression* TRUE に評価します。  
  
-   ない場合は*input_expression* = *when_expression*を TRUE に評価される、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]を返します、*戻り値*ELSE 句がある場合指定された、または ELSE 句が指定されていない場合は、NULL 値です。  
  
 **検索 CASE 式。**  
  
-   指定の順序で評価*Boolean_expression*各 WHEN 句。  
  
-   返します*result_expression*最初の*Boolean_expression* TRUE に評価します。  
  
-   ない場合は*Boolean_expression*を TRUE に評価される、[!INCLUDE[ssDE](../../includes/ssde-md.md)]を返します、*戻り値*ELSE 句が指定されている場合または ELSE 句が指定されていない場合は、NULL 値です。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、Case 式に入れ子にできるのは 10 レベルまでです。  
  
 CASE 式を使用して、Transact-SQL ステートメント、ステートメント ブロック、ユーザー定義関数、およびストアド プロシージャの実行フローを制御することはできません。 フロー制御のメソッドの一覧は、次を参照してください。[フロー制御言語 &#40;です。TRANSACT-SQL と #41 です。](~/t-sql/language-elements/control-of-flow.md).  
  
 CASE ステートメントは条件を順に評価していき、最初に条件が満たされた時点で評価を止めます。 CASE ステートメントには、評価された式の結果が入力として渡されることがあります。 こうした式の評価中にエラーが発生する可能性もあります。 CASE ステートメントの WHEN 引数に指定された集計式は、あらかじめ評価されて CASE ステートメントに渡されます。 たとえば、次のクエリでは、MAX 集計値を生成する際に 0 除算エラーが発生します。 このエラーが発生するのは、CASE 式が評価される前です。  
  
```tsql  
WITH Data (value) AS   
(   
SELECT 0   
UNION ALL   
SELECT 1   
)   
SELECT   
   CASE   
      WHEN MIN(value) <= 0 THEN 0   
      WHEN MAX(1/value) >= 100 THEN 1   
   END   
FROM Data ;  
```  
  
 WHEN 条件が上から順に評価されるという前提は、スカラー式 (スカラー値を返す非相関サブクエリを含む) では問題ありませんが、集計式では成立しないので注意が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-a-select-statement-with-a-simple-case-expression"></a>A. SELECT ステートメントを単純 CASE 式と共に使用する  
 内で、`SELECT`ステートメントでは、単純な`CASE`式が等しいかどうか確認だけことができます。 他の比較は行われません。 `CASE` 式を使用して、製品ラインのカテゴリの表示をわかりやすいものに変更する例を次に示します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT   ProductNumber, Category =  
      CASE ProductLine  
         WHEN 'R' THEN 'Road'  
         WHEN 'M' THEN 'Mountain'  
         WHEN 'T' THEN 'Touring'  
         WHEN 'S' THEN 'Other sale items'  
         ELSE 'Not for sale'  
      END,  
   Name  
FROM Production.Product  
ORDER BY ProductNumber;  
GO  
  
```  
  
### <a name="b-using-a-select-statement-with-a-searched-case-expression"></a>B. SELECT ステートメントを検索 CASE 式と共に使用する  
 内で、`SELECT`ステートメントでは、検索`CASE`式比較値に基づいて結果セット内で置換する値を許容します。 次の例では、表示価格を、製品の価格範囲に基づいたテキスト コメントとして表示しています。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT   ProductNumber, Name, "Price Range" =   
      CASE   
         WHEN ListPrice =  0 THEN 'Mfg item - not for resale'  
         WHEN ListPrice < 50 THEN 'Under $50'  
         WHEN ListPrice >= 50 and ListPrice < 250 THEN 'Under $250'  
         WHEN ListPrice >= 250 and ListPrice < 1000 THEN 'Under $1000'  
         ELSE 'Over $1000'  
      END  
FROM Production.Product  
ORDER BY ProductNumber ;  
GO  
  
```  
  
### <a name="c-using-case-in-an-order-by-clause"></a>C. ORDER BY 句で CASE を使用する  
 次の例では、ORDER BY 句で CASE 式を使用して、指定された列の値に基づいて行の並べ替え順序を決定しています。 最初の例では、値では、`SalariedFlag`の列、`HumanResources.Employee`テーブルが評価されます。 `SalariedFlag` が 1 に設定されている従業員は `BusinessEntityID` の降順で、 従業員が、 `SalariedFlag` 0 に設定するが order by 句で返される、`BusinessEntityID`で昇順に並べ替えます。 2 番目の例では、`TerritoryName` 列が 'United States' と等しい場合は結果セットが `CountryRegionName` 列の順序に従って並べ替えられ、他のすべての列は `CountryRegionName` の順序に従って並べ替えられます。  
  
```  
SELECT BusinessEntityID, SalariedFlag  
FROM HumanResources.Employee  
ORDER BY CASE SalariedFlag WHEN 1 THEN BusinessEntityID END DESC  
        ,CASE WHEN SalariedFlag = 0 THEN BusinessEntityID END;  
GO  
  
```  
  
```  
SELECT BusinessEntityID, LastName, TerritoryName, CountryRegionName  
FROM Sales.vSalesPerson  
WHERE TerritoryName IS NOT NULL  
ORDER BY CASE CountryRegionName WHEN 'United States' THEN TerritoryName  
         ELSE CountryRegionName END;  
  
```  
  
### <a name="d-using-case-in-an-update-statement"></a>D. UPDATE ステートメントで CASE を使用する  
 次の例では、UPDATE ステートメントで CASE 式を使って、列に対して設定されている値を決定する`VacationHours`を持つ従業員`SalariedFlag`を 0 に設定します。 10 時間差し引くと`VacationHours`負の値に結果`VacationHours`40 時間以外、それ以外の場合は、 `VacationHours` 20 時間が増加します。 OUTPUT 句は、この処理の前後の休暇の値を表示するために使用されています。  
  
```  
USE AdventureWorks2012;  
GO  
UPDATE HumanResources.Employee  
SET VacationHours =   
    ( CASE  
         WHEN ((VacationHours - 10.00) < 0) THEN VacationHours + 40  
         ELSE (VacationHours + 20.00)  
       END  
    )  
OUTPUT Deleted.BusinessEntityID, Deleted.VacationHours AS BeforeValue,   
       Inserted.VacationHours AS AfterValue  
WHERE SalariedFlag = 0;  
  
```  
  
### <a name="e-using-case-in-a-set-statement"></a>E. SET ステートメントで CASE を使用する  
 次の例は、テーブル値関数で SET ステートメントで CASE 式を使って`dbo.GetContactInfo`です。 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベースでユーザーに関連するすべてのデータが格納されている、`Person.Person`テーブル。 たとえば、ユーザーには、従業員、仕入先の代表者、または顧客があります。 最初と最後の名前を返します、指定された`BusinessEntityID`とその人物の連絡先の種類。SET ステートメントで CASE 式を表示する列の値を決定`ContactType`の存在に基づいて、`BusinessEntityID`内の列、 `Employee`、 `Vendor`、または`Customer`テーブル。  
  
```  
  
USE AdventureWorks2012;  
GO  
CREATE FUNCTION dbo.GetContactInformation(@BusinessEntityID int)  
    RETURNS @retContactInformation TABLE   
(  
BusinessEntityID int NOT NULL,  
FirstName nvarchar(50) NULL,  
LastName nvarchar(50) NULL,  
ContactType nvarchar(50) NULL,  
    PRIMARY KEY CLUSTERED (BusinessEntityID ASC)  
)   
AS   
-- Returns the first name, last name and contact type for the specified contact.  
BEGIN  
    DECLARE   
        @FirstName nvarchar(50),   
        @LastName nvarchar(50),   
        @ContactType nvarchar(50);  
  
    -- Get common contact information  
    SELECT   
        @BusinessEntityID = BusinessEntityID,   
@FirstName = FirstName,   
        @LastName = LastName  
    FROM Person.Person   
    WHERE BusinessEntityID = @BusinessEntityID;  
  
    SET @ContactType =   
        CASE   
            -- Check for employee  
            WHEN EXISTS(SELECT * FROM HumanResources.Employee AS e   
                WHERE e.BusinessEntityID = @BusinessEntityID)   
                THEN 'Employee'  
  
            -- Check for vendor  
            WHEN EXISTS(SELECT * FROM Person.BusinessEntityContact AS bec  
                WHERE bec.BusinessEntityID = @BusinessEntityID)   
                THEN 'Vendor'  
  
            -- Check for store  
            WHEN EXISTS(SELECT * FROM Purchasing.Vendor AS v            
                WHERE v.BusinessEntityID = @BusinessEntityID)   
                THEN 'Store Contact'  
  
            -- Check for individual consumer  
            WHEN EXISTS(SELECT * FROM Sales.Customer AS c   
                WHERE c.PersonID = @BusinessEntityID)   
                THEN 'Consumer'  
        END;  
  
    -- Return the information to the caller  
    IF @BusinessEntityID IS NOT NULL   
    BEGIN  
        INSERT @retContactInformation  
        SELECT @BusinessEntityID, @FirstName, @LastName, @ContactType;  
    END;  
  
    RETURN;  
END;  
GO  
  
SELECT BusinessEntityID, FirstName, LastName, ContactType  
FROM dbo.GetContactInformation(2200);  
GO  
SELECT BusinessEntityID, FirstName, LastName, ContactType  
FROM dbo.GetContactInformation(5);  
  
```  
  
### <a name="f-using-case-in-a-having-clause"></a>F. HAVING 句で CASE を使用する  
 次の例では、HAVING 句で CASE 式を使用して、SELECT ステートメントで返される行を制限しています。 ステートメント内の各役職の最も高い時給が返されます、`HumanResources.Employee`テーブル。 HAVING 句では、最も高い時給が男性の場合には 40 ドル、女性の場合には 42 ドルを超えている役職のみが返されるように制限しています。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT JobTitle, MAX(ph1.Rate)AS MaximumRate  
FROM HumanResources.Employee AS e  
JOIN HumanResources.EmployeePayHistory AS ph1 ON e.BusinessEntityID = ph1.BusinessEntityID  
GROUP BY JobTitle  
HAVING (MAX(CASE WHEN Gender = 'M'   
        THEN ph1.Rate   
        ELSE NULL END) > 40.00  
     OR MAX(CASE WHEN Gender  = 'F'   
        THEN ph1.Rate    
        ELSE NULL END) > 42.00)  
ORDER BY MaximumRate DESC;  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="g-using-a-select-statement-with-a-case-expression"></a>G. CASE 式と共に SELECT ステートメントを使用します。  
 SELECT ステートメントでは、CASE 式では、比較値に基づいて結果セット内で置換する値。 次の例では、CASE 式を使用して、製品ラインのカテゴリをわかりやすく表示を変更します。 値が存在しない場合、テキスト"販売ではなく ' が表示されます。  
  
```  
-- Uses AdventureWorks  
  
SELECT   ProductAlternateKey, Category =  
      CASE ProductLine  
         WHEN 'R' THEN 'Road'  
         WHEN 'M' THEN 'Mountain'  
         WHEN 'T' THEN 'Touring'  
         WHEN 'S' THEN 'Other sale items'  
         ELSE 'Not for sale'  
      END,  
   EnglishProductName  
FROM dbo.DimProduct  
ORDER BY ProductKey;  
```  
  
### <a name="h-using-case-in-an-update-statement"></a>H. UPDATE ステートメントで CASE を使用する  
 次の例では、UPDATE ステートメントで CASE 式を使って、列に対して設定されている値を決定する`VacationHours`を持つ従業員`SalariedFlag`を 0 に設定します。 10 時間差し引くと`VacationHours`負の値に結果`VacationHours`40 時間以外、それ以外の場合は、 `VacationHours` 20 時間が増加します。  
  
```  
-- Uses AdventureWorks   
  
UPDATE dbo.DimEmployee  
SET VacationHours =   
    ( CASE  
         WHEN ((VacationHours - 10.00) < 0) THEN VacationHours + 40  
         ELSE (VacationHours + 20.00)   
       END  
    )   
WHERE SalariedFlag = 0;  
  
```  
  
## <a name="see-also"></a>参照  
 [式 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [合体 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/coalesce-transact-sql.md)   
 [Iif 関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/logical-functions-iif-transact-sql.md)   
 [選択 (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/logical-functions-choose-transact-sql.md)  
  
  



