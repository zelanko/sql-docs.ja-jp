---
title: "サーバー状態検出イベント カテゴリ | Microsoft Docs"
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
  - "サーバー状態検出イベント カテゴリ"
  - "サーバー状態イベント [Analysis Services]"
  - "サーバー状態検出イベント"
  - "イベント クラス [Analysis Services], サーバー状態検出"
ms.assetid: b62ebf66-d090-4f74-8c83-11ed518b2018
caps.latest.revision: 25
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 25
---
# サーバー状態検出イベント カテゴリ
  サーバー状態検出イベント カテゴリには、次の表に示したイベント クラスがあります。  
  
|Event Class|イベント ID|Description|  
|-----------------|--------------|-----------------|  
|Server State Discover Begin|33|トレースが開始されてからのすべての Server-State XMLA Discover Begin イベントを収集します。|  
|Server State Discover Data|34|トレースが開始されてからのすべての Server-State XMLA Discover Data イベントを収集します。 これらのイベントは、検出要求に対する応答の内容がキャプチャされます。|  
|Server State Discover End|35|トレースが開始されてからのすべての Server-State XMLA Discover End イベントを収集します。|  
  
 Query イベントの各イベント クラスに関連する列の詳細については、「[Discover Server State イベントのデータ列](../../analysis-services/trace-events/discover-server-state-events-data-columns.md)」を参照してください。  
  
## 参照  
 [Analysis Services トレース イベント](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  