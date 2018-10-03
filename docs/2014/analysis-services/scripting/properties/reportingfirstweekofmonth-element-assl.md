---
title: ReportingFirstWeekOfMonth 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ReportingFirstWeekOfMonth Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportingFirstWeekOfMonth
helpviewer_keywords:
- ReportingFirstWeekOfMonth element
ms.assetid: 29818404-ad45-403f-8fd9-3e3246d301ad
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 619064e1e292fea5c66add548571974e5ae01080
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104275"
---
# <a name="reportingfirstweekofmonth-element-assl"></a>ReportingFirstWeekOfMonth 要素 (ASSL)
  レポート月の最初の週を定義、 [TimeBinding](../data-type/binding-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<TimeBinding>  
   ...  
   <ReportingFirstWeekOfMonth>...</ReportingFirstWeekOfMonth>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Integer (1 ～ 4)|  
|既定値|`1`|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[TimeBinding](../data-type/binding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`ReportingFirstWeekOfMonth`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.TimeBinding>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
