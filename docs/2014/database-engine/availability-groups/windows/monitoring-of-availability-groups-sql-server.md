---
title: 可用性グループの監視 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 1d5e3291-0d0a-45a1-88e5-1fc242d17210
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1793032a72ae1dd150caa5ddd1739f7f5620bce1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62790198"
---
# <a name="monitoring-of-availability-groups-sql-server"></a>可用性グループの監視 (SQL Server)
  AlwaysOn 可用性グループのプロパティと状態を監視するには、次のツールを使用します。  
  
|ツール|簡単な説明|リンク|  
|----------|-----------------------|-----------|  
|System Center Monitoring pack for SQL Server|Monitoring pack for SQL Server (SQLMP) は、可用性グループ、可用性レプリカ、および可用性データベースを IT 管理者が監視するための推奨ソリューションです。 
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] に特に関連する監視機能は次のとおりです。<br /><br /> 可用性グループ、可用性レプリカ、および可用性データベースを多数のコンピューターから自動検出する機能。 これにより、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の在庫を簡単に追跡できます。<br /><br /> System Center Operations Manager (SCOM) の完全な警告機能とチケット機能。 これらの機能は、問題の早期解決を可能にする詳細な情報を提供します。<br /><br /> ポリシー ベースの管理 (PBM) を使用した AlwaysOn 正常性状態の監視のカスタム拡張機能。<br /><br /> 正常性状態は、可用性データベースから可用性レプリカにロールアップされます。<br /><br /> System Center Operations Manager コンソールから [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] を管理するカスタム タスク。|監視パック (SQLServerMP.msi) および *SQL Server Management Pack Guide for System Center Operations Manager* (SQLServerMPGuide.doc) をダウンロードするには、以下を参照してください。<br /><br /> [SQL Server 用 System Center 監視パック](https://www.microsoft.com/download/details.aspx?displaylang=en&id=10631)|  
|[!INCLUDE[tsql](../../../includes/tsql-md.md)]|
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のカタログ ビューと動的管理ビューは、可用性グループとそのレプリカ、データベース、リスナー、および WSFC クラスター環境に関する豊富な情報を提供します。|[Transact-sql&#41;&#40;可用性グループの監視](monitor-availability-groups-transact-sql.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|
  **[オブジェクト エクスプローラーの詳細]** ペインには、接続先の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスでホストされている可用性グループの基本情報が表示されます。<br /><br /> ヒント: このペインを使用して、複数の可用性グループ、レプリカ、またはデータベースを選択し、選択したオブジェクトで一般的な管理タスク (可用性グループからの複数の可用性レプリカまたはデータベースの削除など) を実行します。|[オブジェクトエクスプローラーの詳細を使用して、SQL Server Management Studio &#40;可用性グループを監視&#41;](use-object-explorer-details-to-monitor-availability-groups.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|[**プロパティ**] ダイアログボックスを使用すると、可用性グループ、レプリカ、またはリスナーのプロパティを表示できます。また、場合によっては、値を変更することもできます。|[可用性グループのプロパティの表示 &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md)<br /><br /> [可用性レプリカのプロパティの表示 &#40;SQL Server&#41;](view-availability-replica-properties-sql-server.md)<br /><br /> [可用性グループ リスナーのプロパティの表示 &#40;SQL Server&#41;](view-availability-group-listener-properties-sql-server.md)|  
|システム モニター|
  **SQLServer:Availability Replica** パフォーマンス オブジェクトには、可用性レプリカに関する情報を報告するパフォーマンス カウンターが含まれています。|[SQL Server、Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)|  
|システム モニター|
  **SQLServer:Database Replica** パフォーマンス オブジェクトには、特定のセカンダリ レプリカのセカンダリ データベースに関する情報を報告するパフォーマンス カウンターが含まれています。<br /><br /> SQL Server の **SQLServer:Databases** オブジェクトには、トランザクション ログの利用状況などを監視するパフォーマンス カウンターが含まれています。 可用性データベースでのトランザクション ログの利用状況の監視に関連性が高いカウンターは、 **[Log Flush Write Time (ms)]**、 **[Log Flushes/sec]**、 **[Log Pool Cache Misses/sec]**、 **[Log Pool Disk Reads/sec]**、および **[Log Pool Requests/sec]** です。|[SQL Server、データベースレプリカ](../../../relational-databases/performance-monitor/sql-server-database-replica.md)および[SQL Server、Databases オブジェクト](../../../relational-databases/performance-monitor/sql-server-databases-object.md)|  
  
##  <a name="RelatedContent"></a> 関連コンテンツ  
  
-   **Blog**  
  
     [AlwaysOn の正常性モデル: パート 1: 正常性モデルのアーキテクチャ](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/09/overview-of-the-alwayson-manageability-health-model.aspx)  
  
     [AlwaysOn の正常性モデル: パート 2: 正常性モデルの拡張](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx)  
  
     [Monitoring AlwaysOn Health with PowerShell - Part 1: Basic Cmdlet Overview](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-1.aspx)  
  
     [Monitoring AlwaysOn Health with PowerShell - Part 2: Advanced Cmdlet Usage](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-2.aspx)  
  
     [Monitoring AlwaysOn Health with PowerShell - Part 3 : A Simple Monitoring Application](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/monitoring-alwayson-health-with-powershell-part-3.aspx)  
  
     [Monitoring AlwaysOn Health with PowerShell - Part 4 : Integration with SQL Server Agent](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/the-always-on-health-model-part-4.aspx)  
  
     [SQL Server AlwaysOn チームのブログ:SQL Server AlwaysOn チームのオフィシャル ブログ](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server エンジニアのブログ](https://blogs.msdn.com/b/psssql/)  
  
-   **ペーパー**  
  
     [SQL Server 2012 の Microsoft ホワイトペーパー](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server カスタマーアドバイザリチームのホワイトペーパー](http://sqlcat.com/)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループカタログビュー &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql)   
 [Transact-sql&#41;&#40;の動的管理ビューおよび関数の AlwaysOn 可用性グループ](/sql/relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions)   
 [可用性グループの自動フェールオーバーのための柔軟なフェールオーバーポリシー &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [可用性グループとデータベースミラーリングのための自動ページ修復 &#40;&#41;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [AlwaysOn ダッシュボード &#40;SQL Server Management Studio を使用&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
