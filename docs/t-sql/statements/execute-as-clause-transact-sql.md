---
title: "EXECUTE AS 句 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- AS
- AS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- permission sets [SQL Server]
- queues [SQL Server]
- stored procedures [SQL Server], executing
- user-defined functions [SQL Server], execution context
- EXECUTE AS
- triggers [SQL Server], execution context
- execution context [SQL Server]
- switching execution context
- functions [SQL Server], execution context
ms.assetid: bd517aa3-f06e-4356-87d8-70de5df4494a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: baf3fdc592265f1c2117ef3358820ae94ce8536c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="execute-as-clause-transact-sql"></a>EXECUTE AS 句 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]次のユーザー定義モジュールの実行コンテキストを定義することができます: 関数 (インライン テーブル値関数) を除く、プロシージャ、キュー、およびトリガーします。  
  
 モジュールが実行されるコンテキストを指定することにより、[!INCLUDE[ssDE](../../includes/ssde-md.md)]がどのユーザー アカウントを使用して、モジュールによって参照されるオブジェクトの権限を検証するかを制御できます。 これにより、ユーザー定義モジュールとそれらのモジュールによって参照されるオブジェクト間に存在する、オブジェクトのチェーン全体に関する権限の管理を、さらに柔軟に制御できます。 のみ、モジュール自体に対する、参照先オブジェクトに対する明示的なアクセス許可を付与しなくてもユーザーに許可する必要があります。 モジュールによってアクセスされるオブジェクトに対する権限が必要なのは、そのモジュールを実行しているユーザーのみです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- SQL Server Syntax  
Functions (except inline table-valued functions), Stored Procedures, and DML Triggers  
{ EXEC | EXECUTE } AS { CALLER | SELF | OWNER | 'user_name' }   
  
DDL Triggers with Database Scope  
{ EXEC | EXECUTE } AS { CALLER | SELF | 'user_name' }   
  
DDL Triggers with Server Scope and logon triggers  
{ EXEC | EXECUTE } AS { CALLER | SELF | 'login_name' }   
  
Queues  
{ EXEC | EXECUTE } AS { SELF | OWNER | 'user_name' }   
```  
  
```  
  
-- Windows Azure SQL Database Syntax  
Functions (except inline table-valued functions), Stored Procedures, and DML Triggers  
  
{ EXEC | EXECUTE } AS { CALLER | SELF | OWNER | 'user_name' }   
  
DDL Triggers with Database Scope  
  
{ EXEC | EXECUTE } AS { CALLER | SELF | 'user_name' }  
  
