---
title: "OUTPUT 句 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OUTPUT_TSQL
- OUTPUT
dev_langs:
- TSQL
helpviewer_keywords:
- displaying updated rows
- INSERT statement [SQL Server], OUTPUT clause
- outputs [SQL Server]
- OUTPUT clause
- row additions [SQL Server], OUTPUT clause
- viewing updated rows
- row deletions [SQL Server], OUTPUT clause
- viewing deleted rows
- DELETE statement [SQL Server], OUTPUT clause
- row updates [SQL Server]
- displaying inserted rows
- viewing inserted rows
- displaying deleted rows
- UPDATE statement [SQL Server], OUTPUT clause
ms.assetid: 41b9962c-0c71-4227-80a0-08fdc19f5fe4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 6a28059e6a30657a67275d317c70bdb26d2507a2
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="output-clause-transact-sql"></a>OUTPUT 句 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  INSERT、UPDATE、DELETE、または MERGE の各ステートメントの影響を受ける行の情報や、それらに基づく式を返します。 これらの結果は処理アプリケーションに返され、確認メッセージの表示、アーカイブ化、その他のアプリケーション要件で使用することができます。 また、結果をテーブルまたはテーブル変数に挿入することもできます。 さらに、入れ子になった INSERT、UPDATE、DELETE、または MERGE ステートメント内の OUTPUT 句の結果を取得して対象のテーブルまたはビューに挿入することもできます。  
  
> [!NOTE]  
>  UPDATE、INSERT、または DELETE ステートメントに OUTPUT 句があると、ステートメントでエラーが発生してロールバックされた場合にも、クライアントに行が返されます。 ステートメントの実行時にエラーが発生した場合は、結果を使用しないでください。  
  
 **使用されます。**  
  
 [DELETE](../../t-sql/statements/delete-transact-sql.md)  
  
 [INSERT](../../t-sql/statements/insert-transact-sql.md)  
  
 [UPDATE](../../t-sql/queries/update-transact-sql.md)  
  
 [MERGE](../../t-sql/statements/merge-transact-sql.md)  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
<OUTPUT_CLAUSE> ::=  
{  
    [ OUTPUT <dml_select_list> INTO { @table_variable | output_table } [ ( column_list ) ] ]  
    [ OUTPUT <dml_select_list> ]  
}  
<dml_select_list> ::=  
{ <column_name> | scalar_expression } [ [AS] column_alias_identifier ]  
    [ ,...n ]  
  
<column_name> ::=  
{ DELETED | INSERTED | from_table_name } . { * | column_name }  
    | $action  
```  
  
## <a name="arguments"></a>引数  
 @*table_variable*  
 指定します、**テーブル**呼び出し元に返されずに、返された行が挿入される変数です。 @*table_variable* INSERT、UPDATE、DELETE、または MERGE ステートメントの前に宣言する必要があります。  
  
 場合*column_list*が指定されていない、**テーブル**変数は OUTPUT の結果セットと同数の列を持つ必要があります。 ただし、ID 列と計算列はスキップされるため、同じである必要はありません。 場合*column_list*指定は省略された列の null 値を許可するか既定値がある必要がありますに値を代入します。  
  
 詳細については**テーブル**変数を参照してください[テーブル &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/table-transact-sql.md).  
  
 *output_table*  
 返される行を呼び出し元に返さずにテーブルに挿入する場合に、挿入先となるテーブルを指定します。 *output_table*一時テーブルを指定することがあります。  
  
 場合*column_list*が指定されていない、テーブルは OUTPUT の結果セットと同数の列をいる必要があります。 ID 列と計算列は同じである必要はありません。 スキップされるためです。 場合*column_list*指定は省略された列の null 値を許可するか既定値がある必要がありますに値を代入します。  
  
 *output_table*ことはできません。  
  
-   トリガーが定義され有効化されているテーブル  
  
-   FOREIGN KEY 制約のどちらかの側になっているテーブル  
  
-   CHECK 制約が定義されているか、ルールが有効化されているテーブル  
  
*column_list*  
 INTO 句の対象テーブル上のオプションの列名のリストです。 使用できる列リストに似ていますが、[挿入](../../t-sql/statements/insert-transact-sql.md)ステートメントです。  
  
 *scalar_expression*  
 単一の値に評価される、記号や演算子の任意の組み合わせです。 集計関数は使用できません*scalar_expression*です。  
  
 テーブル内の変更する列への参照は、INSERTED プレフィックスまたは DELETED プレフィックスで修飾する必要があります。  
  
 *column_alias_identifier*  
 列名を参照するために使用する代替名です。  
  
 DELETED  
 更新操作または削除操作で削除される値を指定する列プレフィックスです。 DELETED プレフィックスの付いた列は、UPDATE、DELETE、または MERGE ステートメントが完了する前の値を反映します。  
  
 INSERT ステートメント内で DELETED を OUTPUT 句と共に使用することはできません。  
  
 INSERTED  
 挿入操作または更新操作で追加される値を指定する列プレフィックスです。 INSERTED プレフィックスの付いた列は、UPDATE、INSERT、または MERGE ステートメントが完了した後の、トリガーが実行される前の値を反映します。  
  
 DELETE ステートメント内で INSERTED を OUTPUT 句と共に使用することはできません。  
  
 *from_table_name*  
 DELETE、UPDATE、または MERGE ステートメントの FROM 句に含まれるテーブルを指定する列プレフィックスです。更新または削除する行を指定するために使用します。  
  
 変更するテーブルが FROM 句でも指定されている場合には、そのテーブルの列への参照は、すべて INSERTED プレフィックスまたは DELETED プレフィックスで修飾する必要があります。  
  
 \*  
 削除、挿入または更新操作で影響を受けるすべての列を、テーブル中に存在する順序で返すよう指示します。  
  
 たとえば、次の DELETE ステートメントの `OUTPUT DELETED.*` は、`ShoppingCartItem` テーブルから削除されるすべての列を返します。  
  
```  
DELETE Sales.ShoppingCartItem  
    OUTPUT DELETED.*;  
