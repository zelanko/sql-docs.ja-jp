---
title: "モニター アプライアンス正常性状態 (Analytics Platform System)"
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
ms.assetid: 91132e3c-3137-4670-adaa-8a7b234fb8d2
caps.latest.revision: "12"
ms.openlocfilehash: dad3355061bafcbbfa3a34b21d2043b0411129ba
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="monitor-appliance-health-state"></a>アプライアンス正常性状態の監視
このトピックでは、管理コンソールを使用するか、SQL Server PDW 動的管理ビューを直接照会するには、SQL Server PDW アプライアンスの状態を監視する方法について説明します。  
  
## <a name="to-monitor-the-appliance-state"></a>アプライアンスの状態を監視するには  
システム管理者は、ノード、コンポーネント、およびソフトウェアの完全な階層を取得するのに、管理コンソールまたは、SQL Server PDW 動的管理ビュー (Dmv) を使用できます。 次の図は、SQL Server PDW を監視するコンポーネントの高レベルな理解を示します。  
  
![監視の概要](./media/monitor-appliance-health-state/SQL_Server_PDW_Monitoring_Overview.png "SQL_Server_PDW_Monitoring_Overview")  
  
### <a name="monitor-component-status-by-using-the-admin-console"></a>管理者コンソールを使用してモニターのコンポーネントのステータス  
管理者コンソールを使用してコンポーネントのステータスを取得します。  
  
1.  をクリックして、**のアプライアンス状態**タブです。  
  
2.  アプライアンスの状態 ページで、ノードの詳細を表示する特定のノードをクリックします。  
  
    ![PDW 管理コンソールの状態](./media/monitor-appliance-health-state/SQL_Server_PDW_AdminConsol_State.png "SQL_Server_PDW_AdminConsol_State")  
  
### <a name="monitor-component-status-by-using-system-views"></a>システム ビューを使用してモニターのコンポーネントのステータス  
システム ビューを使用してコンポーネントのステータスを取得する[sys.dm_pdw_component_health_status](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md)です。 たとえば、次のクエリは、すべてのコンポーネントのステータスを取得します。  
  
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
  
Status プロパティを返される値は次のとおりです。  
  
-   わかりました  
  
-   重大でないです。  
  
-   重大  
  
-   Unknown  
  
-   サポートされていない  
  
-   到達できません。  
  
-   回復不能です  
  
すべてのコンポーネントのすべてのプロパティを表示するには、削除、`WHERE  p.property_name = 'Status'`句。  
  
**[Update_time]**列コンポーネントが SQL Server PDW の正常性エージェントがポーリングされた最終時刻を示しています。  
  
> [!CAUTION]  
> コンポーネントは 5 分以上; ポーリングされていないときに、問題を調査してください。ソフトウェアのハートビートの問題を示すアラートがあります。  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[アプライアンスの監視 &#40;です。Analytics Platform System &#41;](appliance-monitoring.md)  
  
