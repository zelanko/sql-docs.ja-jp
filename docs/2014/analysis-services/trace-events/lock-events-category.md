---
title: ロック イベント カテゴリ |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06427f8e-89bb-4710-a0c1-dc5e42b7e95e
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8e9bb88bb19f92ea383049ac62a500d1b0f5319f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177603"
---
# <a name="lock-events-category"></a>ロック イベント カテゴリ
  ロック イベントのイベント カテゴリには、次の表に示したイベント クラスがあります。  
  
|Event Class|イベント ID|説明|  
|-----------------|--------------|-----------------|  
|Deadlock|50|トレースが開始されてからのすべてのメタデータ ロックのデッドロック イベントを収集します。|  
|Lock timeout|51|トレースが開始されてからのすべてのメタデータ ロックのタイムアウト イベントを収集します。|  
|Lock Acquired|52|トレースが開始されてから取得したロックについての情報を収集します。|  
|Lock Released|53|トレースが開始されてから解放したロックについての情報を収集します。|  
|Lock Waiting|54|トレースが開始されてから待機状態になっているロックについての情報を収集します。|  
  
 各 Lock イベント クラスに関連する列については、「 [Lock Events Data Columns](lock-events-data-columns.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services トレース イベント](analysis-services-trace-events.md)  
  
  