---
title: 値の要素 (Parameter) (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 904d34b8950246b8ba83b15bb9182d6f04216f30
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="value-element-parameter-xmla"></a>Value 要素 (Parameter) (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
