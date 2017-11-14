---
title: "root 要素 (XMLA) |Microsoft ドキュメント"
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
- Root Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#root
- urn:schemas-microsoft-com:xml-analysis#root
- microsoft.xml.analysis.root
helpviewer_keywords:
- root element
ms.assetid: ecd9d6e8-b16c-4d62-9a87-107c413a0056
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 972757d71db61ed5cbe82d9bf5e91b448c69260c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="root-element-xmla"></a>root 要素 (XMLA)
  によって返される結果を含む、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドまたは、XML for Analysis (XMLA) コマンドを使用して実行、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<return> <!-- or results-->  
   ...  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">...</root> <!-- for Execute method only -->  
   <!-- or -->  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">...</root>  
   <!-- or -->  
   <root xmlns= xmlns="urn:schemas-microsoft-com:xml-analysis:empty">...</root>  
   ...  
</return>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|次の表を参照してください。|  
|既定値|なし|  
|Cardinality|1-n : 必須要素で、複数回の出現が可能です|  
  
|Ancestor|データ型|  
|--------------|---------------|  
|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)|[行セット](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)、 [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|  
|[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)、[行セット](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)、 [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[結果](../../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md)、[を返す](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **ルート**要素には、いずれかで返される情報が含まれています、 [DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md) 、1 つによって返される要素**Discover**メソッドの呼び出し、または、 [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md) 、1 つで実行される単一の XMLA コマンドによって返される要素**Execute**メソッドの呼び出しです。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

