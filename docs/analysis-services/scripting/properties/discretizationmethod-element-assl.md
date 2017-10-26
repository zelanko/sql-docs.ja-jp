---
title: "DiscretizationMethod 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DiscretizationMethod Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DiscretizationMethod
helpviewer_keywords:
- DiscretizationMethod element
ms.assetid: 4cfe015f-ad6c-47e1-8aff-c9c7677867b1
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e2bbf548ba16ccc81d1536c5c64a22e9c69d96d1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="discretizationmethod-element-assl"></a>DiscretizationMethod 要素 (ASSL)
  分離に使用するメソッドを定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationMethod>...</DiscretizationMethod>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*なし*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)、 [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値、 **DiscretizationMethod**要素を決定する方法の値を**DimensionAttribute**または**ScalarMiningStructureColumn**分離されるか、構成されています特定のグループ セットにします。 分離メソッドの詳細については、次を参照してください。[分離メソッド (&) #40 です。 データ マイニング (&) #41;](../../../analysis-services/data-mining/discretization-methods-data-mining.md)です。  
  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*自動*|マイニング構造列における AUTOMATIC 分離メソッドに相当します。|  
|*EqualAreas*|マイニング構造列における EQUAL_AREAS 分離メソッドに相当します。|  
|*クラスター*|マイニング構造列における CLUSTERS 分離メソッドに相当します。|  
|*しきい値*|マイニング構造列における THRESHOLDS 分離メソッドに相当します。|  
|*EqualRanges*|マイニング構造列における EQUAL_RANGES 分離メソッドに相当します。|  
  
 許可される値に対応する列挙**DiscretizationMethod**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DiscretizationMethod>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

