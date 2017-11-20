---
title: "Always On 可用性グループの PowerShell コマンドレットの概要 (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 08/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], PowerShell cmdlets
- Availability Groups [SQL Server], about
- PowerShell [SQL Server], cmdlets
ms.assetid: b3fef0d5-b6d7-4386-a0f0-d06c165ad4de
caps.latest.revision: 36
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: daec226de4b93ae00997c07e25ba84352c5258e4
ms.openlocfilehash: c9b62d5874c2fbe00a1a9508a865f866578ef1db
ms.contentlocale: ja-jp
ms.lasthandoff: 08/31/2017

---
# <a name="overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server"></a>Always On 可用性グループの PowerShell コマンドレットの概要 (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] PowerShell は、特にシステム管理用に設計されている、タスク ベースのコマンド ライン シェルとスクリプト言語です。 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] は、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で一連の PowerShell コマンドレットを提供しており、それらを使用すると可用性グループ、可用性レプリカ、および可用性データベースの配置、管理、および監視ができます。  
  
> [!NOTE]  
>  PowerShell コマンドレットは、アクションを正常に開始した時点で完了できます。 つまり、目的の操作 (可用性グループのフェールオーバーなど) の完了を示すわけではありません。 一連の操作をスクリプト化している場合は、アクションの状態を確認し、完了するまで待機しなければならないことがあります。  
  
 このトピックでは、以下の一連のタスクのためのコマンドレットについて説明します。  
  
