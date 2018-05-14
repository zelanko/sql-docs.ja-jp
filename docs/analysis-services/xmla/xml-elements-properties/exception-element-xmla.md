---
title: Exception 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 91350ba6e82e070707d17b58c82bf305c1e87660
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="exception-element-xmla"></a>Exception 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  例外が返されたことを示す、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)または[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出しです。  
  
 **名前空間** `http://schemas.microsoft.com/analysisservices/2003/exception`  
  
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
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 実行中にエラーが発生した場合、 **Discover**メソッドの呼び出しまたは単一の XMLA コマンドは、 **Execute**メソッドまたはコマンドが完了すると、防止をメソッド呼び出し、**ルート**そのメソッドまたはコマンド要素が含まれています、**例外**要素、および**メッセージ**要素。 **例外**要素は、メソッドまたはコマンドが正常に実行されないようにするエラーが発生したことを示します、**メッセージ**要素には、エラーまたは警告メッセージの一覧が含まれています。エラーに関連しています。  
  
## <a name="see-also"></a>参照  
 [要素をメッセージ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)   
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
