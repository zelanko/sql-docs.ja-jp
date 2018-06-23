---
title: CalculationReference 要素 (ASSL) |Microsoft ドキュメント
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 19d96e9f589a9a83d4d31c5b7b1dfb9c37f29633
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085301"
---
# <a name="calculationreference-element-assl"></a>CalculationReference 要素 (ASSL)
  名前付きセットまたはによって参照される計算されるセルの名前を含む、 [CalculationProperty](../objects/calculationproperty-element-assl.md)です。  
  
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
  
  