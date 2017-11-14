---
title: "CancelAssociated 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- CancelAssociated Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.cancelassociated
- urn:schemas-microsoft-com:xml-analysis#CancelAssociated
- http://schemas.microsoft.com/analysisservices/2003/engine#CancelAssociated
helpviewer_keywords:
- CancelAssociated element
ms.assetid: fd890440-d1a7-4c05-9e81-c81e6b8c274c
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3f1441e6e54a085181bf7afcff8c4961a8a60d9c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="cancelassociated-element-xmla"></a>CancelAssociated 要素 (XMLA)
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
  
## <a name="remarks"></a>解説  
 この要素が指定されて **True**に設定されている場合、親コマンド **Cancel** によって識別される、該当するすべての接続、セッション、およびコマンドが取り消されます。  
  
## <a name="see-also"></a>参照  
 [ConnectionID 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md)   
 [SessionID 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)   
 [SPID 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)   
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

