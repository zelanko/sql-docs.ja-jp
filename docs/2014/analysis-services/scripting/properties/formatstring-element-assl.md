---
title: FormatString 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- FormatString Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- FormatString
helpviewer_keywords:
- FormatString element
ms.assetid: 7b996221-936e-4f36-a3a8-676eb9869c55
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cbcc34f0bdc167f61beebb2e97171027759d6c3b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089862"
---
# <a name="formatstring-element-assl"></a>FormatString 要素 (ASSL)
  表示形式について説明します、 [CalculationProperty](../objects/calculationproperty-element-assl.md)要素または[メジャー](../objects/measure-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <FormatString>...</FormatString>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CalculationProperty](../objects/calculationproperty-element-assl.md)、[メジャー](../objects/measure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `FormatString` プロパティには多次元式 (MDX) が含まれています。 場合に`CalculationProperty`、要素を持つ要素に適用されます、 [CalculationType](calculationtype-element-assl.md)の*メンバー*または*セル*します。  
  
 親に対応する要素`FormatString`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.CalculationProperty>と<xref:Microsoft.AnalysisServices.Measure>します。  
  
## <a name="see-also"></a>参照  
 [CalculationProperties 要素&#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [MdxScript 要素&#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [MdxScripts 要素&#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
