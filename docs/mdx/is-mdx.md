---
title: "(MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 97183b67350b6d3db613bb8bc8e957642bf5bb76
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="is-mdx"></a>IS (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [MDX 演算子リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)  
  
  

