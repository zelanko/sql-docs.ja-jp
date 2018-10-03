---
title: Action 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Action Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Action
helpviewer_keywords:
- Action element
ms.assetid: aaee06a2-91c6-4007-b787-79cb08d63c77
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 48a07020a2c4b8bb2fbc79c5c3d67697a30760d7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48166442"
---
# <a name="action-element-assl"></a>Action 要素 (ASSL)
  使用できるアクションに関する情報を格納する[キューブ](cube-element-assl.md)要素または[パースペクティブ](perspective-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Actions>  
   <Action xsi:type="DrillThroughAction">...</Action> <!-- ancestor: Cube -->  
   <Action xsi:type="ReportAction">...</Action> <!-- ancestor: Cube -->  
   <Action xsi:type="StandardAction">...</Action> <!-- ancestor: Cube -->  
   <!-- or -->  
   <Action xsi:type="PerspectiveAction">...</Action> <!-- ancestor: Perspective -->  
</Actions>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
|先祖または親|データ型|  
|------------------------|---------------|  
|[キューブ](../data-type/action-data-type-assl.md)、 [ReportAction](../data-type/reportaction-data-type-assl.md)、 [StandardAction](../data-type/standardaction-data-type-assl.md)|  
|[パースペクティブ](../data-type/perspectiveaction-data-type-assl.md)|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アクション](../collections/actions-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Action>します。  
  
## <a name="see-also"></a>参照  
 [キューブ要素&#40;ASSL&#41;](cube-element-assl.md)   
 [Perspective 要素&#40;ASSL&#41;](perspective-element-assl.md)   
 [PerspectiveAction データ型&#40;ASSL&#41;](../data-type/perspectiveaction-data-type-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
