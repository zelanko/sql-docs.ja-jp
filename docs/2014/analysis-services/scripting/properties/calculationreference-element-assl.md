---
title: CalculationReference 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CalculationReference Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CalculationReference
helpviewer_keywords:
- CalculationReference element
ms.assetid: 4dd18b1f-55c3-4673-afbe-736d1bce8331
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aace0256c454505e07b4226efc63da0d5d3581c7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224062"
---
# <a name="calculationreference-element-assl"></a>CalculationReference 要素 (ASSL)
  名前付きセットまたはによって参照される計算されるセルの名前を含む、 [CalculationProperty](../objects/calculationproperty-element-assl.md)します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CalculationProperty>  
   ...  
   <CalculationReference>...</CalculationReference>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CalculationProperty](../objects/calculationproperty-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `CalculationReference` の値が既存の名前付きセットまたは計算されるセル定義の名前と一致しない場合、`CalculationReference` は無視されます。  
  
 親に対応する要素`CalculationReference`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.CalculationProperty>します。  
  
## <a name="see-also"></a>参照  
 [CalculationProperties 要素&#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [MdxScript 要素&#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [MdxScripts 要素&#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
