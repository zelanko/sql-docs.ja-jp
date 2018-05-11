---
title: キューブ要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e3a89ca3b7b09e08ea17e588c12f0e5195d20211
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="cube-element-xmla"></a>Cube 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親によって表されるディメンションを格納するキューブを識別[オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Object>  
   ...  
   <Cube>...</Cube>  
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
 **キューブ**要素は、オブジェクト識別子によって表されるディメンションを格納するキューブの名前を含む、**オブジェクト**要素。  
  
## <a name="see-also"></a>参照  
 [Database 要素 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)   
 [Dimension 要素 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/dimension-element-xmla.md)   
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
