---
title: "[アクセス許可の付与]"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.openlocfilehash: d7d685d15eb0e5704698ebd2b79c20589f49ee16
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="grant-permissions"></a>[アクセス許可の付与]

## <a name="grant-permissions-to-submit-database-queries"></a>データベースにクエリを送信するアクセス許可を付与します。
このセクションでは、データベース ロールに権限およびユーザーが SQL Server PDW アプライアンス上のクエリ データに付与する方法について説明します。  
  
クエリのデータへのアクセス許可を付与するためのステートメントは、必要なアクセスのスコープによって異なります。 次の SQL ステートメントが、アプライアンスへのアクセスで KimAbercrombie をという名前のデータベース ユーザーを作成できる KimAbercrombie をという名前のログインを作成、 **AdventureWorksPDW2012**データベース、PDWQueryData をという名前のデータベース ロールの作成、追加使用する KimAbercrombie PDWQueryData ロールと、クエリのアクセス許可の表示 オプションには、オブジェクト、またはデータベース レベルでアクセス権を付与するかどうかに基づいています。  
  
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
  
## <a name="grant-permissions-to-use-the-admin-console"></a>管理コンソールを使用するアクセス許可を付与します。
このセクションでは、管理者コンソールを使用してログインへのアクセス許可を付与する方法について説明します。  
  
**管理コンソールを使用します。**  
  
管理者コンソールを使用して、サーバー レベル ログインする必要があります。 **VIEW SERVER STATE**権限です。 次の SQL ステートメントを許可、 **VIEW SERVER STATE**権限をログイン`KimAbercrombie`kim さんは、SQL Server PDW アプライアンスを監視する管理コンソールを使用できるようにします。  
  
```sql  
USE master;  
GO  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
GO  
```  
  
**セッションを強制終了します。**  
  
ログイン セッションを強制終了するアクセス許可を与える、付与、 **ALTER ANY CONNECTION**次のようにアクセス許可。  
  
```sql  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
## <a name="grant-permissions-to-load-data"></a>データの読み込みをするアクセス許可の付与
このセクションでは、SQL Server PDWappliance にデータを読み込むデータベース ロールとデータベース ユーザーへのアクセス許可を付与する方法について説明します。  
  
次のスクリプトは、各読み込みオプションに必要なアクセス許可を示しています。 特定のニーズに合うように変更できます。  
  
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
  
## <a name="grant-permissions-to-copy-data-off-the-appliance"></a>アプライアンス オフ データをコピーするアクセス許可を付与します。
このセクションでは、SQL Server PDW アプライアンス オフ データをコピーするユーザーまたはデータベース ロールに権限を付与する方法について説明します。  
  
データを別の場所に移動する必要があります。**選択**を移動するデータを含むテーブルに対する権限。  
  
データの送信先が別の SQL Server PDW の場合は、ユーザーがいる必要があります**CREATE TABLE**転送先にアクセス許可と**ALTER SCHEMA**テーブルを含むスキーマに対する権限。  
  
## <a name="grant-permissions-to-manage-databases"></a>データベースの管理アクセス許可の付与
このセクションでは、SQL Server PDW アプライアンス上のデータベースを管理するデータベース ユーザーに権限を付与する方法について説明します。  
  
一部の状況では、会社は、データベース マネージャーを割り当てます。 管理者は、他のログインのデータベースだけでなく、データと、データベース内のオブジェクトにアクセスを制御します。 すべてを管理するオブジェクト、ロール、およびデータベースのユーザーがユーザーに付与、**コントロール**データベースに対する権限。 次のステートメントを許可、**コントロール**に対する権限、 **AdventureWorksPDW2012**をユーザーにデータベース`KimAbercrombie`です。  
  
```sql
USE AdventureWorksPDW2012;  
GO  
GRANT CONTROL ON DATABASE:: AdventureWorksPDW2012 TO KimAbercrombie;  
```  
  
アプライアンス上のすべてのデータベースを制御するアクセス許可をユーザーに付与、付与、 **ALTER ANY DATABASE** master データベースにアクセス許可。  
  
## <a name="grant-permissions-to-manage-logins-users-and-database-roles"></a>ログイン、ユーザーを管理して、データベース ロールに権限を付与します。
このセクションでは、ログイン、データベース ユーザー、およびデータベース ロールを管理するアクセス許可を付与する方法について説明します。  
  
### <a name="PermsAdminConsole"></a>ログインを管理するアクセス許可の付与  
**追加またはログインを管理します。**  
  
次の SQL ステートメントを使用して新しいログインを作成できる KimAbercrombie をという名前のログインの作成、 [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md)ステートメントを使用して既存のログインを変更し、 [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md)ステートメントです。  
  
**ALTER ANY LOGIN**権限によって、新しいログインを作成および既存を削除します。 ログインを使用してログインして管理できますログインが存在する場合は、 **ALTER ANY LOGIN**権限、または**ALTER**そのログインに対する権限。 ログインには、独自のログインのパスワードや既定のデータベースを変更できます。  
  
```sql 
CREATE LOGIN KimAbercrombie   
WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
GRANT ALTER ANY LOGIN TO KimAbercrombie;  
```  
  
### <a name="grant-permissions-to-manage-login-sessions"></a>ログイン セッションを管理するアクセス許可を付与します。  
サーバー上のすべてのセッションを表示することが必要です、 **VIEW SERVER STATE**権限です。 他のログインのセッションを終了する必要があります、 **ALTER ANY CONNECTION**権限です。 次の例では、`KimAbercrombie`先ほど作成したログイン。  
  
```sql  
-- Grant permissions to view sessions and queries  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
  
