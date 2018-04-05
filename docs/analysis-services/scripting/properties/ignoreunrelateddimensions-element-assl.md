---
title: IgnoreUnrelatedDimensions 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IgnoreUnrelatedDimensions Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- IgnoreUnrelatedDimensions
helpviewer_keywords:
- IgnoreUnrelatedDimensions element
ms.assetid: c7d7a1cd-a8e0-4ae7-9464-a1d2a55a86ab
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 717d36bd445d777981c24e466c4bdcea674e00b1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="ignoreunrelateddimensions-element-assl"></a>IgnoreUnrelatedDimensions 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]クエリでメジャー グループに関連付けられているディメンションのメンバーが含まれている場合、関連付けられていないディメンションをトップ レベルに強制かどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureGroup>  
   ...  
   <IgnoreUnrelatedDimensions>...</IgnoreUnrelatedDimensions>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|True|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メジャー グループ](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 ときに**IgnoreUnrelatedDimensions**は**true**、関連付けられていないディメンションが最上位レベルに強制以外の値が**false**ディメンションはトップ レベルに強制されません。 このプロパティは、同様に、多次元式 (MDX) [ValidMeasure](../../../mdx/validmeasure-mdx.md)関数。  
  
 親に対応する要素**IgnoreUnrelatedDimensions**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MeasureGroup>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
