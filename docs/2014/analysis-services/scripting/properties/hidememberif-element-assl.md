---
title: HideMemberIf 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- HideMemberIf Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- HideMemberIf
helpviewer_keywords:
- HideMemberIf element
ms.assetid: ff0e6b19-6216-43ac-ba76-1628da8c333b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ae715268b4b62c88e8d4f660c7d8d1772ccae02c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48109002"
---
# <a name="hidememberif-element-assl"></a>HideMemberIf 要素 (ASSL)
  レベル内のメンバーをクライアント アプリケーションに対して非表示にするかどうかと、そのタイミングを示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Level>  
   ...  
   <HideMemberIf>...</HideMemberIf>  
   ...  
</Level>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*ぜんぜん*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Level](../objects/level-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*ぜんぜん*|メンバーは必ず表示されます。|  
|*OnlyChildWithNoName*|メンバーがその親の唯一の子で、メンバーの名前が空の場合、メンバーは表示されません。|  
|*OnlyChildWithParentName*|メンバーがその親の唯一の子で、メンバーの名前が親の名前と同じである場合、メンバーは表示されません。|  
|*NoName*|メンバーには、その名前が空の場合は表示されません。|  
|*ParentName*|メンバーの名前が親の名前と同じである場合、メンバーは表示されません。|  
  
## <a name="remarks"></a>コメント  
 許容された値に対応する列挙体`HideMemberIf`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.HideIfValue>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
