---
title: VisualTotals 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- VisualTotals Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- VisualTotals
helpviewer_keywords:
- VisualTotals element
ms.assetid: 352a05b1-846c-4d58-ac36-1f5ad418ba7d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f47adf2a45c0c1d06371d7f28db8d5051196bc64
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101742"
---
# <a name="visualtotals-element-assl"></a>VisualTotals 要素 (ASSL)
  この属性のメンバーに対して表示部分の合計を表示するかどうかを決定する多次元式 (MDX) を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributePermission>  
      ...  
      <VisualTotals>...</VisualTotals>  
   ...  
</AttributePermission>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|`0`|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributePermission](../objects/attributepermission-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`VisualTotals`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.AttributePermission>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
