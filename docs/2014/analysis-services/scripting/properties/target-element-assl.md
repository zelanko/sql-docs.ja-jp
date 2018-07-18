---
title: Target 要素 (ASSL) |Microsoft Docs
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec2f4a43b8b03e2f28d4bd8c61a9c6e4a9d20eb5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180769"
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
 この要素の予期される値の値に依存、 [TargetType](targettype-element-assl.md)親要素`Action`します。 次の表は、`Target` の値に基づいた `TargetType` の期待値を示しています。  
  
|TargetType の値|期待値|  
|----------------------|--------------------|  
|*Cube*|キューブの名前|  
|*セル*|サブキューブの式|  
|*設定*|セットの式または名前付きセットの名前 **注:** サブセレクト ステートメントを使用することはできません。|  
|*HierarchyMembers 階層*|階層の名前|  
|*ディメンション、DimensionMembers*|ディメンションの名前|  
|*レベル、LevelMembers*|レベルの名前|  
|*属性、AttributeMembers*|属性の名前|  
  
 親に対応する要素`Target`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Action>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
