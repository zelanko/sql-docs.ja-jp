---
title: "サブスクライバーのセキュリティ保護 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サブスクリプション [SQL Server レプリケーション]、セキュリティ"
  - "サブスクライバ― [SQL Server レプリケーション]、セキュリティ"
  - "セキュリティ [SQL Server レプリケーション]、サブスクライバー"
ms.assetid: c8f0d62a-8b5d-4a21-9aec-223da52bb708
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# サブスクライバーのセキュリティ保護
  マージ エージェントとディストリビューション エージェントはサブスクライバーに接続します。 これらの接続は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインまたは Windows ログインのコンテキスト下で行われます。 最低限必要な権限のみを与え、かつ、すべてのパスワードの格納を保護するという原則に従って、これらの各エージェントに対し適切なログインを提供することが重要です。 各エージェントに必要な権限については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../../relational-databases/replication/security/replication-agent-security-model.md)します。  
  
## ディストリビューション エージェント  
 サブスクリプションごとに 1 つのディストリビューション エージェント (パブリケーションの新規作成ウィザードで既定で作成される独立したエージェント)、またはパブリケーション データベースとサブスクリプション データベースのペアごとに 1 つのディストリビューション エージェント (共有エージェント) があります。 T  
  
 プッシュ サブスクリプションの接続情報を指定するを参照してください。 [プッシュ サブスクリプションを作成](../../../relational-databases/replication/create-a-push-subscription.md)します。  
  
 プル サブスクリプションの接続情報を指定するを参照してください [プル サブスクリプションを作成します。。](../../../relational-databases/replication/create-a-pull-subscription.md)  
  
## [マージ エージェント]  
 マージ サブスクリプションごとにマージ エージェントがあり、パブリッシャーとサブスクライバーの両方に接続し、更新します。  
  
 プッシュ サブスクリプションの接続情報を指定するを参照してください。 [プッシュ サブスクリプションを作成](../../../relational-databases/replication/create-a-push-subscription.md)します。  
  
 プル サブスクリプションの接続情報を指定するを参照してください。 [プル サブスクリプションを作成](../../../relational-databases/replication/create-a-pull-subscription.md)します。  
  
## 即時更新サブスクリプション  
 即時更新サブスクリプションを構成する場合は、パブリッシャーに接続する際のアカウントをサブスクライバーで指定します。 接続はサブスクライバーで起動されるトリガーによって使用され、サブスクライバーに変更を反映します。 接続の種類として、3 つのオプションがあります。  
  
-   レプリケーションが作成するリンク サーバー。構成時に指定した資格情報を使用して接続が行われます。  
  
-   レプリケーションによって作成されるリンク サーバー。サブスクライバーで変更を行うユーザーの資格情報を使用して接続を行います。  
  
-   定義済みのリンク サーバーまたはリモート サーバー。  
  
> [!IMPORTANT]  
>  接続情報を指定するには、ストアド プロシージャを使用して [sp_link_publication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md)します。 使用することも、 **更新可能なサブスクリプション用のログイン** を呼び出すの新しいサブスクリプション ウィザードのページ **sp_link_publication**します。 特定の条件下で、サブスクライバーが [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) 以降を実行し、パブリッシャーがそれよりも前のバージョンを実行している場合、このストアド プロシージャは失敗する可能性があります。 このシナリオでストアド プロシージャが失敗する場合は、パブリッシャーを [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1 以降にアップグレードしてください。  
  
 詳細については、次を参照してください。 [トランザクション パブリケーションに対する更新可能なサブスクリプションを作成する](../../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md) と [ビューとレプリケーションのセキュリティ設定の変更](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)します。  
  
> [!IMPORTANT]  
>  接続用に指定するアカウントには、レプリケーションによってパブリケーション データベース内に作成されるビューのデータの挿入、更新、および削除だけを実行できる権限を与える必要があります。それ以外の権限は与えないでください。 名前の形式は、パブリケーション データベース内のビューに対するアクセス許可を与える **syncobj _***\< HexadecimalNumber>* サブスクライバーごとに構成したアカウントにします。  
  
## キュー更新サブスクリプション  
 キュー更新サブスクリプションを構成する際には、セキュリティに関して、以下の 2 点に注意してください。  
  
-   各ディストリビューターには、キュー リーダー エージェントが 1 つしかありません。 ディストリビューターごとに、キュー更新サブスクリプションを有効にしたパブリケーションを 1 つだけ構成することをお勧めします。  
  
-   キュー リーダー エージェントは、ディストリビューター、パブリッシャー、および各サブスクライバーに接続します。  
  
    -   エージェントの実行とディストリビューターへの接続で使用するアカウントは、エージェントを作成する際に指定します (パブリケーションの新規作成ウィザードを使用する場合は、更新サブスクリプションを有効にしたパブリケーションを作成する際にエージェントが作成されます)。  
  
    -   エージェントがパブリッシャーに接続する際に使用するアカウントは、パブリッシャーのディストリビューションを構成する際に指定します。 エージェントの実行で使用する Windows アカウントか [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アカウントを指定してください。  
  
    -   エージェントがサブスクライバーに接続する際に使用するアカウントは、サブスクリプションを作成する際に指定します。  
  
    > [!IMPORTANT]  
    >  サブスクライバーへの接続には [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用し、各サブスクライバーへの接続にはそれぞれ異なるアカウントを指定してください。 プル サブスクリプションを使用する場合は、レプリケーションによって、常に Windows 認証を使用するように接続が設定されます (プル サブスクリプションでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証が必要なサブスクライバーのメタデータにレプリケーションからアクセスすることはできません)。 その場合、サブスクリプションを構成した後に、接続で [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用するように変更してください。  
  
     詳細については、次を参照してください。 方法: トランザクション パブリケーション (SQL Server Management Studio) に更新可能なサブスクリプションを作成および [ビューとレプリケーションのセキュリティ設定を変更](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)します。  
  
## 参照  
 [データベース エンジンと #40; への暗号化接続を有効にします。SQL Server 構成マネージャーと #41 です。](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)   
 [レプリケーション セキュリティの推奨事項](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [セキュリティと保護と #40 です。レプリケーションと #41 です。](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  