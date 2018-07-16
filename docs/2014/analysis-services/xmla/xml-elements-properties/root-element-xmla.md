---
title: root 要素 (XMLA) |Microsoft Docs
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
- Root Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#root
- urn:schemas-microsoft-com:xml-analysis#root
- microsoft.xml.analysis.root
helpviewer_keywords:
- root element
ms.assetid: ecd9d6e8-b16c-4d62-9a87-107c413a0056
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 11045be6946a5a73f0ad86fdcfcc53610800a6c4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321082"
---
# <a name="root-element-xmla"></a>root 要素 (XMLA)
  によって返される結果が含まれています、 [Discover](../xml-elements-methods-discover.md)メソッドまたは XML for Analysis (XMLA) コマンドの実行を使用して、 [Execute](../xml-elements-methods-execute.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<return> <!-- or results-->  
   ...  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">...</root> <!-- for Execute method only -->  
   <!-- or -->  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">...</root>  
   <!-- or -->  
   <root xmlns= xmlns="urn:schemas-microsoft-com:xml-analysis:empty">...</root>  
   ...  
</return>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|既定値|なし|  
|Cardinality|1-n : 必須要素で、複数回の出現が可能です|  
  
## <a name="data-type-and-length"></a>データ型と長さ  
  
|Ancestor|データ型|  
|--------------|---------------|  
|[DiscoverResponse](../xml-data-types/rowset-data-type-xmla.md)、 [olapxmla_EmptyResult](../xml-data-types/emptyresult-data-type-xmla.md)|  
|[ExecuteResponse](../xml-data-types/mddataset-data-type-xmla.md)、[行セット](../xml-data-types/rowset-data-type-xmla.md)、 [olapxmla_EmptyResult](../xml-data-types/emptyresult-data-type-xmla.md)|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[結果](results-element-xmla.md)、[を返す](return-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `root`要素には、いずれかで返される情報が含まれています、 [DiscoverResponse](../xml-elements-objects-discoverresponse.md) 、1 つによって返される要素`Discover`メソッドの呼び出し、または、 [ExecuteResponse](../xml-elements-objects-executeresponse.md)要素1 つで実行される単一 XMLA コマンドによって返される`Execute`メソッドの呼び出し。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
