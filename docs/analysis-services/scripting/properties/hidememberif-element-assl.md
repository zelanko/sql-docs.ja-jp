---
title: HideMemberIf 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0e01cbbf403636bf42a806ba516f9947eaab20e4
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="hidememberif-element-assl"></a>HideMemberIf 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|親要素|[レベル](../../../analysis-services/scripting/objects/level-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*ぜんぜん*|メンバーは必ず表示されます。|  
|*OnlyChildWithNoName*|メンバーがその親の唯一の子で、メンバーの名前が空の場合、メンバーは表示されません。|  
|*OnlyChildWithParentName*|メンバーがその親の唯一の子で、メンバーの名前が親の名前と同じである場合、メンバーは表示されません。|  
|*NoName*|その名前が空の場合、メンバーは非表示になります。|  
|*ParentName*|メンバーの名前が親の名前と同じである場合、メンバーは表示されません。|  
  
## <a name="remarks"></a>解説  
 許可される値に対応する列挙**HideMemberIf**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.HideIfValue>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
