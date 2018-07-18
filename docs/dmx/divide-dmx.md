---
title: (除算)(DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8ab2b355c551b868cec3ee4329460f8bb0532236
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37972668"
---
# <a name="divide-dmx"></a>(除算)(DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  1 つの数を別の数で除算する算術演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>パラメーター  
 *被除数*  
 数値を返す有効なデータ マイニング拡張機能 (DMX) 式です。  
  
 *除数*  
 数値の値を返す有効な DMX 式。  
  
## <a name="return-value"></a>戻り値  
 優先順位の高いパラメーターのデータ型を持つ値です。  
  
## <a name="remarks"></a>コメント  
 この演算子が返す値は、1 番目の式を 2 番目の式で除算して得られる商を表します。  
  
 両方の式は、同じデータ型でなければなりません。または、一方の式をもう一方の式のデータ型に暗黙的に変換できる必要があります。 除算の結果が NULL 値になる場合、演算子はエラーになります。 除数と被除数の両方の結果が NULL 値になる場合、演算子は NULL 値を返します。  
  
## <a name="see-also"></a>参照  
 [算術演算子&#40;DMX&#41;](../dmx/operators-arithmetic.md)   
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [演算子&#40;DMX&#41;](../dmx/operators-dmx.md)   
 [分割&#40;SSIS 式&#41;](../integration-services/expressions/divide-ssis-expression.md)   
 [&#40;分割&#41; &#40;TRANSACT-SQL&#41;](../t-sql/language-elements/divide-transact-sql.md)  
  
  
