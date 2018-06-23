---
title: 'レッスン 6: ソースからデータベースを移行するコンピューターの内部設置型のターゲット コンピューターに Windows Azure に |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9134ade-7b03-4c5c-8ed3-3bc369a61691
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2f6f0ac359d5358994c0a3a5367c676ca2f83969
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174711"
---
# <a name="lesson-6-migrate-a-database-from-a-source-machine-on-premises-to-a-destination-machine-in-windows-azure"></a>レッスン 6: 内部設置型のソース コンピューターから Windows Azure のターゲット コンピューターにデータベースを移行する
  このレッスンでは、別の内部設置型コンピューターまたは Windows Azure 仮想マシンに存在している別の SQL Server が既にあるものと仮定します。 Windows Azure で SQL Server 仮想マシンを作成する方法については、次を参照してください。 [Windows Azure で SQL Server 仮想マシンのプロビジョニング](http://www.windowsazure.com/manage/windows/common-tasks/install-sql-server/)です。 Windows Azure で SQL Server 仮想マシンを準備した後、別のコンピューターの SQL Server Management Studio 経由でこの仮想マシンの SQL Server インスタンスに接続できることを確認します。  
  
 このレッスンは、次の手順を完了済みであることも前提としています。  
  
-   Windows Azure ストレージ アカウントを入手しました。  
  
-   Windows Azure ストレージ アカウントにコンテナーを作成しました。  
  
-   読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成しました。 SAS キーも生成しました。  
  
-   ソース コンピューターで SQL Server 資格情報を作成しました。  
  
-   Windows Azure で対象の SQL Server 仮想マシンを既に作成しました。 仮想マシンは、SQL Server 2014 を含んでいるプラットフォーム イメージを選択して作成することをお勧めします。  
  
 内部設置型 SQL Server から Windows Azure の別の仮想マシンにデータベースを移行するには、次の手順を実行します。  
  
1.  ソース コンピューター (このチュートリアルでは内部設置型コンピューター) で、SQL Server Management Studio のクエリ ウィンドウを開きます。 次のステートメントを実行して、データベースをデタッチし、別のコンピューターに移動します。  
  
    ```  
    -- Detach the database in the source machine   
    USE master  
    EXEC sp_detach_db 'TestDB1', 'true';  
    ```  
  
2.  ターゲット コンピューターにデータベースを転送する必要がある場合は、まずデータベースを準備しておく必要があります。 ターゲット コンピューターを準備するには、まずターゲット コンピューターで SQL Server 資格情報を作成する必要があります。 暗号化されたデータベースの場合は、証明書もソース コンピューターからターゲット コンピューターにインポートする必要があります。  
  
    1.  ターゲット コンピューターで SQL Server 資格情報を作成するには、次の手順を実行します。  
  
        1.  ソース コンピューターの SQL Server Management Studio 経由でターゲット コンピューターに接続します。  または、ターゲット コンピューターで SQL Server Management Studio を直接起動します。  
  
        2.  標準的なツール バーで、をクリックして**新しいクエリ**です。  
  
        3.  次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更します。 次のステートメントは、ストレージ コンテナーの共有アクセス証明書を格納する SQL Server 資格情報を作成します。  
  
            ```tsql  
  
            USE master   
            GO   
            CREATE CREDENTIAL [http://teststorageaccnt.blob.core.windows.net/testcontainer]   
            WITH IDENTITY='SHARED ACCESS SIGNATURE',   
            SECRET = 'your SAS key'   
            GO  
  
            ```  
  
        4.  使用可能なすべての資格情報を表示するには、クエリ ウィンドウで次のステートメントを実行します。  
  
            ```tsql  
            SELECT * from sys.credentials   
            ```  
  
        5.  ターゲット サーバーに接続して、クエリ ウィンドウを開き、次のステートメントを実行します。  
  
            ```tsql  
  
            -- Create a master key and a server certificate   
            USE master   
            GO   
            CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01'; -- You may use a different password.   
            GO   
            CREATE CERTIFICATE MySQLCert   
            FROM FILE = 'C:\certs\MySQLCert.CER'   
            WITH PRIVATE KEY   
            (   
            FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
            DECRYPTION BY PASSWORD = 'MySQLKey01'   
            );   
            GO  
  
            ```  
  
             この手順が終了すると、ソース コンピューターからバックアップされた暗号化証明書がターゲット コンピューターにインポートされます。 次に、ターゲット コンピューターでデータ ファイルをアタッチできます。  
  
    2.  次に、FOR ATTACH オプションを使用して Windows Azure ストレージの既存のファイルを指すデータ ファイルとログ ファイルを持つデータベースを作成します。 クエリ ウィンドウで、次のステートメントを実行します。  
  
        ```tsql  
  
        --Create a database on the destination server   
        CREATE DATABASE TestDB1onDest   
        ON   
        (NAME = TestDB1_data,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf' )   
        LOG ON   
         (NAME = TestDB1_log,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
        FOR ATTACH   
        GO  
  
        ```  
  
    3.  オブジェクト エクスプローラーで、[データベース] を右クリックし、[更新] をクリックします。 新しく作成したデータベース TestDB1onDest が一覧に表示されることを確認します。  
  
    4.  次に、クエリ ウィンドウで次のステートメントを実行します。  
  
        ```tsql  
  
        USE TestDB1onDest   
        SELECT * FROM Table1;   
        GO  
  
        ```  
  
         これでレッスン 4 で入力したデータがすべて表示されます。  
  
 暗号化されたデータベースがデータ移動なしで別のコンピューター インスタンスに転送されたことに注意してください。  
  
 SQL Server Management Studio を使用して、Windows Azure ストレージの既存のファイルを指すデータ ファイルとログ ファイルを持つデータベースを作成するには、次の手順を実行します。  
  
1.  **オブジェクト エクスプローラー**で、SQL Server データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]** を右クリックし、 **[新しいデータベース]** をクリックします。 次に [TestDB1] を右クリックします。 [タスク] をクリックし、[デタッチ] をクリックします。 [デタッチ] ダイアログ ウィンドウで、[接続の削除] チェック ボックスをオンにします。 **[OK]** をクリックします。  
  
3.  SQL Server 2014 CTP2 以降がインストールされたターゲット コンピューターに接続します。 ターゲット コンピューターを準備するには、ターゲット コンピューターで、TestDB1 を格納した同じコンテナーを指す SQL Server 資格情報を作成する必要があります。 同じコンピューターで再アタッチする場合、別の資格情報を作成する必要はありません。  
  
4.  **オブジェクト エクスプ ローラー**を右クリックして**データベース** をクリック**アタッチ**です。  
  
5.  **データベースのアタッチ**ダイアログ ボックスで、アタッチするデータベースを指定する をクリックして**追加**です。 **データベース ファイルの検索**ダイアログ ウィンドウ。  
  
     データベース データ ファイルの場所を入力:`https://teststorageaccnt.blob.core.windows.net/testcontainer/`です。  
  
     ファイル名を入力:`TestDB1Data.mdf`です。  
  
6.  **[OK]** をクリックします。  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-6-7.gif "SQL 14 CTP2")  
  
 **次のレッスン:**  
  
 [レッスン 7: Windows Azure ストレージにデータ ファイルを移動する](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)  
  
  