```  
  
 *column_name*  
 明示的な列参照です。 変更対象のテーブルへの参照正しく修飾して指定する、INSERTED または DELETED プレフィックス、適切な場合は、たとえば: INSERTED **. * * * column_name*です。  
  
 $action  
 MERGE ステートメントでのみ使用できます。 型の列を示す**nvarchar (10)**を返す行ごとに 3 つの値のいずれかの MERGE ステートメントで OUTPUT 句で: 'INSERT'、'UPDATE'、または 'DELETE'、その行に対して実行されたアクションに従ってします。  
  
## <a name="remarks"></a>解説  
 出力\<dml_select_list > 句、および出力\<dml_select_list > INTO {**@ * * * table_variable* | *output_table* } 句を定義することができます単一の INSERT、UPDATE、DELETE、または MERGE ステートメントでします。  
  
> [!NOTE]  
>  特に指定しない限り、OUTPUT 句への参照は、OUTPUT 句と OUTPUT INTO 句の両方を参照します。  
  
 OUTPUT 句は、INSERT 操作や UPDATE 操作の後で ID 列や計算列の値を取得するのに便利です。  
  
 計算列が含まれている場合、 \<dml_select_list >、出力テーブルまたはテーブル変数内の対応する列は計算列ではありません。 新しい列の値は、ステートメントが実行された時点で計算された値を持つ列になります。  
  
 テーブルに対して変更が適用される順序と、出力テーブルやテーブル変数に行が挿入される順序が、対応する保証はありません。  
  
 UPDATE ステートメントの一部としてパラメーターまたは変数が変更されると、OUTPUT 句は常に、パラメーターや変数の変更後の値ではなく、ステートメントを実行する前の値を返します。  
  
 OUTPUT は、WHERE CURRENT OF 構文を使用したカーソル位置での UPDATE ステートメントや DELETE ステートメントと共に使用することができます。  
  
 OUTPUT 句は、次のステートメントではサポートされません。  
  
-   ローカル パーティション ビュー、分散パーティション ビュー、またはリモート テーブルを参照する DML ステートメント  
  
-   EXECUTE ステートメントを含む INSERT ステートメント  
  
-   データベースの互換性レベルが 100 に設定されている場合、OUTPUT 句でフルテキスト述語を使用することはできません。  
  
-   OUTPUT INTO 句は、ビューまたは行セット関数に挿入して使用することはできません。  
  
-   ユーザー定義関数に出力先がテーブルである OUTPUT INTO 句が含まれている場合、このような関数は作成できません。  
  
 非決定的な動作を防ぐため、OUTPUT 句に次の参照を含めることはできません。  
  
-   ユーザー データやシステム データにアクセスするサブクエリまたはユーザー定義関数、あるいはそのようなアクセスを行うと想定されるサブクエリまたはユーザー定義関数。 ユーザー定義関数は、スキーマ バインドでない場合、データ アクセスを行うと見なされます。  
  
-   列が次のいずれかの方法で定義されている場合のビューまたはインライン テーブル値関数からの列。  
  
    -   サブクエリ。  
  
    -   ユーザー データやシステム データにアクセスするユーザー定義関数、またはそのようなアクセスを行うと想定されるユーザー定義関数  
  
    -   ユーザー データやシステム データにアクセスするユーザー定義関数を定義に含む計算列  
  
     ときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]このような列を検出、OUTPUT 句でエラー 4186 が発生します。   
  
## <a name="inserting-data-returned-from-an-output-clause-into-a-table"></a>OUTPUT 句から返されたデータのテーブルへの挿入  
 入れ子になった INSERT、UPDATE、DELETE、または MERGE ステートメント内の OUTPUT 句の結果を取得して対象のテーブルに挿入する場合は、以下の点に注意してください。  
  
-   この操作全体がアトミックです。 INSERT ステートメントおよび OUTPUT 句を含んでいる入れ子になった DML ステートメントの両方を実行、または、ステートメント全体が失敗します。  
  
-   外部の INSERT ステートメントの対象には次の制限が適用されます。  
  
    -   リモート テーブル、ビュー、または共通テーブル式を対象にすることはできません。  
  
    -   対象に FOREIGN KEY 制約を含めたり、対象を FOREIGN KEY 制約で参照することはできません。  
  
    -   ターゲットでは、トリガーを定義できません。  
  
    -   対象を、マージ レプリケーションや、トランザクション レプリケーションの更新可能なサブスクリプションに加えることはできません。  
  
-   入れ子になった DML ステートメントには次の制限が適用されます。  
  
    -   リモート テーブルまたはパーティション ビューを対象にすることはできません。  
  
    -   ソース自体を含めることはできません、 \<dml_table_source > 句。  
  
-   含む INSERT ステートメントで OUTPUT INTO 句はサポートされていません、 \<dml_table_source > 句。  
  
-   @@ROWCOUNT外部の INSERT ステートメントによってのみ挿入された行を返します。  
  
-   @@IDENTITYSCOPE_IDENTITY、および IDENT_CURRENT は、入れ子になった DML ステートメントでのみ生成された id 値と外部の INSERT ステートメントによって生成されたを返します。  
  
-   クエリ通知は、1 つのエンティティとしてステートメントを扱うし、大幅な変更が外部の INSERT ステートメント自体から場合でも、作成されるすべてのメッセージの型は、入れ子になった DML の種類になります。  
  
-   \<Dml_table_source > 句、SELECT、および句がサブクエリ、集計関数、順位付け関数、フルテキスト述語、データ アクセスを実行するユーザー定義関数または TEXTPTR 関数を含めることはできません。  

## <a name="parallelism"></a>並列処理
 クライアントに結果を返すには OUTPUT 句では、直列プランを常に使用されます。

互換性レベルを 130 以上に設定 insert データベースのコンテキストでしています.選択操作は、SELECT ステートメントの WITH (TABLOCK) ヒントを使用しも出力を使用しています.Insert、一時テーブルまたはユーザー テーブル、対象のテーブルに挿入するには.選択は、サブツリー コストによって並列処理の対象になります。  OUTPUT INTO 句で参照されているターゲット テーブルは、並列処理の対象となるにはできません。 
 
## <a name="triggers"></a>トリガー  
 OUTPUT から返される列は、INSERT ステートメント、UPDATE ステートメント、または DELETE ステートメントが完了した後、トリガーが実行される前のデータを反映します。  
  
 INSTEAD OF トリガーでは、トリガー操作の結果変更が行われない場合でも、INSERT、UPDATE、または DELETE が実際に行われたかのように返される結果が生成されます。 OUTPUT 句を含むステートメントがトリガー本体の中で使用されている場合、トリガーの inserted テーブルおよび deleted テーブルを参照するためには、テーブルの別名を使用する必要があります。これにより、OUTPUT に関連付けられている INSERTED テーブルおよび DELETED テーブルで列参照が重複するのを避けることができます。  
  
 INTO キーワードを指定せずに OUTPUT 句を指定すると、DML 操作を行った先では、その DML アクションに対して定義されたトリガーを有効化できません。 たとえば、UPDATE ステートメント内で OUTPUT 句が定義されていると、対象のテーブルで UPDATE トリガーを有効化できません。  
  
 sp_configure オプション disallow results from triggers が設定されている場合に、INTO 句なしの OUTPUT 句をトリガー内で呼び出すと、ステートメントが失敗します。  
  
## <a name="data-types"></a>データ型  
 OUTPUT 句は、ラージ オブジェクト データ型をサポートしています: **nvarchar (max)**、 **varchar (max)**、 **varbinary (max)**、**テキスト**、 **ntext**、**イメージ**、および**xml**です。 使用する場合、します。WRITE 句を変更する UPDATE ステートメントで、 **nvarchar (max)**、 **varchar (max)**、または**varbinary (max)**列で前に、の値のイメージと後に、完全は参照されているかどうかに返されます。 式の一部として TEXTPTR () 関数は使用できません、**テキスト**、 **ntext**、または**イメージ**OUTPUT 句内の列です。  
  
## <a name="queues"></a>キュー  
 OUTPUT を、テーブルをキューとして使用するアプリケーションで使用したり、中間結果セットを保持するために使用することができます。 つまり、アプリケーションは、テーブルに対して、常に行の追加または削除を行っています。 次の例では、DELETE ステートメント内で OUTPUT 句を使用し、削除された行を呼び出し元アプリケーションに返します。  
  
```  
USE AdventureWorks2012;  
GO  
DELETE TOP(1) dbo.DatabaseLog WITH (READPAST)  
OUTPUT deleted.*  
WHERE DatabaseLogID = 7;  
GO  
  
