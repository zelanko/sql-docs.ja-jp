---
title: "PredictAssociation (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/14/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PredictAssociation
dev_langs:
- DMX
helpviewer_keywords:
- PredictAssociation function
ms.assetid: 33eb66b5-84c6-449f-aaae-316345bc4ad5
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1fcebadb217b3ecbf2de828cc9566f4af5ffeddd
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="predictassociation-dmx"></a>PredictAssociation (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  結合メンバーシップを予測します。  
  
たとえば、PredictAssociation 関数を使用すると、顧客の買い物かごの現在の状態を示した推奨事項のセットを取得します。 
  
## <a name="syntax"></a>構文  
  
```  
  
PredictAssociation(<table column reference>, option1, option2, n ...)  
```  
  
## <a name="applies-to"></a>適用対象  
 予測可能な入れ子になったテーブル関連付けと分類の一部のアルゴリズムにはが含まれているアルゴリズム。 入れ子になったテーブルをサポートする分類アルゴリズムには、[!INCLUDE[msCoName](../includes/msconame-md.md)]デシジョン ツリー、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes、および[!INCLUDE[msCoName](../includes/msconame-md.md)]ニューラル ネットワーク アルゴリズムです。  
  
## <a name="return-type"></a>戻り値の型  
 \<テーブル式 >  
  
## <a name="remarks"></a>解説  
 オプション、 **PredictAssociation**関数には、EXCLUDE_、INCLUDE_、INCLUSIVE、EXCLUSIVE (既定)、INPUT_ONLY、INCLUDE_STATISTICS、および INCLUDE_NODE_ID が含まれます。  
  
> [!NOTE]  
>  INCLUSIVE、EXCLUSIVE、INPUT_ONLY、および INCLUDE_STATISTICS はテーブル列の参照にのみ適用され、EXCLUDE_NULL および INCLUDE_NULL はスカラー列の参照にのみ適用されます。  
  
 INCLUDE_STATISTICS はのみを返します**$Probability**と**$AdjustedProbability**です。  
  
 場合数値パラメーター  *n* を指定すると、 **PredictAssociation**確率に基づく上位の n 個の最も可能性の高い値を返します。  
  
```  
PredictAssociation(colref, [$AdjustedProbability], n)  
```  
  
 含める場合は**$AdjustedProbability**、ステートメントが最上部を返す *n* 値に基づいて、 **$AdjustedProbability**です。  
  
## <a name="examples"></a>使用例  
 次の例では、 **PredictAssociation**データベースの Adventure Works では 4 つの製品を返す関数が一緒に販売できる最も高いです。  
  
```  
SELECT  
  PredictAssociation([Association].[v Assoc Seq Line Items],4)  
From  
  [Association]  
```  
次の例使用方法について説明することができます入れ子になったテーブル、予測関数への入力として、SHAPE 句を使用します。 SHAPE クエリは、1 つの列として customerId および顧客が既に挿入製品の一覧を含む 2 番目の列として入れ子になったテーブルを行セットを作成します。 

~~~~
SELECT T.[CustomerId], PredictAssociation(MyNestedTable, 5) // returns top 5 associated items
FROM My Model
PREDICTION JOIN
SHAPE {
    OPENQUERY([Adventure Works DW],'SELECT CustomerID, OrderNumber
    FROM vAssocSeqOrders ORDER BY OrderNumber')
} APPEND (
    {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, model FROM 
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}
  RELATE OrderNumber to OrderNumber) AS T
~~~~  

  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

