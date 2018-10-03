---
title: オブジェクトの要素 (Dimension) (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Object Element (Dimension)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Object
- urn:schemas-microsoft-com:xml-analysis#Object
- microsoft.xml.analysis.object
helpviewer_keywords:
- Object element
ms.assetid: db7feb39-7cc1-4b54-8979-77ce402ef71f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b4c9fea7e5971bec14f172f482db2ae72efdf154
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051062"
---
# <a name="object-element-dimension-xmla"></a>Object 要素 (Dimension) (XMLA)
  ディメンションのオブジェクト参照を含む親[挿入](../xml-elements-commands/insert-element-xmla.md)、[更新](../xml-elements-commands/update-element-xmla.md)、または[ドロップ](../xml-elements-commands/drop-element-xmla.md)コマンドを実行します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Insert> <!-- or any of the parent elements in the Element Relationships table -->  
...  
   <Object>  
      <Database>...</Database>  
      <Cube>...</Cube>  
      <Dimension>...</Dimension>  
   </Object>  
...  
</Insert>  
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
|親要素|[Drop](../xml-elements-commands/drop-element-xmla.md)、[挿入](../xml-elements-commands/insert-element-xmla.md)、 [Update](../xml-elements-commands/update-element-xmla.md)|  
|子要素|[キューブ](cube-element-xmla.md)、[データベース](database-element-xmla.md)、[ディメンション](dimension-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
