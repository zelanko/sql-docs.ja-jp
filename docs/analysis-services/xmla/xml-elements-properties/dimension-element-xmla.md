---
title: "ディメンションの要素 (XMLA) |Microsoft ドキュメント"
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
- Dimension Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Dimension
- urn:schemas-microsoft-com:xml-analysis#Dimension
- microsoft.xml.analysis.dimension
helpviewer_keywords:
- Dimension element
ms.assetid: 85093468-e971-4b8e-9ee4-7b264ad01711
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eb5f7e0e5c8cb8032074396d43a24efb0429bfe4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dimension-element-xmla"></a>Dimension 要素 (XMLA)
  親によって表されるキューブ ディメンションを識別[オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Object>  
   ...  
   <Dimension>...</Dimension>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **ディメンション**要素は、オブジェクト識別子によって表されるキューブ ディメンションの名前を含む、**オブジェクト**要素。  
  
## <a name="see-also"></a>参照  
 [Database 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)   
 [Dimension 要素 (XMLA)](../../../analysis-services/xmla/xml-elements-properties/dimension-element-xmla.md)   
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

