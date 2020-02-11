---
title: AlwaysOn 可用性グループ用の PowerShell コマンドレットの概要 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], PowerShell cmdlets
- Availability Groups [SQL Server], about
- PowerShell [SQL Server], cmdlets
ms.assetid: b3fef0d5-b6d7-4386-a0f0-d06c165ad4de
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4996a1026b4c85b105efc09b8381913f7a47942a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62789459"
---
# <a name="overview-of-powershell-cmdlets-for-alwayson-availability-groups-sql-server"></a>AlwaysOn 可用性グループの PowerShell コマンドレットの概要 (SQL Server)
  
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] PowerShell は、特にシステム管理用に設計されている、タスク ベースのコマンド ライン シェルとスクリプト言語です。 
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] は、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で一連の PowerShell コマンドレットを提供しており、それらを使用すると可用性グループ、可用性レプリカ、および可用性データベースの配置、管理、および監視ができます。  
  
> [!NOTE]  
>  PowerShell コマンドレットは、アクションを正常に開始した時点で完了できます。 つまり、目的の操作 (可用性グループのフェールオーバーなど) の完了を示すわけではありません。 一連の操作をスクリプト化している場合は、アクションの状態を確認し、完了するまで待機しなければならないことがあります。  
  
 このトピックでは、以下の一連のタスクのためのコマンドレットについて説明します。  
  
