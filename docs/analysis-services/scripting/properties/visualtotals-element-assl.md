---
title: "VisualTotals 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: VisualTotals Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: VisualTotals
helpviewer_keywords: VisualTotals element
ms.assetid: 352a05b1-846c-4d58-ac36-1f5ad418ba7d
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 83b969da423d46d241cbd6af4ca8f1574010c20a
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="visualtotals-element-assl"></a>VisualTotals 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]この属性のメンバーに対して表示部分の合計を表示するかどうかを決定する多次元式 (MDX) 式が含まれています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributePermission>  
      ...  
      <VisualTotals>...</VisualTotals>  
   ...  
</AttributePermission>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|**0**|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributePermission](../../../analysis-services/scripting/objects/attributepermission-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**VisualTotals**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.AttributePermission>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
