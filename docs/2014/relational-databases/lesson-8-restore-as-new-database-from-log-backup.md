---
title: 'レッスン 9:  Windows Azure ストレージからデータベースを復元 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ebba12c7-3d13-4c9d-8540-ad410a08356d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 41fbe4cefb6a759befd8b96ded8487ff54b0a1c6
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66090645"
---
# <a name="lesson-9-restore-a-database-from-windows-azure-storage"></a>レッスン 9:  Windows Azure ストレージからデータベースを復元する
  このレッスンでは、Windows Azure ストレージにあるデータベース バックアップ ファイルを内部設置型または Windows Azure の仮想マシンに存在するデータベースに復元する方法を学習します。 このレッスンを続行するには、レッスン 4、5、6、7 および 8 を実行する必要はありません。  
  
 このレッスンでは、次の手順が既に完了したことを前提としています。  
  
-   ソース コンピューターにデータベースを作成しました。  
  
-   使用して Windows Azure ストレージ (.bak)、データベースのバックアップを作成して、 [SQL Server Backup and Restore with Windows Azure Blob ストレージ サービス](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)機能します。 この手順では、SQL Server 資格情報をもう 1 つ作成する必要があることに注意してください。 この資格情報はストレージ アカウント キーを使用します。  
  
-   Windows Azure ストレージ アカウントを入手しました。  
  
-   Windows Azure ストレージ アカウントにコンテナーを作成しました。  
  
-   読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成しました。 SAS キーも生成しました。  
  
-   Windows Azure ストレージ統合機能のためにコンピューターで SQL Server 資格情報を作成しました。 この資格情報には Shared Access Signature (SAS) キーが必要であることに注意してください。  
  
 Windows Azure ストレージからデータベースを復元するには、次の手順を実行します。  
  
1.  [SQL Server Management Studio] を起動します。 既定のインスタンスに接続します。  
  
2.  クリックして**新しいクエリ**[標準] ツールバー。  
  
3.  次の完全なスクリプトをコピーして、クエリ ウィンドウに貼り付けます。 必要に応じて、スクリプトを変更します。  
  
     **注:** 実行する、`RESTORE`別のコンピューターのデータベース インスタンスを Windows Azure ストレージにデータベースのバックアップ (.bak) を復元するステートメント。  
  
    ```sql  
  
    USE master   
    GO   
    -- Create a new database to be backed up.   
    CREATE DATABASE TestDbRestoreFrom;   
    GO   
    USE TestDbRestoreFrom;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO   
    USE TestDbRestoreFrom;   
    GO   
    SELECT * from dbo.Table1;   
    GO   
    -- Create a credential to be used by SQL Server Backup and Restore with Windows Azure -----Blob Storage Service.   
    USE master;   
    GO   
    CREATE CREDENTIAL BackupCredential    
    WITH IDENTITY= 'teststorageaccnt',   
    SECRET = 'BO1nH/lWRdnc8TGPlQIXmGLWVCoEa48suYSGiAlC73+S0TX5VXo5/LCm8qiyGCYafDg4ZsueDIV3GQ5RXHaRGw=='    
    GO   
    -- Display the newly created credential   
    SELECT * from sys.credentials   
    -- Create a backup in Windows Azure Storage.   
    BACKUP DATABASE TestDBRestoreFrom    
    TO URL = 'https://teststorageaccnt.blob.core.windows.net/testrestorefrom/TestDBRestoreFrom.bak'    
          WITH CREDENTIAL = 'BackupCredential'    
         ,COMPRESSION   
         ,STATS = 5;   
    GO    
    -- Create a Shared Access Signature credential   
    CREATE CREDENTIAL [https://teststorageaccnt.blob.core.windows.net/testrestorefrom]   
    WITH IDENTITY='SHARED ACCESS SIGNATURE',   
    SECRET = 'sv=2012-02-12&sr=c&si=policy_resfrom&sig=EhVpzLUXjG4ThAMLmVhrnoiCt8IfmD3BsuYiMawGzxc%3D'   
    GO   
    USE master;   
    GO   
    RESTORE DATABASE TestDBRestoreFrom    
    FROM URL = 'https://teststorageaccnt.blob.core.windows.net/testrestorefrom/TestDBRestoreFrom.bak'    
    WITH    
    CREDENTIAL = 'BackupCredential',    
    REPLACE,   
    MOVE 'TestDBRestoreFrom' TO 'C:\Backup\TestDBRestoreFrom.mdf',     
    MOVE 'TestDBRestoreFrom_log' TO 'C:\Backup\TestDBRestoreFrom_log.ldf';   
    GO  
  
    ```  
  
 **チュートリアルの終了:Windows Azure ストレージ サービスでは、SQL Server データ ファイル**  
  
  
