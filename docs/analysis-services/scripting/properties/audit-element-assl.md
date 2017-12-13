---
title: "Audit 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: Audit Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Audit
helpviewer_keywords: Audit element
ms.assetid: 26488119-6490-426d-a4e4-274b5bdffbc2
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 06b0bffdf05553931ee4a44a937b1d80fb589ea7
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="audit-element-assl"></a>Audit 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]指定する、[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)要素は、サーバーのパフォーマンス低下を招く場合でも、すべてのイベントを削除できません。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Trace>  
   ...  
   <Audit>...</Audit>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|**False**|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**監査**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Trace>します。  
  
## <a name="see-also"></a>参照  
 [Traces 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/traces-element-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
