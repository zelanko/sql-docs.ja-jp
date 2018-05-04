---
title: ロック イベント カテゴリ |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 06427f8e-89bb-4710-a0c1-dc5e42b7e95e
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fe7c4c743e8a111f4a489ee47c8a1fd8ef865663
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
  
  
