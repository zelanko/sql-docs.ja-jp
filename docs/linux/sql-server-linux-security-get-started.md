---
title: Linux 上の SQL Server のセキュリティの概要 |Microsoft Docs
description: この記事では、一般的なセキュリティ アクションを説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ecc72850-8b01-492e-9a27-ec817648f0e0
ms.openlocfilehash: 655aebb0c07c812a7aa6c81e7c7033d85e8b7ce2
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66705206"
---
# <a name="walkthrough-for-the-security-features-of-sql-server-on-linux"></a>Linux 上の SQL Server のセキュリティ機能のチュートリアル

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

新しい SQL Server にある Linux ユーザーの場合は、次のタスクはセキュリティ タスクの一部を説明します。 これらは Linux に固有のものではありませんが、より詳しく調べたい領域を知るのに役立ちます。 それぞれの例では、リンクがその領域の詳細なドキュメントに提供されます。

> [!NOTE]
>  次の例を使用して、 **AdventureWorks2014**サンプル データベース。 このサンプル データベースを入手し、インストールする方法については、次を参照してください。 [Windows から Linux に SQL Server のデータベースを復元](sql-server-linux-migrate-restore-database.md)。


## <a name="create-a-login-and-a-database-user"></a>ログインとデータベース ユーザーを作成します。 

使用して、master データベースでログインを作成して、SQL Server へのアクセスを与える他のユーザー、 [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md)ステートメント。 以下に例を示します。

```
CREATE LOGIN Larry WITH PASSWORD = '************';  
```

> [!NOTE]
>  上記のコマンドで、アスタリスクの代わりに、強力なパスワードを常に使用します。

ログインでは、SQL Server に接続でき、master データベースに (制限された権限) にアクセスすることができます。 ユーザー データベースに接続するには、ログインには、データベース ユーザーと呼ばれる、データベース レベルで対応する id が必要があります。 ユーザーは、各データベースに固有し、アクセスを許可するには、各データベースで個別に作成する必要があります。 次の例は、AdventureWorks2014 データベースに移動しを使用して、 [CREATE USER](../t-sql/statements/create-user-transact-sql.md) Larry をという名前のログインに関連付けられている Larry という名前のユーザーを作成するステートメント。 ただし、ログインとユーザーは、(相互にマップされる) に関連する、さまざまなオブジェクトであります。 ログインはサーバー レベルのプリンシプルいます。 ユーザーは、データベース レベルのプリンシパルです。

```
USE AdventureWorks2014;
GO
CREATE USER Larry;
GO
```

- SQL Server の管理者アカウントは、任意のデータベースに接続できるし、任意のデータベースで複数のログインとユーザーを作成できます。  
- データベースを作成するとき、そのデータベースに接続できるデータベースの所有者になります。 データベース所有者より多くのユーザーを作成できます。

後で許可することによって複数のログインを作成するには、その他のログインを承認できる、`ALTER ANY LOGIN`権限。 データベース内に付与することでより多くのユーザーを作成するには、他のユーザーを承認することができます、`ALTER ANY USER`権限。 以下に例を示します。   

```
GRANT ALTER ANY LOGIN TO Larry;   
GO   
   
USE AdventureWorks2014;   
GO   
GRANT ALTER ANY USER TO Jerry;    
GO   
```

Larry ログインが複数のログインを作成するようになりましたし、Jerry はユーザーがより多くのユーザーを作成します。


## <a name="granting-access-with-least-privileges"></a>最小限の特権を持つアクセス権の付与

ユーザー データベースに接続する最初のユーザーは、管理者およびデータベース所有者アカウントになります。 ただしこれらのユーザーでは、データベースに使用可能なすべての権限があります。 これは、多くのアクセス許可よりも、ほとんどのユーザーである必要があります。 

組み込みを使用してアクセス許可のいくつかの一般的なカテゴリを割り当てることができますを始めたばかり、ときに*固定データベース ロール*します。 たとえば、`db_datareader`固定データベース ロールが、データベース内のすべてのテーブルが変更しない場合します。 使用しての固定データベース ロールのメンバーシップの付与、 [ALTER ROLE](../t-sql/statements/alter-role-transact-sql.md)ステートメント。 次の例では、ユーザーを追加する`Jerry`を`db_datareader`固定データベース ロール。   
   
