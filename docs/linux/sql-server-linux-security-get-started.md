---
title: "Linux 上の SQL Server のセキュリティの概要 |Microsoft ドキュメント"
description: "このトピックでは、セキュリティの一般的なアクションを説明します。"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.technology: database-engine
ms.assetid: ecc72850-8b01-492e-9a27-ec817648f0e0
ms.custom: 
ms.workload: Inactive
ms.openlocfilehash: cb8f44ae871d3e1ec81d576439d81508ac2c96f5
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="walkthrough-for-the-security-features-of-sql-server-on-linux"></a>SQL Server on Linux のセキュリティ機能のチュートリアル

SQL Server に新しい Linux ユーザーの場合は、次のタスクはセキュリティ タスクの一部を説明します。 これらは一意または Linux に固有でないですがさらに詳しく調査するには、領域の概念を付けると便利です。 各例では、リンクは、その領域の詳細なドキュメントに提供されます。

>  [!NOTE]
>  次の例を使用して、 **AdventureWorks2014**サンプル データベース。 手順を取得して、このサンプル データベースをインストールする方法については、次を参照してください。 [Windows から Linux に SQL Server データベースを復元](sql-server-linux-migrate-restore-database.md)です。


## <a name="create-a-login-and-a-database-user"></a>ログインとデータベース ユーザーを作成します。 

使用して、master データベースでログインを作成して SQL Server へのアクセスを与える他のユーザー、 [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md)ステートメントです。 例:

```
CREATE LOGIN Larry WITH PASSWORD = '************';  
```

>  [!NOTE]
>  上記のアスタリスクの代わりに、強力なパスワードを常に使用します。

ログインでは、SQL Server に接続でき、限られたアクセス権を持つ)、master データベースにアクセスすることができます。 ユーザー データベースに接続するには、ログインには、データベース レベル、データベース ユーザーと呼ばれる、対応する id が必要があります。 ユーザーは各データベースに固有でありアクセスを許可するには、各データベースで個別に作成する必要があります。 次の例は、AdventureWorks2014 データベースに移動しを使用して、 [CREATE USER](../t-sql/statements/create-user-transact-sql.md) Larry をという名前のログインに関連付けられている Larry をという名前のユーザーを作成するステートメント。 ログインとユーザーは、(相互にマップされる) に関連する、さまざまなオブジェクトはします。 ログインは、サーバー レベルの原則です。 ユーザーは、データベース レベルのプリンシパルです。

```
USE AdventureWorks2014;
GO
CREATE USER Larry;
GO
```

- SQL Server の管理者アカウントは、任意のデータベースに接続できるし、任意のデータベースで複数のログインとユーザーを作成できます。  
- データベースを作成するとき、データベース所有者は、そのデータベースに接続可能になります。 データベース所有者より多くのユーザーを作成できます。

後でそれらを付与することで複数のログインを作成するには、他のログインを承認できる、`ALTER ANY LOGIN`権限です。 データベース内に付与することでより多くのユーザーを作成するには、他のユーザーを承認することができます、`ALTER ANY USER`権限です。 例:   

```
GRANT ALTER ANY LOGIN TO Larry;   
GO   
   
USE AdventureWorks2014;   
GO   
GRANT ALTER ANY USER TO Jerry;    
GO   
```

ログイン Jerry ことができますが、複数のログインを作成するようになりましたし Jerry は、ユーザーがより多くのユーザーを作成します。


## <a name="granting-access-with-least-privileges"></a>最小限の特権でのアクセス権の付与

ユーザー データベースに接続する最初の人物は、管理者およびデータベース所有者アカウントになります。 ただしこれらのユーザーがあるすべてのデータベースで使用可能なアクセス許可。 これ以上のアクセス許可は、ほとんどのユーザーが持つ必要があります。 

だけを開始する、ときに、組み込みを使用してアクセス許可のいくつかの一般的なカテゴリを割り当てることができます*固定データベース ロール*です。 たとえば、`db_datareader`固定データベース ロールは、データベース内のすべてのテーブルを読み取ることができますが、変更しないようにします。 使用して、固定データベース ロールのメンバーシップを許可、 [ALTER ROLE](../t-sql/statements/alter-role-transact-sql.md)ステートメントです。 次の例は、ユーザーを追加`Jerry`を`db_datareader`固定データベース ロール。   
   
```   
USE AdventureWorks2014;   
GO   
   
ALTER ROLE db_datareader ADD MEMBER Jerry;   
```   

固定データベース ロールの一覧は、次を参照してください。[データベース レベルのロール](../relational-databases/security/authentication-access/database-level-roles.md)です。

