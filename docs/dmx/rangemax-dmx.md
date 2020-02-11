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
ms.openlocfilehash: 61552cd8e38f77d12d7f4da10e2bbe9281e6073d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041679"
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
 スカラー値。  
  
## <a name="remarks"></a>解説  
 **RangeMax**関数は、 [DMX&#41;クエリ &#62; &#40;&#60;モデルからの SELECT DISTINCT](../dmx/select-distinct-from-model-dmx.md)で使用できます。 この型のクエリで使用される場合、スカラー列の参照には、予測可能列または入力列のいずれかである連続列または不連続列を含めることができます。  
  
 [DMX&#41;&#40;の SELECT FROM &#60;モデル&#62; 予測結合](../dmx/select-from-model-prediction-join-dmx.md)で使用する場合、 **RangeMin**、 **Rangemid**、および**RangeMax**関数は、指定されたバケットの実際の境界値を返します。 たとえば、離散化列で予測を実行する場合、クエリは予測されたバケット数を離散化列に返します。 **RangeMin**、 **rangemid**、および**RangeMax**関数は、予測によって指定されるバケットを記述します。 **RangeMax**関数を予測結合ステートメントと共に使用する場合、スカラー列参照には不連続の予測可能列のみを含めることができます。  
  
## <a name="examples"></a>例  
 次の例では、デシジョンツリーマイニングモデルの年収連続列の最小値、最大値、および平均値を返します。  
  
```  
SELECT DISTINCT   
    RangeMin([Yearly Income]) AS [Bucket Minimum],  
    RangeMid([Yearly Income]) AS [Bucket Average],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
## <a name="see-also"></a>参照  
 [DMX&#41; 関数リファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX&#41;&#40;関数](../dmx/functions-dmx.md)   
 [DMX&#41;&#40;一般的な予測関数](../dmx/general-prediction-functions-dmx.md)   
 [&#40;DMX&#41;の RangeMid](../dmx/rangemid-dmx.md)   
 [DMX&#41;&#40;RangeMin](../dmx/rangemin-dmx.md)  
  
  
