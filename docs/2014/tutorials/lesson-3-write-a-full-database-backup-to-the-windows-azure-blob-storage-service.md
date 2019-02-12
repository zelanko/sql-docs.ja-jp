---
title: 'レッスン 3: Windows Azure Blob ストレージ サービスに対するデータベースの完全バックアップの書き込み |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 242e32b08ec6346c39e149628e773b33554c95d4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56029793"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>レッスン 3: Windows Azure Blob ストレージ サービスに対するデータベースの完全バックアップを書き込み
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
 [レッスン 4:データベースの完全バックアップから復元を実行](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)します。  
  
  
