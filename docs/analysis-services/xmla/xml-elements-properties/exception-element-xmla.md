---
title: Exception 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d3e542534b85d0f87b689b196001e9a00fe49b15
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036770"
---
# <a name="exception-element-xmla"></a>Exception 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  例外が返されたことを示します、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)または[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出し。  
  
 **Namespace** `http://schemas.microsoft.com/analysisservices/2003/exception`  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<root>  
   ...  
   <Exception />  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 実行中にエラーが発生した場合、 **Discover**メソッドの呼び出しまたは単一の XMLA コマンドを**Execute**メソッドまたはコマンドが完了すると、ようにメソッドの呼び出し、**ルート**そのメソッドまたはコマンド要素が含まれています、**例外**要素と**メッセージ**要素。 **例外**要素は、メソッドまたはコマンドが正常に実行できないエラーが発生したことを示します、**メッセージ**要素には、エラーまたは警告メッセージの一覧が含まれています。エラーに関連します。  
  
## <a name="see-also"></a>参照
 [要素をメッセージ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
