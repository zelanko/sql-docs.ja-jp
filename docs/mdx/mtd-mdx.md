---
title: Mtd (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e38d8d3485e50054ee4d1106b1ef7bdfc8ce96ea
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580764"
---
# <a name="mtd-mdx"></a>Mtd (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  時間ディメンションの年 (Year) レベルという制約の中で、指定されたメンバーと同じレベルにある兄弟メンバーのセットを返します。先頭は最初の兄弟、末尾は指定されたメンバーになります。  
  
## <a name="syntax"></a>構文  
  
```  
  
Mtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 既定値は型のレベルを持つ最初の階層の現在のメンバーではメンバー式が指定されていない場合*月*型の最初の次元の*時間*メジャー グループにします。  
  
 **Mtd**関数のショートカット関数では、 [PeriodsToDate](../mdx/periodstodate-mdx.md)レベルの基になる属性階層の Type プロパティ設定されている場合に機能*月*です。 つまり、`Mtd(Member_Expression)`は等価`PeriodsToDate(Month_Level_Expression,Member_Expression)`です。  
  
## <a name="example"></a>例  
 次の例では、July, 2002 年 7 月の 20 日からの Internet sales の運送料の日付を月の合計を返します。  
  
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
 [合計&#40;MDX&#41;](../mdx/sum-mdx.md)   
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
