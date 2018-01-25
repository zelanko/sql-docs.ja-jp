---
title: "設定@local_variable(TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- SET @local_variable
- variables [SQL Server], assigning
- SET statement, @local_variable
- local variables [SQL Server]
ms.assetid: d410e06e-061b-4c25-9973-b2dc9b60bd85
caps.latest.revision: "52"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: fd65fea39ac3f9a9cba0d47ec94365bff9155332
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="set-localvariable-transact-sql"></a>設定@local_variable(TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  DECLARE @ を使用して作成された、指定されたローカル変数を設定する*local_variable*ステートメントでは、指定された値。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET   
{ @local_variable  
    [ . { property_name | field_name } ] = { expression | udt_name { . | :: } method_name }  
}  
|  
{ @SQLCLR_local_variable.mutator_method  
}  
|  
{ @local_variable  
    {+= | -= | *= | /= | %= | &= | ^= | |= } expression  
}  
|   
  { @cursor_variable =   
    { @cursor_variable | cursor_name   
    | { CURSOR [ FORWARD_ONLY | SCROLL ]   
        [ STATIC | KEYSET | DYNAMIC | FAST_FORWARD ]   
        [ READ_ONLY | SCROLL_LOCKS | OPTIMISTIC ]   
        [ TYPE_WARNING ]   
    FOR select_statement   
        [ FOR { READ ONLY | UPDATE [ OF column_name [ ,...n ] ] } ]   
      }   
    }  
}   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET @local_variable {+= | -= | *= | /= | %= | &= | ^= | |= } expression  
  
```  
  
## <a name="arguments"></a>引数  
 **@** *local_variable*  
 除く任意の型の変数の名前を指定**カーソル**、**テキスト**、 **ntext**、**イメージ**、または**テーブル**です。 変数名を記号には 1 つ開始する必要があります (**@**)。 変数名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 *property_name*  
 ユーザー定義型のプロパティを指定します。  
  
 *field_name*  
 ユーザー定義型のパブリック フィールドを指定します。  
  
 *udt_name*  
 共通言語ランタイム (CLR) ユーザー定義型の名前を指定します。  
  
 { **.** | **::** }  
 CLR ユーザー定義型のメソッドを指定します。 (静的ではない) インスタンス メソッドでピリオドを使用 (**.**)。 静的メソッドでは、2 つのコロンを使用して (**::**)。 CLR ユーザー定義型のメソッド、プロパティ、またはフィールドを呼び出すには、その型に対する EXECUTE 権限が必要です。  
  
 *method_name* **(** *argument* [ **,**... *n* ] **)**  
 ユーザー定義型のメソッドを指定します。このメソッドでは、あるデータ型のインスタンスの状態を変更する場合に 1 つ以上の引数を使用します。 静的メソッドはパブリックであることが必要です。  
  
 **@** *SQLCLR_local_variable*  
 型がアセンブリに存在する変数を指定します。 詳細については、「[共通言語ランタイム &#40;CLR&#41; 統合のプログラミング概念](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)」をご覧ください。  
  
 *mutator_method*  
 オブジェクトの状態を変更できるアセンブリのメソッドを指定します。 このメソッドには SQLMethodAttribute.IsMutator が適用されます。  
  
 { **+=** | **-=** | **\*=** | **/=** | **%=** | **&=** | **^=** | **|=** }  
 複合代入演算子です:  
  
 + = 加算して割り当てる  
  
 -= 減算して代入  
  
 * = 乗算して代入  
  
 /= 除算して代入  
  
 % = 剰余を代入  
  
 & = ビットごととし、割り当てます  
  
 ^ = ビットごとの XOR と割り当て  
  
 | = ビットごとの OR と割り当て  
  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)です。  
  
 *cursor_variable*  
 カーソル変数の名前を指定します。 ターゲットのカーソル変数が以前に他のカーソルを参照していた場合は、以前の参照は削除されます。  
  
 *cursor_name*  
 DECLARE CURSOR ステートメントを使用して宣言したカーソルの名前を指定します。  
  
 CURSOR  
 SET ステートメントにカーソルの宣言が含まれることを指定します。  
  
 SCROLL  
 カーソルがすべての FETCH オプション (FIRST、LAST、NEXT、PRIOR、RELATIVE、ABSOLUTE) をサポートすることを指定します。 FAST_FORWARD も指定した場合、SCROLL は指定できません。  
  
 FORWARD_ONLY  
 カーソルで、FETCH NEXT オプションだけがサポートされることを指定します。 カーソルは、最初の行から最後の行への一方向にしか取得できません。 STATIC、KEYSET、DYNAMIC のいずれのキーワードも指定しないで FORWARD_ONLY を指定した場合、カーソルは DYNAMIC として実装されます。 FORWARD_ONLY も SCROLL も指定しなかった場合は、STATIC、KEYSET、または DYNAMIC キーワードを指定しない限り、FORWARD_ONLY が既定値になります。 STATIC、KEYSET、および DYNAMIC カーソルの既定値は SCROLL です。  
  
 STATIC  
 データの一時コピーを作成するためのカーソルを定義します。作成されるコピーは、カーソルで使用されます。 このカーソルに対する要求の応答は、すべて tempdb 内にある一時テーブルから取得されます。したがって、ベース テーブルへの修正は、このカーソルで取得したデータには反映されません。また、このカーソルで修正を行うこともできません。  
  
 KEYSET  
 カーソルを開くときに、カーソル内の行の構成要素と順序が固定されることを指定します。 行を一意に識別するキーのセットは、tempdb の keysettable に組み込まれています。 ベース テーブル内にあるキー以外の値に対する変更が、カーソル所有者によって実行されるか、または他のユーザーによってコミットされると、その変更は、カーソル所有者がカーソルの周囲をスクロールするときに表示されます。 他のユーザーによって行われた挿入は表示されず、および挿入が使用できる、[!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー カーソル。  
  
 かどうか、行が削除された、行をフェッチしようとするを返します、@@FETCH_STATUS -2 です。 カーソルの外部からキー値の更新プログラムは、新しい行を挿入した後に、古い行の削除に似ています。 新しい値を持つ行が表示されないと、古い値を含む行をフェッチする試行を返す、@@FETCH_STATUS -2 です。 新しい値は、WHERE CURRENT OF 句を指定してカーソルから更新を実行した場合に表示されます。  
  
 DYNAMIC  
 結果セット内の行に対して行ったすべてのデータ変更を反映するカーソルを定義します。このデータ変更は、カーソル所有者がカーソルの周囲をスクロールするときに行われたものです。 行のデータ値、順序、構成要素は、各フェッチ操作で変化する可能性があります。 動的カーソルでは、絶対フェッチ オプションと相対フェッチ オプションはサポートされません。  
  
 FAST_FORWARD  
 最適化が有効に設定された FORWARD_ONLY、READ_ONLY カーソルを指定します。 SCROLL も指定した場合、FAST_FORWARD は指定できません。  
  
 READ_ONLY  
 このカーソルによる更新を禁止します。 UPDATE または DELETE ステートメントの WHERE CURRENT OF 句で、このカーソルを参照することはできません。 このオプションは、更新対象のカーソルの既定の機能よりも優先されます。  
  
 SCROLL LOCKS  
 カーソルによって行われる位置指定更新または位置指定削除の成功が保証されることを指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はカーソルに読み取られた行をロックし、後で変更できることを保証します。 FAST_FORWARD を指定した場合、SCROLL_LOCKS は指定できません。  
  
 OPTIMISTIC  
 行がカーソルに読み取られてから更新された場合に、カーソルによって行われる位置指定更新または位置指定削除が失敗します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]カーソルに読み取られるときは、行をロックしません。 代わりに timestamp 列の値を比較するか、テーブルに timestamp 列がない場合はチェックサム値を使用して、行がカーソルに読み込まれてから変更されたかどうかが判別されます。 行が変更されている場合、位置指定更新または位置指定削除の試行は失敗します。 FAST_FORWARD も指定した場合、OPTIMISTIC は指定できません。  
  
 TYPE_WARNING  
 カーソルの種類が、要求されたものから別のものに暗黙的に変換された場合、クライアントに警告メッセージが送信されます。  
  
 *Select_statement*  
 カーソルの結果セットを定義する標準の SELECT ステートメントです。 内で FOR BROWSE および INTO キーワードは許可されません、 *select_statement*カーソル宣言のです。  
  
 DISTINCT、UNION、GROUP BY または HAVING を使用すると、または集計式に含まれるかどうか、 *select_list*カーソルは STATIC として作成されます。  
  
 基になる各テーブルに一意なインデックスがなく、ISO SCROLL カーソルまたは [!INCLUDE[tsql](../../includes/tsql-md.md)] KEYSET カーソルが要求された場合、カーソルは自動的に STATIC カーソルになります。  
  
 場合*select_statement* ORDER BY 句が含まれている列は一意な行識別子、動的カーソルは変換カーソル、キーセット カーソルまたは静的カーソルにキーセット カーソルを開くことができない場合。 STATIC キーワードを指定せず、ISO 構文を使用して定義されたカーソルの場合も、同様の変換が行われます。  
  
 READ ONLY  
 このカーソルによる更新を禁止します。 UPDATE または DELETE ステートメントの WHERE CURRENT OF 句で、このカーソルを参照することはできません。 このオプションは、更新対象のカーソルの既定の機能よりも優先されます。 このキーワードは、以前は READ_ONLY と表記していましたが、今後は、READ と ONLY の間にアンダースコアではなくスペースを指定するようになりました。  
  
 UPDATE [OF *column_name*[ **,**... *n* ] ]  
 カーソル内で更新できる列を定義します。 場合*column_name* [**、**. *n* ] は、指定しただけで示されている列が変更を許可します。 一覧を指定しなかった場合は、カーソルを READ ONLY として定義していない限り、すべての列を更新できます。  
  
## <a name="remarks"></a>解説  
 変数は宣言後、NULL に初期化されます。 宣言された変数に NULL 以外の値を代入するには、SET ステートメントを使用します。 変数に値を代入する SET ステートメントでは、1 つの値が返されます。 複数の変数を初期化する場合は、各ローカル変数に対して 1 つずつ、SET ステートメントを使用してください。  
  
 変数は式の内部だけで使用でき、オブジェクト名やキーワードの代わりに使用することはできません。 動的 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを作成するには、EXECUTE を使用します。  
  
 セットの構文規則 **@ * * * cursor_variable* LOCAL キーワードと GLOBAL キーワードを含めないでください。 ときに、セット **@ * * * cursor_variable* = CURSOR... 構文を使用する、カーソルは default to local cursor データベース オプションの設定に応じて、GLOBAL または LOCAL として作成します。  
  
 カーソル変数は、グローバル カーソルを参照する場合でも、常にローカルです。 カーソル変数でグローバル カーソルを参照する場合、カーソルに対してグローバル カーソル参照とローカル カーソル参照の両方が行われます。 詳細については、例 C を参照してください。  
  
 詳細については、次を参照してください。 [DECLARE CURSOR &#40;です。TRANSACT-SQL と #41 です](../../t-sql/language-elements/declare-cursor-transact-sql.md)。  
  
 複合代入演算子は、変数や、UPDATE、SELECT、および RECEIVE ステートメントの SET など、演算子の右側にある式で代入を行う任意の場所で使用できます。  
  
 SELECT ステートメントで、値を連結する目的で (つまり、集計値を計算する目的で) 変数を使用しないでください。 予期しないクエリ結果が生じる可能性があります。 (代入を含め) SELECT リスト内のすべての式は、出力行ごとに 1 回のみ実行されると保証されていないことが原因です。 詳細については、次を参照してください。[このサポート技術情報記事](http://support.microsoft.com/kb/287515)です。  
  
## <a name="permissions"></a>権限  
 public ロールのメンバーシップが必要です。 すべてのユーザーは、セットを使用できる **@ * * * local_variable*です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-printing-the-value-of-a-variable-initialized-by-using-set"></a>A. SET によって初期化された変数の値を出力する  
 次の例を作成、`@myvar`変数、文字列値では、変数におよびの値を表示、`@myvar`変数。  
  
```  
DECLARE @myvar char(20);  
SET @myvar = 'This is a test';  
SELECT @myvar;  
GO  
```  
  
### <a name="b-using-a-local-variable-assigned-a-value-by-using-set-in-a-select-statement"></a>B. SET によって値が代入されたローカル変数を、SELECT ステートメントで使用する  
 次の例では、`@state` という名前のローカル変数を作成し、このローカル変数を `SELECT` ステートメントで使用して、`Oregon` 州に住む全従業員の姓名を検索します。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @state char(25);  
SET @state = N'Oregon';  
SELECT RTRIM(FirstName) + ' ' + RTRIM(LastName) AS Name, City  
FROM HumanResources.vEmployee  
WHERE StateProvinceName = @state;  
```  
  
### <a name="c-using-a-compound-assignment-for-a-local-variable"></a>C. ローカル変数に対して複合代入を使用する  
 次の 2 つの例では、同じ結果が生成されます。 どちらも `@NewBalance` というローカル変数を作成し、その値に 10 を乗算して、`SELECT` ステートメントでローカル変数の新しい値を表示します。 2 番目の例では、複合代入演算子を使用します。  
  
```  
/* Example one */  
DECLARE  @NewBalance  int ;  
SET  @NewBalance  =  10;  
SET  @NewBalance  =  @NewBalance  *  10;  
SELECT  @NewBalance;  
  
/* Example Two */  
DECLARE @NewBalance int = 10;  
SET @NewBalance *= 10;  
SELECT @NewBalance;  
```  
  
### <a name="d-using-set-with-a-global-cursor"></a>D. グローバル カーソルに対して SET を使用する  
 次の例では、ローカル変数を作成した後、カーソル変数をグローバル カーソル名に設定します。  
  
```  
DECLARE my_cursor CURSOR GLOBAL   
FOR SELECT * FROM Purchasing.ShipMethod  
DECLARE @my_variable CURSOR ;  
SET @my_variable = my_cursor ;   
--There is a GLOBAL cursor declared(my_cursor) and a LOCAL variable  
--(@my_variable) set to the my_cursor cursor.  
DEALLOCATE my_cursor;   
--There is now only a LOCAL variable reference  
--(@my_variable) to the my_cursor cursor.  
```  
  
### <a name="e-defining-a-cursor-by-using-set"></a>E. SET を使用してカーソルを定義する  
 次の例では、`SET`ステートメントがカーソルを定義します。  
  
```  
DECLARE @CursorVar CURSOR;  
  
SET @CursorVar = CURSOR SCROLL DYNAMIC  
FOR  
SELECT LastName, FirstName  
FROM AdventureWorks2012.HumanResources.vEmployee  
WHERE LastName like 'B%';  
  
OPEN @CursorVar;  
  
FETCH NEXT FROM @CursorVar;  
WHILE @@FETCH_STATUS = 0  
BEGIN  
    FETCH NEXT FROM @CursorVar  
END;  
  
CLOSE @CursorVar;  
DEALLOCATE @CursorVar;  
```  
  
### <a name="f-assigning-a-value-from-a-query"></a>F. クエリから値を代入する  
 次の例では、クエリを使用して変数に値を代入します。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @rows int;  
SET @rows = (SELECT COUNT(*) FROM Sales.Customer);  
SELECT @rows;  
```  
  
### <a name="g-assigning-a-value-to-a-user-defined-type-variable-by-modifying-a-property-of-the-type"></a>G. ユーザー定義型のプロパティを変更してユーザー定義型変数に値を代入する  
 次の例は、ユーザー定義型の値を設定`Point`プロパティの値を変更することにより`X`の型。  
  
```  
DECLARE @p Point;  
SET @p.X = @p.X + 1.1;  
SELECT @p;  
GO  
```  
  
### <a name="h-assigning-a-value-to-a-user-defined-type-variable-by-invoking-a-method-of-the-type"></a>H. ユーザー定義型のメソッドを起動してユーザー定義型変数に値を代入する  
 次の例は、ユーザー定義型の値を設定**ポイント**メソッドを呼び出すことによって`SetXY`型のです。  
  
```  
DECLARE @p Point;  
SET @p=point.SetXY(23.5, 23.5);  
```  
  
### <a name="i-creating-a-variable-for-a-clr-type-and-calling-a-mutator-method"></a>I. CLR 型の変数を作成してミューテーター メソッドを呼び出す  
 次の例では、`Point` 型の変数を作成し、`Point` のミューテーター メソッドを実行します。  
  
```  
CREATE ASSEMBLY mytest from 'c:\test.dll' WITH PERMISSION_SET = SAFE  
CREATE TYPE Point EXTERNAL NAME mytest.Point  
GO  
DECLARE @p Point = CONVERT(Point, '')  
SET @p.SetXY(22, 23);  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="j-printing-the-value-of-a-variable-initialized-by-using-set"></a>J. SET によって初期化された変数の値を出力する  
 次の例を作成、`@myvar`変数、文字列値では、変数におよびの値を表示、`@myvar`変数。  
  
```  
DECLARE @myvar char(20);  
SET @myvar = 'This is a test';  
SELECT top 1 @myvar FROM sys.databases;  
  
```  
  
### <a name="k-using-a-local-variable-assigned-a-value-by-using-set-in-a-select-statement"></a>K. SET によって値が代入されたローカル変数を、SELECT ステートメントで使用する  
 次の例では、という名前のローカル変数`@dept`でこのローカル変数を使用して、`SELECT`で勤務するすべての従業員の姓と名を確認するステートメント、`Marketing`部門。  
  
```  
-- Uses AdventureWorks  
  
DECLARE @dept char(25);  
SET @dept = N'Marketing';  
SELECT RTRIM(FirstName) + ' ' + RTRIM(LastName) AS Name  
FROM DimEmployee   
WHERE DepartmentName = @dept;  
```  
  
### <a name="l-using-a-compound-assignment-for-a-local-variable"></a>L. ローカル変数に対して複合代入を使用する  
 次の 2 つの例では、同じ結果が生成されます。 どちらも `@NewBalance` というローカル変数を作成し、その値に `10` を乗算して、`SELECT` ステートメントでローカル変数の新しい値を表示します。 2 番目の例では、複合代入演算子を使用します。  
  
```  
/* Example one */  
DECLARE  @NewBalance  int ;  
SET  @NewBalance  =  10;  
SET  @NewBalance  =  @NewBalance  *  10;  
SELECT  TOP 1 @NewBalance FROM sys.tables;  
  
/* Example Two */  
DECLARE @NewBalance int = 10;  
SET @NewBalance *= 10;  
SELECT TOP 1 @NewBalance FROM sys.tables;  
```  
  
### <a name="m-assigning-a-value-from-a-query"></a>M. クエリから値を代入する  
 次の例では、クエリを使用して変数に値を代入します。  
  
```  
-- Uses AdventureWorks  
  
DECLARE @rows int;  
SET @rows = (SELECT COUNT(*) FROM dbo.DimCustomer);  
SELECT TOP 1 @rows FROM sys.tables;  
```  
  
## <a name="see-also"></a>参照  
 [複合の演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

