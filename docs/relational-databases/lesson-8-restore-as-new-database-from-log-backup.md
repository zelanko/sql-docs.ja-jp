---
title: "レッスン 8: ログ バックアップから新しいデータベースとして復元する | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: ebba12c7-3d13-4c9d-8540-ad410a08356d
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 281259fb737bbc41885a61e62a4fcc83b3001119
ms.lasthandoff: 04/11/2017

---
# <a name="lesson-8-restore-as-new-database-from-log-backup"></a>レッスン 8: ログ バックアップから新しいデータベースとして復元する
このレッスンでは、ファイル スナップショットのトランザクション ログ バックアップから、新しいデータベースとして AdventureWorks2014 データベースを復元します。  
  
このシナリオでは、ビジネス分析やレポートのために、別の仮想マシン上の SQL Server インスタンスに復元を実行します。 別の仮想マシン上の別のインスタンスに復元することによって、この目的に合わせてサイズ調整された専用の仮想マシンにワークロードをオフロードし、トランザクション システムからリソース要件を削除することができます。  
  
ファイル スナップショット バックアップを使用したトランザクション ログ バックアップからの復元は非常に高速で、従来のストリーミング バックアップよりも大幅に高速です。 従来のストリーミング バックアップでは、データベースの完全バックアップ、必要に応じて差分バックアップ、一部またはすべてのトランザクション ログ バックアップ (または新しいデータベースの完全バックアップ) を使用する必要があります。 一方、スナップショット ファイルのログ バックアップでは、最新のログ バックアップ (2 つのログ バックアップ時点間の特定の時点に復元する場合は、もう 1 つのログ バックアップまたは 2 つの隣接するログ バックアップ) のみが必要です。 簡単に言うと、各ファイルスナップショットのログ バックアップによって各データベース ファイルのファイル スナップショット (各データ ファイルとログ ファイル) が作成されるので、ログ ファイル スナップショット バックアップ セットが 1 つだけ必要です。  
  
ファイル スナップショット バックアップを使用して、トランザクション ログ バックアップから新しいデータベースにデータベースを復元するには、次の手順を実行します。  
  
1.  SQL Server Management Studio に接続します。  
  
2.  新しいクエリ ウィンドウを開き、Azure 仮想マシン内にあるデータベース エンジンの SQL Server 2016 インスタンスに接続します。  
  
    > [!NOTE]  
    > 前のレッスンで使用していたものとは別の Azure 仮想マシンを使用する場合は、「 [レッスン 2: Shared Access Signature を使用して SQL Server 資格情報を作成する](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)」の手順に従っていることを確認します。 別のコンテナーに復元する場合は、新しいコンテナーについて、「 [レッスン 1: Azure コンテナーに格納済みアクセス ポリシーと Shared Access Signature を作成する](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md) 」と「 [レッスン 2: Shared Access Signature を使用して SQL Server 資格情報を作成する](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md) 」の手順を実行します。  
  
3.  次の Transact-SQL スクリプトをコピーしてクエリ ウィンドウに貼り付けます。 使用するログ バックアップ ファイルを選択します。 レッスン 1 で指定したコンテナーとストレージ アカウント名に合わせて適宜 URL を変更し、ログ バックアップ ファイルの名前を指定して、次のスクリプトを実行します。  
  
    ```  
  
    -- restore as a new database from a transaction log backup file  
    RESTORE DATABASE AdventureWorks2014_EOM   
        FROM URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/<logbackupfile.bak'    
        WITH MOVE 'AdventureWorks2014_data' to 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_EOM_Data.mdf'  
       , MOVE 'AdventureWorks2014_log' to 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_EOM_Log.ldf'  
       , RECOVERY  
    --, REPLACE  
  
    ```  
  
4.  出力を調べて復元が正常に行われたことを確認します。  
  
5.  オブジェクト エクスプローラーで、Azure ストレージに接続します。  
  
6.  [Containers] を展開します。レッスン 1 で作成したコンテナーを展開し (必要に応じて表示を更新して)、コンテナー内に新しいデータ ファイルとログ ファイルが、前のレッスンで生成された BLOB と共に表示されていることを確認します。  
  
    ![新しいデータベースのデータおよびログ ファイルを示す Azure コンテナー](../relational-databases/media/e9705083-86bc-4309-a0bf-92c15f174c0a.JPG "新しいデータベースのデータおよびログ ファイルを示す Azure コンテナー")  
  
[レッスン 9: バックアップ セットとファイル スナップショット バックアップを管理する](../relational-databases/lesson-9-manage-backup-sets-and-file-snapshot-backups.md)  
  
  
  

