---
title: "(除算)(DMX) |Microsoft ドキュメント"
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
dev_langs:
- DMX
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 7afc06cd-054b-48c3-9c3c-9a0c17d15e63
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8485c6e5cb68fcfd07f1ee812ba4c9a7035b1931
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="divide-dmx"></a>(除算)(DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  1 つの数を別の数で除算する算術演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>パラメーター  
 *被除数*  
 数値を返す有効なデータ マイニング拡張機能 (DMX) 式です。  
  
 *除数*  
 有効な DMX 式、数値を返します。  
  
## <a name="return-value"></a>戻り値  
 優先順位の高いパラメーターのデータ型を持つ値です。  
  
## <a name="remarks"></a>解説  
 この演算子が返す値は、1 番目の式を 2 番目の式で除算して得られる商を表します。  
  
 両方の式は、同じデータ型でなければなりません。または、一方の式をもう一方の式のデータ型に暗黙的に変換できる必要があります。 除算の結果が NULL 値になる場合、演算子はエラーになります。 除数と被除数の両方の結果が NULL 値になる場合、演算子は NULL 値を返します。  
  
## <a name="see-also"></a>参照  
 [算術演算子 &#40; DMX &#41;](../dmx/operators-arithmetic.md)   
 [データ マイニング拡張機能 &#40;DMX"&"#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [演算子 &#40;DMX"&"#41;](../dmx/operators-dmx.md)   
 [除算 &#40;です。SSIS 式 &#41;](../integration-services/expressions/divide-ssis-expression.md)   
 [& # #40; 除算 &#41;&#40;です。TRANSACT-SQL と #41 です。](../t-sql/language-elements/divide-transact-sql.md)  
  
  