-   [AlwaysOn 可用性グループのためのサーバー インスタンスの構成](#ConfiguringServerInstance)  
  
-   [データベースとトランザクションログのバックアップと復元](#BnRcmdlets)  
  
-   [可用性グループの作成と管理](#DeployManageAGs)  
  
-   [可用性グループリスナーの作成と管理](#AGlisteners)  
  
-   [可用性レプリカの作成と管理](#DeployManageARs)  
  
-   [可用性データベースの追加と管理](#DeployManageDbs)  
  
-   [可用性グループのヘルスの監視](#MonitorTblshtAGs)  
  
> [!NOTE]  
>  コマンドレットを使用して[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]タスクを実行[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]する方法について説明しているオンラインブックのトピックの一覧については、「 [AlwaysOn 可用性グループ &#40;SQL Server&#41;の概要](overview-of-always-on-availability-groups-sql-server.md)」の「関連タスク」を参照してください。  
  
##  <a name="ConfiguringServerInstance"></a>AlwaysOn 可用性グループ用のサーバーインスタンスの構成  
  
|コマンドレット|[説明]|サポート対象|  
|-------------|-----------------|------------------|  
|`Disable-SqlAlwaysOn`|サーバー インスタンス上の [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 機能を無効にします。|
  `Path`、`InputObject`、または `Name` パラメーターによって指定されるサーバー インスタンス  ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] をサポートしている [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]のエディションである必要があります)。|  
|`Enable-SqlAlwaysOn`|
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 機能をサポートしている [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のインスタンス上で [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] を有効化します。 の[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]サポートの詳細については、「 [AlwaysOn 可用性グループ &#40;SQL Server&#41;の前提条件、制限事項、および推奨事項](prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] をサポートしている [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の任意のエディション。|  
|`New-SqlHadrEndPoint`|サーバー インスタンス上に新しいデータベース ミラーリング エンドポイントを作成します。 このエンドポイントは、プライマリ データベースとセカンダリ データベース間のデータ移動のために必要です。|の任意のインスタンス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|`Set-SqlHadrEndpoint`|既存のデータベース ミラーリング エンドポイントの名前、状態、認証などのプロパティを変更します。|
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] をサポートしていて、データベース ミラーリング エンドポイントが存在しないサーバー インスタンス。|  
  
##  <a name="BnRcmdlets"></a>データベースとトランザクションログのバックアップと復元  
  
|コマンドレット|[説明]|サポート対象|  
|-------------|-----------------|------------------|  
|`Backup-SqlDatabase`|データまたはログ バックアップを作成します。|任意のオンライン データベース ( [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の場合、プライマリ レプリカをホストしているサーバー インスタンス上のデータベース)|  
|`Restore-SqlDatabase`|バックアップを復元します。|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の任意のインスタンス ( [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の場合、セカンダリ レプリカをホストしているサーバー インスタンス)<br /><br /> **&#42;&#42; の重要な &#42;&#42;** セカンダリデータベースを準備するときは、すべて`-NoRecovery` `Restore-SqlDatabase`のコマンドでパラメーターを使用する必要があります。|  
  
 これらのコマンドレッドを使用してセカンダリ データベースを準備する方法の詳細については、「[可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)」を参照してください。  
  
##  <a name="DeployManageAGs"></a>可用性グループの作成と管理  
  
|コマンドレット|[説明]|サポート対象|  
|-------------|-----------------|------------------|  
|`New-SqlAvailabilityGroup`|新しい可用性グループを作成します。|プライマリ レプリカをホストするサーバー インスタンス|  
|`Remove-SqlAvailabilityGroup`|可用性グループを削除します。|HADR 対応のサーバー インスタンス|  
|`Set-SqlAvailabilityGroup`|可用性グループのプロパティを設定します。可用性グループをオンライン/オフラインにします。|プライマリ レプリカをホストするサーバー インスタンス|  
|`Switch-SqlAvailabilityGroup`|以下のいずれかの形式のフェールオーバーを開始します。<br /><br /> 可用性グループの強制フェールオーバー (データ損失の可能性あり)。<br /><br /> 可用性グループの手動フェールオーバー。|対象のセカンダリ レプリカをホストするサーバー インスタンス|  
  
##  <a name="AGlisteners"></a>可用性グループリスナーの作成と管理  
  
|コマンドレット|[説明]|サポート対象|  
|------------|-----------------|------------------|  
|`New-SqlAvailabilityGroupListener`|新しい可用性グループ リスナーを作成して、既存の可用性グループにアタッチします。|プライマリ レプリカをホストするサーバー インスタンス|  
|`Set-SqlAvailabilityGroupListener`|既存の可用性グループ リスナーのポート設定を変更します。|プライマリ レプリカをホストするサーバー インスタンス|  
|`Add-SqlAvailabilityGroupListenerStaticIp`|既存の可用性グループ リスナー構成に静的 IP アドレスを追加します。 IP アドレスには、サブネットを含む IPv4 アドレス、または IPv6 アドレスを指定できます。|プライマリ レプリカをホストするサーバー インスタンス|  
  
##  <a name="DeployManageARs"></a>可用性レプリカの作成と管理  
  
|コマンドレット|[説明]|サポート対象|  
|-------------|-----------------|------------------|  
|**New-sqlavailabilityreplica**|新しい可用性レプリカを作成します。 
  `-AsTemplate` パラメーターを使用すると、新しい可用性レプリカごとにインメモリの可用性レプリカ オブジェクトを作成できます。|プライマリ レプリカをホストするサーバー インスタンス|  
|`Join-SqlAvailabilityGroup`|セカンダリ レプリカを可用性グループに参加させます。|セカンダリ レプリカをホストするサーバー インスタンス|  
|**New-sqlavailabilityreplica**|可用性レプリカを削除します。|プライマリ レプリカをホストするサーバー インスタンス|  
|`Set-SqlAvailabilityReplica`|可用性レプリカのプロパティを設定します。|プライマリ レプリカをホストするサーバー インスタンス|  
  
##  <a name="DeployManageDbs"></a>可用性データベースの追加と管理  
  
|コマンドレット|[説明]|サポート対象|  
|-------------|-----------------|------------------|  
|**Add-sqlavailabilitydatabase**|プライマリ レプリカ上で、データベースを可用性グループに追加します。<br /><br /> セカンダリ レプリカ上で、セカンダリ データベースを可用性グループに参加させます。|可用性レプリカをホストする任意のサーバー インスタンス (レプリカがプライマリかセカンダリかで動作が異なります)|  
|**Add-sqlavailabilitydatabase**|プライマリ レプリカ上で、可用性グループからデータベースを削除します。<br /><br /> セカンダリ レプリカ上で、ローカル セカンダリ データベースをローカル セカンダリ レプリカから削除します。|可用性レプリカをホストする任意のサーバー インスタンス (レプリカがプライマリかセカンダリかで動作が異なります)|  
|`Resume-SqlAvailabilityDatabase`|中断されている可用性データベースのデータ移動を再開します。|データベースが中断されたサーバー インスタンス|  
|`Suspend-SqlAvailabilityDatabase`|可用性データベースのデータ移動を中断します。|可用性レプリカをホストする任意のサーバー インスタンス|  
  
##  <a name="MonitorTblshtAGs"></a>監視可用性グループヘルス  
 以下の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コマンドレットを使用すると、可用性グループとそのレプリカおよびデータベースの正常性を監視できます。  
  
> [!IMPORTANT]  
>  これらのコマンドレットを実行するには、CONNECT、VIEW SERVER STATE、および VIEW ANY DEFINITION 権限が必要です。  
  
|コマンドレット|[説明]|サポート対象|  
|------------|-----------------|------------------|  
|`Test-SqlAvailabilityGroup`|SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、可用性グループの正常性を査定します。|可用性レプリカをホストする任意のサーバー インスタンス。*|  
|`Test-SqlAvailabilityReplica`|SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、可用性レプリカの正常性を査定します。|可用性レプリカをホストする任意のサーバー インスタンス。*|  
|`Test-SqlDatabaseReplicaState`|SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、参加しているすべての可用性レプリカ上の可用性データベースの正常性を査定します。|可用性レプリカをホストする任意のサーバー インスタンス。*|  
  
 * 可用性グループ内のすべての可用性レプリカについての情報を表示するには、プライマリ レプリカをホストするサーバー インスタンスを使用してください。  
  
 詳細については、「 [AlwaysOn ポリシーを使用して可用性グループの正常性を表示する」 &#40;SQL Server&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)を参照してください。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
  
