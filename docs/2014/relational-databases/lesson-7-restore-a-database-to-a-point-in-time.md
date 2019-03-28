---
title: 'レッスン 8: Windows Azure ストレージにデータベースを復元 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: a9f99670-e1de-441e-972c-69faffcac17a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9e0841c3473baf73033f298cfd3c8402ffc3aa19
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58532564"
---
# <a name="lesson-8-restore-a-database-to-windows-azure-storage"></a>レッスン 8: Windows Azure ストレージにデータベースを復元する
  このレッスンでは、バックアップ ファイルをローカルで作成して、それを Windows Azure ストレージに復元する方法を学習します。 データベースの場所は、内部設置でも、Windows Azure の仮想マシンでもかまいません。 このレッスンを続行するには、レッスン 4、5、6 および 7 を実行する必要はありません。  
  
 このレッスンでは、次の手順が既に完了したことを前提としています。  
  
-   Windows Azure ストレージ アカウントを入手しました。  
  
-   Windows Azure ストレージ アカウントにコンテナーを作成しました。  
  
-   読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成しました。 SAS キーも生成しました。  
  
-   Shared Access Signature に基づいてソース コンピューターで SQL Server 資格情報を作成しました。  
  
-   ソース コンピューターにデータベースを作成しました。  
  
 Windows Azure ストレージにデータベースを復元するには、次の手順を実行します。  
  
1.  ソース コンピューターで、SQL Server Management Studio を起動します。  
  
2.  新しく作成したデータベースに接続すると、クエリ ウィンドウが開きます。 次のステートメントを実行します。  
  
    ```sql  
  
    USE TestDB3Restore;   
    GO   
    BACKUP DATABASE TestDB3Restore   
    TO DISK = 'C:\BACKUP\TestDB3Restore.Bak'   
       WITH FORMAT,   
       NAME = 'Full Backup of TestDB3Restore'   
    GO  
  
    ```  
  
3.  次に、クエリ ウィンドウに次のステートメントをコピーして実行します。  
  
    ```sql  
  
    USE master;   
    GO   
    RESTORE DATABASE TestDB3Restore    
    FROM DISK = 'C:\BACKUP\TestDB3Restore.bak'    
    WITH REPLACE,   
    MOVE 'TestDB3Restore' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore.mdf',     
    MOVE 'TestDB3Restore_log' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore_log.ldf';   
    GO  
  
    ```  
  
     この手順が終了すると、管理ポータルにコンテナーのデータ ファイル (.mdf) とログ ファイル (.ldf) が表示されます。  
  
 SQL Server Management Studio を使用して、Windows Azure ストレージを指すデータ ファイルとログ ファイルを持つデータベースを復元するには、次の手順を実行します。  
  
1.  **オブジェクト エクスプ ローラー**、サーバー ツリーを展開するサーバー名をクリックします。  
  
2.  展開**データベース**、し、データベースを選択します。  
  
3.  データベースを右クリックして **[タスク]** をポイントし、 **[復元]** をクリックします。  
  
4.  **全般**ページで、**復元**ソース セクションをクリックします**ソース**デバイス。  
  
5.  参照 ボタンをクリックして、**ソース**デバイス ボックスが開き、 **バックアップ デバイスの** ダイアログ ボックス。  
  
6.  バックアップ メディアのテキスト ボックスで、次のように選択します。**ファイル**、 をクリックし、**追加**バックアップ (.bak) ファイルを検索するボタンをクリックします。 **[OK]** をクリックします。  
  
7.  クリックして**ファイル**最初のページでします。  
  
8.  **データベース ファイルに復元**セクション**復元**フィールドを次の手順を入力します。  
  
     データ ファイル、入力:`https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf`します。 ログ ファイルの入力:`https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf`します。  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-8.gif "SQL 14 CTP2")  
  
9. **[OK]** をクリックします。  
  
 復元を実行したら、管理ポータルにログインします。 コンテナーの .mdf ファイルおよび .ldf ファイルを次のように確認できる必要があります。  
  
 ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-9.gif "SQL 14 CTP2")  
  
 **次のレッスン:**  
  
 [レッスン 9:Windows Azure ストレージからデータベースを復元する](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)  
  
  
