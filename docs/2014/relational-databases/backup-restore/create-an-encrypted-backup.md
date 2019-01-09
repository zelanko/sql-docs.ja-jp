---
title: 暗号化されたバックアップの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: e29061d3-c2ab-4d98-b9be-8e90a11d17fe
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3959e998111d5fa45eee45b3d7de35501f86f794
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52531848"
---
# <a name="create-an-encrypted-backup"></a>暗号化されたバックアップの作成
  このトピックでは、暗号化されたバックアップを Transact-SQL で作成するために必要な手順について説明します。  
  
## <a name="backup-to-disk-with-encryption"></a>暗号化の使用によるディスクへのバックアップ  
 **前提条件:**  
  
-   データベースのバックアップを作成するための空き領域が十分にあるローカル ディスクまたはストレージへのアクセス。  
  
-   master データベースのデータベース マスター キー、SQL Server インスタンスで使用可能な証明書または非対称キー。 暗号化の要件と権限については、「 [バックアップの暗号化](backup-encryption.md)」を参照してください。  
  
 データベースの暗号化されたバックアップをローカル ディスクに作成するには、次の手順を実行します。 この例では、MyTestDB というユーザー データベースを使用します。  
  
1.  **Master データベースのデータベース マスター _ キーを作成します。** データベースに格納するマスター キーのコピーを暗号化するためのパスワードを指定します。 データベース エンジンに接続して新しいクエリ ウィンドウを開き、次の例をコピーして貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- Creates a database master key.   
    -- The key is encrypted using the password "<master key password>"  
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
2.  **バックアップ証明書を作成します。** Master データベースで、バックアップ証明書を作成します。 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    Use Master  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDB Backup Encryption Certificate';  
    GO  
  
    ```  
  
3.  **データベースをバックアップしてください。** 暗号化アルゴリズムおよび使用する証明書を指定します。 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      COMPRESSION,  
      ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
 EKM で保護されているバックアップの暗号化の例については、「[Azure Key Vault を使用する拡張キー管理 &#40;SQL Server&#41;](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)」を参照してください。  
  
### <a name="backup-to-windows-azure-storage-with-encryption"></a>暗号化の使用による Windows Azure ストレージへのバックアップ  
 **[SQL Server Backup to URL]** オプションを使用して Windows Azure ストレージへのバックアップを作成する場合、暗号化の手順は同じですが、バックアップ先として URL を使用し、Windows Azure ストレージへの認証用に SQL 資格情報を指定する必要があります。 構成する場合[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]暗号化のオプションを使用して、次を参照してください[を設定する SQL Server Managed Backup to Windows Azure](enable-sql-server-managed-backup-to-microsoft-azure.md)と[の可用性グループを設定するSQLServerManagedBackuptoWindowsAzure](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
 **前提条件:**  
  
-   Windows ストレージ アカウントとコンテナー。 詳細については、以下を参照してください。 [レッスン 1:Windows Azure ストレージ オブジェクトの作成](../../tutorials/lesson-1-create-windows-azure-storage-objects.md)です。  
  
-   master データベースのデータベース マスター キー、SQL Server インスタンス上の証明書または非対称キー。 暗号化の要件と権限については、「 [バックアップの暗号化](backup-encryption.md)」を参照してください。  
  
1.  **SQL Server 資格情報を作成します。** SQL Server 資格情報を作成するデータベース エンジンに接続する、新しいクエリ ウィンドウを開くと次の例を貼り付けるし、 をクリックして**Execute**します。  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account    
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account  
    ```  
  
2.  **データベース マスター_キーを作成します。** データベースに格納するマスター キーのコピーを暗号化するためのパスワードを指定します。 データベース エンジンに接続して新しいクエリ ウィンドウを開き、次の例をコピーして貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
3.  **バックアップ証明書を作成します。** Master データベースのバックアップ証明書を作成します。 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    USE Master;  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDBBackupEncryptCert ';  
    GO  
  
    ```  
  
4.  **データベースをバックアップしてください。** 暗号化アルゴリズムと使用する証明書を指定します。 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO URL = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      CREDENTIAL 'mycredential' - this is the name of the credential created in the first step.  
      ,COMPRESSION  
      ,ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
  
