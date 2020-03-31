---
title: T-SQL 権限の付与
description: 並列データ ウェアハウスでのデータベース操作に対する T-SQL アクセス許可を付与します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6bbe78979c393490a52e1051fe158ae138f93dcc
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "79289700"
---
# <a name="grant-t-sql-permissions-for-parallel-data-warehouse"></a>並列データ ウェアハウスに対する T-SQL アクセス許可の付与
並列データ ウェアハウスでのデータベース操作に対する T-SQL アクセス許可を付与します。

## <a name="grant-permissions-to-submit-database-queries"></a>データベース クエリを送信する権限を付与する
このセクションでは、SQL Server PDW アプライアンス上のデータを照会するデータベース ロールとユーザーにアクセス許可を付与する方法について説明します。  
  
データを照会するアクセス許可を付与するために使用されるステートメントは、必要なアクセスの範囲によって異なります。 次の SQL ステートメントは、アプライアンスにアクセスできる KimAbercrombie という名前のログインを作成し **、AdventureWorksPDW2012**データベースに KimAbercrombie という名前のデータベース ユーザーを作成し、PDWQueryData という名前のデータベース ロールを作成し、その後、オブジェクト、データベース レベル、またはデータベース レベルでアクセスが許可されるかどうかに基づいて、そのユーザーに対してクエリ アクセスを許可するためのオプションを表示します。  
  
```sql  
USE master;  
GO  
  
CREATE LOGIN KimAbercrombie WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
USE AdventureWorksPDW2012;  
GO  
  
CREATE USER KimAbercrombie;  
GO  
  
CREATE ROLE PDWQueryData;  
GO  
  
EXEC sp_addrolemember 'PDWQueryData', 'KimAbercrombie'  
GO  
  
-- If the permission is granted against a table or view only, use this syntax:  
GRANT SELECT ON OBJECT::AdventureWorksPDW2012..DimEmployee TO PDWQueryData;  
GO  
  
-- If the permission is granted for the database, use this syntax:  
GRANT SELECT ON DATABASE::AdventureWorksPDW2012 TO PDWQueryData;  
GO  
  
-- If KimAbercrombie is the only user that needs to access a table, use this syntax:  
GRANT SELECT ON OBJECT::AdventureWorksPDW2012..DimEmployee TO KimAbercrombie;  
GO  
```  
  
## <a name="grant-permissions-to-use-the-admin-console"></a>管理コンソールを使用するためのアクセス許可を付与する
このセクションでは、管理コンソールを使用するためのログインにアクセス権を付与する方法について説明します。  
  
**管理コンソールを使用する**  
  
管理コンソールを使用するには、ログインにサーバーレベルの**VIEW SERVER STATE**権限が必要です。 次の SQL ステートメント**VIEW SERVER STATE**は、管理者コンソールを使用して`KimAbercrombie`SQL Server PDW アプライアンスを監視できるように、ログインに VIEW SERVER STATE 権限を付与します。  
  
```sql  
USE master;  
GO  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
GO  
```  
  
**キルセッション**  
  
セッションを強制終了する権限をログインに付与するには、次のように**ALTER ANY CONNECTION**権限を付与します。  
  
```sql  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
## <a name="grant-permissions-to-load-data"></a>データを読み込むためのアクセス許可を付与する
ここでは、SQL Server PDW アプライアンスにデータを読み込むためのデータベース ロールとデータベース ユーザーに権限を付与する方法について説明します。  
  
次のスクリプトは、各読み込みオプションに必要なアクセス許可を示しています。 特定のニーズに合わせて変更できます。  
  
```sql  
-- Create server login for the examples that follow.  
USE master;  
CREATE LOGIN BI_ETLUser WITH PASSWORD = '******';  
  
--Grant BULK Load permissions   
GRANT ADMINISTER BULK OPERATIONS TO BI_ETLUser;  
  
--Grant Staging database permissions  
USE stagedb;  
CREATE USER BI_ETLUser for login BI_ETLUser;  
EXEC sp_addrolemember 'db_datareader','BI_ETLUser';  
EXEC sp_addrolemember 'db_datawriter','BI_ETLUser';  
EXEC sp_addrolemember 'db_ddladmin','BI_ETLUser';  
  
-- The CREATE TABLE permission is required for the database hosting the temporary table.  
-- This may be the staging database (if specified) or destination database.   
-- The CREATE permission is not required if loading in fastappend mode.  
GRANT CREATE TABLE ON database::stagedb TO BI_ETLUser;  
  
