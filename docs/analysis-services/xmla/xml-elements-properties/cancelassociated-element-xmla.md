---
title: CancelAssociated 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8bf682ff9d93ee61fa300d0055e215fa25d4b4e3
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574644"
---
# <a name="cancelassociated-element-xmla"></a>CancelAssociated 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親要素 [Cancel](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) によって、関連するすべてのコマンドを取り消すかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Cancel>  
   ...  
   <ConnectionID>...</ConnectionID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|False|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[キャンセル](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素が指定されて **True**に設定されている場合、親コマンド **Cancel** によって識別される、該当するすべての接続、セッション、およびコマンドが取り消されます。  
  
## <a name="see-also"></a>参照
 [ConnectionID 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md)   
 [SessionID 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)   
 [SPID 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
