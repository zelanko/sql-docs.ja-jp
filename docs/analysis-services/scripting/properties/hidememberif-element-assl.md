---
title: "HideMemberIf 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: HideMemberIf Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: HideMemberIf
helpviewer_keywords: HideMemberIf element
ms.assetid: ff0e6b19-6216-43ac-ba76-1628da8c333b
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a5a53e8896e389b2b0cb4b478ef8a9e8ff9bd45a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="hidememberif-element-assl"></a>HideMemberIf 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]クライアント アプリケーションから、レベル内のメンバーを非表示にしてかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Level>  
   ...  
   <HideMemberIf>...</HideMemberIf>  
   ...  
</Level>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*ぜんぜん*|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Level](../../../analysis-services/scripting/objects/level-element-assl.md)|  
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
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
