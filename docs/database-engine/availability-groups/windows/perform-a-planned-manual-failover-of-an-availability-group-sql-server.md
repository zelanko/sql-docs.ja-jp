---
title: "可用性グループの計画的な手動フェールオーバーの実行 (SQLServer) | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.availabilitygroup.manualfailover.f1
helpviewer_keywords:
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 419f655d-3f9a-4e7d-90b9-f0bab47b3178
caps.latest.revision: 36
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5017d65bb6324f7137c4b5a2a2e0e59b95829748
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="perform-a-planned-manual-failover-of-an-availability-group-sql-server"></a>可用性グループの計画的な手動フェールオーバーの実行 (SQL Server)
  このトピックでは、 *の*、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、または PowerShell を使用して、AlwaysOn 可用性グループ上でデータを失わずに手動フェールオーバー ( [!INCLUDE[tsql](../../../includes/tsql-md.md)]計画的な手動フェールオーバー [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]) を実行する方法について説明します。 可用性グループは、可用性レプリカのレベルでフェールオーバーします。 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] フェールオーバーのような計画的な手動フェールオーバーでは、セカンダリ レプリカはプライマリ ロールに移行し、同時に、それまでのプライマリ レプリカはセカンダリ ロールに移行します。  
  
 計画的な手動フェールオーバーは、プライマリ レプリカおよびターゲット セカンダリ レプリカが同期コミット モードで動作していて、現在同期されている場合にのみサポートされます。この場合、ターゲット セカンダリ レプリカ上の可用性グループに参加しているセカンダリ データベース内のすべてのデータが維持されます。 元のプライマリ レプリカがセカンダリ ロールに移行すると、そのデータベースはセカンダリ データベースになり、新しいプライマリ データベースとの同期が開始されます。 すべてが SYNCHRONIZED 状態に移行した後は、新しいセカンダリ レプリカが、将来の計画的な手動フェールオーバーのターゲットとして機能できるようになります。  
  
> [!NOTE]  
>  セカンダリ レプリカとプライマリ レプリカの両方に対して自動フェールオーバー モードを構成し、セカンダリ レプリカを同期すると、自動フェールオーバーのターゲットとしても機能できるようになります。 詳細については、「 [可用性モード &#40;AlwaysOn 可用性グループ&#41;](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md)、または PowerShell を使用して、AlwaysOn 可用性グループ上で計画的な手動フェールオーバーまたは強制手動フェールオーバー (強制フェールオーバー) を実行する方法について説明します。  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [前提条件と制限](#Prerequisites)  
  
     [セキュリティ](#Security)  
  
-   **可用性グループで手動フェールオーバーを行う方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **補足情報:**  [可用性グループの手動フェールオーバー後](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   フェールオーバー コマンドは、ターゲットのセカンダリ レプリカがコマンドを受け入れた直後に戻ります。 ただし、データベースの復旧は、可用性グループがフェールオーバーを完了した後に非同期で行われます。  
  
-   フェールオーバー時に、可用性グループ内のデータベース間の一貫性が維持されない場合があります。  
  
    > [!NOTE]  
    >  複数のデータベースにまたがるトランザクションと分散トランザクションのサポートは、SQL Server とオペレーティング システムのバージョンによって異なります。 詳細については、「[Always On 可用性グループとデータベース ミラーリングでの複数データベースにまたがるトランザクションと分散トランザクション &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)」を参照してください。  
  
###  <a name="Prerequisites"></a> 前提条件と制限  
  
-   ターゲットのセカンダリ レプリカとプライマリ レプリカは、両方とも同期コミット可用性モードで実行されている必要があります。  
  
-   ターゲットのセカンダリ レプリカは、現在プライマリ レプリカと同期されている必要があります。 このためには、この可用性レプリカのすべてのセカンダリ データベースが可用性グループに参加している必要があり、対応するプライマリ データベースに同期されている必要があります (つまり、ローカル セカンダリ データベースは SYNCHRONIZED 状態である必要があります)。  
  
    > [!TIP]  
    >  セカンダリ レプリカのフェールオーバーの準備状態を調べるには、 **sys.dm_hadr_database_cluster_states** 動的管理ビューで [is_failover_ready](../../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql.md) 列をクエリするか、 **AlwaysOn グループ ダッシュボード** の [[フェールオーバーの準備]](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)列を確認します。  
  
-   このタスクは、ターゲット セカンダリ レプリカ上でのみサポートされます。 ターゲット セカンダリ レプリカをホストするサーバー インスタンスに接続されている必要があります。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **可用性グループで手動フェールオーバーを行うには**  
  
1.  オブジェクト エクスプローラーで、フェールオーバーを行う可用性グループのセカンダリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。  
  
2.  [ **AlwaysOn 高可用性** ] ノードと [ **可用性グループ** ] ノードを展開します。  
  
3.  フェールオーバーする [可用性グループ] ノードを右クリックし、 **[フェールオーバー]** を選択します。  
  
4.  可用性グループのフェールオーバー ウィザードが起動します。 詳細については、このトピックの「 [可用性グループのフェールオーバー ウィザードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)の PowerShell を使用して、AlwaysOn 可用性グループに対する強制フェールオーバー (データ損失の可能性あり) を実行する方法について説明します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **可用性グループで手動フェールオーバーを行うには**  
  
1.  ターゲット セカンダリ レプリカをホストするサーバー インスタンスに接続します。  
  
2.  [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) ステートメントを使用します。次にその例を示します。  
  
     ALTER AVAILABILITY GROUP *group_name* FAILOVER  
  
     *group_name* は可用性グループの名前です。  
  
     次の例では、接続されているセカンダリ レプリカに *MyAg* 可用性グループを手動でフェールオーバーします。  
  
    ```  
    ALTER AVAILABILITY GROUP MyAg FAILOVER;  
    ```  
  
##  <a name="PowerShellProcedure"></a> PowerShell の使用  
 **可用性グループで手動フェールオーバーを行うには**  
  
1.  ディレクトリ変更コマンド (**cd**) を使用して、ターゲット セカンダリ レプリカをホストするサーバー インスタンスに移動します。  
  
2.  **Switch-SqlAvailabilityGroup** コマンドレットを使用します。  
  
    > [!NOTE]  
    >  コマンドレットの構文を表示するには、 **PowerShell 環境で** Get-Help [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] コマンドレットを使用します。 詳細については、「 [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md)」を参照してください。  
  
     次の例では、指定したパスのセカンダリ レプリカに *MyAg* 可用性グループを手動でフェールオーバーします。  
  
    ```  
    Switch-SqlAvailabilityGroup -Path SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MyAg  
    ```  
  
 **SQL Server PowerShell プロバイダーを設定して使用するには**  
  
-   [SQL Server PowerShell プロバイダー](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
-   [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md)  
  
##  <a name="FollowUp"></a> 補足情報: 可用性グループの手動フェールオーバー後  
 可用性グループの [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)] の外側でフェールオーバーした場合、WSFC ノードのクォーラム投票を調整して新しい可用性グループの構成を反映します。 詳細については、「[Windows Server フェールオーバー クラスタリング &#40;WSFC&#41; と SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [フェールオーバーとフェールオーバー モード &#40;AlwaysOn 可用性グループ&#41;](../../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md)   
 [可用性グループの強制手動フェールオーバーの実行 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
  

