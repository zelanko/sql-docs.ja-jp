---
title: Server State イベント カテゴリの検出 |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 953936b1f8054e6294788184750bb9e888b43f0f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34039624"
---
# <a name="discover-server-state-event-category"></a>サーバー状態検出イベント カテゴリ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  サーバー状態検出イベント カテゴリには、次の表に示したイベント クラスがあります。  
  
|Event Class|イベント ID|Description|  
|-----------------|--------------|-----------------|  
|Server State Discover Begin|33|トレースが開始されてからのすべての Server-State XMLA Discover Begin イベントを収集します。|  
|Server State Discover Data|34|トレースが開始されてからのすべての Server-State XMLA Discover Data イベントを収集します。 これらのイベントは、検出要求に対する応答の内容がキャプチャされます。|  
|Server State Discover End|35|トレースが開始されてからのすべての Server-State XMLA Discover End イベントを収集します。|  
  
 Query イベントの各イベント クラスに関連する列の詳細については、「 [Discover Server State イベントのデータ列](../../analysis-services/trace-events/discover-server-state-events-data-columns.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services トレース イベント](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
