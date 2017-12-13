---
title: "要素 (ASSL) の読み取り |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Read Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: Read element
ms.assetid: 2e2c1173-72ca-4e8a-a6cd-fd348ef96d78
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 832f89d5586bd86351604aa9b58cd1c94068a09e
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="read-element-assl"></a>Read 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]データまたはメタデータの機能を読み取れるかどうかを判断、指定された[CubeDimensionPermission](../../../analysis-services/scripting/data-type/cubedimensionpermission-data-type-assl.md)または[権限](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)要素。  
  
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
 [Cube 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Dimension 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [CubePermission 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)   
 [Permission データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
