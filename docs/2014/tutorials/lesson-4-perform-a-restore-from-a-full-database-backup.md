---
title: レッスン 4:データベースの完全バックアップから復元を実行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 077fb708f09db0182bc5f1510f0264b139beab13
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63312069"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a>レッスン 4:データベースの完全バックアップからの復元の実行
  このレッスンでは、TSQL ステートメントを使用して、前のレッスンで作成したデータベースの完全バックアップからの復元を実行する方法を紹介します。  
  
## <a name="perform-a-restore-of-a-database-backup"></a>データベース バックアップの復元の実行  
 データベースの完全バックアップを復元するには、次の手順を実行します。  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]に接続します。  
  
2.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]のインスタンスに接続します。  
  
3.  [標準] メニュー バーの **[新しいクエリ]** をクリックします。  
  
4.  次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更します。  
  
    ```  
    RESTORE DATABASE AdventureWorks2012   
    FROM URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    WITH CREDENTIAL = 'mycredential';  
    , STATS = 5 - use this to see monitor the progress  
    GO  
  
    ```  
  
5.  T-SQL ステートメントを確認し、クリックして**Execute**  
  
### <a name="return-to-tutorials-portal"></a>チュートリアル ポータルに戻る  
 [チュートリアル: SQL Server のバックアップと復元を Windows Azure Blob ストレージ サービス](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)します。  
  
  
