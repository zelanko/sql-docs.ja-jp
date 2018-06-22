---
title: 'レッスン 4: Windows Azure ストレージにデータベースを作成する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a9ae1501-b614-49d3-b975-6569da8350b2
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9b72bfc90936011fc4556fae6021fad89b134c57
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071656"
---
# <a name="lesson-4-create-a-database-in-windows-azure-storage"></a>レッスン 4: Windows Azure ストレージにデータベースを作成する
  このレッスンでは、Windows Azure 機能で SQL Server データ ファイルを使用してデータベースを作成する方法を学習します。 このレッスンの前に、レッスン 1、2、および 3 を完了する必要があることに注意してください。 レッスン 3 は非常に重要な手順です。レッスン 4 の前に、SQL Server の資格情報ストアに、Windows Azure ストレージ コンテナーと関連するポリシー名、および SAS キーに関する情報を格納する必要があるためです。  
  
 データ ファイルまたはログ ファイルによって使用されるストレージ コンテナーごとに、名前がコンテナーのパスに一致する SQL Server 資格情報を作成する必要があります。 その後、Windows Azure ストレージに新しいデータベースを作成できます。  
  
 このレッスンでは、次の手順を完了することを前提としています。  
  
-   Windows Azure ストレージ アカウントを入手しました。  
  
-   Windows Azure ストレージ アカウントにコンテナーを作成しました。  
  
-   読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成しました。 SAS キーも生成しました。  
  
-   ソース コンピューターで SQL Server 資格情報を作成しました。  
  
 Windows Azure 機能内の SQL Server データ ファイルを使用して Windows Azure 内でデータベースを作成するには  
  
1.  SQL Server Management Studio に接続します。  
  
2.  オブジェクト エクスプローラーで、インストールしたデータベース エンジンのインスタンスに接続します。  
  
3.  標準的なツール バーで、新しいクエリ をクリックします。  
  
4.  次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更します。 FILENAME フィールドがストレージ コンテナーにあるデータベース ファイルの URI パスを指し、先頭は https にする必要があることに注意してください。  
  
    ```  
  
    --Create a database that uses a SQL Server credential    
    CREATE DATABASE TestDB1    
    ON   
    (NAME = TestDB1_data,   
       FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf')   
     LOG ON   
    (NAME = TestDB1_log,   
        FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
    GO  
  
    ```  
  
     データベースにデータを追加します。  
  
    ```  
  
    USE TestDB1;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
5.  内部設置型 SQL Server の新しい TestDB1 を表示するには、オブジェクト エクスプローラーでデータベースの表示を更新します。  
  
6.  同様に、ストレージ アカウントに新しく作成したデータベースを表示するには、SQL Server Management Studio (SSMS) 経由でストレージ アカウントに接続します。 SQL Server Management Studio を使用して Windows Azure ストレージに接続する方法については、以下の手順に従ってください。  
  
    1.  まず、ストレージ アカウント情報を取得します。 管理ポータルにログインします。 クリックし、**ストレージ**し、ストレージ アカウントを選択します。 ストレージ アカウントを選択すると、クリックして**アクセス キーの管理**ページの下部にあります。 次のようなダイアログ ウィンドウが開きます。  
  
         ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-1.gif "SQL 14 CTP2")  
  
    2.  コピー、**ストレージ アカウント名**と**プライマリ アクセス キー**値を**Windows Azure ストレージへの接続**SSMS でのダイアログ ウィンドウです。 をクリックし、**接続**です。 これで、次のスクリーン ショットに示すように、ストレージ アカウント コンテナーについての情報が SSMS に表示されます。  
  
         ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2.gif "SQL 14 CTP2")  
  
 次のスクリーン ショットは、内部設置型環境と Windows Azure ストレージ環境の両方で新しく作成したデータベースを示しています。  
  
 ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2b.gif "SQL 14 CTP2")  
  
 **注:** コンテナー内のデータ ファイルに対するアクティブな参照がある場合は、関連付けられている SQL サーバーを削除しようとすると資格情報を失敗します。 同様に、既に BLOB の特定のデータベース ファイルにリースが設定されていて、そのデータベースを削除する場合、まず、BLOB のリースを解除する必要があります。 使用することができますのリースを中断する[Lease Blob](https://msdn.microsoft.com/library/azure/ee691972.aspx)です。  
  
 この新しい機能を使用して、CREATE DATABASE ステートメントの既定値がクラウド対応データベースになるように、SQL Server を構成できます。 言い換えれば、SQL Server Management Studio でサーバー インスタンスのプロパティに既定のデータとログの場所を設定して、データベースを作成すると常にすべてのデータベース ファイル (.mdf、.ldf) が Windows Azure ストレージにページ BLOB として作成されるようにすることができます。  
  
 SQL Server Management Studio を使用して Windows Azure ストレージにデータベースを作成するには、次の手順を実行します。  
  
1.  オブジェクト エクスプローラーで、SQL Server データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。  
  
2.  [データベース] を右クリックし、[新しいデータベース] をクリックします。  
  
3.  [新しいデータベース] ダイアログ ウィンドウで、データベース名を入力します。  
  
4.  プライマリ データ ファイルとトランザクション ログ ファイルの既定値を変更します。[データベース ファイル] グリッドで該当するセルをクリックして、新しい値を入力します。 また、ファイルの場所のパスも指定します。 パスとしては、ストレージ コンテナーの URL パスを入力します (たとえば、`https://teststorageaccnt.blob.core.windows.net/testcontainer/`)。 ファイル名としては、データベース ファイル (.mdf、.ldf) の物理ファイル名を入力します。  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-4.gif "SQL 14 CTP2")  
  
     詳細については、「 [データベースに対するデータ ファイルまたはログ ファイルの追加](databases/add-data-or-log-files-to-a-database.md)」をご覧ください。  
  
5.  その他の値は既定値のままにします。  
  
6.  [OK] をクリックします。  
  
 内部設置型 SQL Server の新しい TestDB1 を表示するには、オブジェクト エクスプローラーでデータベースの表示を更新します。 同様に、ストレージ アカウントに新しく作成したデータベースを表示するには、このレッスンの前の方で説明したように、SQL Server Management Studio (SSMS) 経由でストレージ アカウントに接続します。  
  
 **次のレッスン:**  
  
 [レッスン 5 です。&#40;オプション&#41;TDE を使用して、データベースの暗号化](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)  
  
  