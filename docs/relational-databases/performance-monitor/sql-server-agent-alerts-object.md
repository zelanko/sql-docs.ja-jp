---
title: SQL Server エージェントの Alerts オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 425a2330f8ecb3f33380cf0500de32e82463634e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787401"
---
# <a name="sql-server-agent-alerts-object"></a>SQL Server エージェントの Alerts オブジェクト
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  SQL Server エージェントの **Alerts** パフォーマンス オブジェクトには、SQL Server エージェントの警告に関する情報を報告するパフォーマンス カウンターが含まれています。 次の表は、このオブジェクトに含まれているカウンターを示します。  
  
 次の表では、 **SQLAgent:Alerts** オブジェクトのカウンターを示します。  
  
|Name|説明|  
|----------|-----------------|  
|**Activated alerts**|最後に SQL Server エージェントが再起動されてから SQL Server エージェントによってアクティブ化された警告の合計数が報告されます。|  
|**Alerts activated/minute**|1 分間に SQL Server エージェントによってアクティブ化された警告の数が報告されます。|  
  
> [!NOTE]  
>  この SQL Server エージェント オブジェクトを使用するには、ユーザーが **sysadmin** 固定サーバー ロールのメンバーである必要があります。  
  
## <a name="see-also"></a>参照  
 [Alerts](../../ssms/agent/alerts.md)   
 [パフォーマンス オブジェクトの使用](../../ssms/agent/use-performance-objects.md)   
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
