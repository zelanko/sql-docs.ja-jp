---
title: AttributePermissions 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AttributePermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributePermissions
helpviewer_keywords:
- AttributePermissions element
ms.assetid: ac703177-5936-440e-b1a5-a254a89258bc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 00abbc7be0b8efa045074773ee6e2a3526192694
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227962"
---
# <a name="attributepermissions-element-assl"></a>AttributePermissions 要素 (ASSL)
  個々 の属性の権限のコレクションを格納[ロール](../objects/role-element-assl.md)の特定のディメンション上の要素を[キューブ](../objects/cube-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeDimensionPermission> <!-- or DimensionPermission -->  
   <AttributePermissions>  
      <AttributePermission>...</AttributePermission>  
      </AttributePermissions>  
</CubeDimensionPermission>  
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
|親要素|[CubeDimensionPermission](../data-type/permission-data-type-assl.md)、 [DimensionPermission](../objects/dimensionpermission-element-assl.md)|  
|子要素|[AttributePermission](../objects/attributepermission-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 `DimensionPermission` では、このコレクションには属性ごとに 1 つの `AttributePermission` を格納できます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AttributePermissionCollection>します。  
  
## <a name="see-also"></a>参照  
 [Permission データ型&#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
