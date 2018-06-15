---
title: MiningStructurePermission 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d933d5051a9280d779c23eeb60832aee286dc131
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032553"
---
# <a name="miningstructurepermission-element-assl"></a>MiningStructurePermission 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  メンバーがアクセス権を定義、[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)、個別の要素がある[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningStructurePermissions>  
   <MiningStructurePermission xsi:type="Permission">  
      <AllowDrillthrough>...</AllowDrillthrough>  
  
      <!-- This element also inherits all the child elements listed in Permission -->  
   </MiningStructurePermission>  
</MiningStructurePermissions>  
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
|親要素|[MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.MiningStructurePermission>します。  
  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、アクセス許可**AllowDrillthrough**が拡張されてマイニング構造に適用します。 この権限をロールに割り当てると、そのロールのメンバーであるユーザーは、次の構文を使用して、マイニング構造に直接クエリを実行できます。  
  
```  
SELECT <structure column list> FROM <structure>.CASES  
```  
  
 さらに場合、 **AllowDrillthrough**が有効になって、マイニング構造とマイニング モデルの両方で、ユーザーが次の構文を使用して、マイニング モデルに含まれていない構造列を照会できます。  
  
```  
SELECT StructureColumn('<structure column name>' FROM <model>.CASES  
```  
  
 たとえば、顧客キー、顧客の収入の列のみを使用してモデルを作成して、顧客が購入します。 ユーザーは、ドリルスルーを使用して、顧客の連絡先情報など、マイニング モデルに含まれていないその他の構造列を返すことができます。  
  
 したがって、機密データまたは個人情報を保護する必要がありますを構築、データ ソース ビューを個人情報をマスクし、付与する**AllowDrillthrough**構造体に必要な場合にのみに対する権限。  
  
 詳細については、「[ドリルスルー クエリ (データ マイニング)](../../../analysis-services/data-mining/drillthrough-queries-data-mining.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.MiningModel.AllowDrillThrough%2A>   
 <xref:Microsoft.AnalysisServices.AdomdClient.MiningModel.AllowDrillThrough%2A>   
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
