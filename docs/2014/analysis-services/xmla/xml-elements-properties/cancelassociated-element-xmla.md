---
title: CancelAssociated 要素 (XMLA) |Microsoft ドキュメント
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
- CancelAssociated Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cancelassociated
- urn:schemas-microsoft-com:xml-analysis#CancelAssociated
- http://schemas.microsoft.com/analysisservices/2003/engine#CancelAssociated
helpviewer_keywords:
- CancelAssociated element
ms.assetid: fd890440-d1a7-4c05-9e81-c81e6b8c274c
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 1e747815b30daf86edff4ad976d6fb5370bf9c3b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178731"
---
# <a name="cancelassociated-element-xmla"></a>CancelAssociated 要素 (XMLA)
  親要素 [Cancel](../xml-elements-commands/cancel-element-xmla.md) によって、関連するすべてのコマンドを取り消すかどうかを示します。  
  
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
|親要素|[Cancel](../xml-elements-commands/cancel-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素が指定されており、設定場合`True`、すべての対応する接続、セッション、および親に指定されたコマンド`Cancel`コマンドが取り消されました。  
  
## <a name="see-also"></a>参照  
 [ConnectionID 要素&#40;XMLA&#41;](id-element-xmla.md)   
 [SessionID 要素&#40;XMLA&#41;](sessionid-element-xmla.md)   
 [SPID 要素&#40;XMLA&#41;](spid-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  