---
title: "UnknownMember 要素 (ASSL) |Microsoft ドキュメント"
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
- UnknownMember Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- UnknownMember
helpviewer_keywords:
- UnknownMember element
ms.assetid: 5558961e-e3c6-4f4e-817d-5b12b0734c03
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5da9cdc237512a47a27b21691864b3da523ce70a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="unknownmember-element-assl"></a>UnknownMember 要素 (ASSL)
  不明なメンバーが表示されるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Dimension>  
      ...  
   <UnknownMember>...</UnknownMember>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*なし*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*表示されます。*|不明なメンバーが存在し、表示されます。|  
|*非表示*|不明なメンバーが存在するが、表示されません。|  
|*なし*|不明なメンバーは使用されません。|  
  
 許可される値に対応する列挙**UnknownMember**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.UnknownMemberBehavior>します。  
  
## <a name="see-also"></a>参照  
 [UnknownMemberName 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/unknownmembername-element-assl.md)   
 [UnknownMemberTranslation 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/unknownmembertranslation-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

