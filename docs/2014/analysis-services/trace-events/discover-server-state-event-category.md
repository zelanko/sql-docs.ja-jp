---
title: サーバー状態検出イベント カテゴリ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Discover Server State event category
- server state events [Analysis Services]
- discover server state events
- event classes [Analysis Services], discover server state
ms.assetid: b62ebf66-d090-4f74-8c83-11ed518b2018
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3c55d16650e9ef04ae951a9eb0d7f60fbc6c472a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37197852"
---
# <a name="discover-server-state-event-category"></a>サーバー状態検出イベント カテゴリ
  サーバー状態検出イベント カテゴリには、次の表に示したイベント クラスがあります。  
  
|Event Class|イベント ID|説明|  
|-----------------|--------------|-----------------|  
|Server State Discover Begin|33|トレースが開始されてからのすべての Server-State XMLA Discover Begin イベントを収集します。|  
|Server State Discover Data|34|トレースが開始されてからのすべての Server-State XMLA Discover Data イベントを収集します。 これらのイベントは、検出要求に対する応答の内容がキャプチャされます。|  
|Server State Discover End|35|トレースが開始されてからのすべての Server-State XMLA Discover End イベントを収集します。|  
  
 Query イベントの各イベント クラスに関連する列の詳細については、「 [Discover Server State イベントのデータ列](discover-server-state-events-data-columns.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services トレース イベント](analysis-services-trace-events.md)  
  
  
