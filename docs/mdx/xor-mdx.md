---
title: XOR (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- XOR
dev_langs:
- kbMDX
helpviewer_keywords:
- XOR operator
ms.assetid: 17280f36-df0e-477e-9342-e8129ed5cc3c
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: dfde684aa3b9de8403c16335247826f7d2ae4f29
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="xor-mdx"></a>XOR (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  2 つの数値式の排他的論理和演算を実行します。  
  
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
 ブール値を返す**true**に、1 つの引数が評価された場合**true**、それ以外の**false**です。  
  
## <a name="remarks"></a>解説  
 **XOR**演算子はブール値として両方のパラメーターを処理 (つまり、0 として**false**、それ以外の**true**) 排他的論理和を実行します。 次の表に示しますが、どのように**XOR**論理和を実行します。  
  
|*Expression1*|*Expression2*|戻り値|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**false**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)  
  
  
