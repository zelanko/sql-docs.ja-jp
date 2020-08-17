---
description: Mtd (MDX)
title: Mtd (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 398503bc60be44a0a5fcbcc329f3c455df967d7c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341379"
---
# <a name="mtd-mdx"></a>Mtd (MDX)


  時間ディメンションの年 (Year) レベルという制約の中で、指定されたメンバーと同じレベルにある兄弟メンバーのセットを返します。先頭は最初の兄弟、末尾は指定されたメンバーになります。  
  
## <a name="syntax"></a>構文  
  
```  
  
Mtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 メンバー式が指定されていない場合、既定値は、メジャーグループ内の*Time*型の最初の次元の*月*のレベルを持つ最初の階層の現在のメンバーになります。  
  
 **Mtd**関数は、レベルの基になる属性階層の Type プロパティが*Months*に設定されている場合の、 [PeriodsToDate](../mdx/periodstodate-mdx.md)関数のショートカット関数です。 つまり、 `Mtd(Member_Expression)` はと同じです `PeriodsToDate(Month_Level_Expression,Member_Expression)` 。  
  
## <a name="example"></a>例  
 次の例では、2002年7月の20日目から7月までのインターネット販売について、その月の総運賃コストの合計を返します。  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX&#41;の合計 &#40;](../mdx/sum-mdx.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
