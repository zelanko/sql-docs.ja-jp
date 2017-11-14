---
title: "return 要素 (XMLA) |Microsoft ドキュメント"
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
- return Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.return
- http://schemas.microsoft.com/analysisservices/2003/engine#return
- urn:schemas-microsoft-com:xml-analysis#return
helpviewer_keywords:
- return element
ms.assetid: 3cfe8b74-fec3-4987-a74a-5f731444e024
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 06b93a7d4c785f8e298a40d6b0accd2ad945b53e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="return-element-xmla"></a>return 要素 (XMLA)
  によって返される情報が含まれています、 [DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)への応答内の要素、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドの呼び出しまたは[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)への応答内の要素、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出しです。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DiscoverResponse> <!-- or ExecuteResponse -->  
   <return>  
      <root>...</root>  
      <!-- or -->  
      <results>...</results> <!-- ExecuteResponse only -->  
   </return>  
</DiscoverResponse>  
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
|親要素|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)、 [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|  
|子要素|次の表を参照してください。|  
  
|Ancestor|子要素|  
|--------------|--------------------|  
|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)|[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)または[結果](../../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **返す**要素にはによって返されるデータが含まれています、 **Discover**と**Execute**メソッドです。 通常、**返す**要素には、1 つが含まれています**ルート**を正常に実行によって返されるデータを含む要素**Discover**または**Execute。**メソッドの呼び出しまたは XML for Analysis (XMLA) 例外されなかったメソッド呼び出しによって返されます。 場合、 **Execute**メソッドが含まれています、**バッチ**、複数の操作を実行するコマンド、**返す**要素が含まれています、**結果**要素、さらに、1 つを含む**ルート**成功と失敗によって実行された各コマンドの要素、**バッチ**コマンド。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

