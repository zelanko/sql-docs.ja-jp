---
title: "チュートリアル: Windows Azure BLOB ストレージ サービスへの SQL Server のバックアップと復元 | Microsoft Docs"
ms.custom: ""
ms.date: "02/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-query-tuning"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016 Preview"
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# チュートリアル: Windows Azure BLOB ストレージ サービスへの SQL Server のバックアップと復元
「Windows Azure BLOB ストレージ サービスを使用した SQL Server のバックアップと復元」チュートリアルへようこそ。 このチュートリアルにより、Windows Azure BLOB ストレージ サービスへのバックアップ書き込みと Windows Azure BLOB ストレージ サービスからの復元を実行する方法について把握できます。  
  
## 学習する内容  
このチュートリアルでは、Windows ストレージ アカウント、BLOB コンテナーを作成し、ストレージ アカウントにアクセスするための資格情報の作成、BLOB サービスへのバックアップの書き込み、簡単な復元の実行を行う方法について説明します。 このチュートリアルは、次の 4 つのレッスンで構成されています。  
  
[レッスン 1: Windows Azure ストレージ オブジェクトの作成](../Topic/Lesson%201:%20Create%20Windows%20Azure%20Storage%20Objects.md)  
このレッスンでは、Windows Azure ストレージ アカウントおよび BLOB コンテナーを作成します。  
  
[レッスン 2: SQL Server 資格情報を作成します。](../Topic/Lesson%202:%20Create%20a%20SQL%20Server%20Credential.md)  
このレッスンでは、Windows Azure ストレージ アカウントへのアクセスに使用するセキュリティ情報を格納するための資格情報を作成します。  
  
[レッスン 3: Windows Azure BLOB ストレージ サービスに対するデータベースの完全バックアップの書き込み](../Topic/Lesson%203:%20Write%20a%20Full%20Database%20Backup%20to%20the%20Windows%20Azure%20Blob%20Storage%20Service.md)  
このレッスンでは、T-SQL ステートメントを実行して、Windows Azure BLOB ストレージ サービスに AdventureWorks2012 データベースのバックアップを書き込みます。  
  
[レッスン 4: データベースの完全バックアップからの復元の実行](../Topic/Lesson%204:%20Perform%20a%20Restore%20From%20a%20Full%20Database%20Backup.md)  
このレッスンでは、T-SQL ステートメントを実行して、前のレッスンで作成したデータベース バックアップから復元します。  
  
### 必要条件  
このチュートリアルを完了する必要があります理解しておく [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] バックアップし、復元の概念と T-SQL 構文。 このチュートリアルを使用するには、以下のシステム要件を満たしている必要があります。  
  
-   [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]インスタンス、およびインストールされた AdventureWorks2012 データベース。  
  
    SQL Server インスタンスは、内部設置型でも、Windows Azure バーチャル マシン内に存在してもかまいません。  
  
    AdventureWorks2012 の代わりにユーザー データベースを使用し、それに応じて TSQL コマンド構文を変更できます。  
  
-   BACKUP コマンドまたは RESTORE コマンドの発行に使用するユーザー アカウントは、**資格情報の変更**権限を持つ **db_backup operator** データベース ロールに属している必要があります。  
  
### その他の情報  
[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] バックアップに Windows Azure BLOB ストレージ サービスを使用する場合の概念やベスト プラクティスを理解するための推奨トピックを次に示します。  
  
1.  [Microsoft Azure BLOB ストレージ サービスを使用した SQL Server のバックアップと復元](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
## 参照  
[データベースおよびログをバックアップする](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md#databaselog)  
[プライマリ ファイル グループのファイル全体のバックアップを作成する](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md#filegroups)  
[データベースを復元しファイルを移動する](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md#restoredbwithmove)  
  
