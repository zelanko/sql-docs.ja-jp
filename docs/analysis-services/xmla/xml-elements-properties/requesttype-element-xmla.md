---
title: RequestType 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fe6310da2b2869770e0dca99ad6c1ae6630133db
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="requesttype-element-xmla"></a>RequestType 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  によって返されるメタデータの種類を決定、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドです。  
  
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
|親要素|[検出します。](../../../analysis-services/xmla/xml-elements-methods-discover.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **RequestType**要素は、元のスキーマ行セットを決定、 **Discover**メソッド データを返します。 この列挙体はでサポートされているスキーマ行セットの名前に制限されて[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 スキーマ行セットの詳細については、次を参照してください。 [Analysis Services のスキーマ行セット](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)です。  
  
> [!NOTE]  
>  **RequestType**要素がスキーマ行セットの名前のみを列挙します。 スキーマ行セット GUID が使用された場合、エラーが発生します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
