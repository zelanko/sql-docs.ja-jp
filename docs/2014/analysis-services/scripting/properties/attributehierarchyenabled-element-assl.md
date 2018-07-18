---
title: AttributeHierarchyEnabled 要素 (ASSL) |Microsoft Docs
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
- AttributeHierarchyEnabled Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeHierarchyEnabled
helpviewer_keywords:
- AttributeHierarchyEnabled element
ms.assetid: 1e95307f-530e-4e98-a0e1-2b0462d330a3
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ab14a4adf69281ec919811270c3d2220a76682e6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250872"
---
# <a name="attributehierarchyenabled-element-assl"></a>AttributeHierarchyEnabled 要素 (ASSL)
  属性階層がその属性で有効かどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute><!-- or CubeAttribute -->  
   ...  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
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
|親要素|[CubeAttribute](../data-type/cubeattribute-data-type-assl.md)、 [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `AttributeHierarchyEnabled`要素は、属性階層がによって生成されたかどうかを決定[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]属性。 属性階層が有効でない場合は、ユーザー定義の階層でその属性を使用できず、多次元式 (MDX) ステートメントで属性階層を参照できません。  
  
 親に対応する要素`AttributeHierarchyEnabled`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.CubeAttribute>と<xref:Microsoft.AnalysisServices.DimensionAttribute>します。  
  
## <a name="see-also"></a>参照  
 [AttributeHierarchyVisible 要素&#40;ASSL&#41;](visible-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
