---
title: "レッスン 6: ファイル スナップショット バックアップを使用してアクティビティを生成し、ログをバックアップする | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
caps.latest.revision: 15
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 15
---
# レッスン 6: ファイル スナップショット バックアップを使用してアクティビティを生成し、ログをバックアップする
このレッスンでは、AdventureWorks2014 データベースにアクティビティを生成し、ファイル スナップショット バックアップを使用してトランザクション ログ バックアップを定期的に作成します。 ファイル スナップショット バックアップの使用の詳細については、[「Azure でのデータベース ファイルのスナップショット バックアップ」](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md) を参照してください。  
  
AdventureWorks2014 データベースにアクティビティを生成し、ファイル スナップショット バックアップを使用してトランザクション ログ バックアップを定期的に作成するには、次の手順を実行します。  
  
1.  SQL Server Management Studio に接続します。  
  
2.  新しい 2 つのクエリ ウィンドウを開き、それぞれのクエリ ウィンドウを、Azure 仮想マシン内にあるデータベース エンジンの SQL Server 2016 インスタンスに接続します。  
  
3.  次の Transact-SQL スクリプトをコピーし、いずれかのクエリ ウィンドウに貼り付けて、実行します。 手順 4. で新しい行を追加する前に、Production.Location テーブルには 14 の行があります。  
  
    ```  
  
    -- Verify row count at start  
    SELECT COUNT (*) from AdventureWorks2014.Production.Location;  
  
    ```  
  
4.  次の 2 つの Transact-SQL スクリプトをコピーして 2 つの個別のクエリ ウィンドウに貼り付けます。 レッスン 1 で指定したコンテナーとストレージ アカウント名に合わせて適宜 URL を変更し、個別のクエリ ウィンドウで次のスクリプトを同時に実行します。 これらのスクリプトは、完了まで約 7 分かかります。  
  
    ```  
    -- Insert 30,000 new rows into the Production.Location table in the AdventureWorks2014 database in batches of 75  
    DECLARE @count INT=1, @inner INT;  
    WHILE @count < 400  
       BEGIN  
          BEGIN TRAN;  
             SET @inner =1;  
                WHILE @inner <= 75  
                   BEGIN;  
                      INSERT INTO AdventureWorks2014.Production.Location    
                         (Name, CostRate, Availability, ModifiedDate)   
                            VALUES (NEWID(), .5, 5.2, GETDATE());  
                      SET @inner = @inner + 1;  
                   END;  
          COMMIT;  
       WAITFOR DELAY '00:00:01';   
       SET @count = @count + 1;  
       END;  
    SELECT COUNT (*) from AdventureWorks2014.Production.Location;  
  
    ```  
  
    ```  
    --take 7 transaction log backups with FILE_SNAPSHOT, one per minute, and include the row count and the execution time in the backup file name   
    DECLARE @count INT=1, @device NVARCHAR(120), @numrows INT;  
    WHILE @count <= 7  
       BEGIN  
             SET @numrows = (SELECT COUNT (*) FROM AdventureWorks2014.Production.Location);  
             SET @device = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/tutorial-' + CONVERT (varchar(10),@numrows) + '-' + FORMAT(GETDATE(), 'yyyyMMddHHmmss') + '.bak';  
             BACKUP LOG AdventureWorks2014 TO URL = @device WITH FILE_SNAPSHOT;  
             SELECT * from sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
          WAITFOR DELAY '00:1:00';   
             SET @count = @count + 1;  
       END;  
    ```  
  
5.  1 番目のスクリプトの出力を確認します。最終的な行カウントは 29,939 になっています。  
  
    ![Row count of 29,939 is displayed](../relational-databases/media/5e2f4229-1970-49c9-89b3-e96b6f7fde83.JPG "Row count of 29,939 is displayed")  
  
6.  2 番目のスクリプトの出力を確認します。BACKUP LOG ステートメントが実行されるたびに 2 つの新しいファイル スナップショットが作成されています。ログ ファイルのファイル スナップショットが 1 つと、データ ファイルのファイル スナップショットが 1 つです (データベース ファイルごとに、合計 2 つのファイル スナップショット)。 2 番目のスクリプトが完了すると、ファイル スナップショットは合計で 16 個になっています。データベース ファイルごとに 8 個です (BACKUP DATABASE ステートメントで 1 つ、BACKUP LOG ステートメントの実行のたびに 1 つ)。  
  
    ![results pane showing file snapshots of both data and log file when log backup is taken](../relational-databases/media/acd213b8-895e-425c-bd72-2bf10e65a5ba.JPG "results pane showing file snapshots of both data and log file when log backup is taken")  
  
    ![four file snapshots are displayed](../relational-databases/media/e7eff77d-85b9-4e52-abd8-e49952c8118a.JPG "four file snapshots are displayed")  
  
    ![results pane showing a total of 16 file snapshots](../relational-databases/media/c3ddff17-a83c-4bf0-a670-a38834f9c922.JPG "results pane showing a total of 16 file snapshots")  
  
7.  オブジェクト エクスプローラーで、Azure Storage に接続します。  
  
8.  [Containers] を展開します。レッスン 1 で作成したコンテナーを展開し、新しいバックアップ ファイルが 7 つと、前のレッスンで生成された BLOB が表示されていることを確認します (必要に応じてノードを更新)。  
  
    ![Azure container showing 7 log backup blobs](../relational-databases/media/cfa5a326-87a2-4202-9a04-38bf577d2d0b.JPG "Azure container showing 7 log backup blobs")  
  
**次のレッスン:**  
  
[レッスン 7: 特定の時点にデータベースを復元する](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
  
