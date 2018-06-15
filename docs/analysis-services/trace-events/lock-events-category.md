---
title: ロック イベント カテゴリ |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 62804b077f43b5123b1992a6f52b29af288e2821
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34040337"
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
  
  
