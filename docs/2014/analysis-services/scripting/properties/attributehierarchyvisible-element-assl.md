---
title: AttributeHierarchyVisible 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AttributeHierarchyVisible Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeHierarchyVisible
helpviewer_keywords:
- AttributeHierarchyVisible element
ms.assetid: a3289a9a-dbd6-43e8-a7ca-ee8a1da92a32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ac33cb91014a32f3795b10ef822ab6c85528ac0b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099272"
---
# <a name="attributehierarchyvisible-element-assl"></a>AttributeHierarchyVisible 要素 (ASSL)
  属性階層をクライアント アプリケーションに対して公開するかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute> <!-- or CubeAttribute or PerspectiveAttribute -->  
   ...  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|`True`|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeAttribute](../data-type/cubeattribute-data-type-assl.md)、 [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)、 [PerspectiveAttribute](../data-type/perspectiveattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `AttributeHierarchyVisible` 要素によって、その属性に関連付けられている属性階層がクライアント アプリケーションに表示されるかどうかが決定されます。 この要素が `False` に設定されている場合でも、属性階層を使用したユーザー定義階層の作成、および多次元式 (MDX) ステートメントによる属性階層の参照は可能です。  
  
 親に対応する要素`AttributeHierarchyVisible`分析管理オブジェクト (AMO) オブジェクト モデルは、 <xref:Microsoft.AnalysisServices.CubeAttribute>、 <xref:Microsoft.AnalysisServices.DimensionAttribute>、および<xref:Microsoft.AnalysisServices.PerspectiveAttribute>します。  
  
## <a name="see-also"></a>参照  
 [AttributeHierarchyEnabled 要素&#40;ASSL&#41;](enabled-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
