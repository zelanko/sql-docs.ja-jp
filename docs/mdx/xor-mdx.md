---
title: XOR (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1657d9e58a0ae729a67e179602cd9a886ae923b1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125788"
---
# <a name="xor-mdx"></a>XOR (MDX)


  2つの数値式に対して論理的な除外を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Expression1 XOR Expression2  
  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Expression1*  
 数値を返す有効な多次元式 (MDX) 式です。  
  
 *Expression2*  
 数値を返す有効な MDX 式です。  
  
## <a name="return-value"></a>戻り値  
 1つの引数だけが**true**と評価される場合に**True**を返すブール値です。それ以外の場合は**false**。  
  
## <a name="remarks"></a>解説  
 **XOR**演算子は、両方のパラメーターをブール値として処理した後 (0 は**false**、それ以外の場合は**true**)、演算子が論理的な除外を実行します。 次の表は、 **XOR**演算子が論理的な除外を実行する方法を示しています。  
  
|*Expression1*|*Expression2*|戻り値|  
|-------------------|-------------------|------------------|  
|**本来**|**本来**|**false**|  
|**本来**|**false**|**本来**|  
|**false**|**本来**|**本来**|  
|**false**|**false**|**false**|  
  
## <a name="see-also"></a>参照  
 [Mdx 演算子リファレンス &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