```  
  
 この例では、一度のアクションで、キューとして使用されているテーブルから行を削除し、削除された値を処理アプリケーションに返します。 テーブルを使用したスタックの実装など、別のセマンティクスも実装できます。 ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は行を処理し、OUTPUT 句を使用する DML ステートメントによって返される順序は保証されません。 必要なセマンティクスを保証する適切な WHERE 句を含むかどうかはアプリケーションに依存します。また、複数の行が DML 操作の対象となる場合には順序が保証されないという点に注意してください。 次の例は、サブクエリを使用して、一意性がの特性を前提と、`DatabaseLogID`目的の順序付けセマンティクスを実装するために列です。  
  
```  
USE tempdb;  
GO  
CREATE TABLE dbo.table1  
(  
    id INT,  
    employee VARCHAR(32)  
);  
GO  
  
INSERT INTO dbo.table1 VALUES   
      (1, 'Fred')  
     ,(2, 'Tom')  
     ,(3, 'Sally')  
     ,(4, 'Alice');  
GO  
  
DECLARE @MyTableVar TABLE  
(  
    id INT,  
    employee VARCHAR(32)  
);  
  
PRINT 'table1, before delete'   
SELECT * FROM dbo.table1;  
  
DELETE FROM dbo.table1  
OUTPUT DELETED.* INTO @MyTableVar  
WHERE id = 4 OR id = 2;  
  
