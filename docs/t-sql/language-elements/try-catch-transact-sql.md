---
title: "TRY しています.CATCH (TRANSACT-SQL) |Microsoft ドキュメント"
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
f1_keywords:
- BEGIN_TRY_TSQL
- BEGIN_CATCH_TSQL
- TRY
- BEGIN TRY
- TRY_TSQL
- BEGIN CATCH
dev_langs: TSQL
helpviewer_keywords:
- BEGIN CATCH statement
- uncommittable transactions
- errors [SQL Server], TRY...CATCH
- TRY block [SQL Server]
- XACT_STATE function
- TRY...CATCH [SQL Server]
- BEGIN TRY statement
- CATCH block
ms.assetid: 248df62a-7334-4bca-8262-235a28f4b07f
caps.latest.revision: "79"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: d344044a5ce4a0cd995cc1695b69ac9312d4db74
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="trycatch-transact-sql"></a>TRY...CATCH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  実装のエラー処理[!INCLUDE[tsql](../../includes/tsql-md.md)]での例外処理に似た、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual c# と[!INCLUDE[msCoName](../../includes/msconame-md.md)]Visual C の言語です。 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのグループを TRY ブロックで囲むことができます。 TRY ブロック内でエラーが発生すると、CATCH ブロックで囲まれた別のステートメントのグループに制御が渡されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
BEGIN TRY  
     { sql_statement | statement_block }  
END TRY  
BEGIN CATCH  
     [ { sql_statement | statement_block } ]  
