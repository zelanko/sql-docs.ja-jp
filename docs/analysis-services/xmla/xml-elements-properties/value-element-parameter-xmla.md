---
title: "値の要素 (Parameter) (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
apiname:
- Value Element (Parameter)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.value
- urn:schemas-microsoft-com:xml-analysis#Value
- http://schemas.microsoft.com/analysisservices/2003/engine#Value
helpviewer_keywords:
- Value element
ms.assetid: e590d189-91aa-40c7-8669-09c87812f4ce
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2f421aec3724eb6359bb0c55f825b4e630580b46
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="value-element-parameter-xmla"></a>Value 要素 (Parameter) (XMLA)
  によって表されるパラメーターの値を含む、[パラメーター](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Parameter>  
   ...  
   <Value>...</Value>  
   ...  
</Parameter>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Any|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[パラメーター](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **値**要素を格納できます任意の単純な XML 型だけでなく、XML for Analysis (XMLA)**行セット**データ型は、内の XMLA コマンドによって使用されるパラメーター、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

