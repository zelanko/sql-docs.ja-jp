---
title: RequestType 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 63c1a838d74745b5ef51f73b51e34c95e08a81ff
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37994794"
---
# <a name="requesttype-element-xmla"></a>RequestType 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  によって返されるメタデータの種類を判断、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッド。  
  
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
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[検出](../../../analysis-services/xmla/xml-elements-methods-discover.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 **RequestType**要素は、元のスキーマ行セットを決定します。、 **Discover**メソッドは、データを返します。 この列挙体は、Analysis Services でサポートされているスキーマ行セットの名前に制限されます。 スキーマ行セットの詳細については、次を参照してください。 [Analysis Services のスキーマ行セット](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)します。  
  
> [!NOTE]  
>  **RequestType**要素がスキーマ行セットの名前のみを列挙します。 スキーマ行セット GUID が使用された場合、エラーが発生します。  
  
## <a name="see-also"></a>参照
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
