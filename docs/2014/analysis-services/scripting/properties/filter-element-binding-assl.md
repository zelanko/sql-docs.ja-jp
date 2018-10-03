---
title: Filter 要素 (Binding) (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Filter Element (Binding)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- filter
helpviewer_keywords:
- Filter element
ms.assetid: 3d4cd169-2903-4266-8541-540ece424b7b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0fe300ea7c88924fd463968cae680ded50ebb610
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209952"
---
# <a name="filter-element-binding-assl"></a>Filter 要素 (バインド) (ASSL)
  親要素のコンテンツをフィルター選択する多次元式 (MDX) を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeDimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <Filter>...</Filter>  
   ...  
</CubeDimensionBinding>  
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
|親要素|[CubeDimensionBinding](../data-type/binding-data-type-assl.md)、 [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>Remarks  
 詳細については、`Binding`のテーブルを含む型[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]のスクリプト言語 (ASSL) オブジェクト、`Binding`型との継承階層`Binding`型を参照してください[データ型のバインド&#40;ASSL&#41;](../data-type/binding-data-type-assl.md).  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
 親に対応する要素`Filter`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.CubeDimensionBinding>と<xref:Microsoft.AnalysisServices.MeasureGroupBinding>します。  
  
## <a name="see-also"></a>関連項目  
 [Binding データ型&#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
