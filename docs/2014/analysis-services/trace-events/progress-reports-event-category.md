---
title: 進行状況レポート イベント カテゴリ |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- progress events [Analysis Services]
- Progress Reports event category
- event classes [Analysis Services], progress reports
ms.assetid: c130f160-28ef-49bc-9ee6-da47dc9aab2a
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8bcfa530f87d7a8caaee6814c2e2e2282e2783ed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071271"
---
# <a name="progress-reports-event-category"></a>進行状況レポート イベント カテゴリ
  進行状況レポート イベント カテゴリには、次の表に示したイベント クラスがあります。  
  
|Event Class|イベント ID|説明|  
|-----------------|--------------|-----------------|  
|Progress Report Begin|5|トレースが開始されてからのすべての Progress Report Begin イベントを収集します。|  
|Progress Report End|6|トレースが開始されてからのすべての Progress Report End イベントを収集します。|  
|Progress Report Current|7|トレースが開始されてからのすべての Progress Report Current イベントを収集します。 たとえば、処理時の現在のレポートには、処理中のオブジェクト (ディメンション、パーティション、キューブなど) に関する処理情報が含まれます。|  
|Progress Report Error|8|トレースが開始されてからのすべての Progress Report Error イベントを収集します。|  
  
 Progress Report Begin イベントは、進行状況イベントのストリームで開始され、Progress Report End イベントで終了します。 このストリームには、任意の数の Progress Report Current および Progress Report Error イベントを含めることができます。  
  
 進行状況レポートの各イベント クラスに関連する列については、「 [進行状況レポートのデータ列](progress-reports-data-columns.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services トレース イベント](analysis-services-trace-events.md)  
  
  