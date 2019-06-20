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
manager: kfile
ms.openlocfilehash: 012a2946ff931e1326dcd3fa6321472761d67c56
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62861706"
---
# <a name="using-set-expressions"></a>セット式の使用


  セットは、0 個以上の組の順序付きリストで構成されます。 組を 1 つも含まないセットは、空のセットと呼ばれます。  
  
 一連の完全な式は、ゼロまたは複数の明示的に指定された組、中かっこで囲まれています。  
  
 { [ { *Tuple_expression* | *Member_expression* } [ , { *Tuple_expression* | *Member_expression* } ] ... ] }  
  
 セット式で指定されたメンバー式は、1 つのメンバーの組式に変換されます。  
  
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
  
 このセットは 3 つの組で構成されており、それぞれの組には、Product ディメンションの Product Categories 階層のメンバーと Date ディメンションの Calendar 階層のメンバーへの、2 つの明示的な参照が含まれています。  
  
 セットを返す関数の例については、次を参照してください。[メンバー、組、およびセットの操作&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)します。  
  
## <a name="see-also"></a>参照  
 [式&#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
