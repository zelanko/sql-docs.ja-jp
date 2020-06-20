---
title: 自動フェールオーバーの条件を制御する柔軟なフェールオーバーポリシーの構成 (Always On 可用性グループ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], flexible failover policy
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 1ed564b4-9835-4245-ae35-9ba67419a4ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c938624a3ed39fe2d41f21a21af5231aa76a8c17
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936983"
---
# <a name="configure-the-flexible-failover-policy-to-control-conditions-for-automatic-failover-always-on-availability-groups"></a>自動フェールオーバーの条件を制御する柔軟なフェールオーバー ポリシーの構成 (AlwaysOn 可用性グループ)
  このトピックでは、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] で [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]または PowerShell を使用して AlwaysOn 可用性グループの柔軟なフェールオーバー ポリシーを構成する方法について説明します。 柔軟なフェールオーバー ポリシーを使用すると、可用性グループの自動フェールオーバーを実行する条件をきめ細かく制御できます。 自動フェールオーバーを実行するエラー条件および正常性チェックの頻度を変更することで、自動フェールオーバーの確率値を増減して高可用性の SLA をサポートできます。  
  
  
  
    > [!NOTE]  
    >  The flexible failover policy of an availability group cannot be configured by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-on-automatic-failovers"></a><a name="Limitations"></a> 自動フェールオーバーの制限  
  
-   自動フェールオーバーが行われるには、現在のプライマリ レプリカおよび 1 つのセカンダリ レプリカが自動フェールオーバーを使用する同期コミット可用性モード用に構成され、セカンダリ レプリカがプライマリ レプリカと同期している必要があります。  
  
-   WSFC クラスターでは、可用性グループが WSFC のエラーしきい値を超えると、自動フェールオーバーはその可用性グループに対して実行されません。 また、クラスター管理者が失敗したリソース グループを手動でオンラインにするか、データベース管理者が可用性グループの手動フェールオーバーを実行するまで、可用性グループの WSFC リソース グループはエラー状態のままになります。 *WSFC のエラーしきい値* は、特定の期間に可用性グループに対して許容されるエラーの最大数として定義されています。 既定の期間は 6 時間であり、この期間のエラーの最大数の既定値は *n*-1 です ( *n* は WSFC ノードの数です)。 特定の可用性グループのエラーしきい値を変更するには、WSFC フェールオーバー マネージャー コンソールを使用します。  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> 必要条件  
  
-   プライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
  
|タスク|アクセス許可|  
|----------|-----------------|  
|新しい可用性グループの柔軟なフェールオーバー ポリシーを構成する|**sysadmin** 固定サーバー ロールのメンバーシップと、CREATE AVAILABILITY GROUP サーバー権限、ALTER ANY AVAILABILITY GROUP 権限、CONTROL SERVER 権限のいずれかが必要です。|  
|既存の可用性グループのポリシーを変更する|可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。|  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
 **柔軟なフェールオーバー ポリシーを構成するには**  
  
1.  プライマリ レプリカをホストするサーバー インスタンスに接続します。  
  
