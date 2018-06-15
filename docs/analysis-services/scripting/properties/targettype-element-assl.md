---
title: TargetType 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fe1e79254f4daef21634b4e9c5b2144c857bfee0
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34039396"
---
# <a name="targettype-element-assl"></a>TargetType 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  識別されるアイテムの項目の種類を識別、[ターゲット](../../../analysis-services/scripting/properties/target-element-assl.md)要素。  
  
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
|親要素|[操作](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*Cube*|アクションの対象はキューブです。|  
|*セル*|アクションの対象はサブキューブです。|  
|*設定*|アクションの対象はセットです。|  
|*階層*|アクションの対象は階層です。|  
|*レベル*|アクションの対象はレベルです。|  
|*DimensionMembers*|アクションの対象はディメンションのメンバーです。|  
|*HierarchyMembers*|アクションの対象は階層のメンバーです。|  
|*LevelMembers*|アクションの対象はレベルのメンバーです。|  
|*AttributeMembers*|アクションの対象は属性のメンバーです。|  
  
 許可される値に対応する列挙**TargetType**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ActionTargetType>します。  
  
 親に対応する要素**TargetType**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Action>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
