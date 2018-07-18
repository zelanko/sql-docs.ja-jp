---
title: AggregationFunction 要素 (ASSL) |Microsoft Docs
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
- AggregationFunction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationFunction
helpviewer_keywords:
- AggregationFunction element
ms.assetid: 40cfc7f9-1089-45f9-be90-a29770ed9682
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 90908001138f59d4270811376ac44025148889cf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308442"
---
# <a name="aggregationfunction-element-assl"></a>AggregationFunction 要素 (ASSL)
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
|親要素|[アカウント](../objects/account-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*Sum*|メジャーは `Sum` 関数を使用して集計されます。|  
|*カウント*|メジャーは `Count` 関数を使用して集計されます。|  
|*Min*|メジャーは `Min` 関数を使用して集計されます。|  
|*Max*|メジャーは `Max` 関数を使用して集計されます。|  
|*DistinctCount*|メジャーは `DistinctCount` 関数を使用して集計されます。|  
|*なし*|メジャーは集計されません。|  
|*AverageOfChildren*|メジャーはその子の平均を返すことによって集計されます。|  
|*FirstChild*|メジャーはその最初の子メンバーを返すことによって集計されます。|  
|*LastChild*|メジャーはその最後の子メンバーを返すことによって集計されます。|  
|*FirstNonEmpty*|メジャーはその最初の空でないメンバーを返すことによって集計されます。|  
|*LastNonEmpty*|メジャーはその最後の空でないメンバーを返すことによって集計されます。|  
  
 許容された値に対応する列挙体`AggregationFunction`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.AggregationFunction>します。  
  
## <a name="see-also"></a>参照  
 [要素をアカウント&#40;ASSL&#41;](../collections/accounts-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
