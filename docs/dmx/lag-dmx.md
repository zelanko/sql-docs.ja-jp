---
title: Lag (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0f984e50b2c6a800a66f689d88b21dfcb487e282
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38042830"
---
# <a name="lag-dmx"></a>Lag (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  現在のケースの日付と学習セットの最後の日付の間の時間スライスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Lag()  
```  
  
## <a name="return-type"></a>戻り値の型  
 整数型のスカラー値です。  
  
## <a name="remarks"></a>コメント  
 場合、 **Lag**関数を使用して、KEY TIME 列が入れ子になったテーブル内にあるモデルでは、関数をステートメントの下位選択内にあるにある必要があります。  
  
## <a name="examples"></a>使用例  
 次の例は、最近 12 か月以内にデータがモデルの学習に使用されたケースを返します。  
  
```  
SELECT * FROM [Forecasting].CASES  
WHERE Lag() < 12  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
