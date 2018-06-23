---
title: 可用性グループの作成と構成 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], creating
ms.assetid: 7f89fab8-6ee2-4273-9de0-e594bfb9407f
caps.latest.revision: 27
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: e7d93c8a1b85d663c5c1590b76c4bf98f5050b3c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165312"
---
# <a name="creation-and-configuration-of-availability-groups-sql-server"></a>可用性グループの作成と構成 (SQL Server)
  このセクションの各トピックでは、単一の WSFC (Windows Server フェールオーバー クラスタリング) フェールオーバー クラスターを構成する各 WSFC ノード上の [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のインスタンスに対し、 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の実装を配置する方法について説明します。  
  
 可用性グループを初めて作成する前に、次のトピックの情報をよく理解しておくことを強くお勧めします。  
  
 [前提条件、制限事項、および AlwaysOn 可用性グループに関する推奨事項&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
 このトピックでは、コンピューター、WSFC ノード、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンス、可用性グループ、可用性レプリカ、および可用性データベースに関して、それぞれの前提条件、制限、および推奨事項を取り上げます。 このトピックでは、セキュリティに関する考慮事項も取り上げています。  
  
 [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](getting-started-with-always-on-availability-groups-sql-server.md)  
 サーバー インスタンスの構成、可用性グループの構成、クライアント接続に必要な可用性グループの構成、可用性グループの管理、可用性グループの監視について、それぞれ手順を紹介します。  
  
 
  
##  <a name="RelatedTasks"></a> 関連タスク  
 **サーバー インスタンスを [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**  
  
-   [AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [データベース ミラーリング エンドポイントの AlwaysOn 可用性グループの作成&#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
 **AlwaysOn 可用性グループの構成を開始するには**  
  
-   [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](getting-started-with-always-on-availability-groups-sql-server.md)  
  
 **新しい可用性グループを作成して構成するには**  
  
-   [可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [可用性グループの作成 &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)  
  
-   [可用性グループの作成 &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)  
  
-   [[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [条件を制御する自動フェールオーバー (AlwaysOn 可用性グループ) の柔軟なフェールオーバー ポリシーを構成します。](configure-flexible-automatic-failover-policy.md)  
  
-   [可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [可用性グループの読み取り専用ルーティングの構成 &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [AlwaysOn セカンダリ データベース上のデータ移動の開始&#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [可用性グループのデータベースのためのログインとジョブの管理 &#40;SQL Server&#41;](../../logins-and-jobs-for-availability-group-databases.md)  
  
 **トラブルシューティングするには**  
  
-   [AlwaysOn 可用性グループの構成 (SQL Server) は削除のトラブルシューティングします。](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [失敗したファイルの追加操作のトラブルシューティング&#40;AlwaysOn 可用性グループ&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> 関連コンテンツ  
  
-   **ブログ:**  
  
     [AlwaysON - HADRON 学習シリーズ: Worker Pool Usage for HADRON 対応データベース](http://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [SQL Server AlwaysOn チームのブログ: 公式 SQL Server AlwaysOn チームのブログ](http://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server エンジニアのブログ](http://blogs.msdn.com/b/psssql/)  
  
-   **ビデオ:**  
  
     [Microsoft SQL Server コードネーム"Denali"AlwaysOn シリーズ パート 1: 概要次世代の高可用性ソリューション](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server コードネーム"Denali"AlwaysOn シリーズ パート 2: 構築 AlwaysOn を使用したミッション クリティカルな高可用性ソリューション](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **ホワイト ペーパー:**  
  
     [高可用性と災害復旧の Microsoft SQL Server AlwaysOn ソリューション ガイド](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [SQL Server 2012 に関する Microsoft ホワイト ペーパー](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server ユーザー諮問チームのホワイト ペーパー](http://sqlcat.com/)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [可用性グループの管理 &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md)   
 [AlwaysOn ポリシーの運用上の問題と AlwaysOn 可用性グループ (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md)   
 [可用性グループの監視 &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [AlwaysOn 可用性グループ: 相互運用性 (SQL Server)](always-on-availability-groups-interoperability-sql-server.md)  
  
  