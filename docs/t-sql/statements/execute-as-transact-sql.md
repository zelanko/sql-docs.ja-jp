---
title: "EXECUTE (TRANSACT-SQL) AS |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
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
- EXECUTE AS
- EXECUTE_AS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- REVERT statement
- WITH NO REVERT clause
- sessions [SQL Server], execution context
- EXECUTE AS
- execution context [SQL Server]
- switching execution context
ms.assetid: 613b8271-7f7d-4378-b7a2-5a7698551dbd
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e389fdc50da662deeab7eba030a367e5fc7e97cb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="execute-as-transact-sql"></a>EXECUTE AS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  セッションの実行コンテキストを設定します。  
  
 既定では、セッションはユーザーがログインしたときに開始し、ユーザーがログオフしたときに終了します。 セッション中のすべての操作で、ユーザーに対する権限の確認が行われます。 ときに、 **EXECUTE AS**ステートメントを実行する、指定されたログインまたはユーザー名に、セッションの実行コンテキストが切り替えられます。 相手の呼び出しではなく、そのアカウントのログインとユーザーのセキュリティ トークンに対して権限は確認コンテキストの切り替え後、 **EXECUTE AS**ステートメントです。 実質的に、ユーザーまたはログイン アカウントは、セッションまたはモジュールの実行中、あるいはコンテキスト スイッチが明示的に戻されるまで続けて借用されます。  
  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
{ EXEC | EXECUTE } AS <context_specification>  
[;]  
  
<context_specification>::=  
{ LOGIN | USER } = 'name'  
    [ WITH { NO REVERT | COOKIE INTO @varbinary_variable } ]   
