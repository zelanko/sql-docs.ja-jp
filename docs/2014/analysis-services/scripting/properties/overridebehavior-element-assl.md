---
title: OverrideBehavior 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- OverrideBehavior Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- OverrideBehavior element
ms.assetid: 6a5b361a-6061-4b73-b1a7-1237fb77606c
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e36223c59306b158812d9bdc18fccd3660c54f0c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173801"
---
# <a name="overridebehavior-element-assl"></a>OverrideBehavior 要素 (ASSL)
  記述されるリレーションシップのオーバーライド動作を示す、 [AttributeRelationship](../objects/attributerelationship-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <OverrideBehavior>...</OverrideBehavior>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*厳密な*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeRelationship](../objects/attributerelationship-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `OverrideBehavior` 要素によって、関連属性での配置がその属性での配置にどのように影響するかが決まります。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*厳密な*|AttributeRelationship 要素で記述されるリレーションシップのオーバーライド動作を示します。 一方の属性での配置がもう一方の配置にどのように影響するかを指定します。|  
|*なし*|影響しません。|  
  
 許可される値に対応する列挙`OverrideBehavior`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.OverrideBehavior>します。  
  
## <a name="see-also"></a>参照  
 [属性と属性階層](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  