---
title: MiningModelPermission 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 98045d14e06c73ee0a68082395e95625afb550d0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="miningmodelpermission-element-assl"></a>MiningModelPermission 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  アクセス許可のメンバーを定義、[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)、個別の要素がある[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningModelPermissions>  
   <MiningModelPermission xsi:type="Permission">  
      <!-- The following elements extend Permission -->  
      <AllowDrillThrough>...</AllowDrillThrough>  
      <AllowBrowsing>...</AllowBrowsing>  
   </MiningModelPermission>  
</MiningModelPermissions>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[アクセス許可](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningModelPermissions](../../../analysis-services/scripting/collections/miningmodelpermissions-element-assl.md)|  
|子要素|[AllowBrowsing](../../../analysis-services/scripting/properties/allowbrowsing-element-assl.md)、 [AllowDrillThrough](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、追加することによってマイニング構造でドリルスルーを有効にすることができます、 **AllowDrillthrough**するアクセス許可、 [MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md)コレクション。 場合**AllowDrillthrough**がマイニング構造とマイニング モデルを持つロールのメンバーの両方で有効になって[AllowDrillThrough 要素&#40;ASSL&#41; ](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md)モデルに対する権限を照会できますデータ マイニングをモデル化し、次の構文を使用して、モデルに含まれていない構造列を返します。  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 したがって、機密データまたは個人情報を保護するために、必要な場合は、マイニング モデルのみに **AllowDrillthrough** 権限を許可する必要があります。 詳細については、次を参照してください。 [AllowDrillThrough 要素&#40;ASSL&#41;](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md)です。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.MiningModelPermission>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
