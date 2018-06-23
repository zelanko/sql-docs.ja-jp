---
title: 'レッスン 3: Windows Azure Blob ストレージ サービスへのデータベースの完全バックアップの書き込み |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cec916094b297baa648b743b2c5649ee4fced1c8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174380"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>レッスン 3: Windows Azure BLOB ストレージ サービスに対するデータベースの完全バックアップの書き込み
  このレッスンでは、TSQL ステートメントを使用して Windows Azure BLOB ストレージ サービスにデータベースの完全バックアップを実行する方法を紹介します。  
  
## <a name="perform-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Windows Azure BLOB ストレージ サービスに対するデータベースの完全バックアップの実行  
 データベースの完全バックアップを実行するには、次の手順を実行します。  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]に接続します。  
  
2.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]のインスタンスに接続します。  
  
3.  [標準] メニュー バーの **[新しいクエリ]** をクリックします。  
  
4.  次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更して、 **[実行]** をクリックします。  
  
    ```  
    BACKUP DATABASE[AdventureWorks2012]   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/   
    WITH CREDENTIAL = 'mycredential';  
    /* name of the credential you created in the previous step */   
    GO  
  
    ```  
  
5.  オブジェクト エクスプローラーで、Azure ストレージに接続します。 コンテナーと、新しく作成したバックアップ ファイルを参照して指定します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [Lesson 4: Perform a Restore From a Full Database Backup](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)。  
  
  