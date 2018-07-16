---
title: AllowedRowsExpression 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ec24b11d-d11e-4369-a619-7e41a3c46159
caps.latest.revision: 7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7f335861084f86fa509b8c2bc3f977332d5e1da7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291328"
---
# <a name="allowedrowsexpression-element-assl"></a>AllowedRowsExpression 要素 (ASSL)
  親要素のコンテンツを定義するブール型の Data Analysis Expression (DAX) が含まれます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CellPermission> <!-- or StandardAction -->  
   ...  
   <Expression>...</Expression>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CellPermission](../objects/cellpermission-element-assl.md)、 [StandardAction](../data-type/action-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `CellPermission`要素、`Expression`要素にはによって示される権限に適用されるセルを識別する論理 MDX 式が含まれています、[アクセス](access-element-assl.md)の要素、`CellPermission`要素。 `Expression` 要素の `CellPermission` 要素の値が空である場合、`CellPermission` 要素は無視されます。  
  
 `StandardAction` 要素については、`Expression` 要素はアクションの内容を表す MDX 式を格納します。 `Expression` 要素の `StandardAction` 要素の値が空である場合、`StandardAction` 要素は無視されます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで親に対応する要素は、<xref:Microsoft.AnalysisServices.CellPermission> と <xref:Microsoft.AnalysisServices.StandardAction> です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
