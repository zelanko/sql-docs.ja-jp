---
title: "要素 (ASSL) の読み取り |Microsoft ドキュメント"
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
- Read Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Read element
ms.assetid: 2e2c1173-72ca-4e8a-a6cd-fd348ef96d78
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aff524460850c6e875f5e703f5bbc065fc5ad50a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="read-element-assl"></a>Read 要素 (ASSL)
  データまたはメタデータの機能を読み取れるかどうかを判断、指定された[CubeDimensionPermission](../../../analysis-services/scripting/data-type/cubedimensionpermission-data-type-assl.md)または[権限](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeDimensionPermission> <!-- or Permission -->  
   ...  
   <Read>...</Read>  
   ...  
</CubeDimensionPermission>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*なし*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeDimensionPermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)、[権限](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*なし*|親オブジェクトのデータまたはメタデータへのアクセスは許可されていません。|  
|*許可されています。*|親オブジェクトのデータおよびメタデータへの読み取りアクセスが許可されています。|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**読み取り**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.CubeDimensionPermission>と<xref:Microsoft.AnalysisServices.Permission>です。  
  
## <a name="see-also"></a>参照  
 [Cube 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Dimension 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [CubePermission 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)   
 [Permission データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

