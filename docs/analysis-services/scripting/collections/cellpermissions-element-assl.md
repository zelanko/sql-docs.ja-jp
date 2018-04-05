---
title: CellPermissions 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4b7eca30646d29e5c9c2d7bb34821f4d328098b3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="cellpermissions-element-assl"></a>CellPermissions 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]セルの関連付けられている権限のコレクションを格納[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。  
  
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
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)|  
|子要素|[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 コレクションには、いずれかに格納できる**CellPermission**許容の値ごとにオブジェクト、[アクセス](../../../analysis-services/scripting/properties/access-element-assl.md)要素。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.CellPermissionCollection>します。  
  
## <a name="see-also"></a>参照  
 [Permission データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [コレクション &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
