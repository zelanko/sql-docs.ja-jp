---
title: Kpi 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Kpis Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Kpis
helpviewer_keywords:
- Kpis element
ms.assetid: da4e32a0-1416-4d32-8b7f-7d74be23c9d4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d1b0817a7419aa76d9a015c8409b2f09962e04ad
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168193"
---
# <a name="kpis-element-assl"></a>Kpis 要素 (ASSL)
  主要業績評価指標のコレクションが含まれています ([Kpi](../objects/kpi-element-assl.md)要素)、親要素に関連付けられています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Cube><!-- or Perspective -->  
   ...  
   <Kpis>  
      <Kpi>...</Kpi> <!-- parent: Cube -->  
<!-- or -->  
      <Kpi xsi:type="PerspectiveKpi">...</Kpi> <!-- parent: Perspective -->  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[キューブ](../objects/cube-element-assl.md)、[パースペクティブ](../objects/perspective-element-assl.md)|  
  
|先祖または親|子要素|  
|------------------------|-------------------|  
|[Cube](../objects/cube-element-assl.md)|[Kpi](../objects/kpi-element-assl.md)|  
|[パースペクティブ](../objects/perspective-element-assl.md)|[Kpi](../objects/kpi-element-assl.md)型の[PerspectiveKpi](../data-type/perspectivekpi-data-type-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.KpiCollection>します。  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
