---
title: "RestrictionList 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: RestrictionList Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#RestrictionList
- microsoft.xml.analysis.restrictionlist
- http://schemas.microsoft.com/analysisservices/2003/engine#RestrictionList
helpviewer_keywords: RestrictionList element
ms.assetid: 2297c005-381e-49a4-a207-826f7f9ea93a
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: af4df63d245aacd861c9f4a2a1d8a4c9d8a9b01d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
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
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
