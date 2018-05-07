---
title: DatabasePermissions 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a268db49da5e3b6d5114caa54b526cbf74d2dcd2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="databasepermissions-element-assl"></a>DatabasePermissions 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  コレクションを格納[DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md)要素に関連付けられた、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Database>  
   ...  
   <DatabasePermissions>  
      <DatabasePermission>...</DatabasePermission>  
      </DatabasePermissions>  
      ...  
</Database>  
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
|親要素|[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)|  
|子要素|[DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DatabasePermissionCollection>します。  
  
## <a name="see-also"></a>参照  
 [Permission データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [コレクション & #40 です。ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
