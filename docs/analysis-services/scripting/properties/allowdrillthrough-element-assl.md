---
title: "AllowDrillThrough 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AllowDrillThrough Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AllowDrillThrough
helpviewer_keywords: AllowDrillThrough element
ms.assetid: 53c9e4a3-a376-447d-a13f-80d845cc9789
caps.latest.revision: "51"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e2265da7127d8229ee95d04821f72e532ccc5cdc
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
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
 [Role 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
