---
title: TargetType 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- TargetType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TargetType
helpviewer_keywords:
- TargetType element
ms.assetid: 2c69ea6e-2af7-435b-9841-86117d5554a7
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e4a36c4ca0e38fe00990f2185685205840eafc66
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174014"
---
# <a name="targettype-element-assl"></a>TargetType 要素 (ASSL)
  識別されるアイテムの項目の種類を識別、[ターゲット](target-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Action>  
   ...  
   <TargetType>...</TargetType>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[操作](../objects/action-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*Cube*|アクションの対象はキューブです。|  
|*セル*|アクションの対象はサブキューブです。|  
|*設定*|アクションの対象はセットです。|  
|*Hierarchy*|アクションの対象は階層です。|  
|*Level*|アクションの対象はレベルです。|  
|*DimensionMembers*|アクションの対象はディメンションのメンバーです。|  
|*HierarchyMembers*|アクションの対象は階層のメンバーです。|  
|*LevelMembers*|アクションの対象はレベルのメンバーです。|  
|*AttributeMembers*|アクションの対象は属性のメンバーです。|  
  
 許可される値に対応する列挙`TargetType`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ActionTargetType>します。  
  
 親に対応する要素`TargetType`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Action>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  