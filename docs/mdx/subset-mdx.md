---
title: サブセット (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b1f9a79c0e0ba6d578b82d7b1d072f3543888a1c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68036703"
---
# <a name="subset-mdx"></a>Subset (MDX)


  指定されたセットから組のサブセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Subset(Set_Expression, Start [ ,Count ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
 *Start*  
 返す最初の組の位置を指定する有効な数値式です。  
  
 *Count*  
 返す組の数を指定する有効な数値式です。  
  
## <a name="remarks"></a>Remarks  
 指定されたセットから**サブセット**関数は、指定された開始位置から始まる指定された数の組を含むサブセットを返します。 開始位置は、0から始まるインデックスに基づいています。つまり、ゼロ (0) は、指定されたセット内の最初の組に対応し、1は2番目の組に対応します。  
  
 *Count*が指定されていない場合、関数は、セットの*先頭*から末尾までのすべての組を返します。  
  
## <a name="example"></a>例  
 次の例では、階層とは無関係に、Reseller Gross Profit に基づいて、売上が上位 5 番目までの製品のサブカテゴリに対応する Reseller Sales メジャーを返しています。 **サブセット**関数は、結果が**Order**関数を使用して並べ替えられた後に、結果の最初の5つのセットのみを返すために使用されます。  
  
```  
SELECT Subset  
   (Order   
      ([Product].[Product Categories].[SubCategory].members  
         ,[Measures].[Reseller Gross Profit]  
         ,BDESC  
      )  
   ,0  
   ,5  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
