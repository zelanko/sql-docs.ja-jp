---
title: "MembersWithDataCaption 要素 (ASSL) |Microsoft ドキュメント"
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
- MembersWithDataCaption Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MembersWithDataCaption
helpviewer_keywords:
- MembersWithDataCaption element
ms.assetid: a5d59efd-5d67-485b-a360-67d54a1fe394
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f254c1fb3c747a64e3e8e5df50bf30d532678d09
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="memberswithdatacaption-element-assl"></a>MembersWithDataCaption 要素 (ASSL)
  システムによって生成されるデータ メンバーのキャプションを作成するためのテンプレート文字列を提供します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeTranslation> <!-- or DimensionAttribute -->  
   ...  
   <MembersWithDataCaption>...</MembersWithDataCaption>  
   ...  
</AttributeTranslation>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeTranslation](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)、 [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値、 **MembersWithDataCaption**要素は親属性によってのみ使用 (つまり、他の値、[使用状況](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md)の要素、 **DimensionAttribute**親要素に設定されている*親*)、親属性内のデータ メンバーのキャプションを指定します。 データ メンバーの詳細については、「 [親子階層の属性](../../../analysis-services/multidimensional-models/parent-child-dimension-attributes.md)」を参照してください。  
  
 親に対応する要素**MembersWithDataCaption**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.AttributeTranslation>と<xref:Microsoft.AnalysisServices.DimensionAttribute>です。  
  
## <a name="see-also"></a>参照  
 [MembersWithData 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/memberswithdata-element-assl.md)   
 [AttributeTranslation データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

