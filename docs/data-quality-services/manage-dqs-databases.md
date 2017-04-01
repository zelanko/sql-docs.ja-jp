---
title: "DQS データベースの管理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 655a67aa-d662-42f2-b982-c6217125ada8
caps.latest.revision: 14
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 14
---
# DQS データベースの管理
  ここでは、バックアップ/復元またはデタッチ/アタッチなど DQS のデータベースに対して実行できるデータベース管理アクティビティについて説明します。  
  
##  <a name="BackupRestore"></a> DQS データベースのバックアップと復元  
 SQL Server データベースのバックアップと復元は、バックアップ データベースからデータを復旧して災害時のデータの損失を防ぐためにデータベース管理者が実行する一般的な操作です。 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 主に 2 つの SQL Server データベースによって実装: DQS_MAIN および DQS_PROJECTS です。 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) データベースのバックアップと復元の手順は、他の SQL Server データベースの手順と似ています。DQS データベースのバックアップと復元に関連付けられている次の 3 つの問題があります。  
  
-   DQS データベースのバックアップと復元の操作を同期する必要があります。 同期しない場合、復元された [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] は機能しません。  
  
-   2 つの DQS データベース (DQS_MAIN および DQS_PROJECTS) には、単純なデータベース オブジェクト (テーブルやストアド プロシージャなど) だけではなく、アセンブリおよびその他の複雑なオブジェクトが含まれています。  
  
-   DQS データベースが [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] として機能するために必要な DQS データベース以外のいくつかのエンティティがあります。具体的には、2 つの SQL Server ログイン (##MS_dqs_db_owner_login## と ##MS_dqs_service_login##)、およびマスター データベースの初期化ストアド プロシージャ (DQInitDQS_MAIN) です。  
  
 SQL Server でのデータベースのバックアップと復元の詳細については、「 [Back Up and Restore of SQL Server Databases](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)」を参照してください。  
  
### DQS データベースの既定の自動拡張サイズと復旧モデル  
 DQS データベースおよびトランザクション ログが無限に拡張してハード ディスクがいっぱいになるのを防ぐためには  
  
-   DQS データベースの既定の **[自動拡張]** のサイズを 10% に設定します。  
  
-   DQS データベースの既定の復旧モデルを、 **[単純]**に設定します。 単純復旧モデルでは、トランザクションのログへの記録は最小限になり、トランザクションの完了後にログが自動的に切り捨てられて、トランザクション ログ (.ldf ファイル) の領域が解放されます。 単純復旧モデルの詳細については、次を参照してください。 [データベースの完全バックアップと #40 です。SQL Server と #41;](../relational-databases/backup-restore/full-database-backups-sql-server.md)します。  
  
> [!IMPORTANT]  
>  -   単純復旧モデルでは、ログ レコードが長い間アクティブなままになると (長く、時間のかかるトランザクションの場合など)、ログの切り捨てが遅れて、トランザクション ログがいっぱいになる可能性があります。 また、ログの切り捨てを行っても、物理ログ ファイル (.ldf ファイル) のサイズは縮小されません。 物理ログ ファイルのサイズを削減するには、ログ ファイルを圧縮する必要があります。 トランザクション ログに関する問題のトラブルシューティングについては、次を参照してください。 [トランザクション ログと #40 です。SQL Server と #41;](../relational-databases/logs/the-transaction-log-sql-server.md) または、Microsoft のサポート資料 [http://go.microsoft.com/fwlink/?LinkId=237446](http://go.microsoft.com/fwlink/?LinkId=237446)します。  
> -   DQS データベースの全体のバックアップまたは差分バックアップ、およびトランザクション ログのバックアップを定期的に実行して、データを特定の時点に復旧する必要があります。 詳細については、次を参照してください。 [データベースの完全バックアップと #40 です。SQL Server と #41;](../relational-databases/backup-restore/full-database-backups-sql-server.md)  [#40; (&)、トランザクション ログのバックアップSQL Server と #41;](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)します。  
  
##  <a name="DetachAttach"></a> DQS データベースのデタッチ/アタッチ  
 DQS データベースを同じコンピューターの別の SQL Server インスタンスに変更する、またはデータベースを移動する場合は、DQS データベースのデータ ファイルおよびトランザクション ログ ファイルをデタッチし、その後 SQL Server の同じインスタンスまたは別のインスタンスにデータベースを再度アタッチします。  
  
 前に、と実行中のデタッチとアタッチの SQL Server データベースの考慮事項の詳細については、次を参照してください。 [データベースのデタッチおよびアタッチ & #40 です。SQL Server と #41;](../relational-databases/databases/database-detach-and-attach-sql-server.md)します。  
  
## 関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|DQS データベースでのバックアップと復元の方法について説明します。|[DQS データベースのバックアップと復元](../data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|DQS データベースをデタッチおよびアタッチする方法について説明します。|[Detaching and Attaching DQS Databases](../data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## 参照  
 [DQS 管理](../data-quality-services/dqs-administration.md)  
  
  