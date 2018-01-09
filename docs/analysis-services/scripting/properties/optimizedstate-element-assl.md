---
title: "OptimizedState 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: OptimizedState Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: OptimizedState
helpviewer_keywords: OptimizedState element
ms.assetid: 120dcc4c-8fe8-4471-bbd6-99ad534364f0
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 154348d593c3f1fff01a181be362ad6dbbe19631
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="optimizedstate-element-assl"></a>OptimizedState 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]階層に適用される最適化のレベルを決定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeHierarchy>  
   ...  
   <OptimizedState>...</OptimizedState>  
   ...  
</CubeHierarchy>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*FullyOptimized*|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*FullyOptimized*|インスタンスは、階層のインデックスを構築し、クエリ パフォーマンスを改善します。|  
|*NotOptimized*|インスタンスは追加のインデックスを構築しません。|  
  
 許可される値に対応する列挙**OptimizedState**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.OptimizationType>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
