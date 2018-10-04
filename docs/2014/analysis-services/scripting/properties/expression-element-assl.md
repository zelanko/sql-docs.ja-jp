---
title: Expression 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Expression Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Expression
helpviewer_keywords:
- Expression element
ms.assetid: a9491b21-5279-4531-b6a5-9e8022060dd8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d7801b94d30e0b0c4baa62dd861146ee89fb3717
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48173912"
---
# <a name="expression-element-assl"></a>Expression 要素 (ASSL)
  親要素のコンテンツを定義する多次元式 (MDX) を格納します。  
  
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
  
  
