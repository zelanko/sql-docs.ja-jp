---
title: "AttributeHierarchyVisible 要素 (ASSL) |Microsoft ドキュメント"
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
- AttributeHierarchyVisible Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AttributeHierarchyVisible
helpviewer_keywords:
- AttributeHierarchyVisible element
ms.assetid: a3289a9a-dbd6-43e8-a7ca-ee8a1da92a32
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5e79ef9a4a3d248f9641bc6aae44c50acb83b56b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

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
|既定値|**True**|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md)、 [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)、 [PerspectiveAttribute](../../../analysis-services/scripting/data-type/perspectiveattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **AttributeHierarchyVisible**要素は、属性に関連付けられている属性階層がクライアント アプリケーションに表示されるかどうかを決定します。 この要素に設定されている場合**False**、属性階層がであってもできるユーザー定義階層を作成して、多次元式 (MDX) ステートメントで参照できます。  
  
 親に対応する要素**AttributeHierarchyVisible**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.CubeAttribute>、 <xref:Microsoft.AnalysisServices.DimensionAttribute>、および<xref:Microsoft.AnalysisServices.PerspectiveAttribute>です。  
  
## <a name="see-also"></a>参照  
 [AttributeHierarchyEnabled 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/attributehierarchyenabled-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

