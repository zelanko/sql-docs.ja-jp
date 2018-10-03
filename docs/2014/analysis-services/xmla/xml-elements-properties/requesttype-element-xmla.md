---
title: RequestType 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 322b212853f94a1e1e5b1b48534dee649632d164
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105312"
---
# <a name="requesttype-element-xmla"></a>RequestType 要素 (XMLA)
  によって返されるメタデータの種類を判断、 [Discover](../xml-elements-methods-discover.md)メソッド。  
  
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
|親要素|[検出](../xml-elements-methods-discover.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `RequestType` 要素は、`Discover` メソッドがデータを返す基となるスキーマ行セットを決定します。 この列挙体をサポートするスキーマ行セットの名前に制限は[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。 スキーマ行セットの詳細については、次を参照してください。 [Analysis Services のスキーマ行セット](../../schema-rowsets/analysis-services-schema-rowsets.md)します。  
  
> [!NOTE]  
>  `RequestType` 要素は、スキーマ行セットの名前だけを列挙します。 スキーマ行セット GUID が使用された場合、エラーが発生します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
