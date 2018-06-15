---
title: アプライアンスの状態の監視 - 分析プラットフォーム システム
description: 管理コンソールを使用するか、並列データ ウェアハウスの動的管理ビューを直接照会して、Analytics Platform System アプライアンスの状態を監視する方法。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d8616d291dcaa8afadc01c9bd237903ca6c13573
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31539052"
---
# <a name="monitor-appliance-health-state"></a>アプライアンス正常性状態の監視
この記事では、管理コンソールを使用するか、並列データ ウェアハウスの動的管理ビューを直接照会して、Analytics Platform System アプライアンスの状態を監視する方法について説明します。 
  
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
  
**[Update_time]** 列コンポーネントが SQL Server PDW の正常性エージェントがポーリングされた最終時刻を示しています。  
  
> [!CAUTION]  
> コンポーネントは 5 分以上; ポーリングされていないときに、問題を調査してください。ソフトウェアのハートビートの問題を示すアラートがあります。  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[アプライアンス監視&#40;分析プラットフォーム システム&#41;](appliance-monitoring.md)  
  
