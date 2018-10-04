---
title: MiningModelPermission 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MiningModelPermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModelPermission
helpviewer_keywords:
- MiningModelPermission element
ms.assetid: 4bd2f7e7-ff0d-404e-96fb-7e2c4eeb91e9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c6bad2b1bda46fcc1437a5f4c967ced8a6c726f0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113472"
---
# <a name="miningmodelpermission-element-assl"></a>MiningModelPermission 要素 (ASSL)
  メンバーのアクセス許可を定義、[ロール](role-element-assl.md)要素は、個々 のケースが[MiningModel](miningmodel-element-assl.md)要素。  
  
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
|データ型と長さ|[アクセス許可](../data-type/permission-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningModelPermissions](../collections/miningmodelpermissions-element-assl.md)|  
|子要素|[AllowBrowsing](../properties/allowbrowsing-element-assl.md)、 [AllowDrillThrough](../properties/allowdrillthrough-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、追加することによってマイニング構造でドリルスルーを有効にすることができます、`AllowDrillthrough`へのアクセス許可、 [MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md)コレクション。 場合`AllowDrillthrough`がマイニング構造とマイニング モデルを持つロールのメンバーの両方で有効になって[AllowDrillThrough 要素&#40;ASSL&#41; ](../properties/allowdrillthrough-element-assl.md)モデルに対する権限は、データ マイニング モデルを照会し、返す含まれていないモデルでは、次の構文を使用して構造列:  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 したがって、機密データまたは個人情報を保護するために、必要な場合は、マイニング モデルのみに `AllowDrillthrough` 権限を許可する必要があります。 詳細については、次を参照してください。 [AllowDrillThrough 要素&#40;ASSL&#41;](../properties/allowdrillthrough-element-assl.md)します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.MiningModelPermission>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
