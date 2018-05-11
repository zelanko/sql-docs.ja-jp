---
title: AllowDrillThrough 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0e4897c2e0fdc7ade56a6067b8e24dbaa1bf7d2f
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="allowdrillthrough-element-assl"></a>AllowDrillThrough 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  親要素に対してドリルスルーが許可されているかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningModel> <!-- or MiningModelPermission -->  
<!-- or MiningStructurePermission -->   ...  
   <AllowDrillThrough>...</AllowDrillThrough>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|**False**|  
|Cardinality|0-1:省略可能な要素で、出現する場合は 1 回だけの出現が可能です。|  
  
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
  
 または  
  
 `SELECT StructureColumn('<structure-column-name>') FROM <model>.CASES`  
  
## <a name="see-also"></a>参照  
 [Role 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
