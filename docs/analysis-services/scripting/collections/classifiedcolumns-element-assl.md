---
title: ClassifiedColumns 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ClassifiedColumns Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ClassifiedColumns
helpviewer_keywords:
- ClassifiedColumns element
ms.assetid: f16b4f51-c38d-4601-98b8-1497dbf12d02
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1c4bbdded62dfb95b7e2945384556af73844daf0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="classifiedcolumns-element-assl"></a>ClassifiedColumns 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]によって分類される関連列のコレクションを格納、 [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)要素。  
  
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
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)型の[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|子要素|[ClassifiedColumnID](../../../analysis-services/scripting/properties/classifiedcolumnid-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**ClassifiedColumns**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>します。  
  
## <a name="see-also"></a>参照  
 [MiningStructureColumn データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)   
 [MiningStructure 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)   
 [コレクション &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