PRINT 'table1, after delete'  
SELECT * FROM dbo.table1;  
  
PRINT '@MyTableVar, after delete'  
SELECT * FROM @MyTableVar;  
  
DROP TABLE dbo.table1;  
  
--Results  
--table1, before delete  
--id          employee  
------------- ------------------------------  
--1           Fred  
--2           Tom  
--3           Sally  
--4           Alice  
--  
--table1, after delete  
--id          employee  
------------- ------------------------------  
--1           Fred  
--3           Sally  
--@MyTableVar, after delete  
--id          employee  
------------- ------------------------------  
--2           Tom  
--4           Alice  
  
```  
  
> [!NOTE]  
>  複数のアプリケーションの同じテーブルへの破壊的な読み取りを許可する場合は、UPDATE ステートメントおよび DELETE ステートメントで READPAST テーブル ヒントを使用します。 これにより、テーブル内の最初の該当レコードを別のアプリケーションが既に読み込み中である場合に発生するロックの問題が起こらなくなります。  
  
## <a name="permissions"></a>権限  
 使用して取得するすべての列に対する SELECT 権限が必要\<dml_select_list > で使用されているまたは\<scalar_expression >。  
  
 指定された任意のテーブルに対する INSERT 権限が必要\<output_table >。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-output-into-with-a-simple-insert-statement"></a>A. OUTPUT INTO を単純な INSERT ステートメントと共に使用する  
 次の例 1 行の挿入、`ScrapReason`使用してテーブル、`OUTPUT`句をステートメントの結果を返す、`@MyTableVar``table`変数。 `ScrapReasonID` 列が IDENTITY プロパティで定義されているため、`INSERT` ステートメントではこの列の値を指定していません。 ただし、によって生成された値、[!INCLUDE[ssDE](../../includes/ssde-md.md)]でその列が返される、`OUTPUT`句で列`inserted.ScrapReasonID`です。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table( NewScrapReasonID smallint,  
                           Name varchar(50),  
                           ModifiedDate datetime);  
INSERT Production.ScrapReason  
    OUTPUT INSERTED.ScrapReasonID, INSERTED.Name, INSERTED.ModifiedDate  
        INTO @MyTableVar  
VALUES (N'Operator error', GETDATE());  
  
--Display the result set of the table variable.  
SELECT NewScrapReasonID, Name, ModifiedDate FROM @MyTableVar;  
--Display the result set of the table.  
SELECT ScrapReasonID, Name, ModifiedDate   
FROM Production.ScrapReason;  
GO  
  
```  
  
