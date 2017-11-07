---
title: "ActionID 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ActionID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ActionID
helpviewer_keywords:
- ActionID element
ms.assetid: 2c9c66b2-a7ea-4874-a0ed-020ce3feab20
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7a37bba497503e9d3c01031e3256baa86d1e3e0a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="actionid-element-assl"></a>ActionID 要素 (ASSL)
  名前を含む、[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)要素で定義されている、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素で使用できるようにした、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素として、 [PerspectiveAction](../../../analysis-services/scripting/data-type/perspectiveaction-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<PerspectiveAction>  
   <ActionID>...</ActionID  
</PerspectiveAction>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[PerspectiveAction](../../../analysis-services/scripting/data-type/perspectiveaction-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**ActionID**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.PerspectiveAction>します。  
  
## <a name="see-also"></a>参照  
 [Actions 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/actions-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

