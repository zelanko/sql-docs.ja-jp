---
title: "DQS データベースのバックアップと復元 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3091f62-2234-4a80-a615-cf14c2a1da85
caps.latest.revision: 12
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 12
---
# DQS データベースのバックアップと復元
  このトピックでは、DQS データベースのバックアップと復元を行う方法について説明します。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   DQS サーバーのインストール中に入力したデータベース マスター キーのパスワードを知っている必要があります。  
  
-   DQS で実行中のアクティビティまたはプロセスがないことを確認します。 これは **[アクティビティ監視]** 画面を使用して確認できます。 この画面の操作の詳細については、「 [Monitor DQS Activities](../data-quality-services/monitor-dqs-activities.md)」を参照してください。  
  
-   DQS サーバーにログオンしているユーザーがないことを確認します。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
  
-   バックアップおよび復元操作を実行するには、使用する Windows ユーザー アカウントが、SQL Server インスタンスの sysadmin 固定サーバー ロールのメンバーであることが必要です。  
  
-   DQS の実行中のアクティビティを終了させたり実行中のプロセスを停止させたりするには、DQS_MAIN データベースの dqs_administrator ロールが必要です。  
  
##  <a name="BackupRestore"></a> DQS データベースのバックアップと復元  
  
1.  Microsoft SQL Server Management Studio を起動し、適切な SQL Server インスタンスに接続します。  
  
2.  オブジェクト エクスプローラーで、 **[データベース]** ノードを展開します。  
  
3.  DQS_STAGING_DATA データベースをバックアップします。 SQL Server データベースのバックアップの詳しい手順については、「 [#40; データベースの完全バックアップする (& r)SQL Server と #41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)します。  
  
4.  DQS_PROJECTS データベースをバックアップします。  
  
5.  DQS_MAIN データベースをバックアップします。  
  
6.  SQL Server の現在のインスタンスから切断し、データベースを復元する SQL Server インスタンスに接続します。  
  
7.  DQS_MAIN データベースを復元します。 SQL Server データベースを復元する手順の詳細については、次を参照してください。 [復元、データベースのバックアップを使用して SSMS](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)します。  
  
8.  DQS_PROJECTS データベースを復元します。  
  
9. DQS_STAGING_DATA データベースを復元します。  
  
10. オブジェクト エクスプ ローラーで、サーバーを右クリックし、をクリックして **新しいクエリ**します。  
  
11. クエリ エディター ウィンドウで次の SQL ステートメントをコピーして置き換える *\< パスワード>* データベース マスター_キーの DQS のインストール中に指定したパスワードを使用します。  
  
    ```  
    USE [DQS_MAIN]  
    GO  
    EXECUTE [internal_core].[RestoreDQDatabases] '<PASSWORD>'  
    GO  
  
    ```  
  
12. F5 キーを押してステートメントを実行します。 **[結果]** ペインを確認してステートメントが正常に実行されたことを確認します。  
  
## 参照  
 [DQS データベースの管理](../data-quality-services/manage-dqs-databases.md)  
  
  