---
title: ExecuteResponse 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a1ff44c8e2fb23e40aac30e70c73b4d260145bfd
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979124"
---
# <a name="xml-elements---objects---executeresponse"></a>XML 要素 - オブジェクト - ExecuteResponse
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  応答には、Analysis Services のインスタンスによって返される情報が含まれています、 [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出し。  
  
 **Namespace** urn: スキーマ-microsoft-'http://www.w3.org/2001/xmlschema'-分析  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ExecuteResponse>  
   <return>  
</ExecuteResponse>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[return](../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 **ExecuteResponse**要素は、最上位の要素に対する SOAP 応答の本文内で、 **Execute**メソッド。  
  
## <a name="see-also"></a>参照
 [DiscoverResponse 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)   
 [オブジェクト&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-objects.md)  
  
  
