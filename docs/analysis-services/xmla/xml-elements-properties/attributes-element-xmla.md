---
title: 属性を要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6cd297c26017ec7da189b5ea8b6dd24014b0b928
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="attributes-element-xmla"></a>Attributes 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  コレクションを格納[属性](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)親によって使用される要素[挿入](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)または[更新](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)コマンド、または親[場所](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Insert > <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Attributes>  
      <Attribute>...</Attribute>  
   </Attributes>  
   ...  
</Insert>  
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
|親要素|[挿入](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)、[更新](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)、[場所](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)|  
|子要素|[属性](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
