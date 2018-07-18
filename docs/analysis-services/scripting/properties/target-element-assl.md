---
title: Target 要素 (ASSL) |Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 98ec5c729f5735343f5eaa87e5232fcfb138cf38
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38045780"
---
# <a name="target-element-assl"></a>Target 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  対象を識別、[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)要素。  
  
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
|親要素|[操作](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の予期される値の値に依存、 [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md)親要素**アクション**します。 次の表に、予期される値の**ターゲット**の値に基づく**TargetType**します。  
  
|TargetType の値|期待値|  
|----------------------|--------------------|  
|*Cube*|キューブの名前|  
|*セル*|サブキューブの式|  
|*設定*|セットの式または名前付きセットの名前<br /><br /> 注: サブセレクト ステートメントは使用できません。|  
|*HierarchyMembers 階層*|階層の名前|  
|*ディメンション、DimensionMembers*|ディメンションの名前|  
|*レベル、LevelMembers*|レベルの名前|  
|*属性、AttributeMembers*|属性の名前|  
  
 親に対応する要素**ターゲット**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Action>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
