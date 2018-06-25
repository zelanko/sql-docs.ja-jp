---
title: 'レッスン 2: Create a SQL Server Credential |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64f8805c-1ddc-4c96-a47c-22917d12e1ab
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b16012ed7ff12783e69add14cf8e51011668845e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177210"
---
# <a name="lesson-2-create-a-sql-server-credential"></a>レッスン 2: SQL Server 資格情報を作成します。
  **資格情報:** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資格情報は、SQL Server の外部にあるリソースへの接続に必要な認証情報を保存するために使用されるオブジェクトです。  ここでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]バックアップおよび復元プロセスは、Windows Azure Blob ストレージ サービスを認証する資格情報を使用します。 資格情報には、ストレージ アカウントの名前とその **アクセス キー** 値が格納されます。 作成した資格情報は、BACKUP/RESTORE ステートメントの実行時に WITH CREDENTIAL オプションで指定する必要があります。 詳細については、表示、コピー、またはストレージ アカウントを再生成する方法についての**アクセス キー**を参照してください[ストレージ アカウント アクセス キー](http://msdn.microsoft.com/library/windowsazure/hh531566.aspx)です。  
  
 資格情報の全般的な情報については、「 [資格情報](http://msdn.microsoft.com/library/ms161950.aspx)」を参照してください。  
  
 資格情報が使用されるその他の例については、「 [SQL Server エージェント プロキシの作成](http://msdn.microsoft.com/library/ms175834.aspx)」参照してください。  
  
> [!IMPORTANT]  
>  次に示す SQL Server 資格情報を作成するための要件は次の SQL Server のバックアップ プロセスに固有 ([SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md)、および[SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md))。 SQL Server では、Azure ストレージにアクセスしてバックアップの書き込みまたは読み取りを行う場合、ストレージ アカウント名とアクセス キーの情報を使用します。  Azure ストレージにデータベース ファイルを格納するための資格情報を作成する方法の詳細については、次を参照してください[レッスン 3: SQL Server 資格情報を作成します。](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="create-a-sql-server-credential"></a>SQL Server 資格情報の作成  
 SQL Server 資格情報を作成するには、次の手順を実行します。  
  
1.  SQL Server Management Studio に接続します。  
  
2.  オブジェクト エクスプローラーで、AdventureWorks2012 データベースがインストールされているデータベース エンジンのインスタンスに接続するか、このチュートリアルに使用する独自のデータベースを使用します。  
  
3.  **[標準]** ツール バーの **[新しいクエリ]** をクリックします。  
  
4.  次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更します。  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' – this is the name of the storage account you specified when creating a storage account (See Lesson 1)   
    , SECRET = '<storage account access key>' – this should be either the Primary or Secondary Access Key for the storage account (See Lesson 1)  
  
    ```  
  
     ![sql 資格情報をストレージ アカウントのマッピング](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "sql 資格情報をストレージ アカウントのマッピング")  
  
5.  T-SQL ステートメントを確認し、クリックして**Execute**です。  
  
 バックアップの概念と要件について、Windows Azure Blob ストレージ サービスの詳細については、次を参照してください。 [SQL Server Backup and Restore with Windows Azure Blob Storage Service](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)です。  
  
### <a name="next-lesson"></a>次のレッスン  
 [レッスン 3: Windows Azure Blob ストレージ サービスへのデータベースの完全バックアップの書き込み](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)です。  
  
  