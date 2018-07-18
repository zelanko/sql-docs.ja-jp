---
title: CellPermissions 要素 (ASSL) |Microsoft Docs
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
- CellPermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CellPermissions
helpviewer_keywords:
- CellPermissions element
ms.assetid: 4a604f2f-f4c3-42bd-a42b-951263942cc6
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dafcaf786d58fd8c1441c0f1df50aa5a7d47be31
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176459"
---
# <a name="cellpermissions-element-assl"></a>CellPermissions 要素 (ASSL)
  セルに関連付けられているアクセス許可のコレクションを格納[キューブ](../objects/cube-element-assl.md)要素。  
  
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
|親要素|[CubePermission](../objects/cubepermission-element-assl.md)|  
|子要素|[CellPermission](../objects/cellpermission-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 コレクションに格納できる最大 1 つ`CellPermission`オブジェクトの許容値ごとの[アクセス](../properties/access-element-assl.md)要素。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.CellPermissionCollection>します。  
  
## <a name="see-also"></a>参照  
 [Permission データ型&#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