### <a name="b-using-output-with-a-delete-statement"></a>B. OUTPUT を DELETE ステートメントと共に使用する  
 次の例では、`ShoppingCartItem` テーブル内のすべての行を削除します。 句`OUTPUT deleted.*`ことを指定の結果、`DELETE`削除された行のすべての列では、ステートメントは、呼び出し元のアプリケーションに返されます。 `SELECT`に続くステートメントで、削除操作の結果を検証する、`ShoppingCartItem`テーブル。  
  
```  
USE AdventureWorks2012;  
GO  
DELETE Sales.ShoppingCartItem  
OUTPUT DELETED.*   
WHERE ShoppingCartID = 20621;  
  
--Verify the rows in the table matching the WHERE clause have been deleted.  
SELECT COUNT(*) AS [Rows in Table] FROM Sales.ShoppingCartItem WHERE ShoppingCartID = 20621;  
GO  
  
```  
  
### <a name="c-using-output-into-with-an-update-statement"></a>C. OUTPUT INTO を UPDATE ステートメントと共に使用する  
 次の例では、`VacationHours` テーブル内の最初の 10 個の行について、`Employee` 列を 25% 増しに更新します。 `OUTPUT`句を返します、`VacationHours`適用する前に存在する値、`UPDATE`列内のステートメント`deleted.VacationHours`、列に、更新された値`inserted.VacationHours`を`@MyTableVar``table`変数。  
  
 この後に、`SELECT` 内の値、および `@MyTableVar` テーブルの更新操作の結果を返す 2 つの `Employee` ステートメントが続きます。  
  
```  
USE AdventureWorks2012;  
GO  
  
DECLARE @MyTableVar table(  
    EmpID int NOT NULL,  
    OldVacationHours int,  
    NewVacationHours int,  
    ModifiedDate datetime);  
  
UPDATE TOP (10) HumanResources.Employee  
SET VacationHours = VacationHours * 1.25,  
    ModifiedDate = GETDATE()   
OUTPUT inserted.BusinessEntityID,  
       deleted.VacationHours,  
       inserted.VacationHours,  
       inserted.ModifiedDate  
INTO @MyTableVar;  
  
--Display the result set of the table variable.  
SELECT EmpID, OldVacationHours, NewVacationHours, ModifiedDate  
FROM @MyTableVar;  
GO  
--Display the result set of the table.  
SELECT TOP (10) BusinessEntityID, VacationHours, ModifiedDate  
FROM HumanResources.Employee;  
GO  
  
```  
  
### <a name="d-using-output-into-to-return-an-expression"></a>D. OUTPUT INTO を使用して式を返す  
 式を定義することで、次の例が例 C でビルド、`OUTPUT`の差として更新された句`VacationHours`値、および`VacationHours`値の更新プログラムが適用される前にします。 この式の値に返されます、`@MyTableVar``table`変数、列`VacationHoursDifference`です。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table(  
    EmpID int NOT NULL,  
    OldVacationHours int,  
    NewVacationHours int,  
    VacationHoursDifference int,  
    ModifiedDate datetime);  
  
UPDATE TOP (10) HumanResources.Employee  
SET VacationHours = VacationHours * 1.25,  
    ModifiedDate = GETDATE()  
