---
title: "CellPermissions 要素 (ASSL) |Microsoft ドキュメント"
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
- CellPermissions Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CellPermissions
helpviewer_keywords:
- CellPermissions element
ms.assetid: 4a604f2f-f4c3-42bd-a42b-951263942cc6
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7b370d77708b4948bfccfc53853cc2b1aee7ba21
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="cellpermissions-element-assl"></a>CellPermissions 要素 (ASSL)
  セルの関連付けられている権限のコレクションを格納[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubePermission>  
   ...  
   <CellPermissions>  
      <CellPermission>...</CellPermission>  
   </CellPermissions>  
   ...  
</CubePermission>  
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
|親要素|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)|  
|子要素|[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 コレクションには、いずれかに格納できる**CellPermission**許容の値ごとにオブジェクト、[アクセス](../../../analysis-services/scripting/properties/access-element-assl.md)要素。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.CellPermissionCollection>します。  
  
## <a name="see-also"></a>参照  
 [Permission データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [コレクション & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
