---
title: メッセージの要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Message Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.message
- http://schemas.microsoft.com/analysisservices/2003/engine#Message
- urn:schemas-microsoft-com:xml-analysis#Message
helpviewer_keywords:
- Message element
ms.assetid: 028911e2-9779-43b1-824d-6d7fb2295885
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1fbeb2085c41e239e764621a89f34b4f17661584
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241272"
---
# <a name="message-element-xmla"></a>Message 要素 (XMLA)
  インスタンスから返されたメッセージを含む[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]によって、 [Discover](../xml-elements-methods-discover.md)または[Execute](../xml-elements-methods-execute.md)メソッドの呼び出し。  
  
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
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メッセージ](messages-element-xmla.md)|  
|子要素|[エラー](error-element-xmla.md)、[警告](warning-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 この要素が使用されるのは、`Discover` メソッド呼び出しあるいは `Execute` メソッド呼び出し内の単一の XMLA コマンドが、正常に完了したもののエラーまたは警告が発生した場合です。 そのような場合、他のすべての要素に続いて `Messages` 要素が root 要素に追加され、その中には 1 つ以上の `Message` 要素が含まれます。 各`Message`要素が 1 つを表しますによって返されるメッセージ、エラーまたは警告を[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