```   
USE AdventureWorks2014;   
GO   
   
ALTER ROLE db_datareader ADD MEMBER Jerry;   
```   

固定データベース ロールの一覧では、次を参照してください。[データベース レベル ロール](../relational-databases/security/authentication-access/database-level-roles.md)します。

後で、(強く推奨) データをより正確なアクセスを構成する準備ができたら、作成を使用して、独自のユーザー定義データベース ロール[CREATE ROLE](../t-sql/statements/create-role-transact-sql.md)ステートメント。 カスタム ロールに特定の詳細なアクセス許可を割り当てます。

たとえば、次のステートメントがという名前のデータベース ロールを作成`Sales`、付与、`Sales`を参照してください、更新、および行を削除する機能をグループ化、`Orders`テーブル、およびユーザーを追加`Jerry`を`Sales`ロール。   
   
```   
CREATE ROLE Sales;   
GRANT SELECT ON Object::Sales TO Orders;   
GRANT UPDATE ON Object::Sales TO Orders;   
GRANT DELETE ON Object::Sales TO Orders;   
ALTER ROLE Sales ADD MEMBER Jerry;   
```   

For more information about the permission system, see [Getting Started with Database Engine Permissions](../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).


## Configure row-level security  

[Row-Level Security](../relational-databases/security/row-level-security.md) enables you to restrict access to rows in a database based on the user executing a query. This feature is useful for scenarios like ensuring that customers can only access their own data or that workers can only access data that is pertinent to their department.   

The following steps walk through setting up two Users with different row-level access to the `Sales.SalesOrderHeader` table. 

Create two user accounts to test the row level security:    
   
```   
USE AdventureWorks2014;   
GO   
   
CREATE USER Manager WITHOUT LOGIN;     
   
CREATE USER SalesPerson280 WITHOUT LOGIN;    
```   

Grant read access on the `Sales.SalesOrderHeader` table to both users:    
   
```   
GRANT SELECT ON Sales.SalesOrderHeader TO Manager;      
GRANT SELECT ON Sales.SalesOrderHeader TO SalesPerson280;    
```   
   
Create a new schema and inline table-valued function. The function returns 1 when a row in the `SalesPersonID` column matches the ID of a `SalesPerson` login or if the user executing the query is the Manager user.   
   
```     
CREATE SCHEMA Security;   
GO   
   
CREATE FUNCTION Security.fn_securitypredicate(@SalesPersonID AS int)     
    RETURNS TABLE   
WITH SCHEMABINDING   
AS     
   RETURN SELECT 1 AS fn_securitypredicate_result    
WHERE ('SalesPerson' + CAST(@SalesPersonId as VARCHAR(16)) = USER_NAME())     
    OR (USER_NAME() = 'Manager');    
```   

Create a security policy adding the function as both a filter and a block predicate on the table:  

```
セキュリティ ポリシー SalesFilter を作成します。   
ADD FILTER PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  Sales.SalesOrderHeader、   
ADD BLOCK PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  Sales.SalesOrderHeader で   
WITH (STATE = ON);   
```

Execute the following to query the `SalesOrderHeader` table as each user. Verify that `SalesPerson280` only sees the 95 rows from their own sales and that the `Manager` can see all the rows in the table.  

```    
EXECUTE AS USER = 'SalesPerson280';   
SELECT * FROM Sales.SalesOrderHeader;    
元に戻します。 
 
EXECUTE AS USER = 'Manager';   
SELECT * FROM Sales.SalesOrderHeader;   
元に戻します。   
```
 
Alter the security policy to disable the policy.  Now both users can access all rows. 

```
セキュリティ ポリシー SalesFilter を変更します。   
使用 (状態 = オフ)。    
``` 


## Enable dynamic data masking

[Dynamic Data Masking](../relational-databases/security/dynamic-data-masking.md) enables you to limit the exposure of sensitive data to users of an application by fully or partially masking certain columns. 

Use an `ALTER TABLE` statement to add a masking function to the `EmailAddress` column in the `Person.EmailAddress` table: 
 
