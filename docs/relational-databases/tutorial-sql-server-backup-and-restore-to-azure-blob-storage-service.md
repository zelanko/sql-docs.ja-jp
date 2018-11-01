---
title: 'チュートリアル: Azure Blob Storage サービスへの SQL Server のバックアップと復元 | Microsoft Docs'
ms.custom: ''
ms.date: 04/09/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a33c2bd47bae8bede7fa71e1654627c123e7cdbc
ms.sourcegitcommit: 8dccf20d48e8db8fe136c4de6b0a0b408191586b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48874320"
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a>チュートリアル: Azure Blob Storage サービスへの SQL Server のバックアップと復元
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
このチュートリアルで、Azure Blob Storage サービスへのバックアップの書き込みと、Azure Blob Storage サービスからの復元を実行する方法について学習できます。  このチュートリアルでは、Azure BLOB コンテナーの作成方法と、ストレージ アカウントにアクセスし、Blob service へのバックアップを記述し、簡単な復元を実行するための資格情報の作成方法について説明します。
  
### <a name="prerequisites"></a>Prerequisites  
このチュートリアルを完了するには、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のバックアップと復元の概念と T-SQL 構文についての知識が必要です。 このチュートリアルを使用するには、Azure ストレージ アカウント、SQL Server Management Studio (SSMS)、SQL Server を実行しているサーバーへのアクセス権、AdventureWorks データベースが必要です。 また、BACKUP コマンドと RESTORE コマンドの実行に使用するアカウントは、**alter any credential** 権限を持つ **db_backup operator** データベース ロールに属している必要があります。 

