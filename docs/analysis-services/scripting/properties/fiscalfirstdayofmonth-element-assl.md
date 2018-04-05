---
title: FiscalFirstDayOfMonth 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- FiscalFirstDayOfMonth Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- FiscalFirstDayOfMonth
helpviewer_keywords:
- FiscalFirstDayOfMonth element
ms.assetid: f793e93f-62de-4c3b-90b0-a46bd3cadae5
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bb49e6ea8aee935540a023255c314d4dcbc1179f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="fiscalfirstdayofmonth-element-assl"></a>FiscalFirstDayOfMonth 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]会計月の最初の日を定義、 [TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<TimeBinding>  
   ...  
   <FiscalFirstDayOfMonth>...</FiscalFirstDayOfMonth>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|Integer (1 ～ 31)|  
|既定値|**1**|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**FiscalFirstDayOfMonth**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.TimeBinding>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