後で、(推奨) データをより正確なアクセスを構成する準備ができたらを使用して、独自のユーザー定義データベース ロールを作成[CREATE ROLE](../t-sql/statements/create-role-transact-sql.md)ステートメントです。 カスタム ロールを特定の詳細なアクセス許可を割り当てます。

たとえば、次のステートメントがという名前のデータベース ロールを作成`Sales`、付与、`Sales`を参照してください、更新、および行を削除する権限をグループ化、`Orders`テーブル、およびユーザーを追加`Jerry`を`Sales`ロール。   
   
```   
CREATE ROLE Sales;   
GRANT SELECT ON Object::Sales TO Orders;   
GRANT UPDATE ON Object::Sales TO Orders;   
GRANT DELETE ON Object::Sales TO Orders;   
ALTER ROLE Sales ADD MEMBER Jerry;   
```   

権限システムの詳細については、次を参照してください。[データベース エンジンの権限の概要](../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)です。


## <a name="configure-row-level-security"></a>行レベルのセキュリティを構成します。  

[行レベルのセキュリティ](../relational-databases/security/row-level-security.md)クエリを実行するユーザーに基づくデータベース内の行へのアクセスを制限することができます。 この機能は、顧客が独自のデータにのみアクセスできますか、ワーカーが自分の部署に関連しているデータにアクセスできるのみのようなシナリオに便利です。   

ユーザー設定の 2 つの異なるを通じて、次の手順の行レベルへのアクセス、`Sales.SalesOrderHeader`テーブル。 

行レベルのセキュリティをテストする 2 つのユーザー アカウントを作成します。    
   
```   
USE AdventureWorks2014;   
GO   
   
CREATE USER Manager WITHOUT LOGIN;     
   
CREATE USER SalesPerson280 WITHOUT LOGIN;    
```   

上の読み取りアクセス権の付与、`Sales.SalesOrderHeader`両方のユーザーにテーブル。    
   
```   
GRANT SELECT ON Sales.SalesOrderHeader TO Manager;      
GRANT SELECT ON Sales.SalesOrderHeader TO SalesPerson280;    
```   
   
新しいスキーマとインライン テーブル値関数を作成します。 1 と内の行を返し、`SalesPersonID`の ID と一致する列、`SalesPerson`ログインまたはクエリを実行するユーザーがマネージャー ユーザー。   
   
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

フィルターと、テーブルのブロック述語として関数を追加するセキュリティ ポリシーを作成します。  

```
CREATE SECURITY POLICY SalesFilter   
ADD FILTER PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader,   
ADD BLOCK PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader   
WITH (STATE = ON);   
```

クエリには、次を実行、`SalesOrderHeader`テーブルの各ユーザーとして。 いることを確認`SalesPerson280`だけことと、それぞれの売上から 95 行が表示される、`Manager`テーブル内のすべての行を確認できます。  

```    
EXECUTE AS USER = 'SalesPerson280';   
SELECT * FROM Sales.SalesOrderHeader;    
REVERT; 
 
EXECUTE AS USER = 'Manager';   
SELECT * FROM Sales.SalesOrderHeader;   
REVERT;   
```
 
セキュリティ ポリシーを変更してポリシーを無効にします。  これで両方のユーザーはすべての行にアクセスできます。 

```
ALTER SECURITY POLICY SalesFilter   
WITH (STATE = OFF);    
``` 


## <a name="enable-dynamic-data-masking"></a>動的データ マスクを有効にします。

[動的データ マスク](../relational-databases/security/dynamic-data-masking.md)完全または部分的には、特定の列をマスクして、アプリケーションのユーザーに対してデリケートなデータの露出を制限することができます。 

使用して、`ALTER TABLE`にマスク関数を追加するステートメント、`EmailAddress`内の列、`Person.EmailAddress`テーブル。 
 
```
USE AdventureWorks2014;
GO
ALTER TABLE Person.EmailAddress    
ALTER COLUMN EmailAddress    
ADD MASKED WITH (FUNCTION = 'email()');
``` 
 
新しいユーザーを作成`TestUser`で`SELECT`、テーブルに対する権限としてクエリを実行し、`TestUser`マスクされたデータを表示します。   

```  
CREATE USER TestUser WITHOUT LOGIN;   
GRANT SELECT ON Person.EmailAddress TO TestUser;    
 
EXECUTE AS USER = 'TestUser';   
SELECT EmailAddressID, EmailAddress FROM Person.EmailAddress;       
REVERT;    
```
 
マスキング関数が、最初のレコードからの電子メール アドレスを変更することを確認します。
  
|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |ken0@adventure-works.com |    
 
into 

|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |kXXX@XXXX.com |   


