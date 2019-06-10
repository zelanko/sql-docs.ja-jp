---
title: レプリケーション サブスクライバーと AlwaysOn 可用性グループ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/16/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover subscribers with AlwaysOn
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 0995f269-0580-43ed-b8bf-02b9ad2d7ee6
author: MashaMSFT
ms.author: mathoma
manager: jroth
ms.openlocfilehash: 0aecdc5f275d8d9f14807f57192f4d6699fa5d4c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66787918"
---
# <a name="replication-subscribers-and-always-on-availability-groups-sql-server"></a>レプリケーション サブスクライバーと AlwaysOn 可用性グループ (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  レプリケーション サブスクライバーであるデータベースを含む AlwaysOn 可用性グループがフェールオーバーすると、レプリケーション サブスクリプションが失敗することがあります。 トランザクション レプリケーションのプッシュ サブスクライバーの場合、サブスクリプションが AG リスナー名を使用して作成されていれば、フェールオーバー後にディストリビューション エージェントは自動的にレプリケーションを継続します。 トランザクション レプリケーションのプル サブスクライバーの場合、サブスクリプションが AG リスナー名を使用して作成されており、元のサブスクライバー サーバーが稼働中であれば、フェールオーバー後にディストリビューション エージェントは自動的にレプリケーションを継続します。 これは、ディストリビューション エージェントのジョブは元のサブスクライバー (AG のプライマリ レプリカ) 上でのみ作成されるためです。 マージ サブスクライバーの場合、レプリケーション管理者はサブスクリプションを再作成して、手動でサブスクライバーを再構成する必要があります。  
  
## <a name="what-is-supported"></a>サポート対象  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーションでは、パブリッシャーの自動フェールオーバー、およびトランザクション サブスクライバーの自動フェールオーバーがサポートされます。 マージ サブスクライバーを可用性グループに含めることは可能ですが、フェールオーバー後に新しいサブスクライバーを構成するには、手動アクションが必要です。 可用性グループは、Websync および SQL Server Compact のシナリオと組み合わせることはできません。  
  
## <a name="how-to-create-transactional-subscription-in-an-always-on-environment"></a>AlwaysOn 環境でトランザクション サブスクリプションを作成する方法  
 トランザクション レプリケーションの場合、サブスクライバーの可用性グループを構成およびフェールオーバーするために、次の手順を使用します。  
  
1.  サブスクリプションを作成する前に、適切な AlwaysOn 可用性グループにサブスクライバー データベースを追加します。  
  
2.  サブスクライバーの可用性グループ リスナーを、可用性グループ内のすべてのノードにリンク サーバーとして追加します。 この手順により、すべての潜在的なフェールオーバー パートナーがそのリスナーを認識し、そのリスナーに接続できるようになります。  
  
3.  以下の「 **トランザクション レプリケーションのプッシュ サブスクリプションの作成** 」セクションのスクリプトを使用して、サブスクライバーの可用性グループ リスナーの名前を使用するサブスクリプションを作成します。 フェールオーバー後、リスナー名は常に有効になるのに対し、サブスクライバーの実際のサーバー名は、新しいプライマリになった実際のノードによって異なります。  
  
    > [!NOTE]  
    >  サブスクリプションは [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプトを使用して作成する必要があります。 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]を使用して作成できません。  
  
4.  プル サブスクリプションを作成する場合:  
  
    1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]のプライマリ サブスクライバー ノードで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント ツリーを開きます。  
  
    2.  **プル ディストリビューション エージェント** ジョブを識別し、そのジョブを編集します。  
  
    3.  **[エージェントを実行します]** ジョブ ステップで、 `-Publisher` と `-Distributor` の各パラメーターを確認します。 これらのパラメーターに適切な直接サーバーと、パブリッシャーおよびディストリビューター サーバーのインスタンス名が含まれていることを確認します。  
  
    4.  `-Subscriber` パラメーターを、サブスクライバーの可用性グループ リスナーの名前に変更します。  
  
 この手順に従ってサブスクリプションを作成した場合、フェールオーバー後には何もする必要がありません。  
  
## <a name="creating-a-transactional-replication-push-subscription"></a>トランザクション レプリケーションのプッシュ サブスクリプションの作成  
  
```  
-- commands to execute at the publisher, in the publisher database:  
use [<publisher database name>]  
EXEC sp_addsubscription @publication = N'<publication name>',   
       @subscriber = N'<availability group listener name>',   
       @destination_db = N'<subscriber database name>',   
       @subscription_type = N'Push',   
       @sync_type = N'automatic', @article = N'all', @update_mode = N'read only', @subscriber_type = 0;  
GO  
  
EXEC sp_addpushsubscription_agent @publication = N'<publication name>',   
       @subscriber = N'<availability group listener name>',   
       @subscriber_db = N'<subscriber database name>',   
       @job_login = null, @job_password = null, @subscriber_security_mode = 1;  
GO  
```  
  
## <a name="to-resume-the-merge-agents-after-the-availability-group-of-the-subscriber-fails-over"></a>サブスクライバーの可用性グループがフェールオーバーした後で、マージ エージェントを再開するには  
 マージ レプリケーションでは、レプリケーション管理者が次の手順に従い、手動でサブスクライバーを再構成する必要があります。  
  
1.  **sp_subscription_cleanup** を実行して、サブスクライバー上の古いサブスクリプションを削除します。 この操作は、新しいプライマリ レプリカ (以前のセカンダリ レプリカ) で実行します。  
  
2.  新しいサブスクリプションを作成し、新しいスナップショットから開始して、サブスクリプションを再作成します。  
  
> [!NOTE]  
>  現在のプロセスはマージ レプリケーションのサブスクライバーには不便ですが、マージ レプリケーションの主なシナリオは、サブスクライバーで AlwaysOn 可用性グループを使用しない未接続のユーザー (デスクトップ、ラップトップ、携帯端末) です。  
  
  
