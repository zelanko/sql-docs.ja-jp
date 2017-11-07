---
title: "HierarchyInfo 要素 (XMLA) |Microsoft ドキュメント"
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
- HierarchyInfo Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#HierarchyInfo
- microsoft.xml.analysis.hierarchyinfo
- urn:schemas-microsoft-com:xml-analysis#HierarchyInfo
helpviewer_keywords:
- HierarchyInfo element
ms.assetid: b4472251-1f1d-4233-a8e6-407397862ab4
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 888bacff8501114152ddfd6d33aa8f3e697137ba
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="hierarchyinfo-element-xmla"></a>HierarchyInfo 要素 (XMLA)
  親が含まれている 1 つの階層を表す[AxisInfo](../../../analysis-services/xmla/xml-elements-properties/axisinfo-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AxisInfo>  
   ...  
   <HierarchyInfo name="string">  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </HierarchyInfo>  
   ...  
</AxisInfo>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AxisInfo](../../../analysis-services/xmla/xml-elements-properties/axisinfo-element-xmla.md)|  
|子要素|[キャプション](../../../analysis-services/xmla/xml-elements-properties/caption-element-xmla.md)、 [DisplayInfo](../../../analysis-services/xmla/xml-elements-properties/displayinfo-element-xmla.md)、 [LName](../../../analysis-services/xmla/xml-elements-properties/lname-element-xmla.md)、 [LNum](../../../analysis-services/xmla/xml-elements-properties/lnum-element-xmla.md)、 [UName](../../../analysis-services/xmla/xml-elements-properties/uname-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|Description|  
|---------------|-----------------|  
|名前|必要な**文字列**属性。 階層の名前です。|  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

