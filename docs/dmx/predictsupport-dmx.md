---
title: "PredictSupport (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PredictSupport
dev_langs:
- DMX
helpviewer_keywords:
- PredictSupport function
ms.assetid: 325437d6-7cb5-4ae0-8abe-edb58fe5e90d
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9bf17c59bfc4f2ef548d695bb5a5710ba5ad249c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="predictsupport-dmx"></a>PredictSupport (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定された状態に対するサポート値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
PredictSupport(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>適用対象  
 スカラー列です。  
  
## <a name="return-type"></a>戻り値の型  
 指定された型のスカラー値 *\<*スカラー列参照*>*です。  
  
## <a name="remarks"></a>解説  
 予測された状態が省略されている場合、省略した状態バケットを除いて、最も予測可能性が高い状態が使用されます。 省略した状態バケットを含めるには、設定、\<予測状態 > に**INCLUDE_**です。  
  
 省略した状態のサポートを返すには、設定、\<予測状態 > を NULL にします。  
  
> [!NOTE]  
>  サポートされている値の計算方法は異なります。つまり、クエリの対象となるモデルに応じてこの値の解釈は異なる場合があります。 任意の特定のモデル型のサポートを計算する方法の詳細については、各アルゴリズムの種類を参照してください。[マイニング モデル コンテンツ & #40 です。Analysis Services - データ マイニング &#41;](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).  
  
## <a name="examples"></a>使用例  
 次の例は、単一クエリを使用して、個人が自転車購入者となるかどうかを予測します。また、TM Decision Tree マイニング モデルに基づいて、予測に対するサポートも判断します。  
  
```  
SELECT  
  [Bike Buyer],  
  PredictSupport([Bike Buyer]) AS [Support],  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 (&) #40";"DMX"&"#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数 (&) #40";"DMX"&"#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

