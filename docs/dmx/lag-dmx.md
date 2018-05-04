---
title: Lag (DMX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LAG
dev_langs:
- DMX
helpviewer_keywords:
- Lag function
ms.assetid: 2da6df1a-5506-4871-a0f0-83292f1df41e
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: a376393afd10b36904c7ffad00bf87bbb5cc60e4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>解説  
 場合、 **Lag**関数を使用して KEY TIME 列が入れ子になったテーブル内に配置されているモデルで、、関数は、ステートメントの下位選択内に配置する必要があります。  
  
## <a name="examples"></a>使用例  
 次の例は、最近 12 か月以内にデータがモデルの学習に使用されたケースを返します。  
  
```  
SELECT * FROM [Forecasting].CASES  
WHERE Lag() < 12  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 (&) #40";"DMX"&"#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
