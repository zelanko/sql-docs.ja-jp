---
title: セット式の使用 |Microsoft ドキュメント
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
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744111"
---
# <a name="using-set-expressions"></a>セット式の使用


  セットは、0 個以上の組の順序付けされた一覧で構成されます。 組を 1 つも含まないセットは、空のセットと呼ばれます。  
  
 完全なセット式は、中かっこの中に 0 個以上の組を明示的に指定して表します。  
  
 {[{ *Tuple_expression* | *メンバー式*} [、{ *Tuple_expression* | *メンバー式*}]...]}  
  
 セット式の中で指定されたメンバー式は、1 つのメンバーのみの組式に変換されます。  
  
## <a name="example"></a>例  
 次の例では、クエリの COLUMNS 軸と ROWS 軸で使用される 2 つのセット式を示します。  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]} ON COLUMNS,`  
  
 `{([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),`  
  
 `([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),`  
  
 `([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 COLUMNS 軸のセットを次に示します。  
  
 {[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}  
  
 このセットは、Measures ディメンションの 2 つのメンバーで構成されています。 ROWS 軸のセットを次に示します。  
  
 {([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),  
  
 ([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),  
  
 ([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}  
  
 このセットは 3 つの組で構成されており、それぞれの組には、Product ディメンションの Product Categories 階層のメンバーと Date ディメンションの Calendar 階層のメンバーへの、2 つの明示的な参照が含まれています。  
  
 セットを返す関数の例については、次を参照してください。[メンバー、組、およびセット&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)です。  
  
## <a name="see-also"></a>参照  
 [式&#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
