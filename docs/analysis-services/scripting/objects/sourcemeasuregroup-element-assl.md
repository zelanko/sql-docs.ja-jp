---
title: SourceMeasureGroup 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 85e09e4955e7e7052a64c1e6a449a09789cd664e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sourcemeasuregroup-element-assl"></a>SourceMeasureGroup 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  マイニング構造列のデータ ソースとして機能するメジャー グループを識別します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningStructureColumn xsi:type="TableMiningStructureColumn">  
   ...  
   <SourceMeasureGroup xsi:type="MeasureGroupBinding">...</SourceMeasureGroup>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)型の[TableMiningStructureColumn](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 詳細については、**バインド**の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む、型、**バインド**型との継承階層**バインド**型を参照してください[データ型のバインド&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)です。  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとのバインド & #40 です。SSAS 多次元 & #41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 親に対応する要素**SourceMeasureGroup**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.MiningStructureColumn>と<xref:Microsoft.AnalysisServices.TableMiningStructureColumn>です。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
