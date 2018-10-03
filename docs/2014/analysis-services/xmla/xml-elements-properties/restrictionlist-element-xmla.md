---
title: RestrictionList 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- RestrictionList Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#RestrictionList
- microsoft.xml.analysis.restrictionlist
- http://schemas.microsoft.com/analysisservices/2003/engine#RestrictionList
helpviewer_keywords:
- RestrictionList element
ms.assetid: 2297c005-381e-49a4-a207-826f7f9ea93a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cad57213c69c63dbc45e476d0163a46c111bc8a9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48067952"
---
# <a name="restrictionlist-element-xmla"></a>RestrictionList 要素 (XMLA)
  [Discover](../xml-elements-methods-discover.md) メソッドによって使用される、制限列と値のコレクションを含みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Restrictions>  
   <RestrictionList>  
      <!-- Zero or more restriction columns and values -->  
   </RestrictionList>  
</Restrictions>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[制限](restrictions-element-xmla.md)|  
|子要素|制限列と値 (「解説」を参照してください)。|  
  
## <a name="remarks"></a>コメント  
 `RestrictionList` 要素は、`Discover` メソッドによって返されるデータをフィルター処理するために使用する制限列のコレクションを含みます。 `RestrictionList` 要素内のそれぞれの制限列は、個別の XML 要素によって定義されます。 制限列の値は XML 要素に含まれるデータで、制限列の名前は XML 要素の名前に対応します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