OUTPUT inserted.BusinessEntityID,  
       deleted.VacationHours,  
       inserted.VacationHours,  
       inserted.VacationHours - deleted.VacationHours,  
       inserted.ModifiedDate  
INTO @MyTableVar;  
  
--Display the result set of the table variable.  
SELECT EmpID, OldVacationHours, NewVacationHours,   
    VacationHoursDifference, ModifiedDate  
FROM @MyTableVar;  
GO  
SELECT TOP (10) BusinessEntityID, VacationHours, ModifiedDate  
FROM HumanResources.Employee;  
GO  
  
```  
  
### <a name="e-using-output-into-with-fromtablename-in-an-update-statement"></a>E. OUTPUT INTO を UPDATE ステートメント内で from_table_name と共に使用する  
 次の例の更新プログラム、`ScrapReasonID`内の列、`WorkOrder`テーブルの指定したすべての作業指示`ProductID`と`ScrapReasonID`です。 `OUTPUT INTO` 句は、更新するテーブルの値 (`WorkOrder`) と、`Product` テーブルの値を返します。 更新する行を指定するために、`Product` テーブルを `FROM` 句の中で使用します。 `WorkOrder`テーブルには、 `AFTER UPDATE` 、定義されているトリガー、`INTO`キーワードが必要です。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyTestVar table (  
    OldScrapReasonID int NOT NULL,   
    NewScrapReasonID int NOT NULL,   
    WorkOrderID int NOT NULL,  
    ProductID int NOT NULL,  
    ProductName nvarchar(50)NOT NULL);  
  
UPDATE Production.WorkOrder  
SET ScrapReasonID = 4  
OUTPUT deleted.ScrapReasonID,  
       inserted.ScrapReasonID,   
       inserted.WorkOrderID,  
       inserted.ProductID,  
       p.Name  
    INTO @MyTestVar  
FROM Production.WorkOrder AS wo  
    INNER JOIN Production.Product AS p   
    ON wo.ProductID = p.ProductID   
    AND wo.ScrapReasonID= 16  
    AND p.ProductID = 733;  
  
SELECT OldScrapReasonID, NewScrapReasonID, WorkOrderID,   
    ProductID, ProductName   
FROM @MyTestVar;  
GO  
  
```  
  
### <a name="f-using-output-into-with-fromtablename-in-a-delete-statement"></a>F. OUTPUT INTO を DELETE ステートメント内で from_table_name と共に使用する  
 次の例では、`ProductProductPhoto` テーブルの行を、`FROM` ステートメントの `DELETE` 句内で定義された検索条件に基づいて削除します。 `OUTPUT` 句は削除するテーブルの各列 (`deleted.ProductID`、`deleted.ProductPhotoID`) と、`Product` テーブルの列を返します。 このテーブルは、削除する行を指定するために `FROM` 句内で使用します。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table (  
    ProductID int NOT NULL,   
    ProductName nvarchar(50)NOT NULL,  
    ProductModelID int NOT NULL,   
    PhotoID int NOT NULL);  
  
DELETE Production.ProductProductPhoto  
OUTPUT DELETED.ProductID,  
       p.Name,  
       p.ProductModelID,  
       DELETED.ProductPhotoID  
    INTO @MyTableVar  
FROM Production.ProductProductPhoto AS ph  
JOIN Production.Product as p   
    ON ph.ProductID = p.ProductID   
    WHERE p.ProductModelID BETWEEN 120 and 130;  
  
--Display the results of the table variable.  
SELECT ProductID, ProductName, ProductModelID, PhotoID   
FROM @MyTableVar  
ORDER BY ProductModelID;  
GO  
  
```  
  
### <a name="g-using-output-into-with-a-large-object-data-type"></a>G. OUTPUT INTO をラージ オブジェクト データ型と共に使用する  
 次の例では、`DocumentSummary` テーブル内の `nvarchar(max)` 列である `Production.Document` の部分的な値を、`.WRITE` 句を使用して更新します。 単語`components`は単語に置換`features`を置換する語、既存のデータと交換してください (長さ) を使用する文字数内で置換する単語の開始位置 (オフセット) を指定します。 この例では、`OUTPUT`句を返す前に、のイメージと後、`DocumentSummary`列を`@MyTableVar``table`変数。 なお前に、のイメージと後に、完全、`DocumentSummary`列が返されます。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table (  
    SummaryBefore nvarchar(max),  
    SummaryAfter nvarchar(max));  
  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
OUTPUT deleted.DocumentSummary,   
       inserted.DocumentSummary   
    INTO @MyTableVar  
WHERE Title = N'Front Reflector Bracket Installation';  
  
SELECT SummaryBefore, SummaryAfter   
FROM @MyTableVar;  
GO  
  
```  
  
