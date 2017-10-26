---
title: "+ (文字列連結)(TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- concatenation
- +
- string
dev_langs:
- TSQL
helpviewer_keywords:
- concatenation [SQL Server]
- string concatenation operators
- + (string concatenation)
ms.assetid: 35cb3d7a-48f5-4b13-926c-a9d369e20ed7
caps.latest.revision: 51
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 1fd13b0b05dcb3b15d37d5a642a734b99ad004e5
ms.contentlocale: ja-jp
ms.lasthandoff: 10/24/2017

---
# <a name="-string-concatenation-transact-sql"></a>+ (文字列連結) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  文字列式の中の演算子であり、2 つ以上の文字列やバイナリ文字列、列、文字列と列名の組み合わせを 1 つの式に連結します (文字列演算子)。  たとえば`SELECT 'book'+'case';`返します`bookcase`です。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)任意のデータのいずれかの型文字とバイナリ データ型に分類を除く、**イメージ**、 **ntext**、または**テキスト**データ型。 両方の式は、同じデータ型でなければなりません。または、一方の式をもう一方の式のデータ型に暗黙的に変換できる必要があります。  
  
 2 つのバイナリ間にある任意の文字列を、その両端にあるバイナリ文字列と結合する場合、文字データへの明示的な変換を使用する必要があります。 ときに次の例は`CONVERT`、または`CAST`、バイナリ連結で使用する必要があります、いつ`CONVERT`、または`CAST`、使用する必要はありません。  
  
```  
DECLARE @mybin1 varbinary(5), @mybin2 varbinary(5)  
SET @mybin1 = 0xFF  
SET @mybin2 = 0xA5  
-- No CONVERT or CAST function is required because this example   
-- concatenates two binary strings.  
SELECT @mybin1 + @mybin2  
-- A CONVERT or CAST function is required because this example  
-- concatenates two binary strings plus a space.  
SELECT CONVERT(varchar(5), @mybin1) + ' '   
   + CONVERT(varchar(5), @mybin2)  
-- Here is the same conversion using CAST.  
SELECT CAST(@mybin1 AS varchar(5)) + ' '   
   + CAST(@mybin2 AS varchar(5))  
  
```  
  
## <a name="result-types"></a>戻り値の型  
 優先順位が最も高い引数のデータ型を返します。 詳細については、「[データ型の優先順位 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 + (文字列連結) 演算子は、長さがゼロの空の文字列に対して使用するときと、NULL、または不明な値に対して使用するときでは、動作が異なります。 長さがゼロの文字列は、間に文字を挟まない 2 つの単一引用符で指定できます。 長さがゼロのバイナリ文字列は、16 進定数で指定したバイト値を持たない 0x で指定できます。 長さがゼロの文字列の連結では、常に 2 つの指定された文字列を連結します。 NULL 値の文字列を操作した場合、連結の結果はセッションの設定によって決まります。 NULL 値に対して実行される算術演算の場合、既知の値に NULL 値を追加すると、結果は通常、不明な値になります。同様に、NULL 値に対して実行される文字列連結演算でも、NULL の結果を生成する必要があります。 ただしの設定を変更することでこの動作を変更できます`CONCAT_NULL_YIELDS_NULL`は現在のセッションです。 詳細については、「[SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md)」をご覧ください。  
  
 文字列の連結の結果が 8,000 バイトを超える場合、結果は切り捨てられます。 ただし、連結する文字列の少なくとも一方が大きな値の型の場合、切り捨ては行われません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-string-concatenation"></a>A. 文字列連結を使用する  
 次の例では、複数の文字の列から、`Name` という列見出しで単一の列を作成します。個人の姓に、コンマとスペース 1 つを連結し、さらにその名を連結します。 結果セットは、姓、名の順で昇順に表示されます。  
  
```  
-- Uses AdventureWorks  
  
SELECT (LastName + ', ' + FirstName) AS Name  
FROM Person.Person  
ORDER BY LastName ASC, FirstName ASC;  
```  
  
### <a name="b-combining-numeric-and-date-data-types"></a>B. 数値型と日付型を結合する  
 次の例では、`CONVERT`関数を連結**数値**と**日付**データ型。  
  
```  
-- Uses AdventureWorks  
  
SELECT 'The order is due on ' + CONVERT(varchar(12), DueDate, 101)  
FROM Sales.SalesOrderHeader  
WHERE SalesOrderID = 50001;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ------------------------------------------------  
 The order is due on 04/23/2007  
 (1 row(s) affected)
 ```  
  
### <a name="c-using-multiple-string-concatenation"></a>C. 複数の文字列の連結を使用する  
 次の例では、複数の文字列を連結して 1 つの長い文字列を形成し、[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] の副社長の姓と、名のイニシャルを表示します。 姓の後ろにコンマを追加し、名のイニシャルの後ろにピリオドを追加します。  
  
```  
-- Uses AdventureWorks  
  
SELECT (LastName + ',' + SPACE(1) + SUBSTRING(FirstName, 1, 1) + '.') AS Name, e.JobTitle  
FROM Person.Person AS p  
    JOIN HumanResources.Employee AS e  
    ON p.BusinessEntityID = e.BusinessEntityID  
WHERE e.JobTitle LIKE 'Vice%'  
ORDER BY LastName ASC;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Name               Title  
 -------------      ---------------`  
 Duffy, T.          Vice President of Engineering  
 Hamilton, J.       Vice President of Production  
 Welcker, B.        Vice President of Sales  

 (3 row(s) affected)
 ```  
 
### <a name="d-using-large-strings-in-concatenation"></a>D. 大きな文字列連結を使用してください。
次の例では、1 つの長い文字列を形成する複数の文字列を連結し、最終的な文字列の長さの計算を試みます。 結果セットの最終的な長さ 16000 から式の評価の開始が残っているため、 @x + @z + @y = > (@x + @z) +@yです。 この場合の結果 (@x + @z) が 8,000 バイトで切り捨てられ、 @y 16000 最終的な文字列の長さは、結果セットに追加されます。 @y文字列大きな値の型は、切り捨ては行われません。

```
DECLARE @x varchar(8000) = replicate('x', 8000)
DECLARE @y varchar(max) = replicate('y', 8000)
DECLARE @z varchar(8000) = replicate('z',8000)
SET @y = @x + @z + @y
-- The result of following select is 16000
SELECT len(@y) AS y
GO
```
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 y        
 -------  
 16000  
  
 (1 row(s) affected)
 ```  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-multiple-string-concatenation"></a>E. 複数の文字列の連結を使用する  
 次の例では、姓、名、およびサンプル データベース内の副社長のファースト ネームのイニシャルを表示する 1 つの長い文字列を形成する複数の文字列を連結します。 姓の後ろにコンマを追加し、名のイニシャルの後ろにピリオドを追加します。  
  
```  
-- Uses AdventureWorks  
  
SELECT (LastName + ', ' + SUBSTRING(FirstName, 1, 1) + '.') AS Name, Title  
FROM DimEmployee  
WHERE Title LIKE '%Vice Pres%'  
ORDER BY LastName ASC;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Name               Title                                           
-------------      ---------------  
Duffy, T.          Vice President of Engineering  
Hamilton, J.       Vice President of Production  
Welcker, B.        Vice President of Sales  
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CAST および CONVERT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [データ型の変換 &#40;データベース エンジン"&"#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [式 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [+ = (& a) #40 です。文字列の連結 &#41;& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/string-concatenation-equal-transact-sql.md)  
  
  




