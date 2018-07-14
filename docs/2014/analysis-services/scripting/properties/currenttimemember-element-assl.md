---
title: CurrentTimeMember 要素 (ASSL) |Microsoft Docs
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
- CurrentTimeMember Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CurrentTimeMember
helpviewer_keywords:
- CurrentTimeMember element
ms.assetid: 2e73009c-9f2b-441c-bdf0-ca19b160da4f
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 804b68d36d75741869595232fd09cd67959caa70
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204102"
---
# <a name="currenttimemember-element-assl"></a>CurrentTimeMember 要素 (ASSL)
  ディメンションに関連付けられている時間の現在のメンバーを定義、 [Kpi](../objects/kpi-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Kpi>  
   ...  
   <CurrentTimeMember>...</CurrentTimeMember>  
   ...  
</AggregationDimension>  
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
|親要素|[Kpi](../objects/kpi-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、時間ディメンション内の 1 つのメンバーに評価される多次元式 (MDX) ステートメントで、主要業績評価指標 (KPI) を評価するときに現在のタイムフレームを取得するために使用します。  
  
 親に対応する要素`CurrentTimeMember`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Kpi>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