### <a name="h-using-output-in-an-instead-of-trigger"></a>H. OUTPUT を INSTEAD OF トリガー内で使用する  
 次の例では、トリガー内で `OUTPUT` 句を使用し、トリガー操作の結果を返しています。 まず、`ScrapReason` テーブルでビューを作成し、次にそのビューに対して `INSTEAD OF INSERT` トリガーを定義して、ユーザーがベース テーブルの `Name` 列しか変更できないようにします。 列 `ScrapReasonID` はベース テーブルの `IDENTITY` 列であるため、トリガーはユーザーが指定した値を無視します。 これにより、[!INCLUDE[ssDE](../../includes/ssde-md.md)]を自動的に正しい値を生成します。 ユーザーによって指定される値も、`ModifiedDate`は無視され、現在の日付に設定されています。 `OUTPUT`句に実際に挿入された値が返されます、`ScrapReason`テーブル。  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('dbo.vw_ScrapReason','V') IS NOT NULL  
    DROP VIEW dbo.vw_ScrapReason;  
GO  
CREATE VIEW dbo.vw_ScrapReason  
AS (SELECT ScrapReasonID, Name, ModifiedDate  
    FROM Production.ScrapReason);  
GO  
CREATE TRIGGER dbo.io_ScrapReason   
    ON dbo.vw_ScrapReason  
INSTEAD OF INSERT  
AS  
BEGIN  
--ScrapReasonID is not specified in the list of columns to be inserted   
--because it is an IDENTITY column.  
    INSERT INTO Production.ScrapReason (Name, ModifiedDate)  
        OUTPUT INSERTED.ScrapReasonID, INSERTED.Name,   
               INSERTED.ModifiedDate  
    SELECT Name, getdate()  
    FROM inserted;  
END  
GO  
INSERT vw_ScrapReason (ScrapReasonID, Name, ModifiedDate)  
VALUES (99, N'My scrap reason','20030404');  
GO  
  
```  
  
 以下に、2004 年 4 月 12 日 ('`2004-04-12'`) に生成された結果セットを示します。 注意して、`ScrapReasonIDActual`と`ModifiedDate`列で提供される値ではなく、トリガー操作によって生成される値の反映、`INSERT`ステートメントです。  
  
 ```
 ScrapReasonID  Name             ModifiedDate  
 -------------  ---------------- -----------------------  
 17             My scrap reason  2004-04-12 16:23:33.050
 ```  
  
### <a name="i-using-output-into-with-identity-and-computed-columns"></a>I. OUTPUT INTO を、ID 列および計算列と共に使用する  
 次の例を作成、`EmployeeSales`テーブルが表示され、いくつかの行を使用して挿入、`INSERT`ステートメントを`SELECT`ステートメントのソース テーブルからデータを取得します。 `EmployeeSales`テーブルに id 列が含まれています (`EmployeeID`) し、計算列 (`ProjectedSales`)。  
  
```  
USE AdventureWorks2012 ;  
GO  
IF OBJECT_ID ('dbo.EmployeeSales', 'U') IS NOT NULL  
    DROP TABLE dbo.EmployeeSales;  
GO  
CREATE TABLE dbo.EmployeeSales  
( EmployeeID   int IDENTITY (1,5)NOT NULL,  
  LastName     nvarchar(20) NOT NULL,  
  FirstName    nvarchar(20) NOT NULL,  
  CurrentSales money NOT NULL,  
  ProjectedSales AS CurrentSales * 1.10   
);  
GO  
DECLARE @MyTableVar table(  
  EmployeeID   int NOT NULL,  
  LastName     nvarchar(20) NOT NULL,  
  FirstName    nvarchar(20) NOT NULL,  
  CurrentSales money NOT NULL,  
  ProjectedSales money NOT NULL  
  );  
  
INSERT INTO dbo.EmployeeSales (LastName, FirstName, CurrentSales)  
  OUTPUT INSERTED.LastName,   
         INSERTED.FirstName,   
         INSERTED.CurrentSales  
  INTO @MyTableVar  
    SELECT c.LastName, c.FirstName, sp.SalesYTD  
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.BusinessEntityID LIKE '2%'  
    ORDER BY c.LastName, c.FirstName;  
  
SELECT EmployeeID, LastName, FirstName, CurrentSales, ProjectedSales  
FROM @MyTableVar;  
GO  
SELECT EmployeeID, LastName, FirstName, CurrentSales, ProjectedSales  
FROM dbo.EmployeeSales;  
GO  
  
```  
  
