---
title: セット式の使用 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 622458f3ea3f8baf74b3aaa4aa9c46f94972f490
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038014"
---
# <a name="using-set-expressions"></a>セット式の使用


  セットは、0 個以上のタプルの順序付きリストで構成されます。 タプルを 1 つも含まないセットは、空のセットと呼ばれます。  
  
 一連の完全な式は、ゼロまたは複数の明示的に指定されたタプル、中かっこで囲まれています。  
  
 { [ { *Tuple_expression* | *Member_expression* } [ , { *Tuple_expression* | *Member_expression* } ] ... ] }  
  
 セット式で指定されたメンバー式は、1 つのメンバーのタプル式に変換されます。  
  
## <a name="example"></a>例  
 次の例は、クエリの列と行軸で使用される 2 つのセット式を示しています。  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]} ON COLUMNS,`  
  
 `{([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),`  
  
 `([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),`  
  
 `([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 列の軸のセットに  
  
 {[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}  
  
 2 つのメジャー ディメンションのメンバーで構成されます。 ROWS 軸のセットを次に示します。  
  
 {0} ([product] です。[製品カテゴリ] です。[Category]. [4] と [Date] です。[カレンダー] です。[Calendar Year] です & [2004])、。  
  
 ([Product] です。[製品カテゴリ] です。[Category]. [1] と [Date] です。[カレンダー] です。[Calendar Year] です [2003] &)、。  
  
 ([Product] です。[製品カテゴリ] です。[Category]. [3] と [Date] です。[カレンダー] です。[Calendar Year] です & [2004])}。  
  
 このセットは 3 つのタプルで構成されており、それぞれのタプルには、Product ディメンションの Product Categories 階層のメンバーと Date ディメンションの Calendar 階層のメンバーへの、2 つの明示的な参照が含まれています。  
  
 セットを返す関数の例については、次を参照してください。[メンバー、タプル、およびセットの操作&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)します。  
  
## <a name="see-also"></a>関連項目  
 [式&#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