- 無料の [Azure アカウント](https://azure.microsoft.com/offers/ms-azr-0044p/)を取得する。
- [Azure ストレージ アカウント](https://docs.microsoft.com/azure/storage/common/storage-quickstart-create-account?tabs=portal)を作成する。
- [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) をインストールする。
- [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads) をインストールする。
- [AdventureWorks2016 サンプル データベース](https://docs.microsoft.com/sql/samples/adventureworks-install-configure)をダウンロードする。
- ユーザー アカウントを [db_backupoperator](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles) のロールに割り当て、[alter any credential](https://docs.microsoft.com/sql/t-sql/statements/alter-credential-transact-sql) 権限を付与する。 


## <a name="create-azure-blob-container"></a>Azure BLOB コンテナーを作成する
コンテナーには、一連の BLOB をグループ化するコンテナーが用意されています。 すべての BLOB は 1 つのコンテナーに存在する必要があります。 アカウントには、コンテナーを無制限に含めることができますが、少なくとも 1 つのコンテナーが必要です。 コンテナーには、BLOB を無制限に格納できます。 

コンテナーを作成するには、次の手順を実行します。

1. Azure Portal を開きます。 
1. ストレージ アカウントに移動します。 
   1. ストレージ アカウントを選択し、**[Blob Services]\(Blob services\)** までスクロールします。
   1. **[BLOB]** を選択し、**[+Container]\(+コンテナー\)** を選択して新しいコンテナーを追加します。 
   1. コンテナーの名前を入力し、指定したコンテナー名をメモしておきます。 この情報は、後でこのチュートリアルの T-SQL ステートメントの URL (バックアップ ファイルのパス) 内で使用されます。 
   1. **[OK]** を選択します。 
    
    ![新しいコンテナー](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/new-container.png)


  >[!NOTE]
  >ストレージ アカウントへの認証は、パブリック コンテナーの作成を選択した場合でも、SQL Server のバックアップと復元に必要です。 コンテナーは、REST API を使用してプログラムで作成することもできます。 詳しくは、「[Create Container](https://docs.microsoft.com/rest/api/storageservices/Create-Container)」をご覧ください


## <a name="create-a-sql-server-credential"></a>SQL Server 資格情報の作成
SQL Server 資格情報は、SQL Server の外部にあるリソースへの接続に必要な認証情報を保存するために使用されるオブジェクトです。 ここでは、SQL Server のバックアップおよび復元プロセスで資格情報を使用して、Windows Azure Blob Storage サービスを認証します。 資格情報には、ストレージ アカウントの名前とその **アクセス キー** 値が格納されます。 作成した資格情報は、BACKUP/RESTORE ステートメントの実行時に WITH CREDENTIAL オプションで指定する必要があります。 資格情報について詳しくは、[資格情報](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/credentials-database-engine)に関する記事をご覧ください。 

  >[!IMPORTANT]
  >以下で説明する SQL Server 資格情報の作成要件は、SQL Server バックアップ プロセス ([SQL Server Backup to URL](backup-restore/sql-server-backup-to-url.md) および [Microsoft Azure への SQL Server マネージド バックアップ](backup-restore/sql-server-managed-backup-to-microsoft-azure.md)) に固有です。 SQL Server では、Azure ストレージにアクセスしてバックアップの書き込みまたは読み取りを行う場合、ストレージ アカウント名とアクセス キーの情報が使用されます。

### <a name="access-keys"></a>アクセス キー
Azure Portal は開いたままなので、資格情報の作成に必要なアクセス キーを保存します。 

1. Azure Portal 上で **[ストレージ アカウント]** に移動します。 
1. **[設定]** までスクロールし、**[アクセス キー]** を選択します。 
1. 後でこのチュートリアルで使用するためにキーと接続文字列の両方を保存します。 

   ![アクセス キー](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/access-keys.png)

### <a name="create-a-sql-server-credential"></a>SQL Server 資格情報の作成
保存したアクセス キーを使用して、以下の手順に従って SQL Server 資格情報を作成します。 

1. SQL Server Management Studio を使用して、SQL Server に接続します。 
1. **AdventureWorks2016** データベースを選択し、**[新しいクエリ]** ウィンドウを開きます。 
1. 次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更して実行します。 

  ```sql
  CREATE CREDENTIAL mycredential   
  WITH IDENTITY= 'msftutorialstorage', -- this is the name of the storage account you specified when creating a storage account   
  SECRET = '<storage account access key>' -- this should be either the Primary or Secondary Access Key for the storage account 
  ```
1. 次のステートメントを実行して、資格情報を作成します。 

## <a name="backup-database-to-the-windows-azure-blob-storage-service"></a>Windows Azure Blob Storage サービスへのデータベースのバックアップ
このセクションでは、T-SQL ステートメントを使用して Windows Azure Blob Storage サービスにデータベースの完全バックアップを実行します。 

1. SQL Server Management Studio を使用して、SQL Server に接続します。 
1. **AdventureWorks2016** データベースを選択し、**[新しいクエリ]** ウィンドウを開きます。 
1. 次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更します。 

 ```sql
 BACKUP DATABASE [AdventureWorks2016] 
 TO URL = 'https://msftutorialstorage.blob.core.windows.net/sql-backup/AdventureWorks2016.bak' 
 /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/ 
 WITH CREDENTIAL = 'mycredential';
 /* name of the credential you created in the previous step */ 
 GO
 ```
1. URL に AdventureWorks2016 データベースをバックアップするステートメントを実行します。 

 
## <a name="restore-database-from-windows-azure-blob-storage-service"></a>Windows Azure Blob Storage サービスからのデータベースの復元
このセクションでは、T-SQL ステートメントを使用して、データベースの完全バックアップを復元します。 

1. SQL Server Management Studio を使用して、SQL Server に接続します。 
1. **[新しいクエリ]** ウィンドウを開きます。 
1. 次の例をコピーしてクエリ ウィンドウに貼り付け、必要に応じて変更します。 

 ```sql
 RESTORE DATABASE AdventureWorks2016 
 FROM URL = 'https://msftutorialstorage.blob.core.windows.net/sql-backup/AdventureWorks2016.bak' 
 WITH CREDENTIAL = 'mycredential',
 STATS = 5 -- use this to see monitor the progress
 GO
 ``` 

## <a name="see-also"></a>参照 
[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] バックアップに Azure Blob Storage サービスを使用する場合の概念やベスト プラクティスについて、次の推奨トピックで説明しています。  
  
-   [Microsoft Azure BLOB ストレージ サービスを使用した SQL Server のバックアップと復元](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)   
-   [SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
