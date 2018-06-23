---
title: ManufacturingFirstMonth 要素 (ASSL) |Microsoft ドキュメント
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
- ManufacturingFirstMonth Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ManufacturingFirstMonth
helpviewer_keywords:
- ManufacturingFirstMonth element
ms.assetid: 3b2fb440-662b-4d88-a133-1e098b9c8169
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c14ca57b15ee4c3a80bf415ca6646f1818bf1a4c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179243"
---
# <a name="manufacturingfirstmonth-element-assl"></a>ManufacturingFirstMonth 要素 (ASSL)
  最初の製造月を定義、 [TimeBinding](../data-type/binding-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<TimeBinding>  
   ...  
   <ManufacturingFirstMonth>...</ManufacturingFirstMonth>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Integer (1 ～ 12、ここで 1 は 1 月を表し、12 は 12 月を表す)|  
|既定値|`1`|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[TimeBinding](../data-type/binding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`ManufacturingFirstMonth`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.TimeBinding>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  