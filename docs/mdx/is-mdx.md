---
title: (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IS
dev_langs:
- kbMDX
helpviewer_keywords:
- IS operator
ms.assetid: dc8c0b91-3bb1-49e5-8d70-57545baaa8e0
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 5a3cc017970de59914e639c42a23e7808756f076
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="is-mdx"></a>IS (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  2 つのオブジェクト式の論理比較を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Expression1 IS ( Expression2 | NULL )  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Expression1*  
 MDX オブジェクト参照を返す有効な多次元式 (MDX) 式です。  
  
 *Expression2*  
 MDX オブジェクト参照を返す有効な MDX 式です。  
  
## <a name="return-value"></a>戻り値  
 ブール値を返す**true**両方の引数が同じオブジェクトを指す場合それ以外の場合、 **false**です。 場合、 **NULL**キーワードを指定すると、オペレーターを返します**true**場合*Expression1*は**null**、それ以外の**false**です。  
  
## <a name="remarks"></a>解説  
 **IS**演算子多くの場合、判別されるかどうか組やメンバーがべき等なので、それらが正確に等しいことを意味します。  
  
## <a name="examples"></a>使用例  
 次の例を使用する方法を示しています、 **IS**かどうか、軸上の現在のメンバーは、特定のメンバーをチェックする演算子。  
  
 `With`  
  
 `//Returns TRUE if the currentmember is Bikes`  
  
 `Member [Measures].[IsBikes?] AS`  
  
 `[Product].[Category].CurrentMember IS [Product].[Category].&[1]`  
  
 `SELECT`  
  
 `{[Measures].[IsBikes?]} ON 0,`  
  
 `[Product].[Category].[Category].Members ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
