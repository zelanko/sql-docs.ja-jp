---
title: Always On 可用性グループの相互運用性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], interoperability
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
caps.latest.revision: 18
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: e7a8ea0a461bb261b8a85769b0fe2048e6cc569c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175821"
---
# <a name="always-on-availability-groups-interoperability-sql-server"></a>Always On 可用性グループの相互運用性 (SQL Server)
  このトピックでは、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の他の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 機能との間の [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]の相互運用性について説明します。  
  

  
##  <a name="Interop"></a> AlwaysOn 可用性グループと相互運用機能  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] と相互運用可能な [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]機能を次の表に示します。 **詳細情報** 列のリンクは、特定の機能に関して相互運用性に関する考慮事項が存在することを示します。  
  
|機能|詳細情報|  
|-------------|----------------------|  
|変更データ キャプチャ|[レプリケーション、変更の追跡、変更データ キャプチャ、および AlwaysOn 可用性グループ&#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|変更の追跡|[レプリケーション、変更の追跡、変更データ キャプチャ、および AlwaysOn 可用性グループ&#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|包含データベース|[包含データベースと AlwaysOn 可用性グループ (SQL Server)](always-on-availability-groups-sql-server.md)|  
|データベース暗号化|[暗号化されたデータベースと AlwaysOn 可用性グループ&#40;SQL Server&#41;](encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|データベース スナップショット|[データベースと AlwaysOn 可用性グループのスナップショット&#40;SQL Server&#41;](database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|FILESTREAM と FileTable|[FILESTREAM および FileTable と AlwaysOn 可用性グループ&#40;SQL Server&#41;](filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|フルテキスト検索|注: フルテキスト インデックスは、AlwaysOn セカンダリ データベースと同期されます。|  
|ログ配布|[AlwaysOn 可用性グループからの移行の前提条件のログ配布&#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)|  
|リモート BLOB ストア (RBS)|[リモート Blob ストア&#40;RBS&#41;と AlwaysOn 可用性グループ&#40;SQL Server&#41;](remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|レプリケーション[AlwaysOn 可用性グループ (SQL Server) のレプリケーションを構成します。](configure-replication-for-always-on-availability-groups-sql-server.md)<br /><br /> [AlwaysOn パブリケーション データベースのメンテナンス&#40;SQL Server&#41;](maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [レプリケーション、変更の追跡、変更データ キャプチャ、および AlwaysOn 可用性グループ&#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)<br /><br /> [レプリケーション サブスクライバーと AlwaysOn 可用性グループ&#40;SQL Server&#41;](replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|Analysis Services|[Analysis Services と AlwaysOn 可用性グループ](analysis-services-with-always-on-availability-groups.md)|  
|Reporting Services|読み取り専用セカンダリ レプリカをレポート データ ソースとして使用し、読み取り/書き込み可能なプライマリ レプリカの負荷を軽減します。<br /><br /> [Reporting Services と AlwaysOn 可用性グループ&#40;SQL Server&#41;](reporting-services-with-always-on-availability-groups-sql-server.md)|  
|Service Broker|[Service Broker と AlwaysOn 可用性グループ&#40;SQL Server&#41;](service-broker-with-always-on-availability-groups-sql-server.md)|  
|SQL Server エージェント||  
  
##  <a name="NoInterop"></a> AlwaysOn 可用性グループと相互運用不可能機能  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] は、次の機能との相互運用はできません。  
  
-   複数データベースにまたがるトランザクション/分散トランザクション  
  
     このようなトランザクションがサポートされない理由の詳細については、「[データベース ミラーリングまたは AlwaysOn 可用性グループではサポートされない複数データベースにまたがるトランザクション &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md)」を参照してください。  
  
-   データベース ミラーリング  
  
##  <a name="RelatedContent"></a> 関連コンテンツ  
  
-   **ブログ:**  
  
     [移行ガイド：以前のクラスタリングおよびミラーリングの展開によるSQL Server 2012フェールオーバークラスタリングおよび可用性グループへの移行](http://blogs.msdn.com/b/sqlalwayson/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [SQL Server AlwaysOn チームのブログ: 公式 SQL Server AlwaysOn チームのブログ](http://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server エンジニアのブログ](http://blogs.msdn.com/b/psssql/)  
  
-   **ホワイト ペーパー:**  
  
     [AlwaysOn 可用性グループに移行する移行ガイド: 以前の配置の結合データベース ミラーリングとログ配布から](http://msdn.microsoft.com/library/jj635217)  
  
     [高可用性と災害復旧の Microsoft SQL Server AlwaysOn ソリューション ガイド](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [SQL Server 2012 に関する Microsoft ホワイト ペーパー](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server ユーザー諮問チームのホワイト ペーパー](http://sqlcat.com/)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [前提条件、制限事項、および AlwaysOn 可用性グループに関する推奨事項&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  