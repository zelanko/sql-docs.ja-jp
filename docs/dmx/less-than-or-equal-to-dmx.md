---
title: '&lt;= (以下) (DMX) |Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8d88c4b986ab05ab3bd9e90308257dd94b9e6abf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68008344"
---
# <a name="lt-less-than-or-equal-to-dmx"></a>&lt;= (以下) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  あるデータ マイニング拡張機能 (DMX) 式の値が他の DMX 式の値以下かどうかを判断する比較演算子を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DMX_Expression <= DMX_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DMX_Expression*  
 有効な DMX 式です。  
  
## <a name="return-value"></a>戻り値  
 両方のパラメーターが null 以外で、1番目のパラメーターの値が2番目のパラメーターの値以下の場合に TRUE を含むブール値です。 両方のパラメーターが null 以外で、最初のパラメーターの値が2番目のパラメーターの値よりも大きい場合、ブール値には FALSE が含まれます。 ブール値には、いずれかのパラメーターまたは両方のパラメーターが null 値に評価される場合、null 値が含まれます。  
  
## <a name="see-also"></a>参照  
 [DMX&#41;&#40;比較演算子](../dmx/operators-comparison.md)   
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41;&#40;オペレーター](../dmx/operators-dmx.md)  
  
  
