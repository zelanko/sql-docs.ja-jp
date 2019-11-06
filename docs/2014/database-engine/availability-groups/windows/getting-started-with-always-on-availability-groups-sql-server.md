---
title: AlwaysOn 可用性グループ (SQL Server) の概要 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], about
ms.assetid: 33f2f2d0-79e0-4107-9902-d67019b826aa
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 03758f4ac1a88a6ed3e704d72deb1727c30ebccb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62814280"
---
# <a name="getting-started-with-alwayson-availability-groups-sql-server"></a>AlwaysOn 可用性グループの概要 (SQL Server)
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] をサポートするように [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のインスタンスを構成する手順と可用性グループを作成、管理、および監視する手順について説明します。  
  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="RecommendedReading"></a> 推奨トピック  
 可用性グループを初めて作成する場合は、あらかじめ次のトピックに目を通しておくことをお勧めします。  
  
-   [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
-   [前提条件、制限事項、および AlwaysOn 可用性グループの推奨事項&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
##  <a name="ConfigSI"></a> AlwaysOn 可用性グループをサポートする SQL Server のインスタンスの構成  
  
||手順|リンク|  
|------|----------|-----------|  
|![チェック ボックス](../../media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|**[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を有効にする:** 可用性グループに参加する [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のすべてのインスタンスで [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 機能を有効にする必要があります。<br /><br /> **前提条件:** ホスト コンピューターは、Windows Server フェールオーバー クラスタリング (WSFC) ノードであることが必要です。<br /><br /> その他の前提条件については、「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)」の「SQL Server インスタンスの前提条件と制限」を参照してください。|[有効にして、AlwaysOn 可用性グループを無効にします。](enable-and-disable-always-on-availability-groups-sql-server.md)|  
|![チェック ボックス](../../media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|**データベース ミラーリング エンドポイントを作成する (存在しない場合):** 各サーバー インスタンスに、 [データベース ミラーリング エンドポイント](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)が存在することを確認します。 サーバー インスタンスでは、このエンドポイントを使用して、他のサーバー インスタンスから [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の接続を受信します。|データベース ミラーリング エンドポイントが存在するかどうかを確認するには、次のカタログ ビューを使用します。 [sys.database_mirroring_endpoints](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)<br /><br /> **Windows 認証。** 以下を使用して、データベース ミラーリング エンドポイントを作成するには:<br /><br /> [新しい可用性グループ ウィザード](use-the-availability-group-wizard-sql-server-management-studio.md)<br /><br /> [Transact-SQL](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)<br /><br /> [SQL Server PowerShell](database-mirroring-always-on-availability-groups-powershell.md)<br /><br /> **証明書の認証。** ミラーリング エンドポイントを使用して、データベースを作成するには <br />                    [Transact-SQL](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)|  
  
##  <a name="ConfigAG"></a> Creating and Configuring a New Availability Group  
  
||手順|リンク|  
|------|----------|-----------|  
|![チェック ボックス](../../media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|**可用性グループを作成します。** 可用性グループに追加するデータベースをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスで可用性グループを作成します。<br /><br /> 可用性グループを作成する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスで、少なくとも初期プライマリ レプリカを作成します。 1 ～ 4 個のセカンダリ レプリカを指定できます。 可用性グループとレプリカのプロパティについては、「[CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)」をご覧ください。<br /><br /> [可用性グループ リスナー](../../listeners-client-connectivity-application-failover.md)を作成することを強くお勧めします。<br /><br /> **前提条件:** 可用性グループの可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスは、同じ WSFC クラスターの別のノードに存在する必要があります。 唯一の例外は、別の WSFC クラスターに移行するときに、可用性グループは一時的に 2 つのクラスターにまたがることができるという点です。<br /><br /> その他の前提条件については、「[AlwaysOn 可用性グループの前提条件、制限事項、推奨事項 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)」の「可用性グループの前提条件と制限」、「可用性データベースの前提条件と制限」、および「SQL Server インスタンスの前提条件と制限」を参照してください。|可用性グループを作成する場合は、次のツールを使用できます。<br /><br /> [新しい可用性グループ ウィザード](use-the-availability-group-wizard-sql-server-management-studio.md)<br /><br /> [Transact-SQL](create-an-availability-group-transact-sql.md)<br /><br /> [SQL Server PowerShell](create-an-availability-group-transact-sql.md)|  
|![チェック ボックス](../../media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|**セカンダリ レプリカの可用性グループへの参加** セカンダリ レプリカをホストしている [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] の各インスタンスに接続し、ローカル セカンダリ レプリカを可用性グループに参加させます。|[可用性グループへのセカンダリ レプリカの参加](join-a-secondary-replica-to-an-availability-group-sql-server.md)<br /><br /> ヒント:新しい可用性グループ ウィザードを使用すると、この手順が自動化されます。|  
|![チェック ボックス](../../media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|**セカンダリ データベースを準備する:** セカンダリ レプリカをホストしている各サーバー インスタンスで、RESTORE WITH NORECOVERY を使用してプライマリ データベースのバックアップを復元します。|[セカンダリ データベースの手動準備](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)<br /><br /> ヒント:新しい可用性グループ ウィザードを使用して、セカンダリ データベースを自動的に準備できます。 詳細については、「[[最初のデータの同期を選択] ページ &#40;AlwaysOn 可用性グループ ウィザード&#41;](select-initial-data-synchronization-page-always-on-availability-group-wizards.md)」の「初期データの完全同期を使用するための前提条件」を参照してください。|  
|![チェック ボックス](../../media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|**セカンダリ データベースを可用性グループに参加させる:** セカンダリ レプリカをホストしている各サーバー インスタンスで、各ローカル セカンダリ データベースを可用性グループに参加させます。 可用性グループに参加すると、セカンダリ データベースは対応するプライマリ データベースとのデータ同期を開始します。|[可用性グループへのセカンダリ データベースの参加](join-a-secondary-database-to-an-availability-group-sql-server.md)<br /><br /> ヒント:各セカンダリ レプリカにそれぞれセカンダリ データベースが存在する場合は、新しい可用性グループ ウィザードでこの手順を行うことができます。|  
||**[可用性グループ リスナーの作成]**  可用性グループ リスナーをまだ作成していない場合、可用性グループを作成するときにこの手順を実行する必要があります。|[可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)|  
|![チェック ボックス](../../media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|**アプリケーション開発者にリスナーの DNS ホスト名を伝えます。**  開発者は、可用性グループ リスナーに接続要求を送信するために、接続文字列でこの DNS 名を指定する必要があります。 詳細については、「 [可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)での 1 つ以上の可用性グループの構成と管理において重要です。|「[可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)」の「補足情報:可用性グループ リスナーの作成後」|  
|![チェック ボックス](../../media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|**バックアップ ジョブを実行する場所を構成します。**  セカンダリ データベースでバックアップを実行する場合は、自動バックアップ設定を考慮に入れてバックアップ ジョブのスクリプトを作成する必要があります。 可用性グループの可用性レプリカをホストする各サーバー インスタンスで、可用性グループのデータベースごとにスクリプトを作成します。|「[可用性レプリカでのバックアップの構成 &#40;SQLServer&#41;](configure-backup-on-availability-replicas-sql-server.md)」の「補足情報: セカンダリ レプリカでバックアップを構成した後」|  
  
##  <a name="ManageAGsEtc"></a> Managing Availability Groups, Replicas, and Databases  
  
> [!NOTE]  
>  可用性グループとレプリカのプロパティについては、「[CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)」をご覧ください。  
  
 既存の可用性グループの管理には、次のタスクが 1 つ以上含まれます。  
  
|タスク|リンク|  
|----------|----------|  
|可用性グループの [柔軟なフェールオーバー ポリシー](flexible-automatic-failover-policy-availability-group.md) を変更して、自動フェールオーバーを実行する条件を制御します。 このポリシーは、自動フェールオーバーが可能な場合にのみ関係します。|[可用性グループの柔軟なフェールオーバー ポリシーの構成](configure-flexible-automatic-failover-policy.md)|  
|計画的な手動フェールオーバーか、 *強制フェールオーバー*と通常呼ばれる強制手動フェールオーバー (データ損失の可能性あり) を実行します。 詳細については、「[フェールオーバーとフェールオーバー モード &#40;AlwaysOn 可用性グループ&#41;](failover-and-failover-modes-always-on-availability-groups.md)」を参照してください。|[計画的な手動フェールオーバーの実行](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)<br /><br /> [強制手動フェールオーバーの実行](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)|  
|一連の定義済みポリシーを使用して、可用性グループとレプリカおよびデータベースの正常性を表示します。|[ポリシー ベースの管理を使用した可用性グループの正常性の表示](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)<br /><br /> [AlwaysOn グループ ダッシュ ボードを使用します。](use-the-always-on-dashboard-sql-server-management-studio.md)|  
|セカンダリ レプリカを追加または削除します。|[セカンダリ レプリカの追加](add-a-secondary-replica-to-an-availability-group-sql-server.md)<br /><br /> [セカンダリ レプリカの削除](remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
|可用性データベースを中断または再開します。 セカンダリ データベースを中断すると、データベースを再開するまで現在の状態が維持されます。|[データベースの中断](suspend-an-availability-database-sql-server.md)<br /><br /> [データベースの再開](resume-an-availability-database-sql-server.md)|  
|データベースを追加または削除します。|[データベースの追加](availability-group-add-a-database.md)<br /><br /> [セカンダリ データベースの削除](remove-a-secondary-database-from-an-availability-group-sql-server.md)<br /><br /> [プライマリ データベースの削除](remove-a-primary-database-from-an-availability-group-sql-server.md)|  
|可用性グループ リスナーを再構成または作成します。|[可用性グループ リスナーの作成または構成](create-or-configure-an-availability-group-listener-sql-server.md)|  
|可用性グループを削除します。|[可用性グループの削除](remove-an-availability-group-sql-server.md)|  
|ファイルの追加操作のトラブルシューティングを行います。 これは、プライマリ データベースとセカンダリ データベースのファイル パスが異なる場合に必要となります。|[失敗したファイルの追加操作のトラブルシューティング](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)|  
|可用性レプリカのプロパティを変更します。|[可用性モードの変更](change-the-availability-mode-of-an-availability-replica-sql-server.md)<br /><br /> [フェールオーバー モードの変更](change-the-failover-mode-of-an-availability-replica-sql-server.md)<br /><br /> [バックアップの優先順位 (および自動バックアップ設定) の構成](configure-backup-on-availability-replicas-sql-server.md)<br /><br /> [読み取り専用アクセスの構成](configure-read-only-access-on-an-availability-replica-sql-server.md)<br /><br /> [読み取り専用ルーティングの構成](configure-read-only-routing-for-an-availability-group-sql-server.md)<br /><br /> [セッション タイムアウト期間の変更](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)|  
  
##  <a name="MonitorAGsEtc"></a> 可用性グループの監視  
 AlwaysOn 可用性グループのプロパティと状態を監視するには、次のツールを使用します。  
  
|ツール|簡単な説明|リンク|  
|----------|-----------------------|-----------|  
|System Center Monitoring pack for SQL Server|Monitoring pack for SQL Server (SQLMP) は、可用性グループ、可用性レプリカ、および可用性データベースを IT 管理者が監視するための推奨ソリューションです。 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] に特に関連する監視機能は次のとおりです。<br /><br /> 可用性グループ、可用性レプリカ、および可用性データベースを多数のコンピューターから自動検出する機能。 これにより、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の在庫を簡単に追跡できます。<br /><br /> System Center Operations Manager (SCOM) の完全な警告機能とチケット機能。 これらの機能は、問題の早期解決を可能にする詳細な情報を提供します。<br /><br /> ポリシー ベースの管理 (PBM) を使用した AlwaysOn 正常性状態の監視のカスタム拡張機能。<br /><br /> 正常性状態は、可用性データベースから可用性レプリカにロールアップされます。<br /><br /> System Center Operations Manager コンソールから [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] を管理するカスタム タスク。|監視パック (SQLServerMP.msi) および *SQL Server Management Pack Guide for System Center Operations Manager* (SQLServerMPGuide.doc) をダウンロードするには、以下を参照してください。<br /><br /> [System Center Monitoring pack for SQL Server](https://www.microsoft.com/download/details.aspx?displaylang=en&id=10631)|  
|[!INCLUDE[tsql](../../../includes/tsql-md.md)]|[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のカタログ ビューと動的管理ビューは、可用性グループとそのレプリカ、データベース、リスナー、および WSFC クラスター環境に関する豊富な情報を提供します。|[可用性グループの監視 &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|**[オブジェクト エクスプローラーの詳細]** ペインには、接続先の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスでホストされている可用性グループの基本情報が表示されます。<br /><br /> ヒント:このペインを使用して、複数の可用性グループ、レプリカ、またはデータベースを選択し、選択したオブジェクトで一般的な管理タスク (可用性グループからの複数の可用性レプリカまたはデータベースの削除など) を実行します。|[[オブジェクト エクスプローラーの詳細] を使用した可用性グループの監視](use-object-explorer-details-to-monitor-availability-groups.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|**[プロパティ]** ダイアログ ボックスを使用して、可用性グループ、レプリカ、またはリスナーのプロパティを表示し、必要に応じてその値を変更できます。|[可用性グループのプロパティ](view-availability-group-properties-sql-server.md)<br /><br /> [可用性レプリカのプロパティ](view-availability-replica-properties-sql-server.md)<br /><br /> [可用性グループ リスナーのプロパティ](view-availability-group-listener-properties-sql-server.md)|  
|システム モニター|**SQLServer:Availability Replica** パフォーマンス オブジェクトには、可用性レプリカに関する情報を報告するパフォーマンス カウンターが含まれています。|[SQL Server、Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)|  
|システム モニター|**SQLServer:Database Replica** パフォーマンス オブジェクトには、特定のセカンダリ レプリカのセカンダリ データベースに関する情報を報告するパフォーマンス カウンターが含まれています。<br /><br /> SQL Server の **SQLServer:Databases** オブジェクトには、トランザクション ログの利用状況などを監視するパフォーマンス カウンターが含まれています。 可用性データベースでのトランザクション ログの利用状況の監視に関連性が高いカウンターは、**Log Flush Write Time (ms)** 、**Log Flushes/sec**、**Log Pool Cache Misses/sec**、**Log Pool Disk Reads/sec**、**Log Pool Requests/sec** です。|[SQL Server、データベース レプリカ](../../../relational-databases/performance-monitor/sql-server-database-replica.md)<br /><br /> [SQL Server、Databases オブジェクト](../../../relational-databases/performance-monitor/sql-server-databases-object.md)|  
  
##  <a name="RelatedContent"></a> 関連コンテンツ  
  
-   **AlwaysOn のビデオの概要:** [Microsoft SQL Server コードネーム"Denali"AlwaysOn シリーズ パート 1:次世代高可用性ソリューションの概要](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
-   **ビデオには、AlwaysOn の詳細情報:** [Microsoft SQL Server コードネーム"Denali"AlwaysOn シリーズ パート 2:AlwaysOn を使用したミッション クリティカルな高可用性ソリューションの構築](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **ホワイト ペーパー:** [Microsoft SQL Server AlwaysOn ソリューション ガイド高可用性とディザスター リカバリー](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   **ブログ:** [SQL Server AlwaysOn チームのブログ:SQL Server AlwaysOn チームのオフィシャル ブログ](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ&#40;SQL Server&#41;](always-on-availability-groups-sql-server.md)   
 [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 可用性グループのサーバー インスタンスの構成&#40;SQL Server&#41;](configuration-of-a-server-instance-for-always-on-availability-groups-sql-server.md)   
 [可用性グループの作成と構成 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)   
 [可用性グループの監視 &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [AlwaysOn 可用性グループの TRANSACT-SQL ステートメントの概要&#40;SQL Server&#41;](transact-sql-statements-for-always-on-availability-groups.md)   
 [AlwaysOn 可用性グループの PowerShell コマンドレットの概要&#40;SQL Server&#41;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
  
