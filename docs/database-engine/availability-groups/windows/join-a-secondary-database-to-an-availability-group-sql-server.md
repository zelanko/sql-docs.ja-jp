---
title: "可用性グループへのセカンダリ データベースの参加 (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.availabilitygroup.joindbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: fd7efe79-c1f9-497d-bfe7-b2a2b2321cf5
caps.latest.revision: "39"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 9d3168c015e5039a153a0eac504d1fd92612efec
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="join-a-secondary-database-to-an-availability-group-sql-server"></a>可用性グループへのセカンダリ データベースの参加 (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]で、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)]、または PowerShell を使用して、AlwaysOn 可用性グループにセカンダリ データベースを参加させる方法について説明します。 セカンダリ レプリカのセカンダリ データベースを準備したら、できるだけ早くそのデータベースを可用性グループに参加させる必要があります。 これによって、対応するプライマリ データベースからセカンダリ データベースへのデータの移動が開始されます。  
  
-   **作業を開始する準備:**  
  
     [前提条件](#Prerequisites)  
  
     [セキュリティ](#Security)  
  
-   **以下を使用してセカンダリ データベースを準備するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
> [!NOTE]  
>  セカンダリ データベースをグループに参加させた後の動作については、「 [Always On 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)、または PowerShell を使用して、AlwaysOn 可用性グループにセカンダリ データベースを参加させる方法について説明します。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   セカンダリ レプリカをホストするサーバー インスタンスに接続されている必要があります。  
  
-   セカンダリ レプリカがあらかじめ可用性グループに参加している必要があります。 詳細については、「 [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md)、または PowerShell を使用して、AlwaysOn 可用性グループにセカンダリ データベースを参加させる方法について説明します。  
  
-   セカンダリ データベースが最近準備されたものである必要があります。 詳細については、「 [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)、または PowerShell を使用して、AlwaysOn 可用性グループにセカンダリ データベースを参加させる方法について説明します。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **セカンダリ データベースを可用性グループに参加させるには**  
  
1.  オブジェクト エクスプローラーで、セカンダリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。  
  
2.  **[Always On 高可用性]** ノードと **[可用性グループ]** ノードを展開します。  
  
3.  変更する可用性グループを展開し、 **[可用性データベース]** ノードを展開します。  
  
4.  データベースを右クリックし、 **[可用性グループへの参加]**をクリックします。  
  
5.  これにより、 **[可用性グループへのデータベースの参加]** ダイアログ ボックスが開きます。 タイトル バーに表示される可用性グループ名と、グリッドに表示されるデータベースの名前を確認し、 **[OK]**をクリックするか、 **[キャンセル]**をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **セカンダリ データベースを可用性グループに参加させるには**  
  
1.  セカンダリ レプリカをホストするサーバー インスタンスに接続します。  
  
2.  [ALTER DATABASE ステートメントの SET HADR 句](../../../t-sql/statements/alter-database-transact-sql-set-hadr.md) を使用します。次にその例を示します。  
  
     ALTER DATABASE *database_name* SET HADR AVAILABILITY GROUP = *group_name*  
  
     ここで、 *database_name* は参加させるデータベースの名前で、 *group_name* は可用性グループの名前です。  
  
     次の例では、セカンダリ データベース `Db1` を、`MyAG` 可用性グループのローカル セカンダリ レプリカに参加させます。  
  
    ```  
    ALTER DATABASE Db1 SET HADR AVAILABILITY GROUP = MyAG;  
    ```  
  
    > [!NOTE]  
    >  コンテキストで使用するこの [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを確認するには、「[可用性グループの作成 &#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)」を参照してください。  
  
##  <a name="PowerShellProcedure"></a> PowerShell の使用  
 **セカンダリ データベースを可用性グループに参加させるには**  
  
1.  ディレクトリ変更コマンド (**cd**) を使用して、セカンダリ レプリカをホストするサーバー インスタンスに移動します。  
  
2.  **Add-SqlAvailabilityDatabase** コマンドレットを使用して、セカンダリ データベース (複数可) を可用性グループに参加させます。  
  
     たとえば、次のコマンドでは、セカンダリ レプリカをホストするいずれかのサーバー インスタンスで可用性グループ `Db1`にセカンダリ データベース `MyAG` を参加させます。  
  
    ```  
    Add-SqlAvailabilityDatabase `   
    -Path SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAG `   
    -Database "Db1"  
    ```  
  
    > [!NOTE]  
    >  コマンドレットの構文を表示するには、 **PowerShell 環境で** Get-Help [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コマンドレットを使用します。 詳細については、「 [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md)」を参照してください。  
  
 **SQL Server PowerShell プロバイダーを設定して使用するには**  
  
-   [SQL Server PowerShell プロバイダー](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 可用性グループの構成のトラブルシューティング &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
