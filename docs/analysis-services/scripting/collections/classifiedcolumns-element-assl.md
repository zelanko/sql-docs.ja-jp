---
title: ClassifiedColumns 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b28ff62f33c7a3586dc9c1f7705eac697f189c57
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="classifiedcolumns-element-assl"></a>ClassifiedColumns 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  によって分類される関連列のコレクションを格納、 [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningStructureColumn xsi:type="ScalarMiningStructureColumn">  
   ...  
   <ClassifiedColumns>  
      <ClassifiedColumnID>...</ClassifiedColumnID>  
   </ClassifiedColumns>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)型の[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|子要素|[ClassifiedColumnID](../../../analysis-services/scripting/properties/classifiedcolumnid-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**ClassifiedColumns**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>します。  
  
## <a name="see-also"></a>参照  
 [MiningStructureColumn データ型&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)   
 [MiningStructure 要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)   
 [コレクション & #40 です。ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
