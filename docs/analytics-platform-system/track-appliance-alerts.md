---
title: "アプライアンスのアラート (Analytics Platform System) の追跡します。"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 631345d9-4967-461a-8922-e5f8fd33f48f
caps.latest.revision: "14"
ms.openlocfilehash: a780aa34667280d9e079dad4f44954ba919275d5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="track-appliance-alerts"></a>アプライアンスのアラートを管理します。
このトピックでは、管理コンソールとシステム ビューを使用して、SQL Server PDW アプライアンスにアラートを管理する方法について説明します。  
  
## <a name="to-track-appliance-alerts"></a>アプライアンスのアラートを管理するには  
SQL Server PDW では、注意が必要なハードウェアおよびソフトウェアの問題のアラートを作成します。 各アラートには、タイトルと問題の説明が含まれています。  
  
SQL Server PDW 警告をログに記録、 [sys.dm_pdw_component_health_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-alerts-transact-sql.md) DMV。 システムでは、10,000 のアラートの制限が保持され、制限を超えたときに、まず、最も古いアラートを削除します。  
  
### <a name="view-alerts-by-using-the-admin-console"></a>管理コンソールを使用して、アラートの表示  
**アラート**PDW 地域、HDI リージョンとアプライアンスのファブリック領域のタブです。 フェールオーバーが発生した後は、ページでアラートの数でフェールオーバー イベントが含まれています。 PDW 地域、HDI リージョンとアプライアンスのファブリック領域のページがあります。 各正常性のページには、タブがあります。アラートについての詳細については、をクリックして、**ヘルス** ページで、**アラート** タブし、アラート をクリックします。  
  
![PDW 管理コンソールの警告](./media/track-appliance-alerts/SQL_Server_PDW_AdminConsole_AlertsV2.png "SQL_Server_PDW_AdminConsole_AlertsV2")  
  
**アラート**ページ。  
  
-   アラートの履歴を表示する をクリックして、**レビュー アラート履歴**リンクします。  
  
-   警告のコンポーネントとその現在のプロパティ値を表示するには、アラートの行をクリックします。  
  
-   アラートを生成したノードに関する詳細を表示するには、ノード名をクリックします。  
  
### <a name="view-alerts-by-using-the-system-views"></a>システム ビューを使用してアラートの表示  
アラートを表示するシステム ビューを使用して、クエリ[sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md)です。 この DMV は、修正されたないアラートを表示します。 トリアージの警告とエラーを使用して、 [sys.dm_pdw_errors](../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md) DMV。  
  
次の例は、現在のアラートを表示するための一般的なクエリです。  
  
```sql  
SELECT   
    aa.[pdw_node_id],  
    n.[name] AS [node_name],  
    g.[group_name] ,  
    c.[component_name] ,  
    aa.[component_instance_id] ,   
    a.[alert_name] ,  
    a.[state] ,  
    a.[severity] ,  
    aa.[current_value] ,  
    aa.[previous_value] ,  
    aa.[create_time] ,  
    a.[description]   
FROM [sys].[dm_pdw_component_health_active_alerts] AS aa  
    INNER JOIN sys.dm_pdw_nodes AS n   
        ON aa.[pdw_node_id] = n.[pdw_node_id]  
    INNER JOIN [sys].[pdw_health_components] AS c   
        ON aa.[component_id] = c.[component_id]  
    INNER JOIN [sys].[pdw_health_component_groups] AS g   
        ON c.[group_id] = g.[group_id]  
    INNER JOIN [sys].[pdw_health_alerts] AS a   
        ON aa.[alert_id] = a.[alert_id] and aa.[component_id] = c.[component_id]  
ORDER BY  
    a.alert_id ,  
    aa.[pdw_node_id];  
```  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->
[アプライアンスの監視 &#40;です。Analytics Platform System &#41;](appliance-monitoring.md)  
  
