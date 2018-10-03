---
title: キューブ要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Cube Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cube
- urn:schemas-microsoft-com:xml-analysis#Cube
- http://schemas.microsoft.com/analysisservices/2003/engine#Cube
helpviewer_keywords:
- Cube element
ms.assetid: 2e8662f4-fb2e-43af-b70a-9e0b5872c9b9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: de5c375e5e517e155bd6efb4beeeef61e9f31a79
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103362"
---
# <a name="cube-element-xmla"></a>Cube 要素 (XMLA)
  親によって表されるディメンションを含んでいるキューブを識別する[オブジェクト](object-element-dimension-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Object>  
   ...  
   <Cube>...</Cube>  
   ...  
</Object>  
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
|親要素|[Object](object-element-dimension-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Cube` 要素は、`Object` 要素によって表されるディメンションを含んでいるキューブの名前を含むオブジェクト識別子です。  
  
## <a name="see-also"></a>参照  
 [Database 要素&#40;XMLA&#41;](database-element-xmla.md)   
 [ディメンション要素&#40;XMLA&#41;](dimension-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