| CALLER  
```  
  
## <a name="arguments"></a>引数  
 Login  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 権限を借用する実行コンテキストがログインであることを指定します。 権限借用のスコープはサーバー レベルです。  
  
> [!NOTE]  
>  このオプションが使用できるは、包含データベースまたは SQL データベースではできません。  
  
 User  
 権限を借用するコンテキストが、現在のデータベース内のユーザーであることを指定します。 権限借用のスコープは、現在のデータベースに限定されます。 コンテキスト スイッチの対象がデータベース ユーザーであっても、そのユーザーのサーバー レベルの権限は継承されません。  
  
> [!IMPORTANT]  
>  データベース ユーザーに対するコンテキスト スイッチがアクティブであるときに、データベース外部のリソースへアクセスを試みると、ステートメントが失敗する原因となります。 Use*データベース*ステートメント、分散クエリ、および 3 部または 4 部構成の識別子を使用して別のデータベースを参照するクエリ。  
  
 **'** *名前* **'**  
 有効なユーザーまたはログイン名を指定します。 *名前*のメンバーである必要があります、 **sysadmin**固定サーバー ロール、またはプリンシパルとして存在[sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)または[sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)、それぞれします。  
  
 *名前*ローカル変数として指定することができます。  
  
 *名前*必要があります、単一アカウントであり、グループ、ロール、証明書、キー、または NT authority \localservice、NT authority \networkservice、NT authority \localsystem などのビルトイン アカウントにすることはできません。  
  
 詳細については、次を参照してください。[ユーザーまたはログイン名を指定する](#_user)このトピックで後述します。  
  
 NO REVERT  
 コンテキスト スイッチを以前のコンテキストに戻せないことを示します。 **NO REVERT**オプションは、アドホック レベルでのみ使用できます。  
  
 詳細については、以前のコンテキストに戻す、次を参照してください。 [REVERT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revert-transact-sql.md).  
  
 COOKIE に **@**  *varbinary_variable*  
 実行コンテキストできますのみ戻す前のコンテキストに戻す場合は、呼び出し元の REVERT WITH COOKIE ステートメントが含まれていますが、正しい指定 **@**  *varbinary_variable*値。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Cookie を **@**  *varbinary_variable*です。 **COOKIE に**オプションは、アドホック レベルでのみ使用できます。  
  
 **@***varbinary_variable*は**varbinary (8000)**です。  
  
> [!NOTE]  
>  Cookie**出力**のパラメーターが現在として記載されている**varbinary (8000)**な正しいの最大長。 ただし、現在の実装が返されます**varbinary (100)**です。 アプリケーションが予約**varbinary (8000)**アプリケーションのサイズの増加、将来のリリースでクッキーの戻り値が正しく動作を継続できるようにします。  
  
 CALLER  
 モジュール内で使用した場合、モジュールの呼び出し元のコンテキストで、モジュール内のステートメントが実行されます。  
  
 モジュール外で使用した場合、このステートメントでは何も処理されません。  
  
## <a name="remarks"></a>解説  
 実行コンテキストでの変更は、次のいずれかが行われるまで有効です。  
  
-   別の EXECUTE AS ステートメントの実行  
  
-   REVERT ステートメントの実行  
  
-   セッションが切断されます。  
  
-   コマンドが実行されたストアド プロシージャまたはトリガーの終了  
  
複数のプリンシパルで複数回、EXECUTE AS ステートメントを呼び出すと、実行コンテキストのスタックを作成できます。 これを実行すると、REVERT ステートメントにより、コンテキスト スタックの次の上位レベルのログインまたはユーザーにコンテキストが切り替えられます。 この動作のデモについては、次を参照してください。[例 A](#_exampleA)です。  
  
##  <a name="_user"></a>ユーザーまたはログイン名を指定します。  
 EXECUTE AS で指定されたユーザーまたはログイン名\<context_specification > でプリンシパルとして存在する必要があります**sys.database_principals**または**sys.server_principals**、それぞれ、またはEXECUTE AS ステートメントは失敗します。 さらに、プリンシパルで IMPERSONATE 権限が許可されている必要があります。 呼び出し元は、データベース所有者またはのメンバーである場合を除き、 **sysadmin**固定サーバー ロール、プリンシパル必要がありますもときに、ユーザーがアクセスして、データベースまたはインスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって、Windows グループのメンバーシップ。 たとえば、次のような条件を想定します。 
  
-   **\Sqlusers**グループへのアクセスには、 **Sales**データベース。  
  
-   **\Sqluser1**のメンバーである**SQLUsers**おり、そのため、暗黙のアクセスに、 **Sales**データベース。  
  
 **\Sqluser1**メンバーシップを介してデータベースへのアクセスを持つ、 **SQLUsers** 、ステートメントをグループ`EXECUTE AS USER = 'CompanyDomain\SqlUser1'`ために失敗`CompanyDomain\SqlUser1`内のプリンシパルとして存在しませんデータベースです。  
  
ユーザーが孤立している場合 (関連付けられたログインは存在しません)、およびユーザーが作成されませんでした**WITHOUT LOGIN**、 **EXECUTE AS**ユーザーに対しては失敗します。  
  
## <a name="best-practice"></a>推奨事項  
 セッションで操作を実行する場合に必要となる最低限の権限を持つログインまたはユーザーを指定します。 たとえば、データベース レベルの権限だけが必要な場合、サーバー レベルの権限が与えられているログイン名は指定しません。また、データベース所有者アカウントは、データベース レベルの権限が必要とされない場合は指定しません。  
  
> [!CAUTION]  
>  EXECUTE AS ステートメントを正常に実行限り、[!INCLUDE[ssDE](../../includes/ssde-md.md)]名前を解決することができます。 ドメイン ユーザーが存在する場合、Windows ユーザーに [!INCLUDE[ssDE](../../includes/ssde-md.md)] へのアクセス権がなくても、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のユーザーを解決できることがあります。 これにより、条件ログインへのアクセスなしで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]見えますにログインする権限を借用したログインは public または guest に許可する権限を持つのみです。  
  
## <a name="using-with-no-revert"></a>WITH NO REVERT の使用  
 EXECUTE AS ステートメントにオプションの WITH NO REVERT 句が含まれている場合、REVERT を使用、または別の EXECUTE AS ステートメントを実行して、セッションの実行コンテキストを元に戻すことはできません。 ステートメントで設定されたコンテキストはセッションが削除されるまで有効です。  
  
 ときに、WITH NO REVERT COOKIE = @*varbinary_variabl*e 句を指定する、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] @ する cookie の値を渡します*varbinary_variabl*e です。 ステートメントできますのみ戻す前のコンテキストに場合は、呼び出し元の REVERT WITH COOKIE によって、実行コンテキストが設定 = @*varbinary_variable*ステートメントに含まれる同じ *@varbinary_variable* 値。  
  
 このオプションは、接続プールが使用されている環境で役立ちます。 接続プールには、アプリケーション サーバーのアプリケーションで再利用できるよう、データベース接続のグループが保持されています。 値が渡されるため *@varbinary_variable*  EXECUTE AS の呼び出し元のみが知っているステートメントでは、呼び出し元保証できるほかの人に確立した実行コンテキストを変更することはできません。  
  
## <a name="determining-the-original-login"></a>元のログインの特定  
 使用して、 [ORIGINAL_LOGIN](../../t-sql/functions/original-login-transact-sql.md)のインスタンスに接続したログインの名前を返す関数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 この関数を使用すると、明示的または暗黙的にコンテキストが何度も切り替えられるセッションにおける、元のログインの ID を取得できます。  
  
## <a name="permissions"></a>Permissions  
 指定する**EXECUTE AS**呼び出し元には、ログインに**IMPERSONATE**指定したログインに対する権限名前を指定し、拒否されていない、 **IMPERSONATE ANY LOGIN**権限. 指定する**EXECUTE AS**呼び出し元には、データベース ユーザーで**IMPERSONATE**指定されたユーザー名に対するアクセス許可。 ときに**EXECUTE AS CALLER**が指定されている**IMPERSONATE**権限は必要ありません。  
  
## <a name="examples"></a>使用例  
  
###  <a name="_exampleA"></a> A. EXECUTE AS と REVERT を使用してコンテキストを切り替える  
 次の例では、複数のプリンシパルを使用してコンテキスト実行スタックを作成した後、 `REVERT`前の呼び出し元に、実行コンテキストをリセットするステートメントを使用しています。 `REVERT`実行コンテキストが呼び出し元に設定されるまで、スタックの上層に向かって複数回実行ステートメントです。  
  
```  
USE AdventureWorks2012;  
GO  
--Create two temporary principals  
CREATE LOGIN login1 WITH PASSWORD = 'J345#$)thb';  
CREATE LOGIN login2 WITH PASSWORD = 'Uor80$23b';  
GO  
CREATE USER user1 FOR LOGIN login1;  
CREATE USER user2 FOR LOGIN login2;  
GO  
--Give IMPERSONATE permissions on user2 to user1  
--so that user1 can successfully set the execution context to user2.  
GRANT IMPERSONATE ON USER:: user2 TO user1;  
GO  
--Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
-- Set the execution context to login1.   
EXECUTE AS LOGIN = 'login1';  
--Verify the execution context is now login1.  
SELECT SUSER_NAME(), USER_NAME();  
--Login1 sets the execution context to login2.  
EXECUTE AS USER = 'user2';  
--Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
-- The execution context stack now has three principals: the originating caller, login1 and login2.  
--The following REVERT statements will reset the execution context to the previous context.  
REVERT;  
--Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
REVERT;  
--Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
  
