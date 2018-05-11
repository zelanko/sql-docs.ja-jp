---
title: ロック イベント カテゴリ |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7885e7dd6090a1877ca40337b6aae1abde886132
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="lock-events-category"></a>ロック イベント カテゴリ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
  
  
