---
title: ID 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#ID
- urn:schemas-microsoft-com:xml-analysis#ID
- microsoft.xml.analysis.id
helpviewer_keywords:
- ID element
ms.assetid: f7d67599-6a70-4455-bfdb-1d127e5eff4e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 86a24d14a0c9e198c879e4dce092f430a4755871
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48110132"
---
# <a name="id-element-xmla"></a>ID 要素 (XMLA)
  親を実行するためのロックを識別する[ロック](../xml-elements-commands/lock-element-xmla.md)または[Unlock](../xml-elements-commands/unlock-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Lock> <!-- or Unlock>  
   ...  
   <ID>...</ID>  
   ...  
</Lock>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ロック](../xml-elements-commands/lock-element-xmla.md)、[のロックを解除](../xml-elements-commands/unlock-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `ID` 要素は、ロックを識別するためのグローバル一意識別子 (GUID) を含みます。  
  
## <a name="see-also"></a>参照  
 [要素をオブジェクト&#40;XMLA&#41;](object-element-xmla.md)   
 [Mode 要素&#40;XMLA&#41;](mode-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
