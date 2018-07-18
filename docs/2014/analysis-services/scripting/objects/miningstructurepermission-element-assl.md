---
title: MiningStructurePermission 要素 (ASSL) |Microsoft Docs
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
- MiningStructurePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningStructurePermission
helpviewer_keywords:
- MiningStructurePermission element
ms.assetid: 4ba2bfd2-9003-4eed-8049-a74d452894ea
caps.latest.revision: 43
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2f3789cd5b5b72048b9c9163c11bebf4fe5a77d5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37295492"
---
# <a name="miningstructurepermission-element-assl"></a>MiningStructurePermission 要素 (ASSL)
  そのメンバーのアクセス許可を定義、[ロール](role-element-assl.md)要素は、個々 のケースが[MiningStructure](miningstructure-element-assl.md)要素。  
  
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
|データ型と長さ|[アクセス許可](../data-type/permission-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.MiningStructurePermission>します。  
  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] では、権限 `AllowDrillthrough` が拡張されてマイニング構造に適用されます。 この権限をロールに割り当てると、そのロールのメンバーであるユーザーは、次の構文を使用して、マイニング構造に直接クエリを実行できます。  
  
```  
SELECT <structure column list> FROM <structure>.CASES  
```  
  
 さらに、`AllowDrillthrough` をマイニング構造とマイニング モデルの両方で有効にした場合、ユーザーは、次の構文を使用して、マイニング モデルに含まれていない構造列にクエリを実行できます。  
  
```  
SELECT StructureColumn('<structure column name>' FROM <model>.CASES  
```  
  
 たとえば、顧客キー、顧客の収入の列のみを使用して、モデルを作成して、顧客が購入します。 ユーザーは、ドリルスルーを使用して、顧客の連絡先情報など、マイニング モデルに含まれていないその他の構造列を返すことができます。  
  
 したがって、機密データまたは個人情報を保護するため、個人情報をマスクするデータ ソース ビューを構築し、構造に対する `AllowDrillthrough` 権限は必要な場合にのみ許可する必要があります。  
  
 詳細については、「[ドリルスルー クエリ &#40;データ マイニング&#41;](../../data-mining/drillthrough-queries-data-mining.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.MiningModel.AllowDrillThrough%2A>   
 <xref:Microsoft.AnalysisServices.AdomdClient.MiningModel.AllowDrillThrough%2A>   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
