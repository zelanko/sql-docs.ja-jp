---
title: AttributeAllMemberName 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AttributeAllMemberName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeAllMemberName
helpviewer_keywords:
- AttributeAllMemberName element
ms.assetid: 5ede46a7-d8b0-40be-98d7-b01047b27d2e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4c5d601864d3ceef1af243f819de8d7ef8466e91
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218772"
---
# <a name="attributeallmembername-element-assl"></a>AttributeAllMemberName 要素 (ASSL)
  ディメンションの All メンバーのキャプションを既定の言語で格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Dimension>  
      ...  
   <AttributeAllMemberName>...</AttributeAllMemberName>  
   ...  
</Dimension>  
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
|親要素|[Dimension](../objects/dimension-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`AttributeAllMemberName`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Dimension>します。  
  
## <a name="see-also"></a>参照  
 [構成、&#40;すべて&#41;属性階層のレベル](../../multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
