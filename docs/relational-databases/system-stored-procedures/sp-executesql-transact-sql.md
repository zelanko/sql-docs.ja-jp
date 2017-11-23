---
title: "sp_executesql (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_executesql
- sp_executesql_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sp_executesql
- dynamic SQL
ms.assetid: a8d68d72-0f4d-4ecb-ae86-1235b962f646
caps.latest.revision: "64"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: b6dec48efa27a14443e69158ed9e9fffb55eba29
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spexecutesql-transact-sql"></a>sp_executesql (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  何回も再利用可能な、または動的に作成した [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントやバッチを実行します。 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントやバッチには、埋め込みパラメーターを含めることができます。  
  
> [!IMPORTANT]  
>  実行時にコンパイルされる[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは、悪意のある攻撃にアプリケーションを公開できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_executesql [ @stmt = ] statement  
[   
  { , [ @params = ] N'@parameter_name data_type [ OUT | OUTPUT ][ ,...n ]' }   
     { , [ @param1 = ] 'value1' [ ,...n ] }  
]  
```  
  
## <a name="arguments"></a>引数  
 [ @stmt=]*ステートメント*  
 Unicode 文字列が含まれて、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはバッチです。 @stmtUnicode 定数または Unicode 変数のいずれかにする必要があります。 + 演算子で 2 つの文字列を連結するなどの複雑な Unicode 式は使用できません。 文字定数も使用できません。 Unicode 定数が指定されている場合に付ける必要があります、 **N**です。たとえば、Unicode 定数**N 'sp_who'**有効ですが、文字定数**'sp_who'**はありません。 文字列のサイズは、データベース サーバーで利用可能なメモリにより制限されます。 64 ビット サーバーに、文字列のサイズは 2 GB の最大サイズに制限**nvarchar (max)**です。  
  
> [!NOTE]  
>  @stmtたとえば、名前の変数と同じ形式を持つパラメーターを含めることができます。`N'SELECT * FROM HumanResources.Employee WHERE EmployeeID = @IDParameter'`  
  
 @stmt に含める各パラメーターには、@params パラメーター定義リストとパラメーター値リストの両方に、対応するエントリが存在する必要があります。  
  
 [ @params=] N'@*parameter_name**data_type* [,...*n* ] '  
 @stmt に埋め込まれたすべてのパラメーターの定義が含まれている 1 つの文字列を指定します。この文字列は Unicode 定数または Unicode 変数にする必要があります。 各パラメーター定義は、パラメーター名とデータ型で構成されます。 *n*追加のパラメーター定義を示すプレース ホルダー。 すべてのパラメーターで指定された@stmtmustで定義されている@paramsです。 場合、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはバッチに@stmtパラメーターを含まない@paramsは必要ありません。 このパラメーターの既定値は NULL です。  
  
 [ @param1=] '*value1*'  
 パラメーター文字列に定義する最初のパラメーターの値を指定します。 Unicode 定数または Unicode 変数を指定できます。 @stmt に含まれる各パラメーターに対して、パラメーター値を指定する必要があります。値が必要なときに、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはバッチに@stmtパラメーターを持たない。  
  
 [ OUT | OUTPUT ]  
 パラメーターが出力パラメーターであることを示します。 **テキスト**、 **ntext**、および**イメージ**プロシージャが共通言語ランタイム (CLR) プロシージャでない限り、出力パラメーターとしてパラメーターを使用できます。 OUTPUT キーワードを使用する出力パラメーターは、プロシージャが CLR プロシージャでない限り、カーソルのプレースホルダーにできます。  
  
 *n*  
 追加するパラメーター値のプレースホルダーです。 定数または変数のみを指定できます。 関数などの複雑な式や演算子を使用した式は指定できません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 0 以外 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 SQL 文字列に組み込んだすべての SQL ステートメントから結果セットが返されます。  
  
## <a name="remarks"></a>解説  
 このトピックの「構文」セクションで説明した特定の順序で sp_executesql パラメーターを入力する必要があります。 パラメーターを不適切な順序で入力した場合、エラー メッセージが表示されます。  
  
 sp_executesql は、バッチ、名前の有効範囲、およびデータベース コンテキストに関して、EXECUTE と同じように動作します。 [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはバッチに sp_executesql@stmtパラメーターは、sp_executesql ステートメントが実行されるまでコンパイルされません。 @stmt の内容は、sp_executesql を呼び出したバッチの実行プランとは別の実行プランとしてコンパイルされ、実行されます。 sp_executesql バッチから、sp_executesql を呼び出すバッチ内で宣言されている変数は参照できません。 sp_executesql バッチ内のローカル カーソルまたはローカル変数は、sp_executesql を呼び出すバッチでは認識されません。 データベース コンテキストの変更は、sp_executesql ステートメント終了時まで有効です。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのパラメーター値だけが変わる場合は、ストアド プロシージャの代わりに sp_executesql を使用して、ステートメントを何回でも実行できます。 この場合、パラメーター値が変わるだけで [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントそのものは変わらないため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリ オプティマイザーではステートメントを最初に実行したときに生成した実行プランを再使用できます。  
  
> [!NOTE]  
>  パフォーマンスを向上させるには、ステートメント文字列に完全修飾オブジェクト名を使用します。  
  
 sp_executesql では、次の例に示すように、[!INCLUDE[tsql](../../includes/tsql-md.md)] 文字列とは別にパラメーター値を設定できます。  
  
```  
DECLARE @IntVariable int;  
DECLARE @SQLString nvarchar(500);  
DECLARE @ParmDefinition nvarchar(500);  
  
/* Build the SQL string one time.*/  
SET @SQLString =  
     N'SELECT BusinessEntityID, NationalIDNumber, JobTitle, LoginID  
       FROM AdventureWorks2012.HumanResources.Employee   
       WHERE BusinessEntityID = @BusinessEntityID';  
SET @ParmDefinition = N'@BusinessEntityID tinyint';  
/* Execute the string with the first parameter value. */  
SET @IntVariable = 197;  
EXECUTE sp_executesql @SQLString, @ParmDefinition,  
                      @BusinessEntityID = @IntVariable;  
/* Execute the same string with the second parameter value. */  
SET @IntVariable = 109;  
EXECUTE sp_executesql @SQLString, @ParmDefinition,  
                      @BusinessEntityID = @IntVariable;  
```  
  
 また、出力パラメーターを sp_executesql で使用することもできます。 次の例では、`AdventureWorks2012.HumanResources.Employee` テーブルから役職名を取得し、それを出力パラメーター `@max_title` に返します。  
  
```  
DECLARE @IntVariable int;  
DECLARE @SQLString nvarchar(500);  
DECLARE @ParmDefinition nvarchar(500);  
DECLARE @max_title varchar(30);  
  
SET @IntVariable = 197;  
SET @SQLString = N'SELECT @max_titleOUT = max(JobTitle)   
   FROM AdventureWorks2012.HumanResources.Employee  
   WHERE BusinessEntityID = @level';  
SET @ParmDefinition = N'@level tinyint, @max_titleOUT varchar(30) OUTPUT';  
  
EXECUTE sp_executesql @SQLString, @ParmDefinition, @level = @IntVariable, @max_titleOUT=@max_title OUTPUT;  
SELECT @max_title;  
```  
  
 sp_executesql でパラメーター値を使用すると、EXECUTE ステートメントで文字列を実行する場合と比べて次のような利点があります。  
  
-   sp_executesql 文字列に指定される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの実際のテキストは実行のたびに変わらないので、クエリ オプティマイザーでは、2 回目の実行で [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントと最初の実行時に作成した実行プランが照合される可能性があります。 したがって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では 2 回目のステートメントをコンパイルする必要がありません。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)]文字列が 1 回だけを作成します。  
  
-   整数パラメーターはネイティブ形式で指定します。 Unicode にキャストする必要はありません。  
  
## <a name="permissions"></a>Permissions  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-executing-a-simple-select-statement"></a>A. 簡単な SELECT ステートメントを実行する  
 次の例を作成し、実行、単純な`SELECT`というパラメーターを含んでいるステートメント`@level`です。  
  
```  
EXECUTE sp_executesql   
          N'SELECT * FROM AdventureWorks2012.HumanResources.Employee   
          WHERE BusinessEntityID = @level',  
          N'@level tinyint',  
          @level = 109;  
```  
  
### <a name="b-executing-a-dynamically-built-string"></a>B. 動的に作成した文字列を実行する  
 次の例を使用して`sp_executesql`動的に作成した文字列を実行します。 この例で使用するストアド プロシージャでは、特定の年の販売データをパーティション分割するために使用されるテーブル セットにデータを追加します。 月ごとに次の形式のテーブルが 1 つずつ存在します。  
  
```  
CREATE TABLE May1998Sales  
    (OrderID int PRIMARY KEY,  
    CustomerID int NOT NULL,  
    OrderDate  datetime NULL  
        CHECK (DATEPART(yy, OrderDate) = 1998),  
    OrderMonth int  
        CHECK (OrderMonth = 5),  
    DeliveryDate datetime  NULL,  
        CHECK (DATEPART(mm, OrderDate) = OrderMonth)  
    )  
```  
  
 この例で使用するストアド プロシージャでは、新規の注文を正しいテーブルに追加する `INSERT` ステートメントを動的に作成し、実行します。 この例では、受注日を使用してデータを格納するテーブルの名前を作成し、この名前を `INSERT` ステートメントに組み込みます。  
  
> [!NOTE]  
>  これは sp_executesql の簡単な使用例です。 この例では、エラー チェックや、テーブル間における注文番号の重複の確認などのビジネス ルール チェックは行いません。  
  
```  
CREATE PROCEDURE InsertSales @PrmOrderID INT, @PrmCustomerID INT,  
                 @PrmOrderDate DATETIME, @PrmDeliveryDate DATETIME  
AS  
DECLARE @InsertString NVARCHAR(500)  
DECLARE @OrderMonth INT  
  
-- Build the INSERT statement.  
SET @InsertString = 'INSERT INTO ' +  
       /* Build the name of the table. */  
       SUBSTRING( DATENAME(mm, @PrmOrderDate), 1, 3) +  
       CAST(DATEPART(yy, @PrmOrderDate) AS CHAR(4) ) +  
       'Sales' +  
       /* Build a VALUES clause. */  
       ' VALUES (@InsOrderID, @InsCustID, @InsOrdDate,' +  
       ' @InsOrdMonth, @InsDelDate)'  
  
/* Set the value to use for the order month because  
   functions are not allowed in the sp_executesql parameter  
   list. */  
SET @OrderMonth = DATEPART(mm, @PrmOrderDate)  
  
EXEC sp_executesql @InsertString,  
     N'@InsOrderID INT, @InsCustID INT, @InsOrdDate DATETIME,  
       @InsOrdMonth INT, @InsDelDate DATETIME',  
     @PrmOrderID, @PrmCustomerID, @PrmOrderDate,  
     @OrderMonth, @PrmDeliveryDate  
  
GO  
```  
  
 このプロシージャでは、sp_executesql を使用して文字列を実行しますが、これは EXECUTE を使用する場合と比べて効率的です。 sp_executesql を使用する場合、INSERT 文字列は各月のテーブルごとに 1 つずつ、12 とおり作成されます。 EXECUTE を使用する場合、パラメーター値が異なるので、各 INSERT 文字列は一意になります。 どちらの方法でも作成するバッチの数は同じですが、sp_executesql で作成される INSERT 文字列には類似性があるので、クエリ オプティマイザーで実行プランを再利用しやすくなります。  
  
### <a name="c-using-the-output-parameter"></a>C. OUTPUT パラメーターを使用する  
 次の例では、`OUTPUT`によって生成される結果セットを格納するパラメーター、`SELECT`内のステートメント、`@SQLString`パラメーター。2 つ`SELECT`の値を使用するステートメントを実行し、`OUTPUT`パラメーター。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @SQLString nvarchar(500);  
DECLARE @ParmDefinition nvarchar(500);  
DECLARE @SalesOrderNumber nvarchar(25);  
DECLARE @IntVariable int;  
SET @SQLString = N'SELECT @SalesOrderOUT = MAX(SalesOrderNumber)  
    FROM Sales.SalesOrderHeader  
    WHERE CustomerID = @CustomerID';  
SET @ParmDefinition = N'@CustomerID int,  
    @SalesOrderOUT nvarchar(25) OUTPUT';  
SET @IntVariable = 22276;  
EXECUTE sp_executesql  
    @SQLString  
    ,@ParmDefinition  
    ,@CustomerID = @IntVariable  
    ,@SalesOrderOUT = @SalesOrderNumber OUTPUT;  
-- This SELECT statement returns the value of the OUTPUT parameter.  
SELECT @SalesOrderNumber;  
-- This SELECT statement uses the value of the OUTPUT parameter in  
-- the WHERE clause.  
SELECT OrderDate, TotalDue  
FROM Sales.SalesOrderHeader  
WHERE SalesOrderNumber = @SalesOrderNumber;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-executing-a-simple-select-statement"></a>D. 簡単な SELECT ステートメントを実行する  
 次の例を作成し、実行、単純な`SELECT`というパラメーターを含んでいるステートメント`@level`です。  
  
```  
-- Uses AdventureWorks  
  
EXECUTE sp_executesql   
          N'SELECT * FROM AdventureWorksPDW2012.dbo.DimEmployee   
          WHERE EmployeeKey = @level',  
          N'@level tinyint',  
          @level = 109;  
```  
  
 その他の例では、次を参照してください。 [sp_executesql (TRANSACT-SQL)](http://msdn.microsoft.com/library/ms188001.aspx)です。  
  
## <a name="see-also"></a>参照  
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
