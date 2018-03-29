---
title: マルチサーバー環境の作成 | Microsoft Docs
ms.custom: ''
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, multiserver environments
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- multiserver environments [SQL Server]
ms.assetid: edc2b60d-15da-40a1-8ba3-f1d473366ee6
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a32a243f03f85fcc432c3a84cf31f82cf2e70c69
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="create-a-multiserver-environment"></a>マルチサーバー環境の作成
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database マネージ インスタンスと SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

マルチサーバー管理では、マスター サーバー (MSX) 1 台と、対象サーバー (TSX) 1 台以上を設定する必要があります。 すべての対象サーバーで処理されるジョブは、まずマスター サーバーで定義されてから対象サーバーにダウンロードされます。  
  
既定では、マスター サーバーと対象サーバーの間の接続では、完全な SSL (Secure Sockets Layer) 暗号化と証明書の検証が有効になります。 詳しくは、「 [対象サーバーでの暗号化オプションの設定](../../ssms/agent/set-encryption-options-on-target-servers.md)」をご覧ください。  
  
対象サーバーが多数ある場合、他の [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 機能から多くのパフォーマンス要求を受け取る実稼動サーバー上には、マスター サーバーを定義しないでください。対象サーバーのトラフィックによって実稼動サーバーのパフォーマンスが低下する可能性があります。 また、専用のマスター サーバーにイベントを転送すると、1 つのサーバーに管理を集中することができます。 詳しくは、「 [イベントの管理](../../ssms/agent/manage-events.md)」をご覧ください。  
  
> [!NOTE]  
> マルチサーバー ジョブの処理を使用するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスのアカウントがマスター サーバーの **msdb** データベースの **TargetServersRole** ロールのメンバーでなければなりません。 マスター サーバー ウィザードを使用すると、登録処理の一環としてこのロールがサービス アカウントに自動的に追加されます。  
  
## <a name="considerations-for-multiserver-environments"></a>マルチサーバー環境に関する注意点  
  
マルチサーバー環境を作成するときは、次の点を考慮してください。  
  
-   マスター サーバーとして最新のバージョンを使用します。 現在のバージョンと以前の 2 つのバージョンがサポートされています。

-   各対象サーバーは、1 つのマスター サーバーのみに対してレポートを行います。 対象サーバーを別のマスター サーバーに参加させるには、現在のマスター サーバーからその対象サーバーの参加を解除する必要があります。  
  
-   対象サーバーの名前を変更する場合は、名前を変更する前に参加を解除し、変更を行ってからもう一度参加させる必要があります。  
  
-   マルチサーバー構成を取り消す場合は、マスター サーバーからすべての対象サーバーの参加を解除する必要があります。  
  
-   SQL Server Integration Services は、マスター サーバーのバージョンと同じバージョンまたはそれ以降のバージョンの対象サーバーのみサポートします。  
  
## <a name="related-tasks"></a>Related Tasks  
次のトピックでは、マルチサーバー環境を作成するための一般的な作業について説明します。  
  
|Description|トピック|  
|---------------|---------|  
|マスター サーバーを作成する方法について説明します。|[マスター サーバーの作成](../../ssms/agent/make-a-master-server.md)|  
|対象サーバーを作成する方法について説明します。|[対象サーバーの作成](../../ssms/agent/make-a-target-server.md)|  
|マスター サーバーに対象サーバーを参加させる方法について説明します。|[マスター サーバーへの対象サーバーの参加](../../ssms/agent/enlist-a-target-server-to-a-master-server.md)|  
|マスター サーバーから対象サーバーの参加を解除する方法について説明します。|[マスター サーバーからの対象サーバーの参加の解除](../../ssms/agent/defect-a-target-server-from-a-master-server.md)|  
|マスター サーバーから複数の対象サーバーの参加を解除する方法について説明します。|[マスター サーバーからの複数の対象サーバーの参加の解除](../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)|  
|対象サーバーの状態を確認する方法について説明します。|[sp_help_targetserver (Transact-SQL)](http://msdn.microsoft.com/en-us/f841d3bd-901a-4980-ad0b-1c6eeba3f717)<br /><br />[sp_help_targetservergroup (Transact-SQL)](http://msdn.microsoft.com/en-us/ec3a4a68-b591-431c-9518-053ede522d0c)|  
  
## <a name="see-also"></a>参照  
[プロキシを使用するマルチサーバー ジョブのトラブルシューティング](../../ssms/agent/troubleshoot-multiserver-jobs-that-use-proxies.md)  
  