2.  新しい可用性グループの場合は、 [CREATE AVAILABILITY group](/sql/t-sql/statements/create-availability-group-transact-sql)ステートメントを使用し [!INCLUDE[tsql](../../../includes/tsql-md.md)] ます。 既存の可用性グループを変更する場合は、 [ALTER AVAILABILITY group](/sql/t-sql/statements/alter-availability-group-transact-sql)ステートメントを使用し [!INCLUDE[tsql](../../../includes/tsql-md.md)] ます。  
  
    -   フェールオーバーの条件レベルを設定するには、FAILURE_CONDITION_LEVEL = *n* オプションを使用します。ここで、 *n* は 1 ～ 5 の整数です。  
  
         たとえば、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントでは、既存の可用性グループ `AG1`のエラー条件レベルをレベル 1 に変更します。  
  
        ```sql
        ALTER AVAILABILITY GROUP AG1 SET (FAILURE_CONDITION_LEVEL = 1);  
        ```  
  
         これらの整数値とエラー条件レベルの関係は次のとおりです。  
  
        |[!INCLUDE[tsql](../../../includes/tsql-md.md)] 値|Level|自動フェールオーバーが開始される条件|  
        |------------------------------|-----------|-------------------------------------------|  
        |1|1 つ|サーバーの停止。 フェールオーバーまたは再起動のため、SQL Server サービスが停止した場合。|  
        |2|2 つ|サーバーの応答停止。 下限値の任意の条件が満たされた場合、SQL Server サービスがクラスターに接続され正常性チェックのタイムアウトしきい値を超えた場合、または現在のプライマリ レプリカがエラー状態になった場合。|  
        |3|3|重大なサーバー エラー。 下限値の任意の条件が満たされるか、重大な内部サーバー エラーが発生した場合。<br /><br /> これは既定のレベルです。|  
        |4|4|中程度のサーバー エラー。 下限値の任意の条件が満たされるか、中程度のサーバー エラーが発生した場合。|  
        |5|5|任意の限定されたエラー条件。 下限値の任意の条件が満たされるか、限定されたエラー条件が発生した場合。|  
  
         詳細については、「[可用性グループの自動フェールオーバーのための柔軟なフェールオーバー ポリシー &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md)」を参照してください。  
  
    -   正常性チェックのタイムアウトしきい値を構成するには、HEALTH_CHECK_TIMEOUT = *n* オプションを使用します。ここで *n* は 15000 ミリ秒 (15 秒) ～ 4294967295 ミリ秒の整数です。 既定値は 30000 ミリ秒 (30 秒) です。  
  
         たとえば、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントでは、既存の可用性グループ `AG1`の正常性チェックのタイムアウトしきい値が  60,000 ミリ秒 (1 分) に変更されます。  
  
        ```sql
        ALTER AVAILABILITY GROUP AG1 SET (HEALTH_CHECK_TIMEOUT = 60000);  
        ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> PowerShell の使用  

### <a name="to-configure-the-flexible-failover-policy"></a>柔軟なフェールオーバーポリシーを構成するには * *  
  
1.  既定 (`cd`) を、プライマリ レプリカをホストするサーバー インスタンスに設定します。  
  
2.  可用性グループに可用性レプリカを追加する場合は、`New-SqlAvailabilityGroup` コマンドレットを使用します。 既存の可用性レプリカを変更する場合は、`Set-SqlAvailabilityGroup` コマンドレットを使用します。  
  
    -   フェールオーバーの条件レベルを設定するには、 `FailureConditionLevel` *level*パラメーターを使用します。ここで、 *level*は次の値のいずれかになります。  
  
        |値|Level|自動フェールオーバーが開始される条件|  
        |-----------|-----------|-------------------------------------------|  
        |`OnServerDown`|1 つ|サーバーの停止。 フェールオーバーまたは再起動のため、SQL Server サービスが停止した場合。|  
        |`OnServerUnresponsive`|2 つ|サーバーの応答停止。 下限値の任意の条件が満たされた場合、SQL Server サービスがクラスターに接続され正常性チェックのタイムアウトしきい値を超えた場合、または現在のプライマリ レプリカがエラー状態になった場合。|  
        |`OnCriticalServerError`|3|重大なサーバー エラー。 下限値の任意の条件が満たされるか、重大な内部サーバー エラーが発生した場合。<br /><br /> これは既定のレベルです。|  
        |`OnModerateServerError`|4|中程度のサーバー エラー。 下限値の任意の条件が満たされるか、中程度のサーバー エラーが発生した場合。|  
        |`OnAnyQualifiedFailureConditions`|5|任意の限定されたエラー条件。 下限値の任意の条件が満たされるか、限定されたエラー条件が発生した場合。|  
  
         詳細については、「[可用性グループの自動フェールオーバーのための柔軟なフェールオーバー ポリシー &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md)」を参照してください。  
  
         たとえば、次のコマンドでは、既存の可用性グループ `AG1`のエラー条件レベルをレベル 1 に変更します。  
  
        ```powershell
        Set-SqlAvailabilityGroup `
         -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `
         -FailureConditionLevel OnServerDown  
        ```  
  
    -   正常性チェックのタイムアウトしきい値を設定するには、 `HealthCheckTimeout` *n*パラメーターを使用します。ここで、 *n*は15000ミリ秒 (15 秒) ~ 4294967295 ミリ秒の整数です。 既定値は 30000 ミリ秒 (30 秒) です。  
  
         たとえば、次のコマンドでは、既存の可用性グループ `AG1`の正常性チェックのタイムアウトしきい値が 120,000 ミリ秒 (2 分) に変更されます。  
  
        ```powershell
        Set-SqlAvailabilityGroup `
         -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `
         -HealthCheckTimeout 120000  
        ```  
  
> [!NOTE]  
>  コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。 詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。  
  
 **SQL Server PowerShell プロバイダーを設定して使用するには**  
  
-   [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [可用性モード (AlwaysOn 可用性グループ)](availability-modes-always-on-availability-groups.md)   
 [フェールオーバーとフェールオーバーモード &#40;AlwaysOn 可用性グループ&#41;](failover-and-failover-modes-always-on-availability-groups.md)   
 [Windows Server フェールオーバークラスタリング &#40;WSFC&#41; SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [フェールオーバークラスターインスタンスのフェールオーバーポリシー](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)   
 [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)  
