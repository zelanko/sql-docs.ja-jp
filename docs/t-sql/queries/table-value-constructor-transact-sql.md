---
title: "テーブル値コンス トラクター (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/15/2017
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
- inserting multiple rows
- row value expression
- row constructor [SQL Server]
- table value constructor [SQL Server]
ms.assetid: e57cd31d-140e-422f-8178-2761c27b9deb
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d9920f0a7e6b466541dbd60257385b31ba04cdb5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="table-value-constructor-transact-sql"></a>テーブル値コンストラクター (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  テーブルに設定される行の値式のセットを指定します。 [!INCLUDE[tsql](../../includes/tsql-md.md)] テーブル値コンストラクターを使用すると、単一の DML ステートメントで複数行のデータを指定できます。 テーブル値コンス トラクターは、使用中の INSERT ステートメントの VALUES 句で指定できます\<ソース テーブル > 句と MERGE ステートメントの FROM 句の派生テーブルの定義でします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
VALUES ( <row value expression list> ) [ ,...n ]   
  
<row value expression list> ::=  
    {<row value expression> } [ ,...n ]  
  
<row value expression> ::=  
    { DEFAULT | NULL | expression }  
```  
  
## <a name="arguments"></a>引数  
 VALUES  
 行の値式のリストを指定します。 各リストはかっこで囲み、コンマで区切る必要があります。  
  
 各リストで指定されている値の数が同じであり、値はテーブル内の列と同じ順序で並んでいる必要があります。 テーブル内の各列に対応する値を指定するか、列リストを使用して各入力値を格納する列を明示的に指定する必要があります。  
  
 DEFAULT  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]によって、列に対して定義されている既定値が挿入されます。 既定値がなく、列に対して NULL が許可されている場合は、NULL が挿入されます。 DEFAULT は ID 列には有効ではありません。 テーブル値コンストラクターで指定する場合、DEFAULT は INSERT ステートメント内でのみ使用できます。  
  
 *式 (expression)*  
 定数、変数、または式を指定します。 式には EXECUTE ステートメントを含めることができません。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 テーブル値コンス トラクターは、2 つの方法のいずれかで使用できます挿入の値の一覧内で直接しています.。 値ステートメント、または、派生テーブルとして任意の場所を派生テーブルは許可します。 行の数が最大値を超えた場合、エラー 10738 が返されます。 制限は、複数の行を挿入するには、次のいずれかを使用します。  
  
-   複数の INSERT ステートメントを作成する  
  
-   派生テーブルを使用します。  
  
-   使用してデータを一括インポート、 **bcp**ユーティリティまたは BULK INSERT ステートメント  
  
 単一のスカラー値だけが行の値式として使用できます。 複数の列が関係するサブクエリは行の値式として使用できません。 たとえば、次のコードでは、3 番目の行の値式のリストに複数の列を持つサブクエリが含まれているため、構文エラーが返されます。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE dbo.MyProducts (Name varchar(50), ListPrice money);  
GO  
-- This statement fails because the third values list contains multiple columns in the subquery.  
INSERT INTO dbo.MyProducts (Name, ListPrice)  
VALUES ('Helmet', 25.50),  
       ('Wheel', 30.00),  
       (SELECT Name, ListPrice FROM Production.Product WHERE ProductID = 720);  
GO  
  
```  
  
 ただし、このステートメントは、サブクエリ内の各列を個別に指定するように書き直すことができます。 次の例が正常に次の 3 つの行を挿入、`MyProducts`テーブル。  
  
```  
INSERT INTO dbo.MyProducts (Name, ListPrice)  
VALUES ('Helmet', 25.50),  
       ('Wheel', 30.00),  
       ((SELECT Name FROM Production.Product WHERE ProductID = 720),  
        (SELECT ListPrice FROM Production.Product WHERE ProductID = 720));  
GO  
  
```  
  
## <a name="data-types"></a>データ型  
 複数行の INSERT ステートメントで指定された値は、UNION ALL 構文のデータ型変換プロパティに従います。 これは、結果の高い型に一致しない型の暗黙的な変換で[優先順位](../../t-sql/data-types/data-type-precedence-transact-sql.md)です。 暗黙的な変換がサポートされていない場合は、エラーが返されます。 型の列に、次のステートメントが整数値と文字の値を挿入するなど、 **char**です。  
  
```  
CREATE TABLE dbo.t (a int, b char);  
GO  
INSERT INTO dbo.t VALUES (1,'a'), (2, 1);  
GO  
```  
  
 INSERT ステートメントの実行時に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換しようとしています。 の ' a' を整数データ型の優先順位がことを示します整数文字よりも高い型のです。 変換は失敗して、エラーが返されます。 必要に応じて値を明示的に変換することで、このようなエラーを回避できます。 たとえば、上記のステートメントは次のように記述できます。  
  
```  
INSERT INTO dbo.t VALUES (1,'a'), (2, CONVERT(CHAR,1));  
```  
  
## <a name="examples"></a>使用例  
  
### <a name="a-inserting-multiple-rows-of-data"></a>A. 複数行のデータを挿入する  
 次の例は、テーブルを作成`dbo.Departments`し、テーブル値コンス トラクターを使用して、テーブルに 5 つの行を挿入します。 すべての列の値が指定され、テーブルの列と同じ順序で並んでいるため、列名を列リストで指定する必要はありません。  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO Production.UnitMeasure  
VALUES (N'FT2', N'Square Feet ', '20080923'), (N'Y', N'Yards', '20080923'), (N'Y3', N'Cubic Yards', '20080923');  
GO  
  
```  
  
### <a name="b-inserting-multiple-rows-with-default-and-null-values"></a>B. DEFAULT 値および NULL 値を指定して複数行を挿入する  
 次の例では、テーブル値コンストラクターを使用してテーブルに行を挿入するときに、DEFAULT および NULL を指定する方法を示します。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE Sales.MySalesReason(  
SalesReasonID int IDENTITY(1,1) NOT NULL,  
Name dbo.Name NULL ,  
ReasonType dbo.Name NOT NULL DEFAULT 'Not Applicable' );  
GO  
INSERT INTO Sales.MySalesReason   
VALUES ('Recommendation','Other'), ('Advertisement', DEFAULT), (NULL, 'Promotion');  
  
SELECT * FROM Sales.MySalesReason;  
  
```  
  
### <a name="c-specifying-multiple-values-as-a-derived-table-in-a-from-clause"></a>C. FROM 句で複数の値を派生テーブルとして指定する  
 次の例では、SELECT ステートメントの FROM 句で複数の値を指定するのにテーブル値コンス トラクターを使用します。  
  
```  
SELECT a, b FROM (VALUES (1, 2), (3, 4), (5, 6), (7, 8), (9, 10) ) AS MyTable(a, b);  
GO  
-- Used in an inner join to specify values to return.  
SELECT ProductID, a.Name, Color  
FROM Production.Product AS a  
INNER JOIN (VALUES ('Blade'), ('Crown Race'), ('AWC Logo Cap')) AS b(Name)   
ON a.Name = b.Name;  
  
```  
  
### <a name="d-specifying-multiple-values-as-a-derived-source-table-in-a-merge-statement"></a>D. MERGE ステートメントで複数の行を派生ソース テーブルとして指定する  
 次の例では、MERGE を使用し、行を更新または挿入することで `SalesReason` テーブルを変更します。 ときの値`NewName`テーブル ソース内の値に一致する、 `Name` 、対象のテーブルの列 (`SalesReason`) では、`ReasonType`ターゲット テーブルの列を更新します。 `NewName` の値が一致しない場合は、ソース行が対象テーブルに挿入されます。 ソース テーブルが使用する派生テーブル、[!INCLUDE[tsql](../../includes/tsql-md.md)]ソース テーブルの複数の行を指定するテーブル値コンス トラクターです。  
  
```  
USE AdventureWorks2012;  
GO  
-- Create a temporary table variable to hold the output actions.  
DECLARE @SummaryOfChanges TABLE(Change VARCHAR(20));  
  
MERGE INTO Sales.SalesReason AS Target  
USING (VALUES ('Recommendation','Other'), ('Review', 'Marketing'), ('Internet', 'Promotion'))  
       AS Source (NewName, NewReasonType)  
ON Target.Name = Source.NewName  
WHEN MATCHED THEN  
UPDATE SET ReasonType = Source.NewReasonType  
WHEN NOT MATCHED BY TARGET THEN  
INSERT (Name, ReasonType) VALUES (NewName, NewReasonType)  
OUTPUT $action INTO @SummaryOfChanges;  
  
-- Query the results of the table variable.  
SELECT Change, COUNT(*) AS CountPerChange  
FROM @SummaryOfChanges  
GROUP BY Change;  
  
```  
  
## <a name="see-also"></a>参照  
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [マージ & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/merge-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)  
  
  

