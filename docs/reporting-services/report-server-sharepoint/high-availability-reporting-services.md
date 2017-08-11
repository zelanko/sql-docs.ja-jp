---
title: "高可用性 (Reporting Services) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- high availability [SQL Server], Reporting Services
- high availability [Reporting Services]
- Reporting Services, high availability
ms.assetid: 50e0813f-f591-4688-9cd1-e6389a3808e5
caps.latest.revision: 16
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b4b2d373dfc2467e10a9a6ee79d98aa3a690bd4c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="high-availability-reporting-services"></a>高可用性 (Reporting Services)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーは、アプリケーションのデータ、コンテンツ、プロパティ、およびセッション情報を 2 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リレーショナル データベースに格納するステートレス サーバーです。 したがって、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の可用性を確保するには、次のことを検討する必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]の高可用性機能を使用して、レポート サーバー データベースの稼働時間を最大限に保つ。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスをフェールオーバー クラスターで実行するように構成した場合、そのインスタンスをレポート サーバー データベースの作成時に選択できます。  
  
-   できるだけ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]を、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データベースと共に、またデータ ソース用に使用する。 詳細については、次を参照してください[Always On 可用性グループ &#40; での Reporting Services。SQL Server &#41;](../../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md).  
  
-   複数のレポート サーバーをスケールアウト配置で実行するように構成する。この場合、すべてのサーバーは単一のレポート サーバー データベースを共有することになります。 複数のレポート サーバー インスタンスを (可能であれば異なるサーバーに) スケールアウト配置することにより、いずれかのレポート サーバー インスタンスがダウンした場合でも、サービスの中断を効果的に防ぐことができます。  
  
 スケールアウト配置により、データベースの共有が可能となります。 どれか 1 つのレポート サーバーがダウンしても、同じ配置内の他のサーバーが処理を続行します。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]クラスター対応ではありません。 スケールアウト配置自体は負荷分散機能を備えていないため、レポート サーバーの処理負荷を検出したり、新しい処理要求を最も負荷の低いサーバーにルーティングしたりすることはできません。 エラーが発生して完了しなかった処理要求が再ルーティングされることもありません。 負荷分散機能を実現するためには、レポート サーバーをホストする Web サーバーに対して負荷分散を構成し、それらのレポート サーバーが同じレポート サーバー データベースを共有するようにスケールアウト配置で構成する必要があります。  
  
 レポート サーバーの Web サービスと Windows サービスは単一のレポート サーバー インスタンスとして緊密に統合され、互いに連携して動作します。 どちらか一方のサービスに対して個別に可用性を構成することはできません。  
  
## <a name="see-also"></a>「  
 [高可用性ソリューション &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [スケール アウト配置 - Reporting Services のネイティブ モード & #40 です。構成マネージャー &#41;](http://msdn.microsoft.com/library/4df38294-6f9d-4b40-9f03-1f01c1f0700c)  
  
  
