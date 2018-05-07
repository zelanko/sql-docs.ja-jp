---
title: ReportFormatParameter 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1abce4d8ef10915aef1a0c38fd6b2b98ff6c7dec
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="reportformatparameter-element---asl"></a>ReportFormatParameter 要素 - ASL
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  指定するパラメーターの値と名前を含む方法、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]実行時にレポートを書式設定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ReportFormatParameters>  
   <ReportFormatParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </ReportFormatParameter>  
</ReportFormatParameters>  
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
|親要素|[ReportFormatParameters](../../../analysis-services/scripting/collections/reportformatparameters-element-assl.md)|  
|子要素|[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[値](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**ReportFormatParameter**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ReportAction>します。  
  
## <a name="see-also"></a>参照  
 [ReportAction データ型&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [Action 要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/action-element-assl.md)   
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
