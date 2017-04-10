---
title: "進行状況レポート イベント カテゴリ | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "進行状況イベント [Analysis Services]"
  - "進行状況レポート イベント カテゴリ"
  - "イベント クラス [Analysis Services], 進行状況レポート"
ms.assetid: c130f160-28ef-49bc-9ee6-da47dc9aab2a
caps.latest.revision: 23
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 23
---
# 進行状況レポート イベント カテゴリ
  進行状況レポート イベント カテゴリには、次の表に示したイベント クラスがあります。  
  
|Event Class|イベント ID|Description|  
|-----------------|--------------|-----------------|  
|Progress Report Begin|5|トレースが開始されてからのすべての Progress Report Begin イベントを収集します。|  
|Progress Report End|6|トレースが開始されてからのすべての Progress Report End イベントを収集します。|  
|Progress Report Current|7|トレースが開始されてからのすべての Progress Report Current イベントを収集します。 たとえば、処理時の現在のレポートには、処理中のオブジェクト (ディメンション、パーティション、キューブなど) に関する処理情報が含まれます。|  
|Progress Report Error|8|トレースが開始されてからのすべての Progress Report Error イベントを収集します。|  
  
 Progress Report Begin イベントは、進行状況イベントのストリームで開始され、Progress Report End イベントで終了します。 このストリームには、任意の数の Progress Report Current および Progress Report Error イベントを含めることができます。  
  
 進行状況レポートの各イベント クラスに関連する列については、「[進行状況レポートのデータ列](../../analysis-services/trace-events/progress-reports-data-columns.md)」を参照してください。  
  
## 参照  
 [Analysis Services トレース イベント](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  