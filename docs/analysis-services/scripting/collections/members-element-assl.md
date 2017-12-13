---
title: "Members 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: Members Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Members
helpviewer_keywords: Members element
ms.assetid: 4bf585a3-b681-486d-852b-1244c5658a04
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8ceae98a2d9dc0260c417c1e956dd76532f9f7bf
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="members-element-assl"></a>Members 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]コレクションを格納[メンバー](../../../analysis-services/scripting/objects/member-element-assl.md)親要素の要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Group> <!-- or Role --<  
   ...  
   <Members>  
      <Member>...</Member>  
   </Members>  
   ...  
</Group>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[グループ](../../../analysis-services/scripting/objects/group-element-assl.md)、[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)|  
|子要素|[メンバー](../../../analysis-services/scripting/objects/member-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**メンバー**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.Group>と<xref:Microsoft.AnalysisServices.Role>です。  
  
## <a name="see-also"></a>参照  
 [コレクション &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
