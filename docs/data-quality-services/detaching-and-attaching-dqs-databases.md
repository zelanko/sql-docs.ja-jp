---
title: "DQS データベースのデタッチとアタッチ | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 830e33bc-dd15-4f8e-a4ac-d8634b78fe45
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# DQS データベースのデタッチとアタッチ
  ここでは、DQS データベースをデタッチおよびアタッチする方法について説明します。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Limitations"></a> 制限事項と制約事項  
 制限事項と制約の一覧は、次を参照してください。 [データベースのデタッチおよびアタッチ & #40 です。SQL Server と #41;](../relational-databases/databases/database-detach-and-attach-sql-server.md)します。  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   DQS で実行中のアクティビティまたはプロセスがないことを確認します。 これは **[アクティビティ監視]** 画面を使用して確認できます。 この画面の操作の詳細については、「 [Monitor DQS Activities](../data-quality-services/monitor-dqs-activities.md)」を参照してください。  
  
-   [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]にログオンしているユーザーがいないことを確認します。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
  
-   DQS データベースをデタッチするには、Windows ユーザー アカウントが、SQL Server インスタンスの db_owner 固定サーバー ロールのメンバーであることが必要です。  
  
-   データベースをアタッチするには、Windows ユーザー アカウントに、CREATE DATABASE、CREATE ANY DATABASE、または ALTER ANY DATABASE の権限が必要です。  
  
-   DQS の実行中のアクティビティを終了させたり実行中のプロセスを停止させたりするには、DQS_MAIN データベースの dqs_administrator ロールが必要です。  
  
##  <a name="Detach"></a> DQS データベースのデタッチ  
 SQL Server Management Studio を使用して DQS データベースをデタッチすると、デタッチされたファイルはコンピューターに残り、同じ SQL Server インスタンスに再アタッチすることも、別のサーバーに移動して、そこにアタッチすることもできます。 DQS データベース ファイルは通常、Data Quality Services コンピューターの次の場所: C:\Program files \microsoft SQL Server\MSSQL13*。\< Instance_Name >*\MSSQL\DATA します。  
  
1.  Microsoft SQL Server Management Studio を起動し、適切な SQL Server インスタンスに接続します。  
  
2.  オブジェクト エクスプローラーで、 **[データベース]** ノードを展開します。  
  
3.  右クリックし、 **DQS_MAIN** データベースを指す **タスク**, 、] をクリックし、 **デタッチ**します。 **[データベースのデタッチ]** ダイアログ ボックスが表示されます。  
  
4.  下にあるチェック ボックスをオン、 **ドロップ** 列、およびクリック **[ok]** DQS_MAIN データベースをデタッチします。  
  
5.  DQS_PROJECTS データベースと DQS_STAGING_DATA データベースで手順 3. と 4. を繰り返し、それらをデタッチします。  
  
 Transact-SQL ステートメントで sp_detach_db ストアド プロシージャを使用して、DQS データベースをデタッチすることもできます。 TRANSACT-SQL ステートメントを使用してデータベースのデタッチの詳細については、次を参照してください。 [TRANSACT-SQL](../relational-databases/databases/detach-a-database.md#TsqlProcedure) で [データベースをデタッチ](../relational-databases/databases/detach-a-database.md)します。  
  
##  <a name="Attach"></a> DQS データベースのインポート  
 次の手順を使用して、DQS データベースを (デタッチした場所から) 同じ SQL Server インスタンスまたは [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] がインストールされている別の SQL Server インスタンスにアタッチします。  
  
1.  Microsoft SQL Server Management Studio を起動し、適切な SQL Server インスタンスに接続します。  
  
2.  オブジェクト エクスプ ローラーで右クリック **データベース**, 、クリックして **アタッチ**します。 **[データベースのデタッチ]** ダイアログ ボックスが表示されます。  
  
3.  アタッチするデータベースを指定するには、 **[追加]**をクリックします。 **[データベース ファイルの検索]** ダイアログ ボックスが表示されます。  
  
4.  データベースが存在するディスク ドライブを選択し、ディレクトリ ツリーを展開してデータベースの .mdf ファイルを選択します。 たとえば、DQS_MAIN データベースの場合は、次のようになります。  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\DQS_MAIN.mdf  
    ```  
  
5.   **データベースの詳細** (下部) ペインには、添付するファイルの名前が表示されます。 確認したり、ファイルのパス名を変更したりをクリックして、 **参照** ボタン (...)。  
  
6.  をクリックして **OK** 、DQS_MAIN データベースをアタッチします。  
  
7.  DQS_PROJECTS データベースと DQS_STAGING_DATA データベースで手順 2. ～ 6. を繰り返し、それらをアタッチします。  
  
8.  また、DQS_MAIN データベースを復元した後の次の手順で Transact-SQL ステートメントを実行する必要もあります。これを実行しない場合、Data Quality Client アプリケーションを使用して Data Quality Server に接続しようとするとエラー メッセージが表示され、接続できません。 ただし、DQS_PROJECTS データベースまたは DQS_STAGING_DATA データベースをアタッチし、DQS_MAIN をアタッチしていない場合、手順 9. と 10. を実行する必要はありません。  
  
     オブジェクト エクスプ ローラーで TRANSACT-SQL ステートメントを実行するサーバーを右クリックし、をクリックして **新しいクエリ**します。  
  
9. クエリ エディター ウィンドウで、SQL ステートメントをコピーします。  
  
    ```  
    ALTER DATABASE [DQS_MAIN] SET TRUSTWORTHY ON;  
    EXEC sp_configure 'clr enabled', 1;  
    RECONFIGURE WITH OVERRIDE  
    ALTER DATABASE [DQS_MAIN] SET ENABLE_BROKER  
    ALTER AUTHORIZATION ON DATABASE::[DQS_MAIN] TO [##MS_dqs_db_owner_login##]  
    ALTER AUTHORIZATION ON DATABASE::[DQS_PROJECTS] TO [##MS_dqs_db_owner_login##]  
  
    ```  
  
10. F5 キーを押してステートメントを実行します。 [結果] ペインを確認してステートメントが正常に実行されたことを確認します。 次のメッセージが表示されます。 `Configuration option 'clr enabled' changed from 1 to 1. Run the RECONFIGURE statement to install.`  
  
11. Data Quality Client を使用して Data Quality Server に接続し、正常に接続できるかどうかを確認します。  
  
 また、Transact-SQL ステートメントを使用して DQS データベースをアタッチすることもできます。 TRANSACT-SQL ステートメントを使用してデータベースのインポートの詳細については、次を参照してください。 [TRANSACT-SQL](../relational-databases/databases/attach-a-database.md#TsqlProcedure) で [データベースをアタッチする](../relational-databases/databases/attach-a-database.md)です。  
  
## 参照  
 [DQS データベースの管理](../data-quality-services/manage-dqs-databases.md)  
  
  