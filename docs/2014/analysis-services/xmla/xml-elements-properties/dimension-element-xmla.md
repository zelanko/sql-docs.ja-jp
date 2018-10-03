---
title: ディメンション要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Dimension Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Dimension
- urn:schemas-microsoft-com:xml-analysis#Dimension
- microsoft.xml.analysis.dimension
helpviewer_keywords:
- Dimension element
ms.assetid: 85093468-e971-4b8e-9ee4-7b264ad01711
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1f20dfb338f1dd03923f8f71968f6c6f9f31bf80
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48091132"
---
# <a name="dimension-element-xmla"></a>Dimension 要素 (XMLA)
  親によって表されるキューブ ディメンションを識別する[オブジェクト](object-element-dimension-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Object>  
   ...  
   <Dimension>...</Dimension>  
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
 `Dimension` 要素は、`Object` 要素によって表されるキューブ ディメンションの名前を含むオブジェクト識別子です。  
  
## <a name="see-also"></a>参照  
 [Database 要素&#40;XMLA&#41;](database-element-xmla.md)   
 [Dimension 要素 (XMLA)](dimension-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
