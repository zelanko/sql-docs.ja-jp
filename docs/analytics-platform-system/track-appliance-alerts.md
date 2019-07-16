---
title: アプライアンスの警告 - Analytics Platform System の追跡 |Microsoft Docs
description: Analytics Platform System でアプライアンスの警告を追跡します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 62f116b8e45512d5a6fc5ce50c0fbc76344103be
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960029"
---
# <a name="track-appliance-alerts-in-analytics-platform-system"></a>Analytics Platform System でアプライアンスの警告を追跡します。
このトピックでは、管理コンソールとシステム ビューを使用して、SQL Server PDW アプライアンスでアラートを管理する方法について説明します。  
  
## <a name="to-track-appliance-alerts"></a>アプライアンスの警告を追跡するには  
SQL Server PDW では、注意が必要なハードウェアとソフトウェアの問題のアラートを作成します。 各アラートには、タイトルと、問題の説明が含まれています。  
  
SQL Server PDW でアラートのログ、 [sys.dm_pdw_component_health_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-alerts-transact-sql.md) DMV。 システムでは、10,000 のアラートの制限が保持され、制限を超えたときに最初に、最も古いアラートを削除します。  
  
### <a name="view-alerts-by-using-the-admin-console"></a>管理者コンソールを使用してアラートの表示  
**アラート**PDW リージョンと、アプライアンスの fabric 領域のタブ。 フェールオーバーの発生後のページでアラートの数には、フェールオーバー イベントが含まれます。 PDW リージョンと、アプライアンスのファブリックのリージョンのページがあります。 各正常性ページには、タブがあります。アラートについての詳細については、次のようにクリックします。、**正常性** ページで、**アラート**タブをクリックし、アラート をクリックします。  
  
![PDW 管理コンソールの警告](./media/track-appliance-alerts/SQL_Server_PDW_AdminConsole_AlertsV2.png "SQL_Server_PDW_AdminConsole_AlertsV2")  
  
**アラート**ページ。  
  
-   アラートの履歴を表示する をクリックして、**レビュー アラート履歴**リンク。  
  
-   アラートのコンポーネントとその現在のプロパティ値を表示するには、アラートの行をクリックします。  
  
-   アラートを生成したノードに関する詳細を表示するには、ノード名をクリックします。  
  
### <a name="view-alerts-by-using-the-system-views"></a>システム ビューを使用してアラートの表示  
システム ビューを使用してアラートを表示するにはクエリ[sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md)します。 この DMV ではないが修正されているアラートが表示されます。 アラートのトリアージとエラーについてを使用して、 [sys.dm_pdw_errors](../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md) DMV。  
  
次の例では、現在のアラートを表示するための一般的なクエリです。  
  
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
  
## <a name="see-also"></a>関連項目  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->
[アプライアンスの監視&#40;Analytics Platform System&#41;](appliance-monitoring.md)  
  
