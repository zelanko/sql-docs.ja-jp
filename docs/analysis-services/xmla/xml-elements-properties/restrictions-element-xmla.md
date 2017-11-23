---
title: "Restrictions 要素 (XMLA) |Microsoft ドキュメント"
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
apiname: Restrictions Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Restrictions
- http://schemas.microsoft.com/analysisservices/2003/engine#Restrictions
- microsoft.xml.analysis.restrictions
helpviewer_keywords: Restrictions element
ms.assetid: e745ce13-b468-4372-a6f0-0da3d772dda3
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 577800202732858fe5427ec92220af1cf76c29f4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="restrictions-element-xmla"></a>Restrictions 要素 (XMLA)
  制限列とによって使用されるデータが含まれています、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Discover>  
...  
   <Restrictions>  
      <RestrictionList>...</RestrictionList>  
   </Restrictions>  
...  
</Discover>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[検出します。](../../../analysis-services/xmla/xml-elements-methods-discover.md)|  
|子要素|[RestrictionList](../../../analysis-services/xmla/xml-elements-properties/restrictionlist-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **制限**制限列とデータを使用して取得した情報を制限する要素が表す、 **Discover**メソッドです。  
  
## <a name="example"></a>例  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <RequestType>DISCOVER_PROPERTIES</RequestType>  
   <Restrictions>  
      <RestrictionList xmlns="urn:schemas-microsoft-com:xml-analysis">  
         <PropertyName>Catalog</PropertyName>  
      </RestrictionList>  
   </Restrictions>  
   <Properties />  
</Discover>  
```  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
