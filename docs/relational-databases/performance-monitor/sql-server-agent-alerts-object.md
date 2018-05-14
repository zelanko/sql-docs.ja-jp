---
title: SQL Server エージェントの Alerts オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
caps.latest.revision: 24
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ea269c45f065e03f5583e62ca98f0084e2fb4772
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-agent-alerts-object"></a>SQL Server エージェントの Alerts オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  SQL Server エージェントの **Alerts** パフォーマンス オブジェクトには、SQL Server エージェントの警告に関する情報を報告するパフォーマンス カウンターが含まれています。 次の表は、このオブジェクトに含まれているカウンターを示します。  
  
 次の表では、 **SQLAgent:Alerts** オブジェクトのカウンターを示します。  
  
|[オブジェクト名]|Description|  
|----------|-----------------|  
|**Activated alerts**|最後に SQL Server エージェントが再起動されてから SQL Server エージェントによってアクティブ化された警告の合計数が報告されます。|  
|**Alerts activated/minute**|1 分間に SQL Server エージェントによってアクティブ化された警告の数が報告されます。|  
  
> [!NOTE]  
>  この SQL Server エージェント オブジェクトを使用するには、ユーザーが **sysadmin** 固定サーバー ロールのメンバーである必要があります。  
  
## <a name="see-also"></a>参照  
 [Alerts](http://msdn.microsoft.com/library/3f57d0f0-4781-46ec-82cd-b751dc5affef)   
 [パフォーマンス オブジェクトの使用](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