-- If loading in append or fastappend mode, the INSERT permission is required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
  
-- If loading in reload mode, the INSERT and DELETE permissions are required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
GRANT DELETE ON database::stagedb TO BI_ETLUser;  
  
-- If loading in upsert mode, the INSERT and UPDATE permissions are required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
GRANT UPDATE ON database::stagedb TO BI_ETLUser;  
  
-- Destination DB  
USE tpch_1gb;  
CREATE USER BI_ETLUser FOR LOGIN BI_ETLUser;  
EXEC sp_addrolemember 'db_datareader','BI_ETLUser';  
EXEC sp_addrolemember 'db_datawriter','BI_ETLUser';  
```  
  
## <a name="grant-permissions-to-copy-data-off-the-appliance"></a>アプライアンスからデータをコピーするアクセス許可を付与する
このセクションでは、SQL Server PDW アプライアンスからデータをコピーする権限をユーザーロールまたはデータベース ロールに付与する方法について説明します。  
  
データを別の場所に移動するには、移動するデータを含むテーブルに対する**SELECT**権限が必要です。  
  
データの変換先が別の SQL Server PDW の場合、ユーザーは、変換先で**の CREATE TABLE**権限と、テーブルを含むスキーマに対する ALTER **SCHEMA**権限を持っている必要があります。  
  
## <a name="grant-permissions-to-manage-databases"></a>データベースを管理するためのアクセス許可を付与する
このセクションでは、SQL Server PDW アプライアンス上のデータベースを管理するためのデータベース ユーザーにアクセス許可を付与する方法について説明します。  
  
状況によっては、会社がデータベースの管理者を割り当てる場合があります。 マネージャは、データベースに対する他のログインのアクセス権、およびデータベース内のデータとオブジェクトのアクセスを制御します。 データベース内のすべてのオブジェクト、ロール、およびユーザーを管理するには、データベースに対する**CONTROL**権限をユーザーに与えます。 次のステートメントは **、AdventureWorksPDW2012**データベースに対する**CONTROL** `KimAbercrombie`権限をユーザーに付与します。  
  
```sql
USE AdventureWorksPDW2012;  
GO  
GRANT CONTROL ON DATABASE:: AdventureWorksPDW2012 TO KimAbercrombie;  
```  
  
アプライアンス上のすべてのデータベースを制御する権限を誰かに付与するには、master データベースで**ALTER ANY DATABASE**権限を付与します。  
  
## <a name="grant-permissions-to-manage-logins-users-and-database-roles"></a>ログイン、ユーザー、およびデータベース ロールを管理する権限を付与する
このセクションでは、ログイン、データベース ユーザー、およびデータベース ロールを管理する権限を付与する方法について説明します。  
  
### <a name="grant-permissions-to-manage-logins"></a><a name="PermsAdminConsole"></a>ログインを管理するアクセス許可を付与する  
**ログインの追加または管理**  
  
次の SQL ステートメントは[、CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md)ステートメントを使用して新しいログインを作成し[、ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md)ステートメントを使用して既存のログインを変更できる、KimAbercrombie という名前のログインを作成します。  
  
**ALTER ANY LOGIN**権限は、新しいログインを作成し、エキサシティングを削除する権限を付与します。 ログインが存在すると、ALTER **ANY ログイン**権限またはそのログインに対する**ALTER**権限を持つログインによって、ログインを管理できます。 ログインは、パスワードとデフォルトデータベースを変更して、そのログインを行うことができます。  
  
```sql 
CREATE LOGIN KimAbercrombie   
WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
GRANT ALTER ANY LOGIN TO KimAbercrombie;  
```  
  
### <a name="grant-permissions-to-manage-login-sessions"></a>ログイン セッションを管理するアクセス許可を付与する  
サーバー上のすべてのセッションを表示するには **、VIEW サーバー状態**権限が必要です。 他のログインのセッションを終了する機能には **、ALTER ANY CONNECTION**権限が必要です。 次の例では、`KimAbercrombie`前に作成したログインを使用します。  
  
```sql  
-- Grant permissions to view sessions and queries  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
  
-- Grant permission to end sessions  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
### <a name="grant-permission-to-manage-database-users"></a>データベース ユーザーを管理する権限を付与する  
データベース・ユーザーの作成と削除には **、ALTER ANY ユーザー**権限が必要です。 既存のユーザーを管理するには、**そのユーザー**に対する ALTER ANY ユーザー権限または**ALTER**権限が必要です。 次の例では、`KimAbercrombie`前に作成したログインを使用します。  
  
