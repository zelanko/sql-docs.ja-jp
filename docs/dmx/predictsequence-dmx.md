---
title: "PredictSequence (DMX) |Microsoft ドキュメント"
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
- PredictSequence
dev_langs:
- DMX
helpviewer_keywords:
- PredictSequence function
ms.assetid: c2992dfc-b99d-4430-8dcd-21ad3ffd4590
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e9ddd402be082937ec828a86d82a238d121e55dd
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="predictsequence-dmx"></a>PredictSequence (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
  

