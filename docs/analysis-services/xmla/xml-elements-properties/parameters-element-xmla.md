---
title: Parameters 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 133920742ad3815907af1cdc2d221f169ce238f1
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="parameters-element-xmla"></a>Parameters 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  コレクションを格納[パラメーター](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md)によって使用される要素、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
 **Namespace:**`urn:schemas-microsoft-com:xml-analysis`  
  
## <a name="syntax"></a>構文  
  
```  
  
<Execute>  
...  
   <Parameters>  
      <Parameter>...</Parameter>  
   </Parameters>  
...  
</Execute>  
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
|親要素|[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)|  
|子要素|[パラメーター](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 などのいくつかの XML for Analysis (XMLA) コマンド、[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)コマンド、追加情報が必要になることができます。 **パラメーター**要素は、XMLA コマンドのチャンクされた情報を含む、追加の情報を提供するためのメカニズムを提供します。  
  
 XMLA コマンドを使用しない場合、**パラメーター**要素を呼び出すときに、要素を省略することができます、 **Execute**メソッドです。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
