---
title: 可用性グループの作成 (SQL Server PowerShell) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: bc69a7df-20fa-41e1-9301-11317c5270d2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 43210110405eca5f44fc458311f90582f159aff6
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72797712"
---
# <a name="create-an-availability-group-sql-server-powershell"></a>可用性グループの作成 (SQL Server PowerShell)
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]の AlwaysOn 可用性グループを PowerShell コマンドレットで作成および構成する方法について説明します。 *可用性グループ* は、1 つのまとまりとしてフェールオーバーする一連のユーザー データベースと、フェールオーバーをサポートする一連のフェールオーバー パートナー ( *可用性レプリカ*) を定義します。  
  
> [!NOTE]  
>  可用性グループの概要については、「[AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)」を参照してください。  

> [!NOTE]  
>  PowerShell のコマンドレットの代わりに、可用性グループの作成ウィザードや [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用する方法もあります。 詳細については、「 [[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) 」または「 [可用性グループの作成 &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)の Always On 可用性グループを PowerShell コマンドレットで作成および構成する方法について説明します。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
 可用性グループを初めて作成する場合は、あらかじめこのセクションに目を通しておくことを強くお勧めします。  
  
###  <a name="PrerequisitesRestrictions"></a> 前提条件、制限事項、および推奨事項  
  
-   可用性グループを作成する前に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の各ホスト インスタンスが、同じ Windows Server Failover Clustering (WSFC) フェールオーバー クラスタリングのそれぞれ異なる WSFC ノードに存在していることを確認します。 また、使用するサーバー インスタンスが、他のサーバー インスタンスの前提条件を満たしていることと、他の [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の要件がすべて満たされていること、さらに、自分自身も推奨事項を認識していることを確認してください。 詳細については、「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)」をお読みいただくことを強くお勧めします。  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> アクセス許可  
 **sysadmin** 固定サーバー ロールのメンバーシップと、CREATE AVAILABILITY GROUP サーバー権限、ALTER ANY AVAILABILITY GROUP 権限、CONTROL SERVER 権限のいずれかが必要です。  
  
###  <a name="SummaryPSStatements"></a> 作業の概要および対応する PowerShell コマンドレット  
 次の表は、可用性グループの構成に伴う基本的な作業の一覧です。一覧には PowerShell コマンドレットによってサポートされる作業が示されています。 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] に関連したこれらの作業は、この表に示されている順に実行する必要があります。  
  
|タスク|PowerShell コマンドレット (利用可能な場合) または Transact SQL ステートメント|タスク*を実行する場所 **<sup> </sup>**|  
|----------|--------------------------------------------------------------------|-------------------------------------------|  
|データベース ミラーリング エンドポイントを作成する ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスごとに 1 回)|`New-SqlHadrEndPoint`|データベース ミラーリング エンドポイントが欠落している各サーバー インスタンスで実行します。<br /><br /> 注: 既存のデータベース ミラーリング エンドポイントに変更を加えるには、`Set-SqlHadrEndpoint` を使用します。|  
|可用性グループを作成する|まず、`New-SqlAvailabilityReplica` コマンドレットに `-AsTemplate` パラメーターを指定し、可用性グループに追加する予定の 2 つの可用性レプリカのそれぞれについて、インメモリの可用性レプリカ オブジェクトを作成します。<br /><br /> 次に、`New-SqlAvailabilityGroup` コマンドレットを使用し、可用性レプリカ オブジェクトを参照して、可用性グループを作成します。|初期プライマリ レプリカをホストするサーバー インスタンスで実行します。|  
|セカンダリ レプリカを可用性グループに参加させる|`Join-SqlAvailabilityGroup`|セカンダリ レプリカをホストする各サーバー インスタンスで実行します。|  
|セカンダリ データベースを準備する|`Backup-SqlDatabase` 」、「 `Restore-SqlDatabase`|プライマリ レプリカをホストするサーバー インスタンスでバックアップを作成します。<br /><br /> セカンダリ レプリカをホストする各サーバー インスタンス上で、`NoRecovery` 復元パラメーターを使用してバックアップを復元します。 プライマリ レプリカをホストするコンピューターとターゲット セカンダリ レプリカをホストするコンピューターとでファイル パスが異なる場合は、`RelocateFile` 復元パラメーターも使用します。|  
|各セカンダリ データベースを可用性グループに参加させてデータ同期を開始する|`Add-SqlAvailabilityDatabase`|セカンダリ レプリカをホストする各サーバー インスタンスで実行します。|  
  
 **<sup>*</sup>** 特定のタスクを実行するには、指定されたサーバーインスタンスにディレクトリ (`cd`) を変更します。  
  
###  <a name="PsProviderLinks"></a> SQL Server PowerShell プロバイダーを設定して使用するには  
  
-   [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)  
  
-   [SQL Server PowerShell のヘルプの参照](../../../powershell/sql-server-powershell.md)  
  
##  <a name="PowerShellProcedure"></a> PowerShell を使用した可用性グループの作成と構成  
  
> [!NOTE]  
>  特定のコマンドレットの構文や例を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。 詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。  
  
1.  ディレクトリ (`cd`) を、プライマリレプリカをホストするサーバーインスタンスに変更します。  
  
2.  プライマリ レプリカのインメモリの可用性レプリカ オブジェクトを作成します。  
  
3.  セカンダリ レプリカごとにインメモリの可用性レプリカ オブジェクトを作成します。  
  
4.  可用性グループを作成します。  
  
    > [!NOTE]  
    >  可用性グループ名の最大文字数は 128 文字です。  
  
