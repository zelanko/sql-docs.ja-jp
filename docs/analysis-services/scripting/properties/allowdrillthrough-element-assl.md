---
title: AllowDrillThrough 要素 (ASSL) |Microsoft ドキュメント
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
- AllowDrillThrough Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AllowDrillThrough
helpviewer_keywords:
- AllowDrillThrough element
ms.assetid: 53c9e4a3-a376-447d-a13f-80d845cc9789
caps.latest.revision: 51
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3863648b3c8978fa8ac3b8ba981c6fa634c30ef0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="allowdrillthrough-element-assl"></a>AllowDrillThrough 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]親要素に対してドリルスルーが許可されているかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningModel> <!-- or MiningModelPermission -->  
<!-- or MiningStructurePermission -->   ...  
   <AllowDrillThrough>...</AllowDrillThrough>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|**False**|  
|基数|0-1:省略可能な要素で、出現する場合は 1 回だけの出現が可能です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningModel 要素](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)、 [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md)、 [MiningStructurePermission](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**AllowDrillThrough**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.MiningModel>、 <xref:Microsoft.AnalysisServices.MiningModelPermission>、および<xref:Microsoft.AnalysisServices.MiningStructurePermission>です。  
  
## <a name="drillthrough-on-mining-structures"></a>マイニング構造でのドリルスルー  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]を定義できます**AllowDrillthrough**マイニング構造とマイニング モデルのアクセス許可。 この権限をロールに割り当てると、そのロールのメンバーはデータ マイニング モデルにクエリを実行し、モデルに含まれていない構造列を返すことができます。 たとえば、顧客キー、顧客の収入、および顧客が購入した製品の列のみを使用するモデルを作成します。 モデルでドリルスルーを有効にすると、ユーザーは、顧客の電子メールや名前など、マイニング構造の他の列の情報を返すことができます。  
  
 したがって、機密データを保護するために、列をマイニング構造に追加する場合は注意が必要です。 また、構造には必要な場合にだけ **AllowDrillthrough** 権限を付与してください。  
  
 構造列をドリルスルーするには、次のいずれかの形のクエリを使用します。  
  
 `SELECT * FROM <structure>.CASES`  
  
 内の複数の  
  
 `SELECT StructureColumn('<structure-column-name>') FROM <model>.CASES`  
  
## <a name="see-also"></a>参照  
 [Role 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
