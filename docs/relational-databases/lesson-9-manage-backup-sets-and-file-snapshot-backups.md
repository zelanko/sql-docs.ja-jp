---
title: "レッスン 9: バックアップ セットとファイル スナップショット バックアップを管理する | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 766a0846-db15-4346-b814-4049039bcbfc
caps.latest.revision: 10
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 10
---
# レッスン 9: バックアップ セットとファイル スナップショット バックアップを管理する
このレッスンでは、[sp_delete_backup (Transact-SQL)](../Topic/sp_delete_backup%20(Transact-SQL).md) システム ストアド プロシージャを使用してバックアップ セットを削除します。 このシステム ストアド プロシージャは、このバックアップ セットに関連付けられている各データベース ファイルのバックアップ ファイルおよびスナップショット ファイルを削除します。  
  
> [!NOTE]  
> 単にバックアップ ファイルを Azure BLOB コンテナーから削除することでバックアップ セットを削除しようとした場合は、バックアップ ファイル自体が削除されるだけで、関連付けられているスナップショット ファイルは残ってしまいます。 そのような状況になった場合は、[sys.fn_db_backup_file_snapshots (Transact-SQL)](../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md) システム関数を使用して孤立したファイル スナップショットの URL を特定し、[sp_delete_backup_file_snapshot (Transact-SQL)](../Topic/sp_delete_backup_file_snapshot%20(Transact-SQL).md) システム ストアド プロシージャを使用して孤立した各ファイル スナップショットを削除します。 詳細については、「[Azure でのデータベース ファイルのファイル スナップショット バックアップ](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)」を参照してください。  
  
ファイル スナップショット バックアップ セットを削除するには、次の手順のようにします。  
  
1.  SQL Server Management Studio に接続します。  
  
2.  新しいクエリ ウィンドウを開き、Azure 仮想マシンのデータベース エンジンの SQL Server 2016 インスタンス (または、このコンテナーでの読み取りおよび書き込みアクセス許可を持つ任意の SQL Server 2016 インスタンス) に接続します。  
  
3.  次の Transact-SQL スクリプトをコピーしてクエリ ウィンドウに貼り付けます。 関連付けられているファイル スナップショットと共に削除するログ バックアップを選択します。 レッスン 1 で指定したコンテナーとストレージ アカウント名に合わせて適宜 URL を変更し、ログ バックアップ ファイルの名前を指定して、次のスクリプトを実行します。  
  
    ```  
  
    sys.sp_delete_backup 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/tutorial-9164-20150726012420.bak';  
  
    ```  
  
4.  オブジェクト エクスプローラーで、Azure Storage に接続します。  
  
5.  レッスン 1 で作成したコンテナーを展開し、手順 3 で使用したバックアップ ファイルがこのコンテナーに表示されなくなっていることを確認します (必要に応じてノードの表示を更新します)。  
  
    ![Azure container showing the deletion of the log backup blob](../relational-databases/media/c0070b08-4667-4db5-aaff-987a404ec934.JPG "Azure container showing the deletion of the log backup blob")  
  
6.  次の Transact-SQL スクリプトをコピーし、クエリ ウィンドウに貼り付け、実行して、2 つのファイル スナップショットが削除されていることを確認します。  
  
    ```  
  
    -- verify that two file snapshots have been removed  
    SELECT * from sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
  
    ```  
  
    ![Results pane showing 2 file snapshots deleted](../relational-databases/media/f3891361-dfb6-4f4d-a090-ebfeb977981e.JPG "Results pane showing 2 file snapshots deleted")  
  
**チュートリアルの終了**  
  
## 参照  
[Azure でのデータベース ファイルのファイル スナップショット バックアップ](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)  
[sp_delete_backup (Transact-SQL)](../Topic/sp_delete_backup%20(Transact-SQL).md)  
[sys.fn_db_backup_file_snapshots (Transact-SQL)](../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)  
[sp_delete_backup_file_snapshot (Transact-SQL)](../Topic/sp_delete_backup_file_snapshot%20(Transact-SQL).md)  
  
  
  
