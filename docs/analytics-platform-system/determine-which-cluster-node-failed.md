---
title: 障害が発生したクラスター ノードの Analytics Platform System を決める |Microsoft ドキュメント
description: この記事では、クラスターのフェールオーバーが発生し、クラスター フェールオーバーの警告が発生しました後に失敗しました Analytics Platform System (APS) ノードの名前を確認する方法について説明します。 クラスターのフェイル オーバーのトラブルシューティングの一環として、問題を解決するためにマイクロソフトに連絡する前に失敗したノードの名前を決定する必要があります。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 031c8033e91d7a7f74ca8c4409bc02296a22ebcf
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31544744"
---
# <a name="determine-which-cluster-node-failed-for-analytics-platform-system"></a>どのクラスター決定 Analytics Platform System のノードに失敗しました
このトピックでは、クラスターのフェールオーバーが発生し、クラスター フェールオーバーの警告が発生しました後に失敗しました Analytics Platform System (APS) ノードの名前を確認する方法について説明します。 クラスターのフェイル オーバーのトラブルシューティングの一環として、問題を解決するためにマイクロソフトに連絡する前に失敗したノードの名前を決定する必要があります。  
  
## <a name="Background"></a>バック グラウンド  
SQL Server PDW で高可用性は、コントロールのノードとコンピューティング ノードは、Windows フェールオーバー クラスターのアクティブまたはパッシブのコンポーネントとして構成されます。 アクティブなサーバーは、重要なシステムの要求に応答する失敗した場合、パッシブのサーバーはフェールオーバーされ、失敗したサーバーの機能を実行します。  
  
クラスターのフェールオーバー後に SQL Server PDW は、ノードの状態を報告したときにパッシブのサーバーが、失敗した状態にします。 ただし、にない明白などのサーバーまたはノードが失敗しました、失敗したサーバーがオンラインのままである場合に特にです。 クラスター障害のトラブルシューティング中に、失敗したノードの名前を決定する必要があります。  
  
## <a name="AdminConsoleSolution"></a>管理コンソールのソリューション  
  
#### <a name="to-find-the-name-of-the-node-that-failed"></a>失敗したノードの名前を検索するには  
  
1.  管理コンソールを開きます。 管理者コンソールの詳細については、次を参照してください。[アプライアンスを管理コンソールを使用して監視&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)です。 アラートの数でフェールオーバー イベントが含まれるフェールオーバーが発生した後、**ヘルス**ページ。 **ヘルス**PDW 地域、HDI 地域およびアプライアンスのファブリック領域のページが表示されます。 各正常性のページには、**アラート**タブです。アラートについての詳細については、正常性 ページで、アラート タブをクリックし、アラート をクリックします。  
  
## <a name="SystemView"></a>システム ビューのソリューション  
次の SQL ステートメントを使用する方法を示しています、 [sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md)失敗したサーバーの名前を検索するシステム ビューです。  
  
```sql  
SELECT  
SUBSTRING( component_instance_id, 2, charindex(' ', component_instance_id, 1)-2) AS failed_node_name,  
create_time AS failover_time  
FROM sys.dm_pdw_component_health_active_alerts  
WHERE alert_id = 500139  
ORDER BY failed_node_name;  
```  
  
