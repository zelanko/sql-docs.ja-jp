---
title: RangeMax (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 417f92a00e396952218c6ef04d105245f1e3708e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37968264"
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
  
## <a name="remarks"></a>コメント  
 **RangeMax**で関数を使用できます[SELECT DISTINCT FROM&#60;モデル&#62; &#40;DMX&#41; ](../dmx/select-distinct-from-model-dmx.md)クエリ。 この型のクエリで使用される場合、スカラー列の参照には、予測可能列または入力列のいずれかである連続列または不連続列を含めることができます。  
  
 使用すると[SELECT FROM&#60;モデル&#62;PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)、 **RangeMin**、 **RangeMid**、および**RangeMax**関数、指定されたバケットの実際の境界値を返します。 たとえば、離散化列で予測を実行する場合、クエリは予測されたバケット数を離散化列に返します。 **RangeMin**、 **RangeMid**、および**RangeMax**関数が、予測が指定したバケットを説明します。 ときに、 **RangeMax** PREDICTION JOIN ステートメントを使用して関数を使用すると、スカラー列参照は不連続列および予測可能な列のみを保持できます。  
  
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
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)   
 [RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)  
  
  
