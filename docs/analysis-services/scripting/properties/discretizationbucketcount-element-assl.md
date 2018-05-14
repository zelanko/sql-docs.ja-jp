---
title: DiscretizationBucketCount 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 389719df8815321ab5b2860425e4724b6b622770
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="discretizationbucketcount-element-assl"></a>DiscretizationBucketCount 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  分離対象のバケット数を示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationBucketCount>...</DiscretizationBucketCount>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Integer|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)、 [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値、 **DiscretizationBucketCount**要素数のグループまたは"buckets"が作成されますを決定する値を**DimensionAttribute**または**ScalarMiningStructureColumn**分離されるか、特定の一連のグループに編成します。 要素が指定されていない場合、または、要素の値の 0 が指定されている[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]適切な数の分離メソッドに応じてグループを作成します。 分離メソッドの詳細については、次を参照してください。[分離メソッド&#40;データ マイニング&#41;](../../../analysis-services/data-mining/discretization-methods-data-mining.md)です。  
  
 親に対応する要素**DiscretizationBucketCount**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.DimensionAttribute>と<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>です。  
  
## <a name="see-also"></a>参照  
 [DiscretizationMethod 要素&#40;ASSL&#41;](../../../analysis-services/scripting/properties/discretizationmethod-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
