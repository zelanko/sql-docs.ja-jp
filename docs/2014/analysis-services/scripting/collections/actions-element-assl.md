---
title: Actions 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Actions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Actions
helpviewer_keywords:
- Actions element
ms.assetid: 100a4209-2c22-4902-a8ca-f2bd99bf8fbb
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 583f265b0fb45b22cd0f6b3d20b577276d70ae92
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37183229"
---
# <a name="actions-element-assl"></a>Actions 要素 (ASSL)
  動作のコレクションが含まれています、[キューブ](../objects/cube-element-assl.md)または[パースペクティブ](../objects/perspective-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Cube> <!-- or Perspective -->  
   ...  
   <Actions>  
      <Action xsi:type="DrillThroughAction">...</Action> <!-- ancestor: Cube -->  
      <Action xsi:type="ReportAction">...</Action> <!-- ancestor: Cube -->  
      <Action xsi:type="StandardAction">...</Action> <!-- ancestor: Cube -->  
      <!-- or -->  
      <Action xsi:type="PerspectiveAction">...</Action> <!-- ancestor: Perspective -->  
      </Actions>  
      ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし (コレクション型)|  
|既定値|なし (コレクション型)|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[キューブ](../objects/cube-element-assl.md)、[パースペクティブ](../objects/perspective-element-assl.md)|  
  
|先祖または親|子要素|  
|------------------------|--------------------|  
|[キューブ](../data-type/action-data-type-assl.md)、 [ReportAction](../data-type/reportaction-data-type-assl.md)、 [StandardAction](../data-type/standardaction-data-type-assl.md)|  
|[パースペクティブ](../data-type/perspectiveaction-data-type-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は、<xref:Microsoft.AnalysisServices.ActionCollection> と <xref:Microsoft.AnalysisServices.PerspectiveActionCollection> です。  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
