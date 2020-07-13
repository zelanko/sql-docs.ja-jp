---
title: Lag (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 04b06d1cbe14ee83915bd5626337720acf9bd2a9
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83670347"
---
# <a name="lag-dmx"></a>ラグ (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  現在のケースの日付とトレーニングセットの最後の日付の間のタイムスライスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Lag()  
```  
  
## <a name="return-type"></a>戻り値の型  
 整数型のスカラー値です。  
  
## <a name="remarks"></a>Remarks  
 入れ子になったテーブル内に KEY TIME 列が配置されているモデルで**Lag**関数を使用する場合、関数は、ステートメントのサブ選択内に配置する必要があります。  
  
## <a name="examples"></a>例  
 次の例では、モデルのトレーニングに使用されたデータの過去12か月以内に該当するケースを返します。  
  
```  
SELECT * FROM [Forecasting].CASES  
WHERE Lag() < 12  
```  
  
## <a name="see-also"></a>参照  
 [DMX&#41; 関数リファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX&#41;&#40;関数](../dmx/functions-dmx.md)   
 [DMX&#41;&#40;一般的な予測関数](../dmx/general-prediction-functions-dmx.md)  
  
  
