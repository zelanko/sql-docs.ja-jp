---
title: キューブ要素 (XMLA) |Microsoft Docs
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
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e56bc3b206069265fe21329edf688dfae9254e2d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37228132"
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
  
  
