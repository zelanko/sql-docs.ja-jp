---
title: "ロック イベント カテゴリ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 06427f8e-89bb-4710-a0c1-dc5e42b7e95e
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4fbe7cccb4caaa0b87a7f502ed3ca714e3efa515
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lock-events-category"></a>ロック イベント カテゴリ
  ロック イベントのイベント カテゴリには、次の表に示したイベント クラスがあります。  
  
|Event Class|イベント ID|Description|  
|-----------------|--------------|-----------------|  
|Deadlock|50|トレースが開始されてからのすべてのメタデータ ロックのデッドロック イベントを収集します。|  
|Lock timeout|51|トレースが開始されてからのすべてのメタデータ ロックのタイムアウト イベントを収集します。|  
|Lock Acquired|52|トレースが開始されてから取得したロックについての情報を収集します。|  
|Lock Released|53|トレースが開始されてから解放したロックについての情報を収集します。|  
|Lock Waiting|54|トレースが開始されてから待機状態になっているロックについての情報を収集します。|  
  
 各 Lock イベント クラスに関連する列については、「 [Lock Events Data Columns](../../analysis-services/trace-events/lock-events-data-columns.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services トレース イベント](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  

