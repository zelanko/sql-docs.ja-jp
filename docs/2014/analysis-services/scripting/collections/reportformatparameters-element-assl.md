---
title: ReportFormatParameters 要素 (ASSL) |Microsoft ドキュメント
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
- ReportFormatParameters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportFormatParameters
helpviewer_keywords:
- ReportFormatParameters element
ms.assetid: f2e677bf-7b6b-4ce4-b0ec-75a4999306c9
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0e76ba9b70c485a938910eef7a7285520163b1bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175621"
---
# <a name="reportformatparameters-element-assl"></a>ReportFormatParameters 要素 (ASSL)
  コレクションを格納[ReportFormatParameter](../objects/reportformatparameter-element-asl.md)用の要素、 [ReportAction](../data-type/action-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Action xsi:type="ReportAction">  
   ...  
   <ReportFormatParameters>  
      <ReportFormatParameter>...</ReportFormatParameter>  
   </ReportFormatParameters>  
   ...  
</Action>  
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
|親要素|[アクション](../objects/action-element-assl.md)型の[ReportAction](../data-type/action-data-type-assl.md)|  
|子要素|[ReportFormatParameter](../objects/reportformatparameter-element-asl.md)|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`ReportFormatParameters`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ReportAction>します。  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  