---
title: Always On 可用性グループの相互運用性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], interoperability
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 55e19c050d0dd5d0a07c12f88076c423ade3281a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937218"
---
# <a name="always-on-availability-groups-interoperability-sql-server"></a>Always On 可用性グループの相互運用性 (SQL Server)
  このトピックでは、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の他の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 機能との間の [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]の相互運用性について説明します。  
  

  
##  <a name="features-that-interoperate-with-alwayson-availability-groups"></a><a name="Interop"></a>AlwaysOn 可用性グループと相互運用可能な機能  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] と相互運用可能な [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]機能を次の表に示します。 **詳細情報** 列のリンクは、特定の機能に関して相互運用性に関する考慮事項が存在することを示します。  
  
|機能|詳細情報|  
|-------------|----------------------|  
|変更データ キャプチャ|[レプリケーション、Change Tracking、変更データキャプチャ、AlwaysOn 可用性グループ &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|Change tracking|[レプリケーション、Change Tracking、変更データキャプチャ、AlwaysOn 可用性グループ &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|包含データベース|[包含データベースと AlwaysOn 可用性グループ (SQL Server)](always-on-availability-groups-sql-server.md)|  
|データベース暗号化|[AlwaysOn 可用性グループ &#40;SQL Server を持つ暗号化されたデータベース&#41;](encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|データベース スナップショット|[AlwaysOn 可用性グループ &#40;SQL Server を持つデータベーススナップショット&#41;](database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|FILESTREAM と FileTable|[AlwaysOn 可用性グループ &#40;SQL Server を使用した FILESTREAM と FileTable&#41;](filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|フルテキスト検索|注: フルテキスト インデックスは、AlwaysOn セカンダリ データベースと同期されます。|  
|ログ配布|[ログ配布から AlwaysOn 可用性グループ &#40;SQL Server への移行の前提条件&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)|  
|リモート BLOB ストア (RBS)|[リモート Blob ストア &#40;RBS&#41; と AlwaysOn 可用性グループ &#40;SQL Server&#41;](remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|レプリケーション[で AlwaysOn 可用性グループのレプリケーションを構成する (SQL Server)](configure-replication-for-always-on-availability-groups-sql-server.md)<br /><br /> [AlwaysOn パブリケーションデータベースのメンテナンス &#40;SQL Server&#41;](maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [レプリケーション、Change Tracking、変更データキャプチャ、AlwaysOn 可用性グループ &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)<br /><br /> [レプリケーションサブスクライバーと AlwaysOn 可用性グループ &#40;SQL Server&#41;](replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|Analysis Services|[Analysis Services と AlwaysOn 可用性グループ](analysis-services-with-always-on-availability-groups.md)|  
|Reporting Services|読み取り専用セカンダリ レプリカをレポート データ ソースとして使用し、読み取り/書き込み可能なプライマリ レプリカの負荷を軽減します。<br /><br /> [Reporting Services AlwaysOn 可用性グループ &#40;SQL Server&#41;](reporting-services-with-always-on-availability-groups-sql-server.md)|  
|Service Broker|[Service Broker AlwaysOn 可用性グループ &#40;SQL Server&#41;](service-broker-with-always-on-availability-groups-sql-server.md)|  
|SQL Server エージェント||  
  
##  <a name="features-that-do-not-interoperate-with-alwayson-availability-groups"></a><a name="NoInterop"></a>AlwaysOn 可用性グループと相互運用できない機能  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] は、次の機能との相互運用はできません。  
  
-   複数データベースにまたがるトランザクション/分散トランザクション  
  
     このようなトランザクションがサポートされない理由の詳細については、「[データベース ミラーリングまたは AlwaysOn 可用性グループではサポートされない複数データベースにまたがるトランザクション &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md)」を参照してください。  
  
-   データベース ミラーリング  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> 関連コンテンツ  
  
-   **ブログ:**  
  
     [移行ガイド：以前のクラスタリングおよびミラーリングの展開によるSQL Server 2012フェールオーバークラスタリングおよび可用性グループへの移行](https://blogs.msdn.com/b/sqlalwayson/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [SQL Server AlwaysOn チームのブログ:SQL Server AlwaysOn チームのオフィシャル ブログ](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server エンジニアのブログ](https://blogs.msdn.com/b/psssql/)  
  
-   **ホワイト ペーパー:**  
  
     [Migration Guide: Migrating to AlwaysOn Availability Groups from Prior Deployments Combining Database Mirroring and Log Shipping](https://msdn.microsoft.com/library/jj635217)  
  
     [高可用性と災害復旧のための Microsoft SQL Server AlwaysOn ソリューション ガイド](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [SQL Server 2012 に関する Microsoft ホワイト ペーパー](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server ユーザー諮問チームのホワイト ペーパー](http://sqlcat.com/)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