5.  新しいセカンダリ レプリカを可用性グループに参加させます。 詳細については、「 [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。  
  
6.  可用性グループ内の各データベースについて、セカンダリ データベースを作成します。これは、プライマリ データベースの最新のバックアップを、RESTORE WITH NORECOVERY で復元することによって行います。  
  
7.  新しいセカンダリ データベースをすべて可用性グループに参加させます。 詳細については、「 [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。  
  
8.  必要に応じて、Windows の `dir` コマンドを使用し、新しい可用性グループの内容を確認します。  
  
> [!NOTE]  
>  複数のサーバー インスタンスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントが、それぞれ異なるドメイン ユーザー アカウントで実行されている場合、それぞれのサーバー インスタンス上に、もう一方のサーバー インスタンス用のログインを作成し、そのログインにローカルのデータベース ミラーリング エンドポイントへの CONNECT 権限を付与します。  
  
##  <a name="ExampleConfigureGroup"></a> 例: PowerShell による可用性グループの作成  
 以下の PowerShell スクリプトは、2 つの可用性レプリカと 1 つの可用性データベースから成る `MyAG` という名前の単純な可用性グループを作成、構成する例です。 この例では、次の処理を実行します。  
  
1.  `MyDatabase` とそのトランザクション ログをバックアップします。  
  
2.  `MyDatabase` とそのトランザクション ログを `-NoRecovery` オプションを使用して復元します。  
  
3.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のローカル インスタンス (名前は `PrimaryComputer\Instance`) によってホストされるプライマリ レプリカのメモリ内表現を作成します。  
  
4.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス (名前は `SecondaryComputer\Instance`) によってホストされるセカンダリ レプリカのメモリ内表現を作成します。  
  
5.  `MyAG`という名前の可用性グループを作成します。  
  
6.  セカンダリ レプリカを可用性グループに参加させます。  
  
7.  セカンダリ データベースを可用性グループに参加させます。  
  
```powershell
# Backup my database and its log on the primary  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "PrimaryComputer\Instance"  
  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "PrimaryComputer\Instance" `  
    -BackupAction Log   
  
# Restore the database and log on the secondary (using NO RECOVERY)  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -NoRecovery  
  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -RestoreAction Log `  
    -NoRecovery  
  
# Create an in-memory representation of the primary replica.  
$primaryReplica = New-SqlAvailabilityReplica `  
    -Name "PrimaryComputer\Instance" `  
    -EndpointURL "TCP://PrimaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create an in-memory representation of the secondary replica.  
$secondaryReplica = New-SqlAvailabilityReplica `  
    -Name "SecondaryComputer\Instance" `  
    -EndpointURL "TCP://SecondaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create the availability group  
New-SqlAvailabilityGroup `  
    -Name "MyAG" `  
    -Path "SQLSERVER:\SQL\PrimaryComputer\Instance" `  
    -AvailabilityReplica @($primaryReplica,$secondaryReplica) `  
    -Database "MyDatabase"  
  
# Join the secondary replica to the availability group.  
Join-SqlAvailabilityGroup -Path "SQLSERVER:\SQL\SecondaryComputer\Instance" -Name "MyAG"  
  
# Join the secondary database to the availability group.  
Add-SqlAvailabilityDatabase -Path "SQLSERVER:\SQL\SecondaryComputer\Instance\AvailabilityGroups\MyAG" -Database "MyDatabase"  
```  
  
##  <a name="RelatedTasks"></a> 関連タスク  
 **AlwaysOn 可用性グループ用にサーバーインスタンスを構成するには**  
  
-   [AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [AlwaysOn 可用性グループ&#40;SQL Server PowerShell のデータベースミラーリングエンドポイントを作成する&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
 **可用性グループおよびレプリカのプロパティを構成するには**  
  
-   [可用性レプリカの可用性モードの変更 &#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [可用性レプリカのフェールオーバー モードの変更 &#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [自動フェールオーバーの条件を制御する柔軟なフェールオーバーポリシーの構成 (AlwaysOn 可用性グループ)](configure-flexible-automatic-failover-policy.md)  
  
-   [可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [可用性グループの読み取り専用ルーティングの構成 &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [可用性レプリカのセッション タイムアウト期間の変更 &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **可用性グループの構成を完了するには**  
  
-   [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 **別の方法で可用性グループを作成する**  
  
-   [可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [可用性グループの作成 &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)  
  
 **AlwaysOn 可用性グループ構成のトラブルシューティングを行うには**  
  
-   [AlwaysOn 可用性グループ構成 (SQL Server) の削除に関するトラブルシューティング](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [失敗したファイルの追加操作&#40;のトラブルシューティング AlwaysOn 可用性グループ&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> 関連コンテンツ  
  
-   **ブログ:**  
  
     [AlwaysON-HADRON 学習シリーズ: HADRON 対応データベースのワーカープールの使用](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [SQL Server PowerShell を使用した AlwaysOn の構成](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/configuring-alwayson-with-sql-server-powershell.aspx)  
  
     [AlwaysOn チームのブログの SQL Server: AlwaysOn チームの公式 SQL Server のブログ](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server エンジニアのブログ](https://blogs.msdn.com/b/psssql/)  
  
-   **ビデオ:**  
  
     [Microsoft SQL Server コードネーム "Denali" AlwaysOn シリーズパート 1: 次世代の高可用性ソリューションの概要](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server コードネーム "Denali" AlwaysOn シリーズパート 2: AlwaysOn を使用したミッションクリティカルな高可用性ソリューションの構築](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **ホワイトペーパー:**  
  
     [高可用性とディザスターリカバリーのための AlwaysOn ソリューションガイドの Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [SQL Server 2012 に関する Microsoft ホワイト ペーパー](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server ユーザー諮問チームのホワイト ペーパー](http://sqlcat.com/)  
  
## <a name="see-also"></a>「  
 [データベース ミラーリング エンドポイント &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [AlwaysOn 可用性グループ&#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)  