```  
  
## <a name="arguments"></a>引数  
 **呼び出し元**  
 モジュール内のステートメントを、モジュールの呼び出し元のコンテキストで実行します。 モジュールを実行するユーザーは、モジュール自体に対してだけでなく、そのモジュールによって参照されるすべてのデータベース オブジェクトに対する、適切な権限を持っている必要があります。  
  
 呼び出し元、キューを除くすべてのモジュールの既定値と同じ[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]動作します。  
  
 CALLER は、CREATE QUEUE または ALTER QUEUE ステートメントでは指定できません。  
  
 **SELF**  
 EXECUTE AS SELF は EXECUTE AS に相当*user_name*を指定したユーザーを作成またはモジュールを変更します。 作成またはモジュールを変更するユーザーの実際のユーザー ID が格納されている、 **execute_as_principal_id**内の列、 **sys.sql_modules**または**sys.service_queues**カタログ ビューです。  
  
 SELF は、キューの場合の既定値です。  
  
> [!NOTE]  
>  ユーザー ID を変更する、 **execute_as_principal_id**で、 **sys.service_queues**カタログ ビューを ALTER QUEUE ステートメントで設定として、実行を明示的に指定する必要があります。  
  
 OWNER  
 モジュール内のステートメントを、モジュールの現在の所有者のコンテキストで実行します。 モジュールの所有者が指定されていない場合、そのモジュールのスキーマの所有者が使用されます。 OWNER は、DDL トリガーまたはログオン トリガーに対しては指定できません。  
  
> [!IMPORTANT]  
>  OWNER は、単一アカウントにマップする必要があります。ロールまたはグループにはマップできません。  
  
 **'** *user_name* **'**  
 指定されたユーザーのコンテキストで、モジュール内のステートメントが実行を指定します*user_name*です。 に対して、モジュール内のすべてのオブジェクトに対するアクセス許可が検証されます*user_name*です。 *user_name*の DDL トリガー サーバー スコープまたはログオン トリガーを指定することはできません。 使用して*login_name*代わりにします。  
  
 *user_name*現在のデータベースに存在する必要があり、単一アカウントを指定する必要があります。 *user_name*グループ、ロール、証明書、キー、または NT authority \localservice、NT authority \networkservice、NT authority \localsystem などのビルトイン アカウントにすることはできません。  
  
 実行コンテキストのユーザー ID がメタデータに格納されで表示できます、 **execute_as_principal_id**内の列、 **sys.sql_modules**または**sys.assembly_modules**カタログ ビューです。  
  
 **'** *login_name* **'**  
 コンテキストで、モジュール内のステートメントが実行を指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で指定されたログイン*login_name*です。 に対して、モジュール内のすべてのオブジェクトに対するアクセス許可が検証されます*login_name*です。 *login_name*の DDL トリガー サーバー スコープまたはログオン トリガーに対してのみ指定できます。  
  
 *login_name*グループ、ロール、証明書、キー、または NT authority \localservice、NT authority \networkservice、NT authority \localsystem などのビルトイン アカウントにすることはできません。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]による、モジュール内で参照されるオブジェクトに対する権限の評価方法は、呼び出し元のオブジェクトと参照されるオブジェクト間に存在する所有権の継承によって異なります。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、呼び出し元のユーザーに対して、参照されるすべてのオブジェクトへのアクセスを許可するためには、所有権の継承を使用する方法しかありませんでした。  
  
 所有権の継承には、次のような制限があります。  
  
-   DML ステートメントの SELECT、INSERT、UPDATE、DELETE にのみ適用されます。  
  
-   呼び出し元のオブジェクトと呼び出されたオブジェクトの所有者は同一である必要があります。  
  
-   モジュール内部の動的クエリには適用されません。  
  
 モジュール内で指定される実行コンテキストに関係なく、次の操作が常に適用されます。  
  
-   モジュールを実行すると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]まずモジュールを実行するユーザーがそのモジュールに対する EXECUTE 権限を持っていることを確認します。  
  
-   所有権の継承ルールは、引き続き適用されます。 つまり、呼び出し元のオブジェクトと呼び出されたオブジェクトの所有者が同一の場合、基になるオブジェクトに対する権限は確認されません。  
  
 ユーザーが、CALLER 以外のコンテキスト内で実行するように指定されたモジュールを実行すると、そのユーザーに対してモジュールの実行権限が確認されますが、さらに、そのモジュールによってアクセスされるオブジェクトの追加の権限確認が、EXECUTE AS 句で指定されたユーザー アカウントに対して行われます。 実質的に、モジュールを実行するユーザーは、指定されたユーザーの権限を借用します。  
  
 モジュールの EXECUTE AS 句で指定されたコンテキストは、モジュールの実行中のみ有効です。 モジュールの実行が完了すると、コンテキストは呼び出し元に戻されます。  
  
## <a name="specifying-a-user-or-login-name"></a>ユーザーまたはログイン名の指定  
 モジュールの EXECUTE AS 句で指定されたデータベース ユーザーまたはサーバー ログインは、モジュールが変更されて別のコンテキストで実行されるまでは削除できません。  
  
 EXECUTE AS 句で指定されたユーザーまたはログイン名がプリンシパルとして存在する必要があります**sys.database_principals**または**sys.server_principals**、それぞれ、またはそれ以外の場合、create または alter モジュールの操作が失敗します。. また、モジュールを作成または変更するユーザーには、そのプリンシパルに対する IMPERSONATE 権限が必要です。  
  
 ユーザーが、Windows グループのメンバーシップを使って [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータベースまたはインスタンスに暗黙的にアクセスした場合、モジュールが作成されるときに次のいずれかの要件を満たしていれば、EXECUTE AS 句で指定されたユーザーが暗黙的に作成されます。  
  
-   指定したユーザーまたはログインのメンバーである、 **sysadmin**固定サーバー ロール。  
  
-   モジュールを作成するユーザーに、プリンシパルを作成する権限が与えられていること。  
  
 これらの要件がどちらも満たされない場合、モジュールの作成操作は失敗します。  
  
> [!IMPORTANT]  
>  場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ローカル (MSSQLSERVER) サービスを実行しているアカウント (local service またはローカル ユーザー アカウント) が、EXECUTE AS で指定されている Windows ドメイン アカウントのグループ メンバーシップを取得する権限は与えられません句。 このため、モジュールの実行は失敗します。  
  
 たとえば、次のような条件を想定します。  
  
-   **\Sqlusers**グループへのアクセスには、 **Sales**データベース。  
  
-   **\Sqluser1**のメンバーである**SQLUsers**おり、したがってへのアクセス、 **Sales**データベース。  
  
-   モジュールを作成または変更するユーザーに、プリンシパルを作成する権限が与えられている。  
  
 ときに、次`CREATE PROCEDURE`ステートメントの実行、`CompanyDomain\SqlUser1`が暗黙的に作成、データベースでプリンシパル、`Sales`データベース。  
  
```  
USE Sales;  
GO  
CREATE PROCEDURE dbo.usp_Demo  
WITH EXECUTE AS 'CompanyDomain\SqlUser1'  
AS  
SELECT user_name();  
GO  
```  
  
## <a name="using-execute-as-caller-stand-alone-statement"></a>スタンドアロンの EXECUTE AS CALLER ステートメントの使用  
 スタンドアロンの EXECUTE AS CALLER ステートメントをモジュール内で使用すると、実行コンテキストがそのモジュールの呼び出し元に設定されます。  
  
 次のストアド プロシージャが `SqlUser2` によって呼び出されるとします。  
  
```  
CREATE PROCEDURE dbo.usp_Demo  
WITH EXECUTE AS 'SqlUser1'  
AS  
SELECT user_name(); -- Shows execution context is set to SqlUser1.  
EXECUTE AS CALLER;  
SELECT user_name(); -- Shows execution context is set to SqlUser2, the caller of the module.  
REVERT;  
SELECT user_name(); -- Shows execution context is set to SqlUser1.  
GO  
```  
  
## <a name="using-execute-as-to-define-custom-permission-sets"></a>EXECUTE AS を使用したカスタム権限セットの定義  
 モジュールの実行コンテキストを指定すると、カスタム権限セットを定義する場合に非常に便利です。 たとえば、TRUNCATE TABLE などの操作には、許可できる権限がありません。 モジュール内に TRUNCATE TABLE ステートメントを組み込み、テーブルの変更権限を持つユーザーがモジュールを実行するように指定すると、モジュールの EXECUTE 権限を許可するユーザーに、テーブルを切り捨てる権限を拡張して与えることができます。  
  
 表示するには、指定された実行コンテキストを持つモジュールの定義を使用して、 [sys.sql_modules &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)カタログ ビューです。  
  
## <a name="best-practice"></a>推奨事項  
 モジュール内で定義された操作を実行する場合に必要となる最低限の権限を持つログインまたはユーザーを指定します。 たとえば、データベース レベルの権限が必要とされない場合は、データベース所有者アカウントは指定しないでください。  
  
## <a name="permissions"></a>Permissions  
 EXECUTE AS で指定されたモジュールを実行するには、呼び出し元に、そのモジュールに対する EXECUTE 権限が必要です。  
  
 別のデータベースまたはサーバー内のリソースにアクセスする CLR モジュールを、EXECUTE AS で指定して実行する場合、対象のデータベースまたはサーバーは、モジュールが生成されたデータベース (基になるデータベース) の認証情報を信頼する必要があります。  
  
 モジュールを作成または変更するときに EXECUTE AS 句を指定するには、指定されたプリンシパルに対する IMPERSONATE 権限とそのモジュールを作成する権限が必要です。 ユーザー自身の権限は、常に借用できます。 実行コンテキストが指定されていないか、EXECUTE AS CALLER が指定されている、ときに IMPERSONATE 権限は必要ありません。  
  
 指定する、 *login_name*または*user_name*暗黙的にアクセスできる Windows グループのメンバーシップを介してデータベースに、データベースに対する管理アクセス許可が必要です。  
  
## <a name="examples"></a>使用例  
 次の例のストアド プロシージャの作成、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベースにあり、実行コンテキストを割り当てます`OWNER`です。  
  
```  
CREATE PROCEDURE HumanResources.uspEmployeesInDepartment   
@DeptValue int  
WITH EXECUTE AS OWNER  
AS  
    SET NOCOUNT ON;  
    SELECT e.BusinessEntityID, c.LastName, c.FirstName, e.JobTitle  
    FROM Person.Person AS c   
    INNER JOIN HumanResources.Employee AS e  
        ON c.BusinessEntityID = e.BusinessEntityID  
    INNER JOIN HumanResources.EmployeeDepartmentHistory AS edh  
        ON e.BusinessEntityID = edh.BusinessEntityID  
    WHERE edh.DepartmentID = @DeptValue  
    ORDER BY c.LastName, c.FirstName;  
GO  
  
-- Execute the stored procedure by specifying department 5.  
EXECUTE HumanResources.uspEmployeesInDepartment 5;  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [sys.assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.service_queues &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-service-queues-transact-sql.md)   
 [元に戻す (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revert-transact-sql.md)   
 [実行 AS (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/execute-as-transact-sql.md)  
  
  