-- Grant permission to end sessions  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
### <a name="grant-permission-to-manage-database-users"></a>データベース ユーザーを管理するアクセス許可を付与します。  
作成して、データベース ユーザーを削除する必要があります、 **ALTER ANY USER**権限です。 既存のユーザーを管理するには、 **ALTER ANY USER**権限、または**ALTER**そのユーザーに対する権限。 次の例では、`KimAbercrombie`先ほど作成したログイン。  
  
```sql  
-- Create a user  
USE AdventureWorksPDW2012;  
GO  
CREATE USER KimAbercrombie;  
  
-- Grant permissions to create and drop users   
GRANT ALTER ANY USER TO KimAbercrombie;  
```  
  
### <a name="grant-permisson-to-manage-database-roles"></a>データベース ロールを管理するには、に対するアクセス許可を付与します。  
作成し、ユーザー定義データベース ロールを削除する必要があります、 **ALTER ANY ROLE**権限です。 次の例では、`KimAbercrombie`ログインし、使用する前に作成します。  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
-- Grant permissions to create and drop roles  
GRANT ALTER ANY ROLE TO KimAbercrombie;  
```  
  
### <a name="login-user-and-role-permission-charts"></a>ログイン、ユーザー、およびロールのアクセス許可のグラフ  
次のグラフ、混乱を招くことはできますが、表示 (コントロール) などの方法より高いレバー アクセス許可とは別に (ALTER) など許可できる権限細かくにはが含まれます。 常に最低限の必要なタスクの実行に他のユーザーのアクセス許可を付与するをお勧めします。 実行するには、最上位レベルのアクセス許可ではなくより詳細な権限を付与します。  
  
**ログインの権限:**  
  
![APS セキュリティのログイン権限](./media/grant-permissions/APS_security_login_perms.png "APS_security_login_perms")  
  
**ユーザーのアクセス許可:**  
  
![APS セキュリティ ユーザー権限](./media/grant-permissions/APS_security_user_perms.png "APS_security_user_perms")  
  
**ロールの権限:**  
  
![APS セキュリティの役割権限](./media/grant-permissions/APS_security_role_perms.png "APS_security_role_perms")  
  
<!-- MISSING LINKS
For a list of all permissions, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  
  
-->

## <a name="grant-permissions-to-monitor-the-appliance"></a>アプライアンスを監視するアクセス許可を付与します。
SQL Server PDW アプライアンスは、管理コンソールまたは SQL Server PDW のいずれかのシステム ビューを使用して監視できます。 ログインには、サーバー レベルが必要な**VIEW SERVER STATE**アプライアンスを監視するアクセス許可。 ログインが必要な**ALTER ANY CONNECTION**管理者コンソールを使用して接続を終了する権限、または**KILL**コマンド。 管理者コンソールを使用して必要なアクセス許可については、次を参照してください[管理コンソール &#40; を使用するアクセス許可の付与。SQL Server PDW &#41;](#grant-permissions-to-use-the-admin-console).  
  
### <a name="PermsAdminConsole"></a>システム ビューを使用してアプライアンスを監視するアクセス許可を付与します。  
次の SQL ステートメントがという名前のログインを作成する`monitor_login`し、付与、 **VIEW SERVER STATE**するアクセス許可、`monitor_login`ログインします。  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_login WITH PASSWORD='Password4321';  
GRANT VIEW SERVER STATE TO monitor_login;  
GO  
```  
  
### <a name="grant-permission-to-monitor-the-appliance-by-using-system-views-and-to-terminate-connections"></a>システム ビューを使用してアプライアンスを監視して、接続を終了するアクセス許可を付与します。  
次の SQL ステートメントがという名前のログインを作成する`monitor_and_terminate_login`し、付与、 **VIEW SERVER STATE**と**ALTER ANY CONNECTION**へのアクセス許可、`monitor_and_terminate_login`ログインします。  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_and_terminate_login WITH PASSWORD='Password1234';   
GRANT VIEW SERVER STATE TO monitor_and_terminate_login;   
GRANT ALTER ANY CONNECTION TO monitor_and_terminate_login;  
GO  
```  
  
管理者ログインを作成するを参照してください。[固定サーバー ロール](pdw-permissions.md#fixed-server-roles)です。  
  
## <a name="see-also"></a>参照
[ログインを作成します。](../t-sql/statements/create-login-transact-sql.md)  
[ユーザーを作成します。](../t-sql/statements/create-user-transact-sql.md)  
[ロールを作成します。](../t-sql/statements/create-role-transact-sql.md)  
[負荷](load-overview.md)  
