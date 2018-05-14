---
title: OrderBy 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2d2c8caf392e5d80d82b06a7d7fd9b5cd724a35e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="orderby-element-assl"></a>OrderBy 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  属性に含まれているメンバーの順序付け方法を記述します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <OrderBy>...</OrderBy>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*名前*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*名前*|メンバー名に従った順序になります。|  
|*[キー]*|メンバー キーに従った順序になります。|  
|*AttributeKey*|指定された属性のメンバー キーで並べ替えます、 [OrderByAttributeID](../../../analysis-services/scripting/properties/orderbyattributeid-element-assl.md)要素の**DimensionAttribute**です。|  
|*AttributeName*|指定された属性のメンバー名で並べ替えます、 **OrderByAttributeID**要素の**DimensionAttribute**です。|  
  
 許可される値に対応する列挙**OrderBy**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.OrderBy>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
