---
title: ターゲット要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Target Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Target
helpviewer_keywords:
- Target element
ms.assetid: 08ce0441-94b6-4f1d-acba-f31c8212cb79
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 65150d66769a2ebdb67609989efbc1a7f81e9f89
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072616"
---
# <a name="target-element-assl"></a>Target 要素 (ASSL)
  対象を識別、[アクション](../objects/action-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Action>  
   ...  
   <Target>...</Target>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[操作](../objects/action-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の予期される値は、の値によって異なります、 [TargetType](targettype-element-assl.md)親要素`Action`です。 次の表は、`Target` の値に基づいた `TargetType` の期待値を示しています。  
  
|TargetType の値|期待値|  
|----------------------|--------------------|  
|*Cube*|キューブの名前|  
|*セル*|サブキューブの式|  
|*設定*|セットの式または名前付きセットの名前 **注:** サブセレクト ステートメントを使用することはできません。|  
|*階層、HierarchyMembers*|階層の名前|  
|*ディメンション、DimensionMembers*|ディメンションの名前|  
|*レベル、LevelMembers*|レベルの名前|  
|*属性、AttributeMembers*|属性の名前|  
  
 親に対応する要素`Target`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Action>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  