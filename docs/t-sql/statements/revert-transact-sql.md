---
title: "(TRANSACT-SQL) を元に戻す |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REVERT_TSQL
- REVERT
dev_langs:
- TSQL
helpviewer_keywords:
- REVERT statement
- context switching [SQL Server], reverting
- reverting execution context
- REVERT WITH COOKIE statement
- execution context [SQL Server]
- COOKIE clause
ms.assetid: 4688b17a-dfd1-4f03-8db4-273a401f879f
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 033442da3e10fd834963df30ea071a220464de6f
ms.contentlocale: ja-jp
ms.lasthandoff: 10/24/2017

---
# <a name="revert-transact-sql"></a>REVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  実行コンテキストを、最後の EXECUTE AS ステートメントの呼び出し元に戻します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
REVERT  
    [ WITH COOKIE = @varbinary_variable ]  
```  
  
## <a name="arguments"></a>引数  
 WITH COOKIE = @*varbinary_variable*  
 対応する作成されたクッキー指定[EXECUTE AS](../../t-sql/statements/execute-as-transact-sql.md)スタンドアロンのステートメント。 *@varbinary_variable***varbinary (100)**です。  
  
## <a name="remarks"></a>解説  
 REVERT は、ストアド プロシージャまたはユーザー定義関数などのモジュール内、またはスタンドアロンのステートメントとして指定できます。 モジュール内で指定した場合、REVERT はモジュール内で定義された EXECUTE AS ステートメントにのみ適用されます。 たとえば、次のストアド プロシージャは、`EXECUTE AS`ステートメントの後に、`REVERT`ステートメントです。  
  
```  
CREATE PROCEDURE dbo.usp_myproc   
  WITH EXECUTE AS CALLER  
AS   
    SELECT SUSER_NAME(), USER_NAME();  
    EXECUTE AS USER = 'guest';  
    SELECT SUSER_NAME(), USER_NAME();  
    REVERT;  
    SELECT SUSER_NAME(), USER_NAME();  
GO  
```  
  
 次の例のように、ストアド プロシージャが実行されるセッションで、セッションの実行コンテキストが明示的に `login1` に変更されるとします。  
  
```  
  -- Sets the execution context of the session to 'login1'.  
EXECUTE AS LOGIN = 'login1';  
GO  
EXECUTE dbo.usp_myproc;   
```  
  
 `REVERT`ステートメント内で定義される`usp_myproc`モジュール内に設定された実行コンテキストを切り替えるには、モジュールの外部に設定された実行コンテキストは影響しません。 つまり、セッションの実行コンテキストに設定されたまま`login1`です。  
  
 スタンドアロンのステートメントとして指定した場合、REVERT はバッチまたはセッション内で定義された EXECUTE AS に適用されます。 対応する EXECUTE AS ステートメントに WITH NO REVERT 句が含まれている場合、REVERT は無効です。 この場合、実行コンテキストはセッションが削除されるまで有効です。  
  
## <a name="using-revert-with-cookie"></a>REVERT WITH COOKIE の使用  
 EXECUTE をセッションの実行コンテキストを設定するために使用するステートメントに WITH NO REVERT COOKIE のオプションの句を含めることができます = @*varbinary_variabl*e です。 このステートメントを実行すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] @ する cookie を渡します*varbinary_variabl*e です。 実行コンテキスト設定いるステートメントできますのみ戻す前のコンテキストに場合は、呼び出し元の REVERT WITH COOKIE = @*varbinary_variable*ステートメントが含まれていますが、正しい *@varbinary_variable* 値。  
  
 このメカニズムは、接続プールが使用される環境で役立ちます。 接続プールには、複数のエンド ユーザーがアプリケーションで再利用するデータベース接続のグループが管理されています。 値が渡されるため *@varbinary_variable*  EXECUTE の呼び出し元のみが知っている呼び出し元ステートメントとして (この場合は、アプリケーション)、エンドユーザーが確立した実行コンテキストを変更できないことを保証できますアプリケーションが起動します。 実行コンテキストが戻された後、アプリケーションではコンテキストを他のプリンシパルに切り替えることができます。  
  
## <a name="permissions"></a>Permissions  
 権限は必要ありません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-execute-as-and-revert-to-switch-context"></a>A. EXECUTE AS と REVERT を使用してコンテキストを切り替える  
 次の例では、複数のプリンシパルを使用してコンテキスト実行スタックを作成します。 REVERT ステートメントを使用して実行コンテキストを以前のコンテキストに戻します。 REVERT ステートメントは、実行コンテキストが最初の呼び出し元に設定されるまで、スタックの上層に向かって複数回実行されます。  
  
```  
USE AdventureWorks2012;  
GO  
-- Create two temporary principals.  
CREATE LOGIN login1 WITH PASSWORD = 'J345#$)thb';  
CREATE LOGIN login2 WITH PASSWORD = 'Uor80$23b';  
GO  
CREATE USER user1 FOR LOGIN login1;  
CREATE USER user2 FOR LOGIN login2;  
GO  
-- Give IMPERSONATE permissions on user2 to user1  
-- so that user1 can successfully set the execution context to user2.  
GRANT IMPERSONATE ON USER:: user2 TO user1;  
GO  
-- Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
-- Set the execution context to login1.   
EXECUTE AS LOGIN = 'login1';  
-- Verify that the execution context is now login1.  
SELECT SUSER_NAME(), USER_NAME();  
-- Login1 sets the execution context to login2.  
EXECUTE AS USER = 'user2';  
-- Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
-- The execution context stack now has three principals: the originating caller, login1, and login2.  
-- The following REVERT statements will reset the execution context to the previous context.  
REVERT;  
-- Display the current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
REVERT;  
-- Display the current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
  
-- Remove the temporary principals.  
DROP LOGIN login1;  
DROP LOGIN login2;  
DROP USER user1;  
DROP USER user2;  
GO  
```  
  
### <a name="b-using-the-with-cookie-clause"></a>B. WITH COOKIE 句を使用する  
 次の例は、指定したユーザーのセッションの実行コンテキストを設定し、指定、WITH NO REVERT COOKIE = @*varbinary_variabl*e 句。 `REVERT`ステートメントに渡された値を指定する必要があります、`@cookie`に変数が、`EXECUTE AS`呼び出し元に戻すコンテキストを正常に戻すにはステートメントです。 この例を実行するには、例 A で作成したログイン `login1` とユーザー `user1` が存在している必要があります。  
  
```  
DECLARE @cookie varbinary(100);  
EXECUTE AS USER = 'user1' WITH COOKIE INTO @cookie;  
-- Store the cookie somewhere safe in your application.  
-- Verify the context switch.  
SELECT SUSER_NAME(), USER_NAME();  
--Display the cookie value.  
SELECT @cookie;  
GO  
-- Use the cookie in the REVERT statement.  
DECLARE @cookie varbinary(100);  
-- Set the cookie value to the one from the SELECT @cookie statement.  
SET @cookie = <value from the SELECT @cookie statement>;  
REVERT WITH COOKIE = @cookie;  
-- Verify the context switch reverted.  
SELECT SUSER_NAME(), USER_NAME();  
GO  
```  
  
## <a name="see-also"></a>参照  
 [実行 AS (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/execute-as-transact-sql.md)   
 [EXECUTE AS 句 &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [SUSER_NAME & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/suser-name-transact-sql.md)   
 [USER_NAME & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/user-name-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)  
  
  

