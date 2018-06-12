---
title: Parameter 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e361215425c1e7b0e54b2e8a92b2987d30b00790
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575954"
---
# <a name="parameter-element-xmla"></a>Parameter 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  によって使用されるパラメーターの値と名前が含まれています、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Parameters>  
...  
   <Parameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </Parameter>  
...  
</Parameters>  
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
|親要素|[パラメーター](../../../analysis-services/xmla/xml-elements-properties/parameters-element-xmla.md)|  
|子要素|[名前](../../../analysis-services/xmla/xml-elements-properties/name-element-parameter-xmla.md)、[値](../../../analysis-services/xmla/xml-elements-properties/value-element-parameter-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 などのいくつかの XML for Analysis (XMLA) コマンド、[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)コマンド、追加情報が必要になることができます。 **パラメーター**要素は、XMLA コマンドのチャンクされた情報を含む、追加の情報を提供するためのメカニズムを提供します。  
  
## <a name="see-also"></a>参照
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
