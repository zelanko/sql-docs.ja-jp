---
title: Members 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Members Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Members
helpviewer_keywords:
- Members element
ms.assetid: 4bf585a3-b681-486d-852b-1244c5658a04
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b7d2be7834c48c5a65877ae6fd480f2a7d6ea459
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191062"
---
# <a name="members-element-assl"></a>Members 要素 (ASSL)
  コレクションを格納[メンバー](../objects/member-element-assl.md)の親要素の要素。  
  
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
|親要素|[グループ](../objects/group-element-assl.md)、[ロール](../objects/role-element-assl.md)|  
|子要素|[Member](../objects/member-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`Members`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.Group>と<xref:Microsoft.AnalysisServices.Role>します。  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