END CATCH  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *sql_statement*  
 いずれかである[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。  
  
 *statement_block*  
 すべてのグループ[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ内のステートメントまたは BEGIN で囲むしています.終了ブロック。  
  
## <a name="remarks"></a>解説  
 TRY...CATCH 構造は、データベース接続を閉じない、重大度が 10 を超えるすべての実行エラーを検出します。  
  
 TRY ブロックの直後には、関連する CATCH ブロックを記述する必要があります。 END TRY ステートメントと BEGIN CATCH ステートメントの間に他のステートメントを含めると、構文エラーが生成されます。  
  
 TRY...CATCH 構造は複数のバッチをまたぐことはできません。 TRY しています.CATCH 構造での複数のブロックをまたぐことはできません[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 たとえば、試してみてください.CATCH 構造では、次の 2 つの開始をまたぐことはできません.最後のブロック[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント IF にまたがって配置できないとしています.それ以外の場合を構築します。  
  
 TRY ブロックで囲まれたコードでエラーが発生しなかった場合は、TRY ブロック内の最後のステートメントの実行が完了すると、END CATCH ステートメントの直後にあるステートメントに制御が渡されます。 TRY ブロックで囲まれたコードでエラーが発生した場合は、CATCH ブロック内の最初のステートメントに制御が渡されます。 END CATCH ステートメントがストアド プロシージャまたはトリガー内の最後のステートメントである場合は、そのストアド プロシージャの呼び出しまたはトリガーの起動を実行したステートメントに制御が渡されます。  
  
 CATCH ブロック内のコードが完了すると、END CATCH ステートメントの直後にあるステートメントに制御が渡されます。 CATCH ブロックによってトラップされたエラーは、呼び出し元のアプリケーションに返されません。 エラー情報の一部をアプリケーションに返す必要がある場合は、CATCH ブロック内のコードでその処理を行います。これには、SELECT 結果セットや、RAISERROR ステートメントおよび PRINT ステートメントなどのメカニズムを使用します。  
  
 TRY...CATCH 構造は入れ子にすることができます。 TRY ブロックと CATCH ブロックのどちらにも、入れ子になった TRY...CATCH 構造を含めることができます。 たとえば、CATCH ブロックに TRY...CATCH 構造を埋め込み、CATCH コードによって発生したエラーを処理することができます。  
  
 CATCH ブロックで発生したエラーは、他の場所で生成されたエラーと同じように扱われます。 CATCH ブロックに入れ子になった TRY...CATCH 構造が含まれている場合、入れ子になった TRY ブロックでエラーが発生すると、入れ子になった CATCH ブロックに制御が渡されます。 入れ子になった TRY...CATCH 構造が存在しない場合、エラーは呼び出し元に返されます。  
  
 TRY...CATCH 構造では、TRY ブロック内のコードによって実行されたストアド プロシージャまたはトリガーからの処理されないエラーが検出されます。 また、ストアド プロシージャまたはトリガーに独自の TRY...CATCH 構造を含めて、それらのコードによって生成されたエラーを処理することもできます。 たとえば、TRY ブロックでストアド プロシージャを実行し、そのストアド プロシージャでエラーが発生した場合、次の方法でエラーを処理できます。  
  
-   ストアド プロシージャに独自の TRY...CATCH 構造が含まれていない場合、エラーが発生すると、EXECUTE ステートメントを含んでいる TRY ブロックに関連付けられた CATCH ブロックに制御が返されます。  
  
-   ストアド プロシージャに TRY...CATCH 構造が含まれている場合、エラーによってストアド プロシージャ内の CATCH ブロックに制御が渡されます。 CATCH ブロックのコードが完了すると、ストアド プロシージャを呼び出した EXECUTE ステートメントの直後にあるステートメントに制御が返されます。  
  
 GOTO ステートメントを使用して TRY ブロックまたは CATCH ブロックに入ることはできません。 GOTO ステートメントは、同じ TRY ブロックまたは CATCH ブロック内のラベルに移動したり、TRY ブロックまたは CATCH ブロックから抜けるために使用できます。  
  
 TRY...CATCH 構造をユーザー定義関数内で使用することはできません。  
  
## <a name="retrieving-error-information"></a>エラー情報の取得  
 CATCH ブロックのスコープ内では、次のシステム関数を使用して、CATCH ブロックが実行される原因となったエラーに関する情報を取得できます。  
  
-   [ERROR_NUMBER()](../../t-sql/functions/error-number-transact-sql.md)エラーの数を返します。  
  
-   [ERROR_SEVERITY()](../../t-sql/functions/error-severity-transact-sql.md)重大度を返します。  
  
-   [ERROR_STATE()](../../t-sql/functions/error-state-transact-sql.md)エラー状態番号を返します。  
  
-   [ERROR_PROCEDURE()](../../t-sql/functions/error-procedure-transact-sql.md)エラーが発生したストアド プロシージャまたはトリガーの名前を返します。  
  
-   [ERROR_LINE()](../../t-sql/functions/error-line-transact-sql.md)エラーを発生させたルーチン内の行番号を返します。  
  
-   [ERROR_MESSAGE()](../../t-sql/functions/error-message-transact-sql.md)エラー メッセージの全文を返します。 このテキストには、長さ、オブジェクト名、回数など、置き換え可能なパラメーターに提供される値が含まれます。  
  
 CATCH ブロックのスコープの外側から呼び出されると、これらの関数は NULL を返します。 エラー情報は、CATCH ブロックのスコープ内のどこからでも、これらの関数を使用して取得できます。 たとえば、次のスクリプトでは、エラー処理関数を含んでいるストアド プロシージャを示しています。 `CATCH` 構造の `TRY…CATCH` ブロックでは、このストアド プロシージャを呼び出して、エラーに関する情報を返しています。  
  
```sql  
-- Verify that the stored procedure does not already exist.  
IF OBJECT_ID ( 'usp_GetErrorInfo', 'P' ) IS NOT NULL   
    DROP PROCEDURE usp_GetErrorInfo;  
GO  
  
-- Create procedure to retrieve error information.  
CREATE PROCEDURE usp_GetErrorInfo  
AS  
SELECT  
    ERROR_NUMBER() AS ErrorNumber  
    ,ERROR_SEVERITY() AS ErrorSeverity  
    ,ERROR_STATE() AS ErrorState  
    ,ERROR_PROCEDURE() AS ErrorProcedure  
    ,ERROR_LINE() AS ErrorLine  
    ,ERROR_MESSAGE() AS ErrorMessage;  
GO  
  
BEGIN TRY  
    -- Generate divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    -- Execute error retrieval routine.  
    EXECUTE usp_GetErrorInfo;  
END CATCH;   
```  
  
 エラー\_ \*関数でも、動作、`CATCH`ブロック、[ネイティブ コンパイル ストアド プロシージャ](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)です。  
  
## <a name="errors-unaffected-by-a-trycatch-construct"></a>TRY...CATCH 構造の影響を受けないエラー  
 TRY...CATCH 構造では、次の条件はトラップされません。  
  
-   重大度が 10 以下の警告または情報メッセージ。  
  
-   重大度が 20 以上で、そのセッションの [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] タスク処理を終了させるエラー。 重大度が 20 以上のエラーが発生し、データベース接続が切断されない場合、TRY...CATCH によってエラーが処理されます。  
  
-   クライアントの割り込み要求や中断されたクライアント接続などのアテンション。  
  
-   システム管理者による KILL ステートメントを使用したセッションの終了。  
  
 次の種類のエラーは、TRY...CATCH 構造と同じ実行レベルで発生した場合には、CATCH ブロックによって処理されません。  
  
-   構文エラーなど、バッチの実行を妨げるコンパイル エラー。  
  
-   名前の遅延解決のためのコンパイル後に発生するオブジェクト名の解決エラーなどのステートメント レベルの再コンパイル中に発生するエラーです。  
  
 これらのエラーは、バッチ、ストアド プロシージャ、またはトリガーを実行したレベルに返されます。  
  
 TRY ブロック内の下位の実行レベル (たとえば、sp_executesql またはユーザー定義のストアド プロシージャを実行しているとき) でのコンパイル中またはステートメントレベルの再コンパイル中にエラーが発生した場合、そのエラーは TRY...CATCH 構造よりも下位のレベルで発生し、関連する CATCH ブロックによって処理されます。  
  
 次の例は、オブジェクト名の解決エラーの生成方法を示しています、`SELECT`ステートメントがによってキャッチされない、`TRY…CATCH`構築が、によってキャッチされました、`CATCH`をブロックするときに、同じ`SELECT`ステートメントが実行される格納された内部プロシージャです。  
  
```sql  
BEGIN TRY  
    -- Table does not exist; object name resolution  
    -- error not caught.  
    SELECT * FROM NonexistentTable;  
END TRY  
BEGIN CATCH  
    SELECT   
        ERROR_NUMBER() AS ErrorNumber  
       ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH  
```  
  
 エラーはキャッチされず、制御からパスのうち、`TRY…CATCH`上位のレベルを構築します。  
  
 実行している、`SELECT`ストアド プロシージャ内のステートメントより低いレベルで発生するエラーが発生、`TRY`ブロックします。 このエラーは `TRY…CATCH` 構造によって処理されます。  
  
```sql  
-- Verify that the stored procedure does not exist.  
IF OBJECT_ID ( N'usp_ExampleProc', N'P' ) IS NOT NULL   
    DROP PROCEDURE usp_ExampleProc;  
GO  
  
-- Create a stored procedure that will cause an   
-- object resolution error.  
CREATE PROCEDURE usp_ExampleProc  
AS  
    SELECT * FROM NonexistentTable;  
GO  
  
BEGIN TRY  
    EXECUTE usp_ExampleProc;  
END TRY  
BEGIN CATCH  
    SELECT   
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
```  
  
## <a name="uncommittable-transactions-and-xactstate"></a>コミット不可能なトランザクションと XACT_STATE  
 TRY ブロックで生成されたエラーによって現在のトランザクションの状態が無効になる場合、トランザクションはコミット不可能なトランザクションとして分類されます。 通常は TRY ブロックの外部でトランザクションを終了させるエラーが、TRY ブロックの内部で発生すると、トランザクションはコミット不可能な状態になります。 コミット不可能なトランザクションでは、読み取り操作または ROLLBACK TRANSACTION のみを実行できます。 このトランザクションで、書き込み操作または COMMIT TRANSACTION を生成する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行することはできません。 XACT_STATE 関数は、トランザクションがコミット不可能なトランザクションと分類されている場合、値 -1 を返します。 バッチが完了すると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]によってコミット不可能なトランザクションがロールバックされます。 トランザクションがコミット不可能な状態になったときにエラー メッセージが送信されなかった場合、バッチが完了すると、エラー メッセージがクライアント アプリケーションに送信されます。 これは、コミット不可能なトランザクションが検出され、ロールバックされたことを示します。  
  
 コミット不可能なトランザクションと XACT_STATE 関数の詳細については、次を参照してください。 [XACT_STATE (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/xact-state-transact-sql.md).  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-trycatch"></a>A. TRY...CATCH の使用  
 次の例は、 `SELECT` 0 除算エラーを生成するステートメント。 エラーが原因で、関連付けられているジャンプは実行`CATCH`ブロックします。  
  
```sql  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_LINE() AS ErrorLine  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
### <a name="b-using-trycatch-in-a-transaction"></a>B. トランザクション内で TRY...CATCH を使用する  
 次の例では、トランザクション内での `TRY…CATCH` ブロックの動作を示しています。 内のステートメント、`TRY`ブロックには、制約違反エラーが生成されます。  
  
```sql  
BEGIN TRANSACTION;  
  
BEGIN TRY  
    -- Generate a constraint violation error.  
    DELETE FROM Production.Product  
    WHERE ProductID = 980;  
END TRY  
BEGIN CATCH  
    SELECT   
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_LINE() AS ErrorLine  
        ,ERROR_MESSAGE() AS ErrorMessage;  
  
    IF @@TRANCOUNT > 0  
        ROLLBACK TRANSACTION;  
END CATCH;  
  
IF @@TRANCOUNT > 0  
    COMMIT TRANSACTION;  
GO  
```  
  
### <a name="c-using-trycatch-with-xactstate"></a>C. TRY...CATCH と XACT_STATE を使用する  
 次の例を使用する方法を示しています、`TRY…CATCH`コンストラクトをトランザクション内で発生するエラーを処理します。 `XACT_STATE` 関数により、トランザクションをコミットすべきか、またはロールバックすべきかが決定されます。 この例では `SET XACT_ABORT` は `ON` です。 これにより、制約違反エラーが発生したときに、トランザクションはコミット不可能になります。  
  
```sql  
-- Check to see whether this stored procedure exists.  
IF OBJECT_ID (N'usp_GetErrorInfo', N'P') IS NOT NULL  
    DROP PROCEDURE usp_GetErrorInfo;  
GO  
  
-- Create procedure to retrieve error information.  
CREATE PROCEDURE usp_GetErrorInfo  
AS  
    SELECT   
         ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_LINE () AS ErrorLine  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_MESSAGE() AS ErrorMessage;  
GO  
  
-- SET XACT_ABORT ON will cause the transaction to be uncommittable  
-- when the constraint violation occurs.   
SET XACT_ABORT ON;  
  
BEGIN TRY  
    BEGIN TRANSACTION;  
        -- A FOREIGN KEY constraint exists on this table. This   
        -- statement will generate a constraint violation error.  
        DELETE FROM Production.Product  
            WHERE ProductID = 980;  
  
    -- If the DELETE statement succeeds, commit the transaction.  
    COMMIT TRANSACTION;  
END TRY  
BEGIN CATCH  
    -- Execute error retrieval routine.  
    EXECUTE usp_GetErrorInfo;  
  
    -- Test XACT_STATE:  
        -- If 1, the transaction is committable.  
        -- If -1, the transaction is uncommittable and should   
        --     be rolled back.  
        -- XACT_STATE = 0 means that there is no transaction and  
        --     a commit or rollback operation would generate an error.  
  
    -- Test whether the transaction is uncommittable.  
    IF (XACT_STATE()) = -1  
    BEGIN  
        PRINT  
            N'The transaction is in an uncommittable state.' +  
            'Rolling back transaction.'  
        ROLLBACK TRANSACTION;  
    END;  
  
    -- Test whether the transaction is committable.  
    IF (XACT_STATE()) = 1  
    BEGIN  
        PRINT  
            N'The transaction is committable.' +  
            'Committing transaction.'  
        COMMIT TRANSACTION;     
    END;  
END CATCH;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-trycatch"></a>D. TRY...CATCH の使用  
 次の例は、 `SELECT` 0 除算エラーを生成するステートメント。 エラーが原因で、関連付けられているジャンプは実行`CATCH`ブロックします。  
  
```sql  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [THROW &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/throw-transact-sql.md)   
 [データベース エンジン エラーの重大度](../../relational-databases/errors-events/database-engine-error-severities.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40; です。TRANSACT-SQL と&#41; です。](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)   
 [GOTO &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/goto-transact-sql.md)   
 [作業を開始してください.END &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [XACT_STATE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/xact-state-transact-sql.md)   
 [SET XACT_ABORT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-xact-abort-transact-sql.md)  
  
  

