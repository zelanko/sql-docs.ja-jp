---
title: Wtd (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eee40829c72394bf95a1bc06540a434a1c74e166
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68125810"
---
# <a name="wtd-mdx"></a>Wtd (MDX)


  時間ディメンションの週 (Week) レベルという制約の中で、指定されたメンバーと同じレベルにある兄弟メンバーのセットを返します。先頭は最初の兄弟、末尾は指定されたメンバーになります。  
  
## <a name="syntax"></a>構文  
  
```  
  
Wtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>Remarks  
 メンバー式が指定されていない場合、既定値は、メジャーグループ内の型 (Time **. CurrentMember**) の最初の次元で、週型のレベルを持つ最初の階層の現在のメンバーになります。  
  
 **Wtd**関数は、レベルが*週*に設定されている[PeriodsToDate](../mdx/periodstodate-mdx.md)関数のショートカット関数です。 つまり、 `Wtd(Member_Expression)`はと同じです`PeriodsToDate(Week_Level_Expression,Member_Expression)`。  
  
## <a name="see-also"></a>参照  
 [Qtd &#40;MDX&#41;](../mdx/qtd-mdx.md)   
 [Mtd &#40;MDX&#41;](../mdx/mtd-mdx.md)   
 [Ytd &#40;MDX&#41;](../mdx/ytd-mdx.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
