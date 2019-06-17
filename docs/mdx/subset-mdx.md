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
manager: kfile
ms.openlocfilehash: 07d813587dc530924becbb187a970f78022e5476
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63136090"
---
# <a name="subset-mdx"></a>Subset (MDX)


  指定したセットから組のサブセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Subset(Set_Expression, Start [ ,Count ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *[開始]*  
 返す最初の組の位置を指定する有効な数値式です。  
  
 *Count*  
 返す組の数を指定する有効な数値式です。  
  
## <a name="remarks"></a>コメント  
 指定したセットから、**サブセット**関数は、指定数の組を指定した開始位置を格納しているサブセットを返します。 開始位置は、0 から始まるインデックスをに基づいてください。つまり、ゼロ (0) が指定されたセット内の最初の組に対応して、1、2 番目に対応しています。  
  
 場合*カウント*が指定されていない、関数からのすべての組を返します*開始*セットの末尾にします。  
  
## <a name="example"></a>例  
 次の例では、階層とは無関係に、Reseller Gross Profit に基づいて、売上が上位 5 番目までの製品のサブカテゴリに対応する Reseller Sales メジャーを返しています。 **サブセット**関数を使用してを使用して結果を並べ替えてから、結果の最初の 5 つのセットのみを返す、**順序**関数。  
  
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
  
  
