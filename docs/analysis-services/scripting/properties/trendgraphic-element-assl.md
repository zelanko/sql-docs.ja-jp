---
title: "TrendGraphic 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- TrendGraphic Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TrendGraphic
helpviewer_keywords:
- TrendGraphic element
ms.assetid: 7448fd80-3072-4d85-b3a0-6606d1d20885
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c209d484e004deddd1c9ba2e169511c07658e13d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="trendgraphic-element-assl"></a>TrendGraphic 要素 (ASSL)
  傾向の推奨のグラフィカル表示が含まれています、 [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Kpi>  
   ...  
   <TrendGraphic>...</TrendGraphic>  
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
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*標準の矢印*|標準の矢印|  
|*状態の矢印 - 昇順*|状態の矢印|  
|*降順の状態の矢印*|反転した状態の矢印|  
|*スマイリー フェイス*|顔マーク|  
  
 親に対応する要素**TrendGraphic**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Kpi>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

