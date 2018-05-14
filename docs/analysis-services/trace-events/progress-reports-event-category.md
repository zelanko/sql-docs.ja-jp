---
title: 進行状況レポート イベント カテゴリ |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f3e48e34e5b85093793b0ea70786b106d72235a7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="progress-reports-event-category"></a>進行状況レポート イベント カテゴリ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
  
  
