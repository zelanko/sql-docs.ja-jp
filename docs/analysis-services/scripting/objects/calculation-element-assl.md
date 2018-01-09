---
title: "Calculation 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Calculation Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Calculation
helpviewer_keywords: Calculation element
ms.assetid: c96e37cf-b7ff-4296-a043-f9a5a5c444ce
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 061c954fdf8a6e19375edd385e70bd994222aa4d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="calculation-element-assl"></a>Calculation 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]計算 Asssociates、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Calculations>  
   <Calculation xsi:type="PerspectiveCalculation">  
      </Calculation>  
</Calculations>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|[PerspectiveCalculation](../../../analysis-services/scripting/data-type/perspectivecalculation-data-type-assl.md)|  
|既定値|なし|  
|基数|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[計算](../../../analysis-services/scripting/collections/calculations-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は、<xref:Microsoft.AnalysisServices.CalculationType> と <xref:Microsoft.AnalysisServices.PerspectiveCalculationType> です。  
  
## <a name="see-also"></a>参照  
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
