---
title: アプライアンスの状態の監視 - Analytics Platform System
description: 管理者コンソールを使用して、または Parallel Data Warehouse の動的管理ビューを直接照会して、Analytics Platform System appliance の状態を監視する方法。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: c69e46ad6a37a17a12c37f83625b5c7f6eaf8078
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960614"
---
# <a name="monitor-appliance-health-state"></a>アプライアンス正常性状態の監視
この記事では、管理者コンソールを使用して、または Parallel Data Warehouse の動的管理ビューを直接照会して、Analytics Platform System appliance の状態を監視する方法について説明します。 
  
## <a name="to-monitor-the-appliance-state"></a>アプライアンスの状態を監視するには  
システム管理者は、ノード、コンポーネント、およびソフトウェアの完全な階層を取得するのに管理コンソールまたは、SQL Server PDW 動的管理ビュー (Dmv) を使用できます。 次の図は、SQL Server PDW を監視するコンポーネントの高レベルの理解をできます。  
  
![監視の概要](./media/monitor-appliance-health-state/SQL_Server_PDW_Monitoring_Overview.png "SQL_Server_PDW_Monitoring_Overview")  
  
### <a name="monitor-component-status-by-using-the-admin-console"></a>管理者コンソールを使用して監視コンポーネントのステータス  
管理者コンソールを使用して、コンポーネントのステータスを取得します。  
  
1.  をクリックして、**のアプライアンス状態**タブ。  
  
2.  アプライアンスの状態 ページで、ノードの詳細を表示する特定のノードをクリックします。  
  
    ![PDW 管理コンソールの状態](./media/monitor-appliance-health-state/SQL_Server_PDW_AdminConsol_State.png "SQL_Server_PDW_AdminConsol_State")  
  
### <a name="monitor-component-status-by-using-system-views"></a>システム ビューを使用して監視コンポーネントのステータス  
システム ビューを使用してコンポーネントのステータスを取得する[sys.dm_pdw_component_health_status](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md)します。 たとえば、次のクエリでは、すべてのコンポーネントのステータスを取得します。  
  
```sql  
SELECT   
   s.[pdw_node_id],  
   n.[name] as [node_name],  
   n.[address] ,  
   g.[group_id] ,  
   g.[group_name] ,  
   c.[component_id] ,  
   c.[component_name] ,  
   s.[component_instance_id] ,   
   p.[property_name] ,  
   s.[property_value] ,  
   s.[update_time]  
FROM [sys].[dm_pdw_component_health_status] AS s  
JOIN sys.dm_pdw_nodes AS n   
   ON s.[pdw_node_id] = n.[pdw_node_id]  
JOIN [sys].[pdw_health_components] AS c   
   ON s.[component_id] = c.[component_id]  
JOIN [sys].[pdw_health_component_groups] AS g   
   ON c.[group_id] = g.[group_id]  
JOIN [sys].[pdw_health_component_properties] AS p   
   ON s.[property_id] = p.[property_id] AND s.[component_id] = p.[component_id]  
WHERE p.property_name = 'Status'  
ORDER BY  
   s.[pdw_node_id],  
   g.[group_name] ,   
   s.[component_instance_id] ,  
   c.[component_name] ,   
   p.[property_name];  
```  
  
Status プロパティの返される値は次のとおりです。  
  
-   わかりました  
  
-   重大でないです。  
  
-   重大  
  
-   Unknown  
  
-   サポートされていない  
  
-   到達できません。  
  
-   回復不能です  
  
すべてのコンポーネントのすべてのプロパティを表示するには、削除、`WHERE  p.property_name = 'Status'`句。  
  
**[Update_time]** 列には、コンポーネントが SQL Server PDW の正常性エージェントがポーリングされた最終時刻。  
  
> [!CAUTION]  
> コンポーネントは 5 分以上; ポーリングされていないすると、問題を調査してください。ソフトウェアのハートビートの問題を示すアラートがあります。  
  
## <a name="see-also"></a>関連項目  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[アプライアンスの監視&#40;Analytics Platform System&#41;](appliance-monitoring.md)  
  
