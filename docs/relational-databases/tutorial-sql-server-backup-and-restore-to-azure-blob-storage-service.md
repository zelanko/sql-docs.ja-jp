---
title: "チュートリアル: Azure Blob Storage サービスへの SQL Server のバックアップと復元 | Microsoft Docs"
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-query-tuning
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016 Preview
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: a59c1224d71e9c8a8626c325dbef600c19078e38
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a>チュートリアル: Azure Blob Storage サービスへの SQL Server のバックアップと復元
このチュートリアルで、Azure Blob Storage サービスへのバックアップの書き込みと、Azure Blob Storage サービスからの復元を実行する方法について学習できます。  
  
## <a name="what-you-will-learn"></a>学習する内容  
このチュートリアルでは、ストレージ アカウント、BLOB コンテナーの作成、ストレージ アカウントにアクセスするための資格情報の作成、BLOB サービスへのバックアップの書き込み、簡単な復元を実行する方法について説明します。 このチュートリアルは、次の 4 つのレッスンで構成されています。  
  
[レッスン 1: Azure ストレージ オブジェクトの作成](http://msdn.microsoft.com/library/74edd1fd-ab00-46f7-9e29-7ba3f1a446c5)  
このレッスンでは、Azure ストレージ アカウントおよび BLOB コンテナーを作成します。  
  
[レッスン 2: SQL Server 資格情報の作成](http://msdn.microsoft.com/library/64f8805c-1ddc-4c96-a47c-22917d12e1ab)  
このレッスンでは、Azure ストレージ アカウントへのアクセスに使用するセキュリティ情報を格納するための資格情報を作成します。  
  
[レッスン 3: Azure Blob Storage サービスに対するデータベースの完全バックアップの書き込み](http://msdn.microsoft.com/library/454c8296-64e9-46ed-b141-5ebfbc8a4fe2)  
このレッスンでは、T-SQL ステートメントを実行して、Azure Blob Storage サービスに AdventureWorks2012 データベースのバックアップを書き込みます。  
  
[レッスン 4: データベースの完全バックアップからの復元](http://msdn.microsoft.com/library/580f76e6-9802-4abc-9043-db6de592c733)  
このレッスンでは、T-SQL ステートメントを実行して、前のレッスンで作成したデータベース バックアップから復元します。  
  
### <a name="requirements"></a>必要条件  
このチュートリアルを完了するには、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のバックアップと復元の概念と T-SQL 構文についての知識が必要です。 このチュートリアルを使用するには、以下のシステム要件を満たしている必要があります。  
  
-   [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] インスタンス、およびインストールされた AdventureWorks2012 データベース。  
  
    SQL Server インスタンスは、オンプレミスと Azure Virtual Machine のどちらに存在してもかまいません。  
  
    AdventureWorks2012 の代わりにユーザー データベースを使用し、それに応じて TSQL コマンド構文を変更できます。  
  
-   BACKUP コマンドまたは RESTORE コマンドの実行に使用するユーザー アカウントは、**ALTER ANY CREDENTIAL** 権限を持つ **db_backup operator** データベース ロールに属している必要があります。  
  
### <a name="additional-reading"></a>その他の情報  
[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] バックアップに Azure Blob Storage サービスを使用する場合の概念やベスト プラクティスについて、次の推奨トピックで説明しています。  
  
1.  [SQL Server Backup and Restore with Microsoft Azure Blob Storage Service (Microsoft Azure Blob Storage サービスを使用した SQL Server のバックアップと復元)](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [SQL Server Backup to URL Best Practices and Troubleshooting (SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング)](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
## <a name="see-also"></a>参照  
[SQL Server Backup and Restore with Microsoft Azure Blob Storage Service (Microsoft Azure Blob Storage サービスを使用した SQL Server のバックアップと復元)](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)

