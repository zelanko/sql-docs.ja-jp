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
ms.openlocfilehash: 46273fc70b7362f5f1d5b5ca11cb1114ffe65d4b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84958656"
---
# <a name="create-an-encrypted-backup"></a>暗号化されたバックアップの作成
  このトピックでは、暗号化されたバックアップを Transact-SQL で作成するために必要な手順について説明します。  
  
## <a name="backup-to-disk-with-encryption"></a>暗号化の使用によるディスクへのバックアップ  
 **前提条件:**  
  
-   データベースのバックアップを作成するための空き領域が十分にあるローカル ディスクまたはストレージへのアクセス。  
  
-   master データベースのデータベース マスター キー、SQL Server インスタンスで使用可能な証明書または非対称キー。 暗号化の要件と権限については、「 [バックアップの暗号化](backup-encryption.md)」を参照してください。  
  
 データベースの暗号化されたバックアップをローカル ディスクに作成するには、次の手順を実行します。 この例では、MyTestDB というユーザー データベースを使用します。  
  
1.  **master データベースのデータベース マスター キーの作成:** データベースに格納するマスター キーのコピーを暗号化するためのパスワードを指定します。 データベース エンジンに接続して新しいクエリ ウィンドウを開き、次の例をコピーして貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- Creates a database master key.   
    -- The key is encrypted using the password "<master key password>"  
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
2.  **バックアップ証明書の作成:** master データベースでバックアップ証明書を作成します。 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    Use Master  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDB Backup Encryption Certificate';  
    GO  
  
    ```  
  
3.  **データベースのバックアップ:** 使用する暗号化アルゴリズムと証明書を指定します。 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
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
  
### <a name="backup-to-azure-storage-with-encryption"></a>暗号化して Azure Storage にバックアップする  
 **[SQL Server Backup to URL]** オプションを使用して Azure Storage へのバックアップを作成する場合、暗号化の手順は同じですが、バックアップ先として URL を使用し、Azure Storage への認証用に SQL 資格情報を指定する必要があります。 暗号化オプションを使用してを構成する場合は [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 、「 [azure への管理](enable-sql-server-managed-backup-to-microsoft-azure.md)されたバックアップのセットアップ SQL Server」および「 [azure への管理されたバックアップの SQL Server 設定](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)」を参照してください。  
  
 **前提条件:**  
  
-   Windows ストレージ アカウントとコンテナー。 詳細については、以下を参照してください。 [レッスン 1:Azure ストレージ オブジェクトの作成](../../tutorials/lesson-1-create-windows-azure-storage-objects.md)。  
  
-   master データベースのデータベース マスター キー、SQL Server インスタンス上の証明書または非対称キー。 暗号化の要件と権限については、「 [バックアップの暗号化](backup-encryption.md)」を参照してください。  
  
1.  **SQL Server 資格情報の作成:** SQL Server 資格情報を作成するには、データベース エンジンに接続して新しいクエリ ウィンドウを開き、次の例をコピーして貼り付け、 **[実行]** をクリックします。  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account    
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account  
    ```  
  
2.  **データベースのマスター キーを作成する:** データベースに格納するマスター キーのコピーを暗号化するためのパスワードを指定します。 データベース エンジンに接続して新しいクエリ ウィンドウを開き、次の例をコピーして貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
3.  **バックアップ証明書の作成:** master データベースでバックアップ証明書を作成します。 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    USE Master;  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDBBackupEncryptCert ';  
    GO  
  
    ```  
  
4.  **データベースのバックアップ:** 使用する暗号化アルゴリズムと証明書を指定します。 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
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
  
  
