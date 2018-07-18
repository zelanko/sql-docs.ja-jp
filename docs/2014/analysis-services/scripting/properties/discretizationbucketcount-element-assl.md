---
title: DiscretizationBucketCount 要素 (ASSL) |Microsoft Docs
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
- DiscretizationBucketCount Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DiscretizationBucketCount
helpviewer_keywords:
- DiscretizationBucketCount element
ms.assetid: 551a73ae-59e1-4079-a2d9-988df96b5e07
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0309610c503a229c698cc3d959eae10a5acbca06
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233732"
---
# <a name="discretizationbucketcount-element-assl"></a>DiscretizationBucketCount 要素 (ASSL)
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
|親要素|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)、 [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `DiscretizationBucketCount` 要素の値は、`DimensionAttribute` または `ScalarMiningStructureColumn` の値が特定のグループ セットに分離される (編成される) ときに作成されるグループ (つまり "バケット") の数を決定します。 要素が指定されていない場合、または、要素の値に 0 が指定されて場合[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]適切な数の分離メソッドに応じてグループを作成します。 分離メソッドの詳細については、次を参照してください。[分離メソッド&#40;データ マイニング&#41;](../../data-mining/discretization-methods-data-mining.md)します。  
  
 親に対応する要素`DiscretizationBucketCount`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.DimensionAttribute>と<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>します。  
  
## <a name="see-also"></a>参照  
 [Type 要素&#40;MeasureGroupAttribute&#41; &#40;ASSL&#41;](discretizationmethod-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
