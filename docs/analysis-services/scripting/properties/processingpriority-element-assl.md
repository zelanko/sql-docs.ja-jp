---
title: "ProcessingPriority 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ProcessingPriority Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ProcessingPriority element
ms.assetid: 95d07f1c-ef8d-4e38-9682-ebb7719dbe52
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9b7c417953e755171f5baeba30539372f82c0244
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="processingpriority-element-assl"></a>ProcessingPriority 要素 (ASSL)
  レイジー集計、インデックス作成、クラスター化など、バックグラウンド操作中の親オブジェクトの処理の優先順序を決定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Dimension> <!-- or MeasureGroup, Partition -->  
   ...  
   <ProcessingPriority>...</ProcessingPriority>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Integer|  
|既定値|**0**|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ディメンション](../../../analysis-services/scripting/data-type/dimension-data-type-assl.md)、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**ProcessingPriority**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.Dimension>、 <xref:Microsoft.AnalysisServices.MeasureGroup>、および<xref:Microsoft.AnalysisServices.Partition>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

