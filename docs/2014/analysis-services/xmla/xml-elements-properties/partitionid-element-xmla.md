---
title: PartitionID 要素 (XMLA) |Microsoft Docs
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
- PartitionID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#PartitionID
- urn:schemas-microsoft-com:xml-analysis#PartitionID
- microsoft.xml.analysis.partitionid
helpviewer_keywords:
- PartitionID element
ms.assetid: 19f06454-9719-488e-aeb6-3fc879313351
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 663d1723598354cf4ea762ee51d34921feb516c7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231832"
---
# <a name="partitionid-element-xmla"></a>PartitionID 要素 (XMLA)
  オブジェクト参照を含む親要素内で、パーティションを識別します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Object> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <PartitionID>...</PartitionID>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|先祖または親 =<br />                        [Source](source-element-xmla.md)、[Target](../xml-elements-properties/target-element-xmla.md)<br /><br /> Cardinality= 1-1: 必須要素で、1 回だけ出現します。<br /><br /> 先祖または親 = その他すべて:<br /><br /> Cardinality = 0-1: 省略可能な要素で、出現する場合は 1 回だけの出現が可能です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Object](object-element-xmla.md)、[ParentObject](parentobject-element-xmla.md)、[Source](source-element-xmla.md)、[Target](../xml-elements-properties/target-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
