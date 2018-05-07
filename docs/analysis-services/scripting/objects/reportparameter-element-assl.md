---
title: ReportParameter 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 133ddf4701a979ae8041ca470d5f18eaca9bd9be
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="reportparameter-element---assl"></a>ReportParameter 要素 - ASSL
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|親要素|[ReportParameters](../../../analysis-services/scripting/collections/reportparameters-element-assl.md)|  
|子要素|[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[値](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 **値**要素は、多次元式 (MDX) 式を含める必要があります。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ReportParameter>します。  
  
## <a name="see-also"></a>参照  
 [ReportAction データ型&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [Action 要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/action-element-assl.md)   
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
