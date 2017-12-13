---
title: "Trend 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Trend Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Trend
helpviewer_keywords: Trend element
ms.assetid: d1d92d10-a181-4402-aacb-c0b2adc96bba
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8ef66ad34c074994bd651908180b525b8fec18c9
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="trend-element-assl"></a>Trend 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]傾向インジケーターを返す多次元式 (MDX) 式が含まれています、 [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Kpi>  
   ...  
   <Trend>...</Trend>  
   ...  
</Kpi>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **傾向**要素には、-1 ~ 1 の数値に評価される MDX 式が含まれています。  
  
 親に対応する要素**傾向**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Kpi>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
