---
title: 'レッスン 7: データファイルを Azure Storage に移動する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 25ae3cee8e08292297449914bfb6e40dfc1b4b3a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "70175456"
---
# <a name="lesson-7-move-your-data-files-to-azure-storage"></a>レッスン 7: Azure Storage にデータ ファイルを移動する
  このレッスンでは、(SQL Server インスタンスではなく) Azure Storage にデータファイルを移動する方法を学習します。 このレッスンを続行するには、レッスン 4、5、および 6 を実行する必要はありません。  
  
 データファイルを Azure Storage に移動するには、 `ALTER DATABASE`ステートメントを使用します。これは、データファイルの場所を変更するのに役立ちます。  
  
 このレッスンでは、次の手順を既に完了していることを前提としています。  
  
-   Azure Storage アカウントを持っています。  
  
-   Azure Storage アカウントでコンテナーを作成しました。  
  
-   読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成しました。 SAS キーも生成しました。  
  
-   ソース コンピューターで SQL Server 資格情報を作成しました。  
  
 次に、次の手順を使用して、データファイルを Azure Storage に移動します。  
  
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
    -- the new location of the file in Azure Storage container.   
    ALTER DATABASE TestDB1Alter    
        MODIFY FILE ( NAME = TestDB1Alter,    
                    FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontaineralter/TestDB1AlterData.mdf');   
    GO  
  
    ```  
  
3.  これを実行すると、システムカタログで "ファイル" TestDB1Alter "が変更されていることがわかります。 新しいパスは、次回データベースを起動するときに使用されます。  
  
4.  続いて、データベースをオフラインにします。  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET OFFLINE;   
    GO  
  
    ```  
  
5.  次に、 [Azcopy ツール](https://blogs.msdn.com/b/windowsazurestorage/archive/2012/12/03/azcopy-uploading-downloading-files-for-windows-azure-blobs.aspx)、 [Put Page](https://msdn.microsoft.com/library/azure/ee691975.aspx)、 [storage Client Library Reference](https://msdn.microsoft.com/library/azure/dn261237.aspx)、またはサードパーティのストレージエクスプローラーツールのいずれかの方法を使用して、データファイルを Azure Storage にコピーする必要があります。  
  
     **重要:** この新しい機能強化を使用する場合は、必ずブロック blob ではなくページ blob を作成してください。  
  
6.  続いて、データベースをオンラインにします。  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET ONLINE;   
    GO  
  
    ```  
  
 **次のレッスン:**  
  
 [レッスン8。Azure Storage にデータベースを復元する](lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
