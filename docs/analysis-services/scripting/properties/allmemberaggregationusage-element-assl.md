---
title: AllMemberAggregationUsage 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AllMemberAggregationUsage Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AllMemberAggregationUsage
helpviewer_keywords:
- AllMemberAggregationUsage element
ms.assetid: 264fe9d8-8e9a-4642-8cee-7c2804126926
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d279ebfd901a66ecc762874800a9a9cca46a0488
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="allmemberaggregationusage-element-assl"></a>AllMemberAggregationUsage 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  コントロール方法で、集計デザイナー [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]集計をデザインします。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeDimension>  
   ...  
   <AllMemberAggregationUsage>...</AllMemberAggregationUsage>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*[Default]*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*[完全]*|キューブの各集計に、All メンバーが含まれている必要があります。|  
|*なし*|キューブの集計に All メンバーを含めることはできません。|  
|*制限なし*|集計デザイナーに対して制約を課しません。|  
|*[Default]*|同じ*無制限*です。|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**AllMemberAggregationUsage**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.CubeDimension>します。  
  
## <a name="see-also"></a>参照  
 [Cube 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Dimension 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
