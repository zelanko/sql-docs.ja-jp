---
title: "DatabaseID 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DatabaseID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.databaseid
- urn:schemas-microsoft-com:xml-analysis#DatabaseID
- http://schemas.microsoft.com/analysisservices/2003/engine#DatabaseID
helpviewer_keywords:
- DatabaseID element
ms.assetid: 2df720dd-9b42-449a-9df6-0d12930603f0
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 53f64d6a5f1842a3fde67a4eb5877503e66b1785
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="databaseid-element-xmla"></a>DatabaseID 要素 (XMLA)
  オブジェクト参照を含む親要素内で、データベースを識別します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Object> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <DatabaseID>...</DatabaseID>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|次の表を参照してください。|  
  
|先祖または親|Cardinality|  
|------------------------|-----------------|  
|[Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)、[Target](../../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)|1-1 : 必須要素で、1 回だけ出現します|  
|他のすべて|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Object](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)、[ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)、[Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)、[Target](../../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