-   [Always On 可用性グループのためのサーバー インスタンスの構成](#ConfiguringServerInstance)  
  
-   [データベースおよびトランザクション ログのバックアップと復元](#BnRcmdlets)  
  
-   [可用性グループの作成と管理](#DeployManageAGs)  
  
-   [可用性グループ リスナーの作成と管理](#AGlisteners)  
  
-   [可用性レプリカの作成と管理](#DeployManageARs)  
  
-   [可用性データベースの追加と管理](#DeployManageDbs)  
  
-   [可用性グループの正常性の監視](#MonitorTblshtAGs)  
  
> [!NOTE]  
>  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]のタスクを実行するコマンドレットの使用方法を説明している [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] オンライン ブックのトピックの一覧については、「[Always On 可用性グループ &#40;SQL Server&#41 の概要](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)」の「関連タスク」を参照してください。  
  
##  <a name="ConfiguringServerInstance"></a> Configuring a Server Instance for Always On Availability Groups  
  
|コマンドレット|説明|サポート対象|  
|-------------|-----------------|------------------|  
|**Disable-SqlAlwaysOn**|サーバー インスタンス上の [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 機能を無効にします。|**Path**、 **InputObject**、または **Name** パラメーターによって指定されるサーバー インスタンス。 ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] をサポートしている [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]のエディションである必要があります)。|  
|**Enable-SqlAlwaysOn**|[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 機能をサポートしている [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のインスタンス上で [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] を有効化します。 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のサポートの詳細については、「[Always On 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] をサポートしている [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の任意のエディション。|  
|**New-SqlHadrEndPoint**|サーバー インスタンス上に新しいデータベース ミラーリング エンドポイントを作成します。 このエンドポイントは、プライマリ データベースとセカンダリ データベース間のデータ移動のために必要です。|の任意のインスタンス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|**Set-SqlHadrEndpoint**|既存のデータベース ミラーリング エンドポイントの名前、状態、認証などのプロパティを変更します。|[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] をサポートしていて、データベース ミラーリング エンドポイントが存在しないサーバー インスタンス。|  
  
##  <a name="BnRcmdlets"></a> Backing Up and Restoring Databases and Transaction Logs  
  
|コマンドレット|説明|サポート対象|  
|-------------|-----------------|------------------|  
|**Backup-SqlDatabase**|データまたはログ バックアップを作成します。|任意のオンライン データベース ( [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の場合、プライマリ レプリカをホストしているサーバー インスタンス上のデータベース)|  
|**Restore-SqlDatabase**|バックアップを復元します。|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の任意のインスタンス ( [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の場合、セカンダリ レプリカをホストしているサーバー インスタンス)<br /><br /> **\*\* 重要 \*\*** セカンダリ データベースを準備している場合は、すべての **Restore-SqlDatabase** コマンドで **-NoRecovery** パラメーターを使用する必要があります。|  
  
 これらのコマンドレッドを使用してセカンダリ データベースを準備する方法の詳細については、「[可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)」を参照してください。  
  
##  <a name="DeployManageAGs"></a> Creating and Managing an Availability Group  
  
|コマンドレット|説明|サポート対象|  
|-------------|-----------------|------------------|  
|**New-SqlAvailabilityGroup**|新しい可用性グループを作成します。|プライマリ レプリカをホストするサーバー インスタンス|  
|**Remove-SqlAvailabilityGroup**|可用性グループを削除します。|HADR 対応のサーバー インスタンス|  
|**Set-SqlAvailabilityGroup**|可用性グループのプロパティを設定します。可用性グループをオンライン/オフラインにします。|プライマリ レプリカをホストするサーバー インスタンス|  
|**Switch-SqlAvailabilityGroup**|以下のいずれかの形式のフェールオーバーを開始します。<br /><br /> 可用性グループの強制フェールオーバー (データ損失の可能性あり)。<br /><br /> 可用性グループの手動フェールオーバー。|対象のセカンダリ レプリカをホストするサーバー インスタンス|  
  
##  <a name="AGlisteners"></a> Creating and Managing an Availability Group Listener  
  
|コマンドレット|説明|サポート対象|  
|------------|-----------------|------------------|  
|**New-SqlAvailabilityGroupListener**|新しい可用性グループ リスナーを作成して、既存の可用性グループにアタッチします。|プライマリ レプリカをホストするサーバー インスタンス|  
|**Set-SqlAvailabilityGroupListener**|既存の可用性グループ リスナーのポート設定を変更します。|プライマリ レプリカをホストするサーバー インスタンス|  
|**Add-SqlAvailabilityGroupListenerStaticIp**|既存の可用性グループ リスナー構成に静的 IP アドレスを追加します。 IP アドレスには、サブネットを含む IPv4 アドレス、または IPv6 アドレスを指定できます。|プライマリ レプリカをホストするサーバー インスタンス|  
  
##  <a name="DeployManageARs"></a> Creating and Managing an Availability Replica  
  
|コマンドレット|説明|サポート対象|  
|-------------|-----------------|------------------|  
|**New-SqlAvailabilityReplica**|新しい可用性レプリカを作成します。 **-AsTemplate** パラメーターを使用すると、新しい可用性レプリカごとにインメモリの可用性レプリカ オブジェクトを作成できます。|プライマリ レプリカをホストするサーバー インスタンス|  
|**Join-SqlAvailabilityGroup**|セカンダリ レプリカを可用性グループに参加させます。|セカンダリ レプリカをホストするサーバー インスタンス|  
|**Remove-SqlAvailabilityReplica**|可用性レプリカを削除します。|プライマリ レプリカをホストするサーバー インスタンス|  
|**Set-SqlAvailabilityReplica**|可用性レプリカのプロパティを設定します。|プライマリ レプリカをホストするサーバー インスタンス|  
  
##  <a name="DeployManageDbs"></a> Adding and Managing an Availability Database  
  
|コマンドレット|説明|サポート対象|  
|-------------|-----------------|------------------|  
|**Add-SqlAvailabilityDatabase**|プライマリ レプリカ上で、データベースを可用性グループに追加します。<br /><br /> セカンダリ レプリカ上で、セカンダリ データベースを可用性グループに参加させます。|可用性レプリカをホストする任意のサーバー インスタンス (レプリカがプライマリかセカンダリかで動作が異なります)|  
|**Remove-SqlAvailabilityDatabase**|プライマリ レプリカ上で、可用性グループからデータベースを削除します。<br /><br /> セカンダリ レプリカ上で、ローカル セカンダリ データベースをローカル セカンダリ レプリカから削除します。|可用性レプリカをホストする任意のサーバー インスタンス (レプリカがプライマリかセカンダリかで動作が異なります)|  
|**Resume-SqlAvailabilityDatabase**|中断されている可用性データベースのデータ移動を再開します。|データベースが中断されたサーバー インスタンス|  
|**Suspend-SqlAvailabilityDatabase**|可用性データベースのデータ移動を中断します。|可用性レプリカをホストする任意のサーバー インスタンス|  
  
##  <a name="MonitorTblshtAGs"></a> Monitoring Availability Group Health  
 以下の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コマンドレットを使用すると、可用性グループとそのレプリカおよびデータベースの正常性を監視できます。  
  
> [!IMPORTANT]  
>  これらのコマンドレットを実行するには、CONNECT、VIEW SERVER STATE、および VIEW ANY DEFINITION 権限が必要です。  
  
|コマンドレット|説明|サポート対象|  
|------------|-----------------|------------------|  
|**Test-SqlAvailabilityGroup**|SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、可用性グループの正常性を査定します。|可用性レプリカをホストする任意のサーバー インスタンス。*|  
|**Test-SqlAvailabilityReplica**|SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、可用性レプリカの正常性を査定します。|可用性レプリカをホストする任意のサーバー インスタンス。*|  
|**Test-SqlDatabaseReplicaState**|SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、参加しているすべての可用性レプリカ上の可用性データベースの正常性を査定します。|可用性レプリカをホストする任意のサーバー インスタンス。*|  
  
 * 可用性グループ内のすべての可用性レプリカについての情報を表示するには、プライマリ レプリカをホストするサーバー インスタンスを使用してください。  
  
 詳細については、「[Always On ポリシーを使用した可用性グループの正常性の確認 &#40;SQL Server&#41](../../../database-engine/availability-groups/windows/use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Always On 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [SQL Server PowerShell のヘルプの参照](../../../relational-databases/scripting/get-help-sql-server-powershell.md)  
  
  