### <a name="j-using-output-and-output-into-in-a-single-statement"></a>J. OUTPUT と OUTPUT INTO を単一のステートメント内で使用する  
 次の例では、`ProductProductPhoto` テーブルの行を、`FROM` ステートメントの `DELETE` 句内で定義された検索条件に基づいて削除します。 `OUTPUT INTO`句が削除されているテーブルから列を返します (`deleted.ProductID`、 `deleted.ProductPhotoID`) と列を`Product`テーブル、`@MyTableVar``table`変数。 `Product`でテーブルが使用される、`FROM`句を削除する行を指定します。 `OUTPUT`句を返します、 `deleted.ProductID`、`deleted.ProductPhotoID`から行を削除した列の日付と時間、`ProductProductPhoto`呼び出し元のアプリケーションにテーブルです。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table (  
    ProductID int NOT NULL,   
    ProductName nvarchar(50)NOT NULL,  
    ProductModelID int NOT NULL,   
    PhotoID int NOT NULL);  
  
DELETE Production.ProductProductPhoto  
OUTPUT DELETED.ProductID,  
       p.Name,  
       p.ProductModelID,  
       DELETED.ProductPhotoID  
    INTO @MyTableVar  
OUTPUT DELETED.ProductID, DELETED.ProductPhotoID, GETDATE() AS DeletedDate   
FROM Production.ProductProductPhoto AS ph  
JOIN Production.Product as p   
    ON ph.ProductID = p.ProductID   
WHERE p.ProductID BETWEEN 800 and 810;  
  
--Display the results of the table variable.  
SELECT ProductID, ProductName, PhotoID, ProductModelID   
FROM @MyTableVar;  
GO  
  
```  
  
### <a name="k-inserting-data-returned-from-an-output-clause"></a>K. OUTPUT 句から返されたデータを挿入する  
 次の例では、`OUTPUT` ステートメントの `MERGE` 句から返されたデータをキャプチャし、そのデータを別のテーブルに挿入します。 `MERGE`ステートメントの更新プログラム、`Quantity`の列、`ProductInventory`テーブル内で処理される注文に基づいてでは、毎日、`SalesOrderDetail`テーブル。 また、在庫が `0` 以下になった製品の行を削除します。 例が削除され、別のテーブルに挿入される行はキャプチャ`ZeroInventory`、製品在庫がないを追跡します。  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Production.ZeroInventory', N'U') IS NOT NULL  
    DROP TABLE Production.ZeroInventory;  
GO  
--Create ZeroInventory table.  
CREATE TABLE Production.ZeroInventory (DeletedProductID int, RemovedOnDate DateTime);  
GO  
  
INSERT INTO Production.ZeroInventory (DeletedProductID, RemovedOnDate)  
SELECT ProductID, GETDATE()  
FROM  
(   MERGE Production.ProductInventory AS pi  
    USING (SELECT ProductID, SUM(OrderQty) FROM Sales.SalesOrderDetail AS sod  
           JOIN Sales.SalesOrderHeader AS soh  
           ON sod.SalesOrderID = soh.SalesOrderID  
           AND soh.OrderDate = '20070401'  
           GROUP BY ProductID) AS src (ProductID, OrderQty)  
    ON (pi.ProductID = src.ProductID)  
    WHEN MATCHED AND pi.Quantity - src.OrderQty <= 0  
        THEN DELETE  
    WHEN MATCHED  
        THEN UPDATE SET pi.Quantity = pi.Quantity - src.OrderQty  
    OUTPUT $action, deleted.ProductID) AS Changes (Action, ProductID)  
WHERE Action = 'DELETE';  
IF @@ROWCOUNT = 0  
PRINT 'Warning: No rows were inserted';  
GO  
SELECT DeletedProductID, RemovedOnDate FROM Production.ZeroInventory;  
  
```  
  
## <a name="see-also"></a>参照  
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [挿入 &#40; です。Transact SQL と &#41; です。](../../t-sql/statements/insert-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [テーブルと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/table-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
