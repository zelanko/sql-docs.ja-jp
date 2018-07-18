---
title: return 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e8746fb9f8b397ef50b1a5c66a2132e5f0cf5c87
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37968444"
---
# <a name="return-element-xmla"></a>return 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  によって返される情報が含まれています、 [DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)への応答内の要素を[Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドの呼び出しまたは[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md) に応じて要素の[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出し。  
  
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
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)、 [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|  
|子要素|次の表を参照してください。|  
  
|Ancestor|子要素|  
|--------------|--------------------|  
|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)|[root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)または[結果](../../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 **返す**要素にはによって返されるデータが含まれています、 **Discover**と**Execute**メソッド。 通常、**返す**要素には、1 つが含まれています**ルート**を正常に実行によって返されるデータを含む要素**Discover**または**Execute。** メソッドの呼び出しまたは XML for Analysis (XMLA) 例外が、失敗したメソッドの呼び出しによって返されます。 場合、 **Execute**メソッドが含まれています、**バッチ**、複数の操作を実行するコマンドです、**返す**要素が含まれています、**結果**要素をさらに、1 つを含む**ルート**各コマンドの実行が成功したかによって、**バッチ**コマンド。  
  
## <a name="see-also"></a>参照
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
