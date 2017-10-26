---
title: "Ordinal 要素 (ASSL) |Microsoft ドキュメント"
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
- Ordinal Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Ordinal
helpviewer_keywords:
- Ordinal element
ms.assetid: 64e68ad5-439c-4c1d-9df4-ee90c56761b4
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f82b14a571fad0753e3b8835a3e0829a4975c583
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="ordinal-element-assl"></a>Ordinal 要素 (ASSL)
  キーおよび翻訳などコレクション内でバインドする序数を示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeBinding> <!-- or CubeAttributeBinding -->  
   ...  
   <Ordinal>...</Ordinal>  
   ...  
</AttributeBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Integer|  
|既定値|**0**|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)、 [CubeAttributeBinding](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **AttributeBinding**と**CubeAttributeBinding**要素を[型](../../../analysis-services/scripting/properties/type-element-binding-assl.md)プロパティに設定されている*キー*または*翻訳*はさらに、データ ソース ビュー内の列のコレクションにバインドする属性をバインドできます。 値、**序数**要素は、列が決まります、 **AttributeBinding**または**CubeAttributeBinding**そのコレクション内の参照します。  
  
 親に対応する要素**序数**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.AttributeBinding>と<xref:Microsoft.AnalysisServices.CubeAttributeBinding>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

