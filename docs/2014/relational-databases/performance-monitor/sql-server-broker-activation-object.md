---
title: 'SQL Server: Broker Activation オブジェクト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLServer:Broker Activation
- Broker Activation object
ms.assetid: cd9b6880-c924-42c7-b333-09c303317c0b
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 641769c00de48f5acadc69816071893fb6594050
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072760"
---
# <a name="sql-server-broker-activation-object"></a>SQL Server: Broker Activation オブジェクト
  **SQLServer:BrokerActivation** パフォーマンス オブジェクトには、ストアド プロシージャのアクティブ化に関する情報を報告するパフォーマンス カウンターが含まれています。 次の表は、このオブジェクトに含まれているカウンターを示します。  
  
|SQL Server Broker Activation カウンター|説明|  
|-------------------------------------------|-----------------|  
|**Stored Procedures Invoked/sec**|インスタンス内のすべてのキュー モニターによって 1 秒間に呼び出されたアクティブ化ストアド プロシージャの合計数が報告されます。|  
|**Task Limit Reached**|キューに登録できる最大数のタスクが既に実行されているために、キュー モニターで新しいタスクの開始に失敗した合計回数が報告されます。|  
|**Task Limit Reached/sec**|キューに登録できる最大数のタスクが既に実行されているために、キュー モニターで 1 秒間に新しいタスクの開始に失敗した回数が報告されます。|  
|**Tasks Aborted/sec**|エラーが発生して終了したか、メッセージを受信できないためにキュー モニターによって中断されたアクティブ化ストアド プロシージャのタスク数が報告されます。|  
|**Tasks Running**|現在実行中のアクティブ化ストアド プロシージャの数が報告されます。|  
|**Tasks Started/sec**|インスタンス内のすべてのキュー モニターによって 1 秒間に開始されたアクティブ化ストアド プロシージャの数が報告されます。|  
  
## <a name="see-also"></a>参照  
 [sys.dm_broker_activated_tasks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql)   
 [sys.dm_broker_queue_monitors &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql)   
 [リソースの利用状況の監視 &#40;システム モニター&#41;](monitor-resource-usage-system-monitor.md)  
  
  
