---
title: 'レッスン 5:  (省略可能)TDE を使用して、データベースの暗号化 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0850fb7b6be85f8052781ca70f97477d5cb3e403
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743308"
---
# <a name="lesson-5-optional-encrypt-your-database-using-tde"></a>レッスン 5:  (省略可) TDE を使用してデータベースを暗号化する
  省略可能な手順として、新しく作成したデータベースを暗号化できます。 透過的なデータ暗号化 (TDE) では、データとログ ファイルの暗号化と暗号化解除がリアルタイムの I/O で実行されます。 この種の暗号化にはデータベース暗号化キー (DEK) が使用されます。これは、復旧時に使用できるようにデータベース ブート レコードに保存されます。 詳細については、次を参照してください。 [Transparent Data Encryption &#40;TDE&#41; ](security/encryption/transparent-data-encryption.md)と[TDE で保護されたデータベースを別の SQL Server に移動](security/encryption/move-a-tde-protected-database-to-another-sql-server.md)します。  
  
 このレッスンは、次の手順を完了済みであることを前提としています。  
  
-   Windows Azure ストレージ アカウントを入手しました。  
  
-   Windows Azure ストレージ アカウントにコンテナーを作成しました。  
  
-   読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成しました。 SAS キーも生成しました。  
  
-   ソース コンピューターで SQL Server 資格情報を作成しました。  
  
-   レッスン 4 で説明された手順に従って、データベースを作成しました。  
  
 データベースを暗号化する場合は、次の手順を実行します。  
  
1.  ソース コンピューターで、クエリ ウィンドウで次のステートメントを変更して実行します。  
  
    ```  
  
    -- Create a master key and a server certificate   
    USE master   
    GO   
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01';   
    GO   
    CREATE CERTIFICATE MySQLCert WITH SUBJECT = 'SQL - Azure Storage Certification'   
    GO   
    -- Create a backup of the server certificate in the master database.   
    -- Store TDS certificates in the source machine locally.   
    BACKUP CERTIFICATE MySQLCert   
    TO FILE = 'C:\certs\MySQLCert.CER'   
    WITH PRIVATE KEY   
    (   
    FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
    ENCRYPTION BY PASSWORD = 'MySQLKey01'   
    );  
  
    ```  
  
2.  次の手順に従って、ソース コンピューターの新しいデータベースを暗号化します。  
  
    ```  
  
    -- Switch to the new database.   
    -- Create a database encryption key, that is protected by the server certificate in the master database.    
    -- Alter the new database to encrypt the database using TDE.   
    USE TestDB1;   
    GO   
    -- Encrypt your database   
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER CERTIFICATE MySQLCert   
    GO   
  
    ALTER DATABASE TestDB1   
    SET ENCRYPTION ON   
    GO  
  
    ```  
  
 データベースの暗号化の状態と、関連付けられたデータベース暗号化キーを確認するには、次のステートメントを実行します。  
  
```  
  
SELECT * FROM sys.dm_database_encryption_keys;   
GO  
  
```  
  
 このレッスンで使用されている詳細情報: TRANSACT-SQL ステートメントでは、次を参照してください[CREATE DATABASE &#40;SQL Server TRANSACT-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)、 [ALTER DATABASE &#40;TRANSACT-SQL&#41; 。](/sql/t-sql/statements/alter-database-transact-sql)、 [CREATE MASTER KEY &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)、[証明書の作成&#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)、および[sys.dm_database_encryption_keys &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)します。  
  
 **次のレッスン:**  
  
 [レッスン 6:ソースからデータベースの移行のターゲット コンピューターに Windows Azure にオンプレミスのマシン](lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
