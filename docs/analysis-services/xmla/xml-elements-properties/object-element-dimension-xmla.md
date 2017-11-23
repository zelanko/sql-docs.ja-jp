---
title: "オブジェクトの要素 (Dimension) (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
apiname: Object Element (Dimension)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Object
- urn:schemas-microsoft-com:xml-analysis#Object
- microsoft.xml.analysis.object
helpviewer_keywords: Object element
ms.assetid: db7feb39-7cc1-4b54-8979-77ce402ef71f
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8e71db80848a496260137fb3f3937ed755e9ed95
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="object-element-dimension-xmla"></a>Object 要素 (Dimension) (XMLA)
  ディメンションのオブジェクト参照が含まれています、親[挿入](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)、[更新](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)、または[ドロップ](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)コマンドを実行します。  
  
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
|親要素|[Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)、[挿入](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)、[更新](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|  
|子要素|[キューブ](../../../analysis-services/xmla/xml-elements-properties/cube-element-xmla.md)、[データベース](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)、[ディメンション](../../../analysis-services/xmla/xml-elements-properties/dimension-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
