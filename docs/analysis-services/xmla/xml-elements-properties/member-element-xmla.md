---
title: Member 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1c962452675a0c1c91a3573546f0763060dfb44e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37994644"
---
# <a name="member-element-xmla"></a>Member 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  1 つの親メンバーを表す[メンバー](../../../analysis-services/xmla/xml-elements-properties/members-element-xmla.md)または[タプル](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Members>  
   ...  
   <Member>  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Members>  
<!-- or -->  
<Tuple>  
   ...  
   <Member Hierarchy="string">  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Tuple>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メンバー](../../../analysis-services/xmla/xml-elements-properties/members-element-xmla.md)、[タプル](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md)|  
|子要素|[キャプション](../../../analysis-services/xmla/xml-elements-properties/caption-element-xmla.md)、 [DisplayInfo](../../../analysis-services/xmla/xml-elements-properties/displayinfo-element-xmla.md)、 [LName](../../../analysis-services/xmla/xml-elements-properties/lname-element-xmla.md)、 [LNum](../../../analysis-services/xmla/xml-elements-properties/lnum-element-xmla.md)、 [UName](../../../analysis-services/xmla/xml-elements-properties/uname-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|Hieararchy|必要な**文字列**属性 (親の**タプル**要素のみ)。 によって表されるメンバーを階層の名前、**メンバー**要素が属しています。|  
  
## <a name="remarks"></a>コメント  
 **メンバー**要素には識別し、指定された階層内のメンバーを表示するための情報が含まれています。 親の**メンバー**要素では、階層は指定された、**階層**親要素の属性です。 親の**タプル**、要素を使用して、階層を指定、**階層**の属性、**メンバー**要素。  
  
## <a name="see-also"></a>参照
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
