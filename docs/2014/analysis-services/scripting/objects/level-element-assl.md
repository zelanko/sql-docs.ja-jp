---
title: 上位の要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Level Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- LEVEL
helpviewer_keywords:
- Level element
ms.assetid: 66ee2c16-d6b8-4dd3-879f-1f2b6923bc43
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b057f53f04003755fecf4f297012559d48c6f09d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048249"
---
# <a name="level-element-assl"></a>Level 要素 (ASSL)
  内のレベルを定義、[階層](hierarchy-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Levels>  
      <Level>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <SourceAttributeID>...</SourceAttributeID>  
      <HideMemberIf>...</HideMemberIf>  
      <Translations>...</Translations>  
      <Annotations>...</Annotations>  
   </Level>  
</Levels>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Levels](../collections/levels-element-assl.md)|  
|子要素|[注釈](../collections/annotations-element-assl.md)、[説明](../properties/description-element-assl.md)、 [HideMemberIf](../properties/hidememberif-element-assl.md)、 [ID](../properties/id-element-assl.md)、[名前](../properties/name-element-assl.md)、 [SourceAttributeID](../properties/attributeid-element-assl.md)、[翻訳](../collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 このデータ型には、いずれの配置モード (1 - 多次元およびデータ マイニング、2 - SharePoint、および 3 - テーブル) でも制限はありません。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Level>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