```sql  
-- Create a user  
USE AdventureWorksPDW2012;  
GO  
CREATE USER KimAbercrombie;  
  
-- Grant permissions to create and drop users   
GRANT ALTER ANY USER TO KimAbercrombie;  
```  
  
### <a name="grant-permisson-to-manage-database-roles"></a>データベース ロールを管理するアクセス許可を付与する  
ユーザー定義のデータベース ロールを作成および削除するには **、ALTER ANY ROLE**権限が必要です。 次の例では、`KimAbercrombie`以前に作成したログインと使用を使用します。  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
-- Grant permissions to create and drop roles  
GRANT ALTER ANY ROLE TO KimAbercrombie;  
```  
  
### <a name="login-user-and-role-permission-charts"></a>ログイン、ユーザー、およびロール権限のグラフ  
次のグラフは混乱を招く可能性がありますが、より高いレベルのレバーのアクセス許可 (CONTROL など) に、個別に付与できるより細かいアクセス許可 (ALTER など) が含まれていることがわかります。 必要なタスクを完了するために、常に最小限のアクセス許可を付与することをお勧めします。 そのためには、最上位レベルのアクセス許可ではなく、より具体的なアクセス許可を付与します。  
  
**ログイン権限:**  
  
![APS セキュリティのログイン権限](./media/grant-permissions/APS_security_login_perms.png "APS_security_login_perms")  
  
**ユーザーのアクセス許可:**  
  
![APS セキュリティのユーザー権限](./media/grant-permissions/APS_security_user_perms.png "APS_security_user_perms")  
  
**ロールのアクセス許可:**  
  
![APS セキュリティのロール権限](./media/grant-permissions/APS_security_role_perms.png "APS_security_role_perms")  
  
<!-- MISSING LINKS
For a list of all permissions, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  
  
-->

## <a name="grant-permissions-to-monitor-the-appliance"></a>アプライアンスを監視するためのアクセス許可を付与する
SQL Server PDW アプライアンスは、管理コンソールまたは SQL Server PDW システム ビューを使用して監視できます。 ログインには、アプライアンスを監視するためのサーバー・レベル**の VIEW SERVER STATE**権限が必要です。 ログインには、管理コンソールまたは**KILL**コマンドを使用して接続を終了するために **、ALTER ANY CONNECTION**権限が必要です。 管理コンソールを使用するために必要なアクセス許可については、「 [SQL Server PDW&#41;&#40;管理コンソールを使用するためのアクセス許可の付与](#grant-permissions-to-use-the-admin-console)」を参照してください。  
  
### <a name="grant-permission-to-monitor-the-appliance-by-using-system-views"></a><a name="PermsAdminConsole"></a>システム ビューを使用してアプライアンスを監視するアクセス許可を付与する  
次の SQL ステートメントは、`monitor_login`名前の付いたログインを作成し、`monitor_login`そのログインに VIEW SERVER **STATE**権限を付与します。  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_login WITH PASSWORD='Password4321';  
GRANT VIEW SERVER STATE TO monitor_login;  
GO  
```  
  
### <a name="grant-permission-to-monitor-the-appliance-by-using-system-views-and-to-terminate-connections"></a>システム ビューを使用してアプライアンスを監視し、接続を終了するアクセス許可を付与する  
次の SQL ステートメントは、`monitor_and_terminate_login`名前の付いたログインを作成し **、VIEW SERVER** `monitor_and_terminate_login` STATE と**任意の接続の変更**権限をログインに付与します。  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_and_terminate_login WITH PASSWORD='Password1234';   
GRANT VIEW SERVER STATE TO monitor_and_terminate_login;   
GRANT ALTER ANY CONNECTION TO monitor_and_terminate_login;  
GO  
```  
  
管理者ログインを作成するには、「[固定サーバー ロール](pdw-permissions.md#fixed-server-roles)」を参照してください。  
  
## <a name="see-also"></a>関連項目
[ログインの作成](../t-sql/statements/create-login-transact-sql.md)  
[CREATE USER](../t-sql/statements/create-user-transact-sql.md)  
[CREATE ROLE](../t-sql/statements/create-role-transact-sql.md)  
[読み込み](load-overview.md)  
