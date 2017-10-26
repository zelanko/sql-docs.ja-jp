---
title: "RestrictionList 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- RestrictionList Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#RestrictionList
- microsoft.xml.analysis.restrictionlist
- http://schemas.microsoft.com/analysisservices/2003/engine#RestrictionList
helpviewer_keywords:
- RestrictionList element
ms.assetid: 2297c005-381e-49a4-a207-826f7f9ea93a
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: df82fa9bb12094ae01535977f10f26622cbac6b2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="restrictionlist-element-xmla"></a>RestrictionList 要素 (XMLA)
  [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) メソッドによって使用される、制限列と値のコレクションを含みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Restrictions>  
   <RestrictionList>  
      <!-- Zero or more restriction columns and values -->  
   </RestrictionList>  
</Restrictions>  
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
|親要素|[制限](../../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
|子要素|制限列と値 (「解説」を参照してください)。|  
  
## <a name="remarks"></a>解説  
 **RestrictionList** 要素は、 **Discover** メソッドによって返されるデータをフィルター処理するために使用する制限列のコレクションを含みます。 **RestrictionList** 要素内のそれぞれの制限列は、個別の XML 要素によって定義されます。 制限列の値は XML 要素に含まれるデータで、制限列の名前は XML 要素の名前に対応します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

