---
title: RequestType 要素 (XMLA) |Microsoft ドキュメント
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
- RequestType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#RequestType
- urn:schemas-microsoft-com:xml-analysis#RequestType
- microsoft.xml.analysis.requesttype
helpviewer_keywords:
- RequestType element
ms.assetid: 54270a57-e327-4233-b4b2-d85b44652ac5
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: b1b2bcc4bf6f97659239a9e53d4adac52d7794a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176247"
---
# <a name="requesttype-element-xmla"></a>RequestType 要素 (XMLA)
  によって返されるメタデータの種類を決定、 [Discover](../xml-elements-methods-discover.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Discover>  
   ...  
   <RequestType>...</RequestType>  
   ...  
</Discover>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[検出します。](../xml-elements-methods-discover.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `RequestType` 要素は、`Discover` メソッドがデータを返す基となるスキーマ行セットを決定します。 この列挙体はでサポートされているスキーマ行セットの名前に制限されて[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 スキーマ行セットの詳細については、次を参照してください。 [Analysis Services のスキーマ行セット](../../schema-rowsets/analysis-services-schema-rowsets.md)です。  
  
> [!NOTE]  
>  `RequestType` 要素は、スキーマ行セットの名前だけを列挙します。 スキーマ行セット GUID が使用された場合、エラーが発生します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  