---
title: AggregationFunction 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AggregationFunction Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregationFunction
helpviewer_keywords:
- AggregationFunction element
ms.assetid: 40cfc7f9-1089-45f9-be90-a29770ed9682
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c7c9aedc12abbeb5ab805e0d85cfe1421857749b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="aggregationfunction-element-assl"></a>AggregationFunction 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  勘定科目の種類に使用する集計関数を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Account>  
   ...  
   <AggregationFunction>...</AggregationFunction>  
   ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*Sum*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アカウント](../../../analysis-services/scripting/objects/account-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*Sum*|使用してメジャーを集計、**合計**関数。|  
|*Count*|使用してメジャーを集計、**カウント**関数。|  
|*Min*|使用してメジャーを集計、 **Min**関数。|  
|*Max*|使用してメジャーを集計、 **Max**関数。|  
|*DistinctCount*|使用してメジャーを集計、 **DistinctCount**関数。|  
|*なし*|メジャーは集計されません。|  
|*AverageOfChildren*|メジャーはその子の平均を返すことによって集計されます。|  
|*FirstChild*|メジャーはその最初の子メンバーを返すことによって集計されます。|  
|*LastChild*|メジャーはその最後の子メンバーを返すことによって集計されます。|  
|*FirstNonEmpty*|メジャーはその最初の空でないメンバーを返すことによって集計されます。|  
|*LastNonEmpty*|メジャーはその最後の空でないメンバーを返すことによって集計されます。|  
  
 許可される値に対応する列挙**AggregationFunction**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.AggregationFunction>します。  
  
## <a name="see-also"></a>参照  
 [要素をアカウント&#40;ASSL&#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
