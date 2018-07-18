---
title: return 要素 (XMLA) |Microsoft Docs
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
- return Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.return
- http://schemas.microsoft.com/analysisservices/2003/engine#return
- urn:schemas-microsoft-com:xml-analysis#return
helpviewer_keywords:
- return element
ms.assetid: 3cfe8b74-fec3-4987-a74a-5f731444e024
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4808372fbf80b2b3a79bc11e3f2423511eb717be
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192410"
---
# <a name="return-element-xmla"></a>return 要素 (XMLA)
  によって返される情報が含まれています、 [DiscoverResponse](../xml-elements-objects-discoverresponse.md)への応答内の要素を[Discover](../xml-elements-methods-discover.md)メソッドの呼び出しまたは[ExecuteResponse](../xml-elements-objects-executeresponse.md) に応じて要素の[Execute](../xml-elements-methods-execute.md)メソッドの呼び出し。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DiscoverResponse> <!-- or ExecuteResponse -->  
   <return>  
      <root>...</root>  
      <!-- or -->  
      <results>...</results> <!-- ExecuteResponse only -->  
   </return>  
</DiscoverResponse>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DiscoverResponse](../xml-elements-objects-discoverresponse.md)、 [ExecuteResponse](../xml-elements-objects-executeresponse.md)|  
|先祖:[DiscoverResponse](../xml-elements-objects-discoverresponse.md)|子: <br />                        [root](root-element-xmla.md)|  
|先祖: <br />                        [ExecuteResponse](../xml-elements-objects-executeresponse.md)|子:[ルート](root-element-xmla.md)または[結果](results-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `return` 要素は、`Discover` および `Execute` メソッドによって返されるデータを含みます。 通常、`return` 要素には単一の `root` 要素が含まれ、その要素には正常に実行された `Discover` または `Execute` メソッド呼び出しによって返されたデータ、あるいは正常に実行されなかったメソッド呼び出しによって返された XML for Analysis (XMLA) 例外が含まれます。 複数の操作を実行する `Execute` コマンドが `Batch` メソッドの中に含まれる場合、`return` 要素には `results` 要素が含まれ、その中には、`root` コマンドによって正常に実行された (および正常に実行されなかった) 各コマンドごとに 1 つの `Batch` 要素が含まれます。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
