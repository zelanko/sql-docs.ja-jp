---
title: ClassifiedColumns 要素 (ASSL) |Microsoft Docs
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
- ClassifiedColumns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ClassifiedColumns
helpviewer_keywords:
- ClassifiedColumns element
ms.assetid: f16b4f51-c38d-4601-98b8-1497dbf12d02
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 38436c97f74adef2af6d5645aea6547682740894
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37286048"
---
# <a name="classifiedcolumns-element-assl"></a>ClassifiedColumns 要素 (ASSL)
  により分類される関連列のコレクションを格納、 [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)要素。  
  
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
|親要素|[MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)型の[ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|子要素|[ClassifiedColumnID](../properties/id-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`ClassifiedColumns`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>します。  
  
## <a name="see-also"></a>参照  
 [MiningStructureColumn データ型&#40;ASSL&#41;](../data-type/miningstructurecolumn-data-type-assl.md)   
 [MiningStructure 要素&#40;ASSL&#41;](../objects/miningstructure-element-assl.md)   
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
