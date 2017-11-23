---
title: "失敗した (Analytics Platform System) のクラスター ノードを特定します。"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1e001117-a1b6-4357-bf25-e85aba3f1cf0
caps.latest.revision: "21"
ms.openlocfilehash: 59f188526cff2d605c5bffcf2187b3c765276c81
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="determine-which-cluster-node-failed"></a>クラスター ノードでエラーの特定します。
このトピックでは、クラスターのフェールオーバーが発生したし、クラスター フェールオーバーの警告が発生しましたが失敗した SQL Server PDW ノードの名前を確認する方法について説明します。 クラスターのフェイル オーバーのトラブルシューティングの一環として、問題を解決するためにマイクロソフトに連絡する前に失敗したノードの名前を決定する必要があります。  
  
## <a name="Background"></a>バック グラウンド  
SQL Server PDW で高可用性は、コントロールのノードとコンピューティング ノードは、Windows フェールオーバー クラスターのアクティブまたはパッシブのコンポーネントとして構成されます。 アクティブなサーバーは、重要なシステムの要求に応答する失敗した場合、パッシブのサーバーはフェールオーバーされ、失敗したサーバーの機能を実行します。  
  
クラスターのフェールオーバー後に SQL Server PDW は、ノードの状態を報告したときにパッシブのサーバーが、失敗した状態にします。 ただし、にない明白などのサーバーまたはノードが失敗しました、失敗したサーバーがオンラインのままである場合に特にです。 クラスター障害のトラブルシューティング中に、失敗したノードの名前を決定する必要があります。  
  
## <a name="AdminConsoleSolution"></a>管理コンソールのソリューション  
  
#### <a name="to-find-the-name-of-the-node-that-failed"></a>失敗したノードの名前を検索するには  
  
1.  管理コンソールを開きます。 管理者コンソールの詳細については、次を参照してください[アプライアンスを管理コンソール &#40; を使用して監視する。Analytics Platform System &#41;](monitor-the-appliance-by-using-the-admin-console.md). アラートの数でフェールオーバー イベントが含まれるフェールオーバーが発生した後、**ヘルス**ページ。 **ヘルス**PDW 地域、HDI 地域およびアプライアンスのファブリック領域のページが表示されます。 各正常性のページには、**アラート**タブです。アラートについての詳細については、正常性 ページで、アラート タブをクリックし、アラート をクリックします。  
  
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
  
