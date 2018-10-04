---
title: Type 要素 (PerspectiveCalculation) (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Type Element (PerspectiveCalculation)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: d7b87aea-3265-4f3c-a7ee-4f3e90f9a0b7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2795ff88f0536a0c02ed2364cd768e893cd8db1f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48223932"
---
# <a name="type-element-perspectivecalculation-assl"></a>Type 要素 (PerspectiveCalculation) (ASSL)
  型を示す、 [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<PerspectiveCalculation>  
   ...  
   <Type>...</Type>  
   ...  
</PerspectiveCalculation>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*Member*|計算されるメンバー|  
|*設定*|名前付きセット|  
  
 許容された値に対応する列挙体`Type`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.PerspectiveCalculationType>します。  
  
 親に対応する要素`Type`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.PerspectiveCalculation>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
