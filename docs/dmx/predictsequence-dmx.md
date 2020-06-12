---
title: PredictSequence (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 09911d0d0d8553ab26d0fc141bcc07ed2f479728
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83666972"
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
 \<テーブル式>。  
  
## <a name="remarks"></a>Remarks  
 *N*パラメーターを指定すると、次の値が返されます。  
  
-   *N*が0より大きい場合は、次の*n*ステップで最も可能性の高いシーケンス値です。  
  
-   *N 開始*と*n エンド*の両方が指定されている場合は、 *n から開始*まで*のシーケンス値です。*  
  
## <a name="examples"></a>例  
 次の例では、 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] シーケンスクラスターマイニングモデルに基づいて、データベース内の顧客によって購入される可能性が最も高い5つの製品のシーケンスを返します。  
  
```  
SELECT  
  PredictSequence([Sequence Clustering].[v Assoc Seq Line Items],5)  
From  
  [Sequence Clustering]  
```  
  
## <a name="see-also"></a>参照  
 [DMX&#41; 関数リファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX&#41;&#40;関数](../dmx/functions-dmx.md)   
 [DMX&#41;&#40;一般的な予測関数](../dmx/general-prediction-functions-dmx.md)  
  
  