```
AdventureWorks2014; の使用します。移動の ALTER TABLE Person.EmailAddress     ALTER 列 EmailAddress    
ADD MASKED WITH (FUNCTION = 'email()');
``` 
 
Create a new user `TestUser` with `SELECT` permission on the table, then execute a query as `TestUser` to view the masked data:   

```  
CREATE USER TestUser WITHOUT LOGIN;   
GRANT SELECT ON Person.EmailAddress TO TestUser;    
 
EXECUTE AS USER = 'TestUser';   
SELECT EmailAddressID, EmailAddress FROM Person.EmailAddress;       
元に戻します。    
```
 
Verify that the masking function changes the email address in the first record from:
  
|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |ken0@adventure-works.com |    
 
into 

|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |kXXX@XXXX.com |   


## Enable Transparent Data Encryption

One threat to your database is the risk that someone will steal the database files off of your hard-drive. This could happen with an intrusion that gets elevated access to your system, through the actions of a problem employee, or by theft of the computer containing the files (such as a laptop).

Transparent Data Encryption (TDE) encrypts the data files as they are stored on the hard drive. The master database of the SQL Server database engine has the encryption key, so that the database engine can manipulate the data. The database files cannot be read without access to the key. High-level administrators can manage, backup, and recreate the key, so the database can be moved, but only by selected people. When TDE is configured, the `tempdb` database is also automatically encrypted. 

Since the Database Engine can read the data, Transparent Data Encryption does not protect against unauthorized access by administrators of the computer who can directly read memory, or access SQL Server through an administrator account.

### Configure TDE

- Create a master key
- Create or obtain a certificate protected by the master key
- Create a database encryption key and protect it by the certificate
- Set the database to use encryption

Configuring TDE requires `CONTROL` permission on the master database and `CONTROL` permission on the user database. Typically an administrator configures TDE. 

The following example illustrates encrypting and decrypting the `AdventureWorks2014` database using a certificate installed on the server named `MyServerCert`.


```
USE master;  
GO  

CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**********';  
GO  

CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My Database Encryption Key Certificate';  
GO  

USE AdventureWorks2014;   GO
  
CREATE DATABASE ENCRYPTION KEY  
アルゴリズムで AES_256 を =  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO
  
ALTER DATABASE AdventureWorks2014  
セットの暗号化。   
```

To remove TDE, execute `ALTER DATABASE AdventureWorks2014 SET ENCRYPTION OFF;`   

The encryption and decryption operations are scheduled on background threads by SQL Server. You can view the status of these operations using the catalog views and dynamic management views in the list that appears later in this topic.   

> [!WARNING]
>  Backup files of databases that have TDE enabled are also encrypted by using the database encryption key. As a result, when you restore these backups, the certificate protecting the database encryption key must be available. This means that in addition to backing up the database, you have to make sure that you maintain backups of the server certificates to prevent data loss. Data loss will result if the certificate is no longer available. For more information, see [SQL Server Certificates and Asymmetric Keys](../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  

For more information about TDE, see [Transparent Data Encryption (TDE)](../relational-databases/security/encryption/transparent-data-encryption-tde.md).   


## Configure backup encryption
SQL Server has the ability to encrypt the data while creating a backup. By specifying the encryption algorithm and the encryptor (a certificate or asymmetric key) when creating a backup, you can create an encrypted backup file.    
  
> [!WARNING]  
>  It is very important to back up the certificate or asymmetric key, and preferably to a different location than the backup file it was used to encrypt. Without the certificate or asymmetric key, you cannot restore the backup, rendering the backup file unusable. 
 
 
The following example creates a certificate, and then creates a backup protected by the certificate.
```
使用して master; 移動 証明書の作成 BackupEncryptCert サブジェクト = 'データベースのバックアップ'; データベースのバックアップ [AdventureWorks2014] に移動して ディスク N'/var/opt/mssql/backups/AdventureWorks2014.bak を ='  
WITH  
  圧縮、  
  ENCRYPTION   
   (  
   アルゴリズム、AES_256 を =  
   SERVER CERTIFICATE = BackupEncryptCert  
   ),  
  STATS = 10  
GO  
```

For more information, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).


## Next steps

For more information about the security features of SQL Server, see [Security Center for SQL Server Database Engine and Azure SQL Database](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).
