---
title: Grant T-SQL でのアクセス許可 - Parallel Data Warehouse |Microsoft Docs
description: Parallel Data Warehouse でのデータベース操作のアクセス許可を付与 T-SQL です。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 15798edc4d6a9b1f00c8dd489dfed76a39e5f340
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960943"
---
# <a name="grant-t-sql-permissions-for-parallel-data-warehouse"></a>Parallel Data Warehouse のアクセス許可を付与 T-SQL
Parallel Data Warehouse でのデータベース操作のアクセス許可を付与 T-SQL です。

## <a name="grant-permissions-to-submit-database-queries"></a>データベース クエリを送信するアクセス許可を付与します。
このセクションでは、データベース ロールへのアクセス許可と、SQL Server PDW アプライアンス上のクエリ データをユーザーに付与する方法について説明します。  
  
クエリのデータへのアクセス許可を付与するために使用するステートメントは、必要なアクセスのスコープによって異なります。 次の SQL ステートメントは、アプライアンスへのアクセスで KimAbercrombie をという名前のデータベース ユーザーを作成できる KimAbercrombie という名前のログインを作成、 **AdventureWorksPDW2012**データベース、PDWQueryData をという名前のデータベース ロールの作成、追加します使用 KimAbercrombie PDWQueryData のロールと、クエリのアクセス許可の表示オプションには、オブジェクト、またはデータベース レベルでアクセス権を付与するかどうかに基づいています。  
  
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
  
## <a name="grant-permissions-to-use-the-admin-console"></a>管理者コンソールを使用してアクセス許可を付与します。
このセクションでは、管理者コンソールを使用してログインへのアクセス許可を付与する方法について説明します。  
  
**管理者コンソールを使用してください。**  
  
管理者コンソールを使用して、サーバー レベル ログインする必要があります。 **VIEW SERVER STATE**権限。 次の SQL ステートメントを許可、 **VIEW SERVER STATE**権限をログイン`KimAbercrombie`Kim は、SQL Server PDW アプライアンスの監視を管理コンソールを使用できるようにします。  
  
```sql  
USE master;  
GO  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
GO  
```  
  
**セッションを強制終了します。**  
  
ログイン セッションを強制終了するアクセス許可を付与するには、付与、 **ALTER ANY CONNECTION**次のようにアクセス許可。  
  
```sql  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
## <a name="grant-permissions-to-load-data"></a>データを読み込むためのアクセス許可の付与
このセクションでは、SQL Server の PDWappliance にデータを読み込むデータベース ロールとデータベース ユーザーへのアクセス許可を付与する方法について説明します。  
  
次のスクリプトは、各読み込みのオプションに必要なアクセス許可を示しています。 特定のニーズに合うように変更できます。  
  
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
このセクションでは、SQL Server PDW アプライアンスからデータをコピーするユーザーまたはデータベース ロールにアクセス許可を付与する方法について説明します。  
  
別の場所にデータを移動する必要があります。**選択**移動するデータを含むテーブルに対する権限。  
  
データの送信先が別の SQL Server PDW の場合は、ユーザーがいる必要があります**CREATE TABLE** 、転送先にアクセス許可と**ALTER SCHEMA**テーブルを含むスキーマに対する権限。  
  
## <a name="grant-permissions-to-manage-databases"></a>データベースを管理するアクセス許可の付与
このセクションでは、SQL Server PDW アプライアンス上のデータベースを管理するデータベース ユーザーにアクセス許可を付与する方法について説明します。  
  
状況によってでは、企業は、データベースの管理者を割り当てます。 管理者は、他のログイン、データベースだけでなく、データと、データベース内のオブジェクトへのアクセスを制御します。 すべてを管理するオブジェクト、ロール、およびデータベースのユーザーをユーザーに付与、**コントロール**データベースに対する権限。 次のステートメントを許可、**コントロール**に対する権限、 **AdventureWorksPDW2012**をユーザーにデータベース`KimAbercrombie`します。  
  
```sql
USE AdventureWorksPDW2012;  
GO  
GRANT CONTROL ON DATABASE:: AdventureWorksPDW2012 TO KimAbercrombie;  
```  
  
だれかに、アプライアンス上のすべてのデータベースを制御するアクセス許可を与えるには、付与、 **ALTER ANY DATABASE** master データベースにアクセスを許可します。  
  
## <a name="grant-permissions-to-manage-logins-users-and-database-roles"></a>ログイン、ユーザーの管理およびデータベース ロールへのアクセス許可を付与します。
このセクションでは、ログイン、データベース ユーザー、およびデータベース ロールを管理するアクセス許可を付与する方法について説明します。  
  
### <a name="PermsAdminConsole"></a>ログインを管理するアクセス許可の付与  
**追加またはログインの管理**  
  
次の SQL ステートメントを使用して、新しいログインを作成できる KimAbercrombie という名前のログインの作成、 [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md)ステートメントを使用して既存のログインを変更して、 [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md)ステートメント。  
  
**ALTER ANY LOGIN**アクセス許可には、新しいログインを作成および既存を削除する権限が付与されます。 持つログインでログインを管理できるログインが存在すると、 **ALTER ANY LOGIN**権限、または**ALTER**そのログインに権限。 ログインには、独自のログインのパスワードや既定のデータベースを変更できます。  
  
```sql 
CREATE LOGIN KimAbercrombie   
WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
GRANT ALTER ANY LOGIN TO KimAbercrombie;  
```  
  
### <a name="grant-permissions-to-manage-login-sessions"></a>ログイン セッションを管理するアクセス許可を付与します。  
サーバー上のすべてのセッションを表示することが必要です、 **VIEW SERVER STATE**権限。 他のログインのセッションを終了する機能が必要です、 **ALTER ANY CONNECTION**権限。 次の例では、`KimAbercrombie`ログイン前に作成します。  
  
```sql  
-- Grant permissions to view sessions and queries  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
  
