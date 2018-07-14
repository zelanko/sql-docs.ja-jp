---
title: FiscalYearName 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- FiscalYearName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- FiscalYearName
helpviewer_keywords:
- FiscalYearName element
ms.assetid: ce613a21-6890-4796-aac5-b029eca46255
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2564345c916d73c5984be851523a234d2be6bbe4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37197892"
---
# <a name="fiscalyearname-element-assl"></a>FiscalYearName 要素 (ASSL)
  会計年度の名前の命名規則を定義、 [TimeBinding](../data-type/binding-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<TimeBinding>  
   ...  
   <FiscalYearName>...</FiscalYearName>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*NextCalendarYearName*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[TimeBinding](../data-type/binding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*CalendarYearName*|現在のカレンダー年度の名前を会計年度に割り当てます。|  
|*NextCalendarYearName*|来年のカレンダー年度の名前を会計年度に割り当てます。|  
  
 許容された値に対応する列挙体`FiscalYearName`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.FiscalYearName>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
