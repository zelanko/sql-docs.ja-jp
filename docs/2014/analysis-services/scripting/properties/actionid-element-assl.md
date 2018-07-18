---
title: ActionID 要素 (ASSL) |Microsoft Docs
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
- ActionID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ActionID
helpviewer_keywords:
- ActionID element
ms.assetid: 2c9c66b2-a7ea-4874-a0ed-020ce3feab20
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7405b3b6dd7f673b199509388d43164f47dd90eb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37304552"
---
# <a name="actionid-element-assl"></a>ActionID 要素 (ASSL)
  名前を含む、[アクション](../objects/action-element-assl.md)要素で定義されている、[キューブ](../objects/cube-element-assl.md)要素で使用可能になる、[パースペクティブ](../objects/perspective-element-assl.md)要素として、 [PerspectiveAction](../data-type/action-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<PerspectiveAction>  
   <ActionID>...</ActionID  
</PerspectiveAction>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[PerspectiveAction](../data-type/action-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`ActionID`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.PerspectiveAction>します。  
  
## <a name="see-also"></a>参照  
 [Actions 要素&#40;ASSL&#41;](../collections/actions-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