--Remove temporary principals.  
DROP LOGIN login1;  
DROP LOGIN login2;  
DROP USER user1;  
DROP USER user2;  
GO  
```  
  
### <a name="b-using-the-with-cookie-clause"></a>B. WITH COOKIE 句を使用する  
 次の例は、指定したユーザーのセッションの実行コンテキストを設定し、指定、WITH NO REVERT COOKIE = @*varbinary_variabl*e 句。 `REVERT`ステートメントに渡された値を指定する必要があります、`@cookie`に変数が、`EXECUTE AS`呼び出し元に戻すコンテキストを正常に戻すにはステートメントです。 この例を実行するには、例 A で作成したログイン `login1` とユーザー `user1` が存在している必要があります。  
  
```  
DECLARE @cookie varbinary(8000);  
EXECUTE AS USER = 'user1' WITH COOKIE INTO @cookie;  
-- Store the cookie in a safe location in your application.  
-- Verify the context switch.  
SELECT SUSER_NAME(), USER_NAME();  
--Display the cookie value.  
SELECT @cookie;  
GO  
-- Use the cookie in the REVERT statement.  
DECLARE @cookie varbinary(8000);  
-- Set the cookie value to the one from the SELECT @cookie statement.  
SET @cookie = <value from the SELECT @cookie statement>;  
REVERT WITH COOKIE = @cookie;  
-- Verify the context switch reverted.  
SELECT SUSER_NAME(), USER_NAME();  
GO  
```  
  
## <a name="see-also"></a>参照  
 [元に戻す (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revert-transact-sql.md)   
 [EXECUTE AS 句 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/execute-as-clause-transact-sql.md)  
  
  


