---
title: "TargetType 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- TargetType Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TargetType
helpviewer_keywords:
- TargetType element
ms.assetid: 2c69ea6e-2af7-435b-9841-86117d5554a7
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 49c2fd13925130bfb76730708775f6bb0d5e79ca
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="targettype-element-assl"></a>TargetType 要素 (ASSL)
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
|*Hierarchy*|アクションの対象は階層です。|  
|*Level*|アクションの対象はレベルです。|  
|*DimensionMembers*|アクションの対象はディメンションのメンバーです。|  
|*HierarchyMembers*|アクションの対象は階層のメンバーです。|  
|*LevelMembers*|アクションの対象はレベルのメンバーです。|  
|*AttributeMembers*|アクションの対象は属性のメンバーです。|  
  
 許可される値に対応する列挙**TargetType**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ActionTargetType>します。  
  
 親に対応する要素**TargetType**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Action>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

