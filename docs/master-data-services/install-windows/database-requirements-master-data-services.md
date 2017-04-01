---
title: "データベース要件 (マスター データ サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe731839-c5c4-4884-bb6a-644eca28bb30
caps.latest.revision: 18
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 16
---
# データベース要件 (マスター データ サービス)
  マスター データはすべて [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースに格納されます。 このデータベースをホストするコンピューターでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]  インスタンスを実行する必要があります。  
  
 ローカル コンピューターまたはリモート コンピューターで [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] データベースを作成および構成するには、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]を使用します。 環境間でデータベースを移動する場合、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web サービスと[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]を新しい場所のデータベースに関連付けることにより、新しい環境で情報を維持できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] のコンポーネントをインストールするコンピューターはすべてライセンス供与を受けている必要があります。 詳細については、使用許諾契約書 (EULA) を参照してください。  
  
## 必要条件  
 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースを作成する前に、次の要件が満たされていることを確認してください。  
  
### SQL Server のエディション  
 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースは、次のエディションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でホストできます。  
  
 
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] Enterprise (64 ビット) x64  
  
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] Developer (64 ビット) x64  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence (64 ビット) x64  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (64 ビット) x64  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer (64 ビット) x64  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Business Intelligence (64 ビット) x64  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Enterprise (64 ビット) x64 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise からのアップグレードの場合のみ)  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Developer (64 ビット) x64  
  
-   Microsoft SQL Server 2008 R2 Enterprise (64 ビット) x64  
  
-   Microsoft SQL Server 2008 R2 Developer (64 ビット) x64  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各エディションでサポートされる機能の一覧については、「[SQL Server 2016 の各エディションがサポートする機能](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)」を参照してください。  
  
### オペレーティング システム  
 サポートされている Windows オペレーティング システムおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]に関する他の要件の詳細については、「[SQL Server 2016 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)」を参照してください。  
  
### アカウントと権限  
  
|型|説明|  
|----------|-----------------|  
|ユーザー アカウント|[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]では、Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントを使用して [!INCLUDE[ssDE](../../includes/ssde-md.md)] の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続し、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースをホストできます。 このユーザー アカウントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスの **sysadmin** サーバー ロールに属している必要があります。 **sysadmin** ロールの詳細については、「[サーバー レベルのロール](../../relational-databases/security/authentication-access/server-level-roles.md)」を参照してください。|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 管理者アカウント|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースを作成する場合、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] システム管理者となるドメイン ユーザー アカウントを指定する必要があります。 このユーザーは、このデータベースに関連付けられているすべての[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションについて、すべての機能領域のすべてのモデルおよびすべてのデータを更新できます。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../../master-data-services/administrators-master-data-services.md)」を参照してください。|  
  
### データベース バックアップ  
 システムの使用率が低い時間帯にデータベース全体を毎日バックアップし、使用している環境のニーズに応じて、毎日数回、トランザクション ログをバックアップすることをお勧めします。 データベース バックアップの詳細については、「[バックアップの概要 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)」を参照してください。  
  
## 参照  
 [マスター データ サービスのインストール](../../master-data-services/install-windows/install-master-data-services.md)   
 [マスター データ サービス データベースの作成](../../master-data-services/install-windows/create-a-master-data-services-database.md)   
 [マスター データ サービス データベース](../../master-data-services/master-data-services-database.md)   
 [[マスター データ サービス データベースへの接続] ダイアログ ボックス](../Topic/Connect%20to%20a%20Master%20Data%20Services%20Database%20Dialog%20Box.md)   
 [データベースの作成ウィザード &#40;マスター データ サービス構成マネージャー&#41;](../../master-data-services/create-database-wizard-master-data-services-configuration-manager.md)  
  
  