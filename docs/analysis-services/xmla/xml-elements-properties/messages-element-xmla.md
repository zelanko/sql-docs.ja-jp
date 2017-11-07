---
title: "メッセージの要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Messages Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Messages
- microsoft.xml.analysis.messages
- urn:schemas-microsoft-com:xml-analysis#Messages
helpviewer_keywords:
- Messages element
ms.assetid: 719d15ff-f18b-4c56-80ba-a9114c0b7d8a
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b45be9ceeaf0feb601ea873b5e62f3a34e99ae5a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="messages-element-xmla"></a>Messages 要素 (XMLA)
  コレクションを格納[メッセージ](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)要素のインスタンスから返されます[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]によって、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)または[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッド呼び出しです。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Resultset>  
   <Messages>  
      <Message>  
   </Messages>  
</Resultset>  
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
|親要素|[結果セット](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|子要素|[メッセージ](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 この要素が使用されるのは、 **Discover** メソッド呼び出しあるいは **Execute** メソッド呼び出し内の単一の XMLA コマンドが、正常に完了したもののエラーまたは警告が発生した場合です。 このような場合、**メッセージ**に要素を追加、[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)1 つまたは複数を格納する要素の後にその他のすべての要素では、**メッセージ**要素。 各**メッセージ**を表す 1 つの要素によって返されるメッセージ、エラーまたは警告のいずれか、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

