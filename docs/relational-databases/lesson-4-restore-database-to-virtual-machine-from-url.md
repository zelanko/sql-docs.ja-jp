---
title: 'レッスン 4: URL から仮想マシンにデータベースを復元する | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bbf0e07231829ec1bbe68ee405b86541365d13f3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="lesson-4-restore-database-to-virtual-machine-from-url"></a>レッスン 4: URL から仮想マシンにデータベースを復元する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
このレッスンでは、Azure 仮想マシン内の SQL Server 2016 インスタンスに AdventureWorks2014 データベースを復元します。
  
> [!NOTE]  
> このチュートリアルではわかりやすくするために、データ ファイルおよびログ ファイル用のコンテナーとして、データベースのバックアップの場合と同じものを使用します。 運用環境では、多くの場合、複数のコンテナーを使用し、データ ファイルも複数を頻繁に使用することになります。 SQL Server 2016 では、大規模なデータベースをバックアップする場合にそのパフォーマンスを向上させるために、バックアップを複数の BLOB でストライプ化することも検討可能です。  
  
Azure BLOB ストレージから Azure 仮想マシン内の SQL Server 2016 インスタンスに SQL Server 2014 データベースを復元するには、次の手順を実行します。  
  
1.  SQL Server Management Studio に接続します。  
  
2.  新しいクエリ ウィンドウを開き、Azure 仮想マシン内にあるデータベース エンジンの SQL Server 2016 インスタンスに接続します。  
  
3.  次の Transact-SQL スクリプトをコピーしてクエリ ウィンドウに貼り付けます。 レッスン 1 で指定したコンテナーとストレージ アカウント名に合わせて適宜 URL を変更し、次のスクリプトを実行します。  
  
    ```  
  
    -- Restore AdventureWorks2014 from URL to SQL Server instance using Azure blob storage for database files  
    RESTORE DATABASE AdventureWorks2014   
       FROM URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_onprem.bak'   
       WITH  
          MOVE 'AdventureWorks2014_data' to 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_Data.mdf'  
         ,MOVE 'AdventureWorks2014_log' to 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_Log.ldf'  
    --, REPLACE  
  
    ```  
  
4.  オブジェクト エクスプローラーを開き、Azure SQL Server 2016 インスタンスに接続します。  
  
5.  オブジェクト エクスプローラーで、[データベース] ノードを展開し、AdventureWorks2014 データベースが復元されていることを確認します (必要に応じてノードを更新する)。  
  
    ![仮想マシンで SQL Server 2016 に復元された Adventure Works 2014 データベース](../relational-databases/media/311f69a6-8443-4df5-8f30-3103c2472300.JPG "仮想マシンで SQL Server 2016 に復元された Adventure Works 2014 データベース")  
  
6.  オブジェクト エクスプローラーで AdventureWorks2014 を右クリックし、[プロパティ] をクリックします (確認したら [キャンセル] をクリックする)。  
  
7.  [ファイル] をクリックして、2 つのデータベース ファイルのパスが、Azure ブログ コンテナー内の BLOB を指す URL であることを確認します。  
  
    ![論理データ ファイルのファイル パスを URL として示すデータベース プロパティ](../relational-databases/media/cfeee576-6319-460e-9fa2-f0922e02ee23.JPG "論理データ ファイルのファイル パスを URL として示すデータベース プロパティ")  
  
8.  オブジェクト エクスプローラーで、Azure Storage に接続します。  
  
9. コンテナーの展開。レッスン 1 で作成したコンテナーを展開して、このコンテナーの中に、上記の手順 3 で作成した AdventureWorks2014_Data.mdf と AdventureWorks2014_Log.ldf が、レッスン 3 で作成したバックアップ ファイルと一緒に表示されていることを確認します (必要に応じて、ノードを更新する)。  
  
    ![Adventure Works 2014 データとログ ファイルが Azure コンテナーに blob として表示される](../relational-databases/media/156c7d73-44be-4754-9653-04cccb6c3066.JPG "Adventure Works 2014 データとログ ファイルが Azure コンテナーに blob として表示される")  
  
**次のレッスン:**  
  
[レッスン 5: ファイル スナップショット バックアップを使用してデータベースをバックアップする](../relational-databases/lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
  
