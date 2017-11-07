---
title: "DimensionPermissions 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DimensionPermissions Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DimensionPermissions
helpviewer_keywords:
- DimensionPermissions element
ms.assetid: cb9fdfbf-2118-423b-ba02-fa36813dbea0
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 23915ccc9ebc496be05c9ae2c0d092961e9db615
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dimensionpermissions-element-assl"></a>DimensionPermissions 要素 (ASSL)
  適用できる権限のコレクションを格納、[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)要素または[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Dimension> <!-- or CubePermission -->  
   ...  
   <DimensionPermissions>  
            <DimensionPermission>...</DimensionPermission> <!-- parent: Dimension -->  
      <!-- or -->  
      <DimensionPermission xsi:type="CubeDimensionPermission">...</DimensionPermission> <!-- parent: CubePermission -->  
      </DimensionPermissions>  
   ...  
</Dimension>  
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
|親要素|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)、[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|子要素|[DimensionPermission](../../../analysis-services/scripting/objects/dimensionpermission-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 **CubePermission**要素、 **DimensionPermission**このコレクション内の要素で指定されたアクセス許可を上書きする、 **DimensionPermissions**それぞれのコレクション明示的に参照ディメンションです。 このコレクション内のディメンションを参照していない場合、 **CubePermission**要素で指定された権限の継承、 **DimensionPermissions**ディメンションのコレクション。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DimensionPermissionCollection>します。  
  
## <a name="see-also"></a>参照  
 [コレクション & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

