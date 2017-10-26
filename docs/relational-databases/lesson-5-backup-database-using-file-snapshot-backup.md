---
title: "レッスン 5: ファイル スナップショット バックアップを使用してデータベースをバックアップする | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: d9134ade-7b03-4c5c-8ed3-3bc369a61691
caps.latest.revision: 19
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: dd3226cf6bf52151c94853d87b4de28e54b5d2df
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-5-backup-database-using-file-snapshot-backup"></a>レッスン 5: ファイル スナップショット バックアップを使用してデータベースをバックアップする
このレッスンでは、AdventureWorks2014 データベースを Azure のスナップショットを使用して、ほぼ瞬時に Azure 仮想マシンにファイル スナップショット バックアップでバックアップを行います。 ファイル スナップショット バックアップの詳細については、「 [Azure でのデータベース ファイルのスナップショット バックアップ](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)」を参照してください。  
  
AdventureWorks2014 をファイル スナップショット バックアップを使用してバックアップするには、次の手順に従います。  
  
1.  SQL Server Management Studio に接続します。  
  
2.  新しいクエリ ウィンドウを開き、Azure 仮想マシン内にあるデータベース エンジンの SQL Server 2016 インスタンスに接続します。  
  
3.  次の TRANSACT-SQL スクリプトをコピーして、クエリ ウィンドウに貼り付け、実行します (このクエリ ウィンドウは閉じないでください。このスクリプトは、手順 5 で再度実行します)。 このシステム ストアド プロシージャでは、指定したデータベースを構成する既存のファイル スナップショット バックアップの各ファイルを確認できます。 このデータベースのファイル スナップショット バックアップはありません。  
  
    ```  
  
    -- Verify that no file snapshot backups exist  
    SELECT * FROM sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
  
    ```  
  
4.  次の Transact-SQL スクリプトをコピーしてクエリ ウィンドウに貼り付けます。 レッスン 1 で指定したコンテナーとストレージ アカウント名に合わせて適宜 URL を変更し、次のスクリプトを実行します。 非常に早くバックアップされます。  
  
    ```  
  
    -- Backup the AdventureWorks2014 database with FILE_SNAPSHOT  
    BACKUP DATABASE AdventureWorks2014   
       TO URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_Azure.bak'   
       WITH FILE_SNAPSHOT;  
  
    ```  
  
    ![各データベース ファイルのファイル スナップショットを示す結果ペイン](../relational-databases/media/2a9320e0-067a-485a-8e0e-636660005e5c.JPG "各データベース ファイルのファイル スナップショットを示す結果ペイン")  
  
5.  手順 4 のスクリプトが正常に実行されたことを確認した後、次のスクリプトを再度実行します。 手順 4 のファイル スナップショット バックアップ操作で、データとログ ファイルの両方のファイル スナップショットが生成されました。  
  
    ```  
  
    -- Verify that two file-snapshot backups exist  
    SELECT * FROM sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
  
    ```  
  
    ![2 つのスナップショットを示す sys.fn_db_backup_file_snapshots 関数の結果](../relational-databases/media/fca1436e-9607-4432-97ee-f66ac2f2108d.JPG "2 つのスナップショットを示す sys.fn_db_backup_file_snapshots 関数の結果")  
  
6.  Azure 仮想マシンの SQL Server 2016 インスタンスのオブジェクト エクスプ ローラーで、[データベース] ノードを展開し、AdventureWorks2014 データベースがこのインスタンスに復元されたことを確認します (ノードは必要に応じて更新します)。  
  
7.  オブジェクト エクスプローラーで、Azure Storage に接続します。  
  
8.  レッスン 1 で作成したコンテナーを展開して、上記の手順 4 で作成した AdventureWorks2014_Azure.bak が、レッスン 3 で作成したバックアップ ファイルとレッスン 4 で作成したデータベース ファイル一緒にこのコンテナーの中に表示されていることを確認します (ノードは必要に応じて更新します)。  
  
    ![Azure コンテナーに表示されているファイル スナップショット バックアップ](../relational-databases/media/181bc970-4af7-4272-a9ae-4bef674f2e02.JPG "Azure コンテナーに表示されているファイル スナップショット バックアップ")  
  
**次のレッスン:**  
  
[レッスン 6: ファイル スナップショット バックアップを使用してアクティビティを生成し、ログをバックアップする](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)  
  
## <a name="see-also"></a>参照  
[Azure でのデータベース ファイルのスナップショット バックアップ](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)  
[sys.fn_db_backup_file_snapshots (Transact-SQL)](../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)  
  
  
  

