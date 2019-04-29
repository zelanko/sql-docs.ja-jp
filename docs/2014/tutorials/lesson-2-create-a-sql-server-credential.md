---
title: レッスン 2:SQL Server 資格情報の作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 64f8805c-1ddc-4c96-a47c-22917d12e1ab
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: fbea11b0500c075105bff885cdb1cd8264b320d6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62931636"
---
# <a name="lesson-2-create-a-sql-server-credential"></a>レッスン 2:SQL Server 資格情報の作成
  **資格情報:**[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資格情報は、SQL Server の外部にあるリソースへの接続に必要な認証情報を保存するために使用されるオブジェクトです。  ここでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のバックアップおよび復元プロセスで資格情報を使用して、Windows Azure BLOB ストレージ サービスを認証します。 資格情報には、ストレージ アカウントの名前とその **アクセス キー** 値が格納されます。 作成した資格情報は、BACKUP/RESTORE ステートメントの実行時に WITH CREDENTIAL オプションで指定する必要があります。 詳細については、表示、コピー、またはストレージ アカウントを再生成する方法についての**アクセス キー**を参照してください[ストレージ アカウント アクセス キー](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx)します。  
  
 資格情報の全般的な情報については、「 [資格情報](../relational-databases/security/authentication-access/credentials-database-engine.md)」を参照してください。  
  
 資格情報が使用されるその他の例については、「 [SQL Server エージェント プロキシの作成](../ssms/agent/create-a-sql-server-agent-proxy.md)」参照してください。  
  
> [!IMPORTANT]  
>  次に示す SQL Server 資格情報を作成するための要件は次の SQL Server のバックアップ プロセスに固有 ([SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md)、および[SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md))。 SQL Server では、Azure ストレージにアクセスしてバックアップの書き込みまたは読み取りを行う場合、ストレージ アカウント名とアクセス キーの情報を使用します。  Azure storage にデータベース ファイルを格納するための資格情報を作成する方法の詳細については、次を参照してください。[レッスン 3。SQL Server 資格情報を作成します。](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="create-a-sql-server-credential"></a>SQL Server 資格情報の作成  
 SQL Server 資格情報を作成するには、次の手順を実行します。  
  
1.  SQL Server Management Studio に接続します。  
  
2.  オブジェクト エクスプローラーで、AdventureWorks2012 データベースがインストールされているデータベース エンジンのインスタンスに接続するか、このチュートリアルに使用する独自のデータベースを使用します。  
  
3.  **[標準]** ツール バーの **[新しいクエリ]** をクリックします。  
  
4.  次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更します。  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account (See Lesson 1)   
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account (See Lesson 1)  
  
    ```  
  
     ![sql 資格情報をストレージ アカウントのマッピング](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "sql 資格情報をストレージ アカウントのマッピング")  
  
5.  T-SQL ステートメントを確認し、クリックして**Execute**します。  
  
 バックアップの概念と要件の Windows Azure Blob ストレージ サービスの詳細については、次を参照してください。 [SQL Server Backup and Restore with Windows Azure Blob ストレージ サービス](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)します。  
  
### <a name="next-lesson"></a>次のレッスン  
 [レッスン 3:Windows Azure Blob ストレージ サービスに対するデータベースの完全バックアップの書き込み](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)します。  
  
  
