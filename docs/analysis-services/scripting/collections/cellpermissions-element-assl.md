---
title: CellPermissions 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a15ef5ebac41399e140ea2693f09be749c1ee413
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="cellpermissions-element-assl"></a>CellPermissions 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Permission データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [コレクション & #40 です。ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
