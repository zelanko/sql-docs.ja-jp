---
title: "PredictSequence (DMX) |Microsoft ドキュメント"
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
f1_keywords: PredictSequence
dev_langs: DMX
helpviewer_keywords: PredictSequence function
ms.assetid: c2992dfc-b99d-4430-8dcd-21ad3ffd4590
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: aaeb95f70c9afc6872bd56df494a8eba88f98f91
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="predictsequence-dmx"></a>PredictSequence (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定された一連のシーケンス データに対して予測される将来のシーケンス値です。  
  
## <a name="syntax"></a>構文  
  
```  
  
PredictSequence(<table column reference>)  
PredictSequence(\<table column reference, n>)  
PredictSequence(\<table column reference, n-start, n-end>)  
```  
  
## <a name="return-type"></a>戻り値の型  
 A\<テーブル式 >。  
  
## <a name="remarks"></a>解説  
 場合、  *n* パラメーターを指定すると、次の値を返します。  
  
-   場合 *n* が 0 の場合、次に、最も可能性の高いシーケンス値より大きい *n* 手順を実行します。  
  
-   両方*n 開始*と*n エンド*指定すると、シーケンスの値から*n 開始*に*n エンド*です。  
  
## <a name="examples"></a>使用例  
 次の例は、顧客が購入する可能性が高い 5 つの製品のシーケンスを返す、 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] Sequence Clustering マイニング モデルに基づいて、データベース。  
  
```  
SELECT  
  PredictSequence([Sequence Clustering].[v Assoc Seq Line Items],5)  
From  
  [Sequence Clustering]  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
