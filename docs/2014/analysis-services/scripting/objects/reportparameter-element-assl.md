---
title: ReportParameter 要素 (ASSL) |Microsoft ドキュメント
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
- ReportParameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportParameter
helpviewer_keywords:
- ReportParameter element
ms.assetid: 653a5c64-f1af-4796-bb7b-b44a40e52901
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 58aeafeaee114c1d08d0ad8b0119bee2dc5d5dea
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084400"
---
# <a name="reportparameter-element-assl"></a>ReportParameter 要素 (ASSL)
  渡されるパラメーターの値と名前が含まれています、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]実行時にレポートします。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ReportParameters>  
      <ReportParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </ReportParameter>  
</ReportParameters>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ReportParameters](../collections/reportparameters-element-assl.md)|  
|子要素|[名前](../properties/name-element-assl.md)、[値](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 `Value` 要素には多次元式 (MDX) が含まれている必要があります。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ReportParameter>します。  
  
## <a name="see-also"></a>参照  
 [ReportAction データ型&#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [Action 要素&#40;ASSL&#41;](action-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  