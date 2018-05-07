---
title: AttributePermission 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 64c7807809a8f0007ccda75a144f20d74cf90172
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="attributepermission-element-assl"></a>AttributePermission 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  メンバーがアクセス権を定義、[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)で個々 のディメンションの属性に要素がある、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributePermissions>  
   <AttributePermission>  
      <AttributeID>...</AttributeID>  
      <Description>...</Description>  
      <DefaultMember>...</DefaultMember>  
            <VisualTotals>...</VisualTotals>  
      <AllowedSet>...</AllowedSet>  
            <DeniedSet>...</DeniedSet>  
      <Annotations>...</Annotations>  
   </AttributePermission>  
</AttributePermissions>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributePermissions](../../../analysis-services/scripting/collections/attributepermissions-element-assl.md)|  
|子要素|[AllowedSet](../../../analysis-services/scripting/properties/allowedset-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md)、 [DefaultMember](../../../analysis-services/scripting/properties/defaultmember-element-assl.md)、 [DeniedSet](../../../analysis-services/scripting/properties/deniedset-element-assl.md)、[の説明](../../../analysis-services/scripting/properties/description-element-assl.md)、 [VisualTotals](../../../analysis-services/scripting/properties/visualtotals-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AttributePermission>します。  
  
## <a name="see-also"></a>参照  
 [CubeDimensionPermission データ型&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/cubedimensionpermission-data-type-assl.md)   
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