## <a name="enable-transparent-data-encryption"></a>透過的なデータ暗号化の有効化

データベースに 1 つの脅威とは、ハード ドライブからデータベース ファイルを盗もうだれかがリスクです。 これが侵入の発生 (ラップトップ) などのファイルを含むコンピューターの盗難、または、問題の従業員のアクションをシステムに昇格されたアクセス権を取得すると発生する可能性があります。

Transparent Data Encryption (TDE) は、ハード ドライブに格納されているデータ ファイルを暗号化します。 SQL Server データベース エンジンの master データベースは、データベース エンジンがデータを操作できるようにに暗号化キーを持っています。 キーにアクセスすることがなく、データベース ファイルを読み取ることができません。 高レベルの管理者は、管理、バックアップ、および、ため、データベースを移動することができますが、選択したユーザーによってのみ、キーを再作成できます。 TDE を構成すると、`tempdb`データベースが自動的に暗号化します。 

データベース エンジンは、データを読み取ることができます、ので、透過的なデータ暗号化は直接メモリの読み取りまたは管理者アカウントで SQL Server にアクセスできるコンピューターの管理者による不正なアクセスから保護されません。

### <a name="configure-tde"></a>TDE を構成します。

- マスター キーを作成します。
- マスター キーで保護された証明書を作成または取得します。
- データベース暗号化キーを作成し、証明書で保護します。
- 暗号化を使用するようにデータベースを設定します。

TDE を構成する必要があります`CONTROL`master データベースでのアクセス許可と`CONTROL`ユーザー データベースに対する権限。 通常、管理者は、TDE を構成します。 

次の例では、 `AdventureWorks2014` という名前のサーバーにインストールされた証明書を使用して、 `MyServerCert`データベースを暗号化および暗号化解除しています。


```
USE master;  
GO  

CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**********';  
GO  

CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My Database Encryption Key Certificate';  
GO  

USE AdventureWorks2014;  
GO
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO
  
ALTER DATABASE AdventureWorks2014  
SET ENCRYPTION ON;   
```

TDE を削除するには、次のように実行します。`ALTER DATABASE AdventureWorks2014 SET ENCRYPTION OFF;`   

暗号化および暗号化解除の操作は、SQL Server によってバック グラウンド スレッドでスケジュールされます。 これらの操作の状態は、この後の一覧に示すカタログ ビューおよび動的管理ビューを使用して確認できます。   

>  [!WARNING]
>  TDE が有効になっているデータベースのバックアップ ファイルも、データベース暗号化キーを使用して暗号化されます。 このため、このバックアップを復元するときには、データベース暗号化キーを保護している証明書が必要です。 つまり、データの損失を防ぐには、データベースをバックアップするだけでなく、サーバー証明書のバックアップも確実に保守する必要があります。 証明書が使用できなくなると、データの損失が発生します。 詳細については、「 [SQL Server Certificates and Asymmetric Keys](../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)」を参照してください。  

TDE の詳細については、次を参照してください。 [Transparent Data Encryption (TDE)](../relational-databases/security/encryption/transparent-data-encryption-tde.md)です。   


## <a name="configure-backup-encryption"></a>バックアップの暗号化を構成します。
SQL Server では、バックアップの作成中にデータを暗号化する機能があります。 暗号化アルゴリズムおよび暗号化機能 (証明書または非対称キー) を指定してバックアップを作成する場合は、暗号化されたバックアップ ファイルを作成することができます。    
  
> [!WARNING]  
>  証明書または非対称キーをバックアップすることが非常に重要であり、これらを使用して暗号化したバックアップ ファイルとは別の場所に保存することをお勧めします。 証明書または非対称キーがないと、バックアップ ファイルが使用不可能になり、バックアップを復元することができません。 
 
 
次の例では、証明書を作成し、証明書によって保護されているバックアップが作成されます。
```
USE master;  
GO  
CREATE CERTIFICATE BackupEncryptCert   
   WITH SUBJECT = 'Database backups';  
GO 
BACKUP DATABASE [AdventureWorks2014]  
TO DISK = N'/var/opt/mssql/backups/AdventureWorks2014.bak'  
WITH  
  COMPRESSION,  
  ENCRYPTION   
   (  
   ALGORITHM = AES_256,  
   SERVER CERTIFICATE = BackupEncryptCert  
   ),  
  STATS = 10  
GO  
```

詳細については、次を参照してください。[バックアップの暗号化](../relational-databases/backup-restore/backup-encryption.md)です。


## <a name="next-steps"></a>次の手順

SQL Server のセキュリティ機能の詳細については、次を参照してください。 [SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)です。
