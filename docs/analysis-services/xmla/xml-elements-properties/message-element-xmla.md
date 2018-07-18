---
title: メッセージの要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 29780b5578c5e48c2ff8781719f9ebffe065e62c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38065890"
---
# <a name="message-element-xmla"></a>Message 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Analysis Services のインスタンスから返されたメッセージが含まれています、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)または[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出し。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Messages>  
   ...  
   <Message>  
      <Error>...</Error>  
      <!-- or -->  
      <Warning>...</Warning>  
   </Message>  
   ...  
</Messages>  
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
|親要素|[メッセージ](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)|  
|子要素|[エラー](../../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)、[警告](../../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 この要素が使用されるのは、 **Discover** メソッド呼び出しあるいは **Execute** メソッド呼び出し内の単一の XMLA コマンドが、正常に完了したもののエラーまたは警告が発生した場合です。 このような場合、**メッセージ**要素に追加されますルート要素の他のすべての要素の後に 1 つまたは複数を格納する**メッセージ**要素。 各**メッセージ**要素が 1 つを表しますによって返されるメッセージ、エラーまたは警告を[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
## <a name="see-also"></a>参照
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
