---
title: MeasureExpression 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MeasureExpression Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureExpression
helpviewer_keywords:
- MeasureExpression element
ms.assetid: a0b6490d-a793-41be-8c97-41b08e1580a1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: edcf32c71f681bf6d8892b8848dfaa67ca8674b1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113392"
---
# <a name="measureexpression-element-assl"></a>MeasureExpression 要素 (ASSL)
  親メジャーの値を取得する方法を定義する多次元式 (MDX) を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Measure>  
   ...  
   <MeasureExpression>...</MeasureExpression>  
   ...  
</Measure>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メジャー](../objects/measure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`MeasureExpression`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Measure>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