-- Grant permission to end sessions  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
### <a name="grant-permission-to-manage-database-users"></a>データベース ユーザーを管理するアクセス許可を付与します。  
作成して、データベース ユーザーを削除する必要があります、 **ALTER ANY USER**権限。 既存のユーザーを管理するには、 **ALTER ANY USER**権限、または**ALTER**そのユーザーに対する権限。 次の例では、`KimAbercrombie`ログイン前に作成します。  
  
```sql  
-- Create a user  
USE AdventureWorksPDW2012;  
GO  
CREATE USER KimAbercrombie;  
  
-- Grant permissions to create and drop users   
GRANT ALTER ANY USER TO KimAbercrombie;  
```  
  
### <a name="grant-permisson-to-manage-database-roles"></a>データベース ロールを管理するアクセスを許可します。  
作成し、ユーザー定義データベース ロールを削除する必要があります、 **ALTER ANY ROLE**権限。 次の例では、`KimAbercrombie`ログインし、使用前に作成します。  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
-- Grant permissions to create and drop roles  
GRANT ALTER ANY ROLE TO KimAbercrombie;  
```  
  
### <a name="login-user-and-role-permission-charts"></a>ログイン、ユーザー、およびロールのアクセス許可のグラフ  
次のグラフを混乱させることができますが、表示 (コントロールなど) の方法より高いレバー アクセス許可とは別に (ALTER) などで許可できるきめ細かなアクセス許可が含まれます。 常に最低限の必要なタスクの実行に他のユーザーのアクセス許可を付与することをお勧めします。 そのためには、最上位レベルのアクセス許可ではなく、特定の権限を付与します。  
  
**ログインのアクセス許可:**  
  
![APS セキュリティのログイン権限](./media/grant-permissions/APS_security_login_perms.png "APS_security_login_perms")  
  
**ユーザーのアクセス許可:**  
  
![APS セキュリティ ユーザー権限](./media/grant-permissions/APS_security_user_perms.png "APS_security_user_perms")  
  
**ロールのアクセス許可:**  
  
![APS セキュリティの役割権限](./media/grant-permissions/APS_security_role_perms.png "APS_security_role_perms")  
  
<!-- MISSING LINKS
For a list of all permissions, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  
  
-->

## <a name="grant-permissions-to-monitor-the-appliance"></a>アプライアンスの監視へのアクセス許可を付与します。
SQL Server PDW アプライアンスは、管理コンソールまたは SQL Server PDW のいずれかのシステム ビューを使用して監視できます。 必要なサーバー レベルのログイン**VIEW SERVER STATE**アプライアンスの監視を許可します。 ログインが必要な**ALTER ANY CONNECTION**管理者コンソールを使用して接続を終了するためのアクセス許可、または**KILL**コマンド。 管理者コンソールを使用して必要なアクセス許可については、次を参照してください。[管理者コンソールを使用してアクセス許可の付与&#40;SQL Server PDW&#41;](#grant-permissions-to-use-the-admin-console)します。  
  
### <a name="PermsAdminConsole"></a>システム ビューを使用してアプライアンスの監視を許可します。  
次の SQL ステートメントがという名前のログインを作成`monitor_login`付与、 **VIEW SERVER STATE**へのアクセス許可、`monitor_login`ログインします。  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_login WITH PASSWORD='Password4321';  
GRANT VIEW SERVER STATE TO monitor_login;  
GO  
```  
  
### <a name="grant-permission-to-monitor-the-appliance-by-using-system-views-and-to-terminate-connections"></a>システム ビューを使用してアプライアンスの監視と、接続を終了するためのアクセス許可を付与します。  
次の SQL ステートメントがという名前のログインを作成`monitor_and_terminate_login`付与、 **VIEW SERVER STATE**と**ALTER ANY CONNECTION**へのアクセス許可、`monitor_and_terminate_login`ログインします。  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_and_terminate_login WITH PASSWORD='Password1234';   
GRANT VIEW SERVER STATE TO monitor_and_terminate_login;   
GRANT ALTER ANY CONNECTION TO monitor_and_terminate_login;  
GO  
```  
  
管理者のログインを作成するを参照してください。[固定サーバー ロール](pdw-permissions.md#fixed-server-roles)します。  
  
## <a name="see-also"></a>関連項目
[CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md)  
[ユーザーを作成します。](../t-sql/statements/create-user-transact-sql.md)  
[ロールを作成します。](../t-sql/statements/create-role-transact-sql.md)  
[[読み込み]](load-overview.md)  
