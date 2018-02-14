---
title: "チュートリアル: Azure Blob Storage サービスと SQL Server 2016 データベースの使用 | Microsoft Docs"
ms.custom: 
ms.date: 01/07/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 26c6376594efc1b34e50f2c058578387b6f8b7f0
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="tutorial-use-azure-blob-storage-service-with-sql-server-2016"></a>チュートリアル: Azure Blob Storage サービスと SQL Server 2016 データベースの使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Microsoft Azure Blob Storage サービスでの SQL Server 2016 の使用に関するチュートリアルへようこそ。 このチュートリアルは、Microsoft Azure Blob Storage サービスを SQL Server データ ファイルや SQL Server バックアップに使用する方法を理解するのに役立ちます。  
  
SQL Server による Microsoft Azure Blob Storage サービスの統合のサポートは、SQL Server 2012 Service Pack 1 CU2 の拡張機能として開始され、SQL Server 2014 および SQL Server 2016 でさらに強化されました。 この機能の概要と使用した場合利点については、「 [Microsoft Azure 内の SQL Server データ ファイル](../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md)」を参照してください。 ライブ デモについては、 [特定の時点での復元に関するデモ](https://channel9.msdn.com/Blogs/Windows-Azure/File-Snapshot-Backups-Demo)を参照してください。  
  
  
**ダウンロード**<br /><br />**>>**  [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]をダウンロードするには、  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**にアクセスしてください。<br /><br />**>>**  Azure アカウントをすでにお持ちですか?  すでにお持ちの場合は、 **[こちら](https://azure.microsoft.com/en-us/services/virtual-machines/sql-server/)** にアクセスして、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] がインストール済みの仮想マシンをすぐにご利用いただけます。  
  
## <a name="what-you-will-learn"></a>学習する内容  
このチュートリアルでは、複数のレッスンに分けて、Microsoft Azure Blob Storage サービスで SQL Server データ ファイルを使用する方法を説明します。 各レッスンでは特定のタスクに重点を置いており、レッスンは順番に完了する必要があります。 まず、格納済みアクセス ポリシーと Shared Access Signature で Blob ストレージに新しいコンテナーを作成する方法を学習します。 次に、SQL Server を Azure Blob Storage と統合するための SQL Server 資格情報を作成する方法を学習します。 さらに、Blob ストレージにデータベースをバックアップし、Azure の仮想マシンに復元します。 SQL Server 2016 のファイル スナップショットのトランザクション ログ バックアップを使用して、特定の時点、または新しいデータベースに復元することができます。 最後に、このチュートリアルでは、ファイル スナップショットのバックアップについて理解し、使用できるようにするために、メタ データ システムのストアド プロシージャと関数の使用方法を紹介します。  
  
この記事では、次のことを前提としています。  
  
-   SQL Server 2016 のオンプレミス インスタンスと AdventureWorks2014 のコピーがインストールされている。  
  
-   Azure ストレージ アカウントを取得している。  
  
-   少なくとも 1 つの Azure 仮想マシンに SQL Server 2016 がインストールされ、この仮想マシンを「[Azure ポータルでの SQL Server 仮想マシンのプロビジョニング](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-provision-sql-server/)」に従ってプロビジョニングしている。 オプションとして、「[レッスン 8: ログ バックアップから新しいデータベースとして復元する](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)」のシナリオでは、2 つ目の仮想マシンを使用できます。  
  
このチュートリアルは、9 つのレッスンに分かれており、順番に完了する必要があります。  
  
**[レッスン 1: Azure コンテナーに格納済みアクセス ポリシーと Shared Access Signature を作成する](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)**  
このレッスンでは、新しい Blob コンテナーに対するポリシーを作成し、SQL Server 資格情報の作成に使用する Shared Access Signature を生成します。  
  
**[レッスン 2: Shared Access Signature を使用して SQL Server 資格情報を作成する](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**  
このレッスンでは、SAS キーを使用して、Microsoft Azure ストレージ アカウントへのアクセスに使用するセキュリティ情報を格納するための資格情報を作成します。  
  
**[レッスン 3: URL へのデータベースのバックアップ](../relational-databases/lesson-3-database-backup-to-url.md)**  
このレッスンでは、Microsoft Azure Blob ストレージに、オンプレミス データベースをバックアップします。  
  
**[レッスン 4: URL から仮想マシンにデータベースを復元する](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**  
このレッスンでは Windows Azure Blob ストレージから Azure 仮想マシンにデータベースを復元します。  
  
**[レッスン 5: ファイル スナップショット バックアップを使用してデータベースをバックアップする](../relational-databases/lesson-5-backup-database-using-file-snapshot-backup.md)**  
このレッスンでは、ファイル スナップショット バックアップを使用してデータベースをバックアップし、ファイル スナップショットのメタデータを表示します。  
  
**[レッスン 6: ファイル スナップショット バックアップを使用してアクティビティを生成し、ログをバックアップする](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**  
このレッスンでは、ファイル スナップショット バックアップを使用して、データベース内のアクティビティを生成し、いくつかのログ バックアップを実行します。また、ファイル スナップショットのメタデータを表示します。  
  
**[レッスン 7: 特定の時点にデータベースを復元する](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**  
このレッスンでは、2 つのファイル スナップショット ログのバックアップを使用して、特定の時点にデータベースを復元します。  
  
**[レッスン 8: ログ バックアップから新しいデータベースとして復元する](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)**  
このレッスンでは、ファイル スナップショットのログ バックアップから別の仮想マシン上の新しいデータベースに復元します。  
  
**[レッスン 9: バックアップ セットとファイル スナップショット バックアップを管理する](../relational-databases/lesson-9-manage-backup-sets-and-file-snapshot-backups.md)**  
このレッスンでは、不要なバックアップ セットを削除し、孤立したファイル スナップショット バックアップを (必要に応じて) 削除する方法について説明します。  
  
## <a name="did-this-article-help-you-were-listening"></a>この記事は役に立ちましたか? フィードバックをお待ちしております。  
どのような情報をお探しでしたか? お探しの情報は見つかりましたか? コンテンツ改善のため、フィードバックをお待ちしています。 [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Tutorial:%20Using%20the%20Microsoft%20Azure%20Blob%20storage%20service%20with%20SQL%20Server%202016%20databases%20page) にコメントをお送りください  
  
## <a name="see-also"></a>参照  
[Microsoft Azure 内の SQL Server データ ファイル](../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md)  
[Azure でのデータベース ファイルのファイル スナップショット バックアップ](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)  
[SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md)  
  
  
  

