---
title: "RefreshPolicy 要素 (ASSL) |Microsoft ドキュメント"
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
- RefreshPolicy Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- RefreshPolicy
helpviewer_keywords:
- RefreshPolicy element
ms.assetid: f4c36280-1a39-4f1c-a3ab-fbeb81742d6d
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 61b41604867be33a8045a80ea8bdf74cf342fba1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="refreshpolicy-element-assl"></a>RefreshPolicy 要素 (ASSL)
  どのくらいの頻度を決定ディメンションまたはメジャー グループの動的部分 (で指定されたとおり、[永続化](../../../analysis-services/scripting/properties/persistence-element-assl.md)要素) の変更がチェックされます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <RefreshPolicy>...</RefreshPolicy>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|次の表を参照してください。|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
|先祖または親|既定値|  
|------------------------|-------------------|  
|[DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)|*ByQuery*|  
|[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|なし|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)、 [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*ByQuery*|すべてのクエリで、ソース データが変更されたかどうかを確認します。|  
|*ByInterval*|ソース データがで指定された間隔での変更チェックのみ[RefreshInterval](../../../analysis-services/scripting/properties/refreshinterval-element-assl.md)です。|  
  
 許可される値に対応する列挙**RefreshPolicy**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.RefreshPolicy>します。  
  
## <a name="see-also"></a>参照  
 [Persistence 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/persistence-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

