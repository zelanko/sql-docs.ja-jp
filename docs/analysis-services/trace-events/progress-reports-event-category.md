---
title: "進行状況レポート イベント カテゴリ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: trace-events
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- progress events [Analysis Services]
- Progress Reports event category
- event classes [Analysis Services], progress reports
ms.assetid: c130f160-28ef-49bc-9ee6-da47dc9aab2a
caps.latest.revision: "23"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c45bcf105dcd2de68f1ba25bdafebc9cb77c295d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="progress-reports-event-category"></a>進行状況レポート イベント カテゴリ
  進行状況レポート イベント カテゴリには、次の表に示したイベント クラスがあります。  
  
|Event Class|イベント ID|Description|  
|-----------------|--------------|-----------------|  
|Progress Report Begin|5|トレースが開始されてからのすべての Progress Report Begin イベントを収集します。|  
|Progress Report End|6|トレースが開始されてからのすべての Progress Report End イベントを収集します。|  
|Progress Report Current|7|トレースが開始されてからのすべての Progress Report Current イベントを収集します。 たとえば、処理時の現在のレポートには、処理中のオブジェクト (ディメンション、パーティション、キューブなど) に関する処理情報が含まれます。|  
|Progress Report Error|8|トレースが開始されてからのすべての Progress Report Error イベントを収集します。|  
  
 Progress Report Begin イベントは、進行状況イベントのストリームで開始され、Progress Report End イベントで終了します。 このストリームには、任意の数の Progress Report Current および Progress Report Error イベントを含めることができます。  
  
 進行状況レポートの各イベント クラスに関連する列については、「 [進行状況レポートのデータ列](../../analysis-services/trace-events/progress-reports-data-columns.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services トレース イベント](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
