---
title: "DependsOnDimensionID 要素 (ASSL) |Microsoft ドキュメント"
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
- DependsOnDimensionID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DependsOnDimensionID
helpviewer_keywords:
- DependsOnDimensionID element
ms.assetid: 66ec20dd-b475-4895-a92c-7ac0e7e1c675
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ace71b2fe51a5699f18a726576984ceb9e49c127
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dependsondimensionid-element-assl"></a>DependsOnDimensionID 要素 (ASSL)
  親ディメンションが依存する別のディメンションの識別子 (ID) を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Dimension>  
      ...  
   <DependsOnDimensionID>...</DependsOnDimensionID>  
   ...  
</Dimension>  
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
|親要素|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **DependsOnDimensionID** 要素は、どのディメンションに依存しているかを識別するために、従属ディメンションによって使用されます。  
  
 親に対応する要素**DependsOnDimensionID**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Dimension>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

