---
title: 'レッスン 7: Windows Azure ストレージへのデータ ファイルの移動 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 45004f8544efc0f0cc02292dbe28fdd75d6dc1de
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743258"
---
# <a name="lesson-7-move-your-data-files-to-windows-azure-storage"></a>レッスン 7: Microsoft Azure ストレージへのデータ ファイルの移動
  このレッスンでは、Windows Azure ストレージ (SQL Server インスタンスではなく) にデータ ファイルを移動する方法について学習します。 このレッスンを続行するには、レッスン 4、5、および 6 を実行する必要はありません。  
  
 Windows Azure ストレージにデータ ファイルを移動するには、データ ファイルの場所を変更できる `ALTER DATABASE` ステートメントを使用できます。  
  
 このレッスンでは、次の手順が既に完了したことを前提としています。  
  
-   Windows Azure ストレージ アカウントを入手しました。  
  
-   Windows Azure ストレージ アカウントにコンテナーを作成しました。  
  
-   読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成しました。 SAS キーも生成しました。  
  
-   ソース コンピューターで SQL Server 資格情報を作成しました。  
  
 次に、以下の手順を使用して、Windows Azure ストレージにデータ ファイルを移動します。  
  
1.  まず、ソース コンピューターにテスト データベースを作成し、それにデータを追加します。  
  
    ```sql  
  
    USE master;   
    CREATE DATABASE TestDB1Alter;   
    GO   
    USE TestDB1Alter;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
2.  次のコードを実行します。  
  
    ```sql  
  
    -- In the following statement, modify the path specified in FILENAME to   
    -- the new location of the file in Windows Azure Storage container.   
    ALTER DATABASE TestDB1Alter    
        MODIFY FILE ( NAME = TestDB1Alter,    
                    FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontaineralter/TestDB1AlterData.mdf');   
    GO  
  
    ```  
  
3.  これを実行すると、このメッセージが表示されます。"ファイル"TestDB1Alter"がシステム カタログに変更されました。 新しいパスが使用次回データベースを起動します。"  
  
4.  続いて、データベースをオフラインにします。  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET OFFLINE;   
    GO  
  
    ```  
  
5.  ここで、次のメソッドのいずれかを使用して Windows Azure ストレージにデータ ファイルをコピーする必要があります。[AzCopy ツール](https://blogs.msdn.com/b/windowsazurestorage/archive/2012/12/03/azcopy-uploading-downloading-files-for-windows-azure-blobs.aspx)、 [Put Page](https://msdn.microsoft.com/library/azure/ee691975.aspx)、[ストレージ クライアント ライブラリ リファレンス](https://msdn.microsoft.com/library/azure/dn261237.aspx)、またはサード パーティのストレージ エクスプ ローラー ツール。  
  
     **重要:** この新しい機能強化を使用して、常にブロック blob ではなくページ blob を作成することを確認します。  
  
6.  続いて、データベースをオンラインにします。  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET ONLINE;   
    GO  
  
    ```  
  
 **次のレッスン:**  
  
 [レッスン 8:Windows Azure ストレージにデータベースを復元する](lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
