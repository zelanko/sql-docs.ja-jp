---
title: 高可用性 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], Reporting Services
- high availability [Reporting Services]
- Reporting Services, high availability
ms.assetid: 50e0813f-f591-4688-9cd1-e6389a3808e5
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0884a284e6d9169ce978d3c47330a683e2bb6b52
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37150223"
---
# <a name="high-availability-reporting-services"></a>高可用性 (Reporting Services)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバーは、アプリケーションのデータ、コンテンツ、プロパティ、およびセッション情報を 2 つの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] リレーショナル データベースに格納するステートレス サーバーです。 などの可用性を確保する最善の方法として[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]機能は、次の操作には。  
  
-   高可用性機能を使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)]レポート サーバー データベースのアップタイムを最大にします。 構成する場合、[!INCLUDE[ssDE](../includes/ssde-md.md)]インスタンス、フェールオーバー クラスターで実行する、レポート サーバー データベースを作成するときに、そのインスタンスを選択できます。  
  
-   できるだけ、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../includes/sshadr-md.md)]を、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] データベースと共に、またデータ ソース用に使用する。 詳細については、「[Reporting Services with AlwaysOn Availability Groups (SQL Server)](../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md)」(Reporting Services と AlwaysOn 可用性グループ (SQL Server)) を参照してください。  
  
-   複数のレポート サーバーをスケールアウト配置で実行するように構成する。この場合、すべてのサーバーは単一のレポート サーバー データベースを共有することになります。 複数のレポート サーバー インスタンスを (可能であれば異なるサーバーに) スケールアウト配置することにより、いずれかのレポート サーバー インスタンスがダウンした場合でも、サービスの中断を効果的に防ぐことができます。  
  
 スケールアウト配置により、データベースの共有が可能となります。 どれか 1 つのレポート サーバーがダウンしても、同じ配置内の他のサーバーが処理を続行します。  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] はクラスターに対応していません。 スケールアウト配置自体は負荷分散機能を備えていないため、レポート サーバーの処理負荷を検出したり、新しい処理要求を最も負荷の低いサーバーにルーティングしたりすることはできません。 エラーが発生して完了しなかった処理要求が再ルーティングされることもありません。 負荷分散機能を実現するためには、レポート サーバーをホストする Web サーバーに対して負荷分散を構成し、それらのレポート サーバーが同じレポート サーバー データベースを共有するようにスケールアウト配置で構成する必要があります。  
  
 レポート サーバーの Web サービスと Windows サービスは単一のレポート サーバー インスタンスとして緊密に統合され、互いに連携して動作します。 どちらか一方のサービスに対して個別に可用性を構成することはできません。  
  
## <a name="see-also"></a>参照  
 [高可用性ソリューション &#40;SQL Server&#41;](../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [ネイティブ モード レポート サーバーのスケール アウト配置構成&#40;SSRS 構成マネージャー&#41;](install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
  
  
