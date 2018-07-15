---
title: AlwaysOn ポリシーを使用して可用性グループ (SQL Server) の正常性の表示 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6f1bcbc3-1220-4071-8e53-4b957f5d3089
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4189c70c8e4cf9e3d2fce378dbbb039ae2c0c601
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297142"
---
# <a name="use-alwayson-policies-to-view-the-health-of-an-availability-group-sql-server"></a>AlwaysOn ポリシーを使用した可用性グループの正常性の確認 (SQL Server)
  このトピックでは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] の AlwaysOn ポリシーまたは [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]の PowerShell を使用して、AlwaysOn 可用性グループの運用状態の正常性を確認する方法について説明します。 AlwaysOn ポリシー ベースの管理については、次を参照してください。[運用上の問題と AlwaysOn 可用性グループ (SQL Server) の AlwaysOn ポリシー](always-on-policies-for-operational-issues-always-on-availability.md)します。  
  
> [!IMPORTANT]  
>  AlwaysOn ポリシーでは、カテゴリの名前が ID として使用されます。 AlwaysOn カテゴリの名前を変更すると、正常性評価の機能を使用できなくなります。 このため、AlwaysOn カテゴリの名前は変更しないでください。  
  

  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 CONNECT、VIEW SERVER STATE、および VIEW ANY DEFINITION 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> AlwaysOn ダッシュ ボードの使用  
 **AlwaysOn ダッシュ ボードを開く**  
  
1.  オブジェクト エクスプローラーで、可用性レプリカの 1 つをホストするサーバー インスタンスに接続します。 可用性グループ内のすべての可用性レプリカについての情報を表示するには、プライマリ レプリカをホストするサーバー インスタンスを使用してください。  
  
2.  サーバー名をクリックし、サーバー ツリーを展開します。  
  
3.  **[AlwaysOn 高可用性]** ノードを展開します。  
  
     **[可用性グループ]** ノードを右クリックするか、このノードを展開し、特定の可用性グループを右クリックします。  
  
4.  **[ダッシュボードの表示]** をクリックします。  
  
 AlwaysOn ダッシュボードの使用方法の詳細については、「[AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)」を参照してください。  
  
##  <a name="PowerShellProcedure"></a> PowerShell の使用  
 **AlwaysOn ポリシーを使用して、可用性グループのヘルスを表示するには**  
  
1.  既定の設定 (`cd`) 可用性レプリカの 1 つをホストするサーバー インスタンスにします。 可用性グループ内のすべての可用性レプリカについての情報を表示するには、プライマリ レプリカをホストするサーバー インスタンスを使用してください。  
  
2.  次のコマンドレットを使用します。  
  
     `Test-SqlAvailabilityGroup`  
     SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、可用性グループの正常性を査定します。 このコマンドレットを実行するには、CONNECT、VIEW SERVER STATE、および VIEW ANY DEFINITION 権限が必要です。  
  
     たとえば、次のコマンドでは、サーバー インスタンス `Computer\Instance`上で正常性状態が "Error" の可用性グループすべてを表示します。  
  
    ```  
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups `   
    | Test-SqlAvailabilityGroup | Where-Object { $_.HealthState -eq "Error" }  
    ```  
  
     `Test-SqlAvailabilityReplica`  
     SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、可用性レプリカの正常性を査定します。 このコマンドレットを実行するには、CONNECT、VIEW SERVER STATE、および VIEW ANY DEFINITION 権限が必要です。  
  
     たとえば、次のコマンドは、可用性グループ `MyReplica` 内の `MyAg` という名前の可用性レプリカの正常性を評価し、概要を出力します。  
  
    ```  
    Test-SqlAvailabilityReplica `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
     `Test-SqlDatabaseReplicaState`  
     SQL Server のポリシー ベースの管理 (PBM) のポリシーを評価することによって、参加しているすべての可用性レプリカ上の可用性データベースの正常性を査定します。  
  
     たとえば、次のコマンドは、可用性グループ `MyAg` 内のすべての可用性データベースの正常性を評価し、各データベースの概要を出力します。  
  
    ```  
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\DatabaseReplicaStates `   
     | Test-SqlDatabaseReplicaState  
    ```  
  
     これらのコマンドレットでは、次のオプションを使用できます。  
  
    |オプション|説明|  
    |------------|-----------------|  
    |`AllowUserPolicies`|AlwaysOn ポリシーのカテゴリにあるユーザー ポリシーを実行します。|  
    |`InputObject`|可用性グループ、可用性レプリカ、または可用性データベースの状態 (使用するコマンドレットに応じて異なります) を表すオブジェクトのコレクションです。 コマンドレットを実行すると、指定されたオブジェクトの正常性が計算されます。|  
    |`NoRefresh`|このパラメーターが設定されている場合、コマンドレットは手動で更新されませんで指定されたオブジェクト、`-Path`または`-InputObject`パラメーター。|  
    |`Path`|可用性グループ、1 つ以上の可用性レプリカ、または可用性データベースのデータベース レプリカ クラスターの状態へのパス (使用するコマンドレットに応じて異なります) です。 これは省略可能なパラメーターです。 このパラメーターの値を指定しない場合、既定では、現在の場所に設定されます。|  
    |`ShowPolicyDetails`|このコマンドレットで実行された各ポリシー評価の結果を表示します。 コマンドレットを実行すると、ポリシー評価ごとに 1 つのオブジェクトが出力されます。このオブジェクトには評価の結果を表すフィールド (ポリシーが渡されるかどうかに関係なく、ポリシー名、カテゴリなど) があります。|  
  
     たとえば、次の `Test-SqlAvailabilityGroup` コマンドは、`-ShowPolicyDetails` パラメーターを指定して、可用性グループ `MyAg` 上で実行されたポリシー ベースの管理 (PBM) のポリシーごとに、このコマンドレットによって実行されたそれぞれのポリシー評価の結果を表示します。  
  
    ```  
    Test-SqlAvailabilityGroup `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\AgName `  
    -ShowPolicyDetails  
  
    ```  
  
    > [!NOTE]  
    >  コマンドレットの構文を表示する、`Get-Help`コマンドレット、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境。 詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。  
  
 **SQL Server PowerShell プロバイダーを設定して使用するには**  
  
-   [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
##  <a name="RelatedContent"></a> 関連コンテンツ  
 **SQL Server AlwaysOn チームのブログ: PowerShell を使用した AlwaysOn 正常性状態を監視します。**  
  
-   [パート 1: 基本的なコマンドレットの概要](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-1.aspx)  
  
-   [パート 2: 高度なコマンドレットの使用方法](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-2.aspx)  
  
-   [パート 3: 単純な監視アプリケーション](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/monitoring-alwayson-health-with-powershell-part-3.aspx)  
  
-   [パート 4: SQL Server エージェントの統合](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/the-always-on-health-model-part-4.aspx)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [可用性グループの管理 &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md)   
 [可用性グループの監視 &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [AlwaysOn ポリシーの運用上の問題と AlwaysOn 可用性グループ (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md) 
  
  
