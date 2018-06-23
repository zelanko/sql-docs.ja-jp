---
title: レッスン 5 です。 (省略可能)TDE を使用して、データベースの暗号化 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c8ef2e904c197822721a5c48f811a2a895b5ca59
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177750"
---
# <a name="lesson-5-optional-encrypt-your-database-using-tde"></a>レッスン 5 です。 (省略可) TDE を使用してデータベースを暗号化する
  省略可能な手順として、新しく作成したデータベースを暗号化できます。 透過的なデータ暗号化 (TDE) では、データとログ ファイルの暗号化と暗号化解除がリアルタイムの I/O で実行されます。 この種の暗号化にはデータベース暗号化キー (DEK) が使用されます。これは、復旧時に使用できるようにデータベース ブート レコードに保存されます。 詳細については、次を参照してください。 [Transparent Data Encryption &#40;TDE&#41; ](security/encryption/transparent-data-encryption.md)と[TDE で保護されているデータベースを別の SQL Server に移動](security/encryption/move-a-tde-protected-database-to-another-sql-server.md)です。  
  
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
  
 For detailed information the Transact-SQL statements that have been used in this lesson, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql), [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql), [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql), [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql), and [sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql).  
  
 **次のレッスン:**  
  
 [レッスン 6: 内部設置型のソース コンピューターから Windows Azure のターゲット コンピューターにデータベースを移行する](lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
