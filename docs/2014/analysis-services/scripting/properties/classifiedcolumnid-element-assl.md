---
title: ClassifiedColumnID 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ClassifiedColumnID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ClassifiedColumnID
helpviewer_keywords:
- ClassifiedColumnID element
ms.assetid: c294b9c5-3ac2-4554-8ba8-d9f15d7e85c0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bb48844934cc5783d2e25210bc406e348e2a6b85
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129382"
---
# <a name="classifiedcolumnid-element-assl"></a>ClassifiedColumnID 要素 (ASSL)
  によって分類される関連列の識別子 (ID) を含む、 [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ClassifiedColumns>  
   <ClassifiedColumnID>...</<ClassifiedColumnID>  
</ClassifiedColumns>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ClassifiedColumns](../collections/columns-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで `ClassifiedColumns` コレクションの親に対応する要素は、<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn> です。  
  
## <a name="see-also"></a>参照  
 [要素のコンテンツ&#40;ASSL&#41;](content-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
