---
title: AttributePermission 要素 (ASSL) |Microsoft ドキュメント
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
- AttributePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributePermission
helpviewer_keywords:
- AttributePermission element
ms.assetid: efc8aa63-3959-4b2e-98f8-2a9c424298c2
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5ee5d846cdf849959bc1a916dd82fd95de60e6e8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083520"
---
# <a name="attributepermission-element-assl"></a>AttributePermission 要素 (ASSL)
  メンバーがアクセス権を定義、[ロール](role-element-assl.md)で個々 のディメンションの属性に要素がある、[キューブ](cube-element-assl.md)要素。  
  
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
|親要素|[AttributePermissions](../collections/attributepermissions-element-assl.md)|  
|子要素|[AllowedSet](../properties/allowedset-element-assl.md)、[注釈](../collections/annotations-element-assl.md)、 [AttributeID](../properties/id-element-assl.md)、 [DefaultMember](member-element-assl.md)、 [DeniedSet](../properties/deniedset-element-assl.md)、[の説明](../properties/description-element-assl.md)、 [VisualTotals](../properties/visualtotals-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AttributePermission>します。  
  
## <a name="see-also"></a>参照  
 [CubeDimensionPermission データ型&#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  