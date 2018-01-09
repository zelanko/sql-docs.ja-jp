---
title: "RangeMax (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: RangeMax
dev_langs: DMX
helpviewer_keywords: RangeMax function
ms.assetid: 6798d9d7-c3dc-40fb-bd8e-56cb1a6d0e5f
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 24559ff09a5791897a41627941d0cf98c7c3cabf
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="rangemax-dmx"></a>RangeMax (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  離散化列に対して検出された予測済みバケットの上端を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RangeMax(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>適用対象  
 スカラー列。  
  
## <a name="return-type"></a>戻り値の型  
 スカラー値です。  
  
## <a name="remarks"></a>解説  
 **RangeMax**で関数を使用できます[SELECT DISTINCT FROM &60;モデル &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)クエリ。 この型のクエリで使用される場合、スカラー列の参照には、予測可能列または入力列のいずれかである連続列または不連続列を含めることができます。  
  
 使用すると[SELECT FROM &#60; モデル &#62;。予測結合 &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)、 **RangeMin**、 **RangeMid**、および**RangeMax**関数は、指定されたバケットの実際の境界値を返します。 たとえば、離散化列で予測を実行する場合、クエリは予測されたバケット数を離散化列に返します。 **RangeMin**、 **RangeMid**、および**RangeMax**関数は、予測が指定したバケットを説明します。 ときに、 **RangeMax** PREDICTION JOIN ステートメントを使用して関数が使用される、スカラー列参照は不連続列および予測可能な列のみを含めることができます。  
  
## <a name="examples"></a>使用例  
 次の例は、Decision Tree マイニング モデルの Yearly Income 連続列に対する最小値、最大値、および平均値を返します。  
  
```  
SELECT DISTINCT   
    RangeMin([Yearly Income]) AS [Bucket Minimum],  
    RangeMid([Yearly Income]) AS [Bucket Average],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)   
 [RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)  
  
  
