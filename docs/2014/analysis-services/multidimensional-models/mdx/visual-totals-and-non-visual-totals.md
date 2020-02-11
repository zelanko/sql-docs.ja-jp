---
title: ビジュアルの合計と非表示の合計 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ea9d02f2-a668-4547-ade5-e3d077a2e1bd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f110b54d1a8a057f16b5e5682adc3beb04c54f6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66073727"
---
# <a name="visual-totals-and-non-visual-totals"></a>表示部分の合計と非表示部分の合計
  表示部分の合計とは、列または行の最後に表示される合計で、列または行内に表示されるすべてのアイテムを加算したものです。 これは、ほとんどのテーブルが表示されるときの既定の動作です。 ただし、非表示の行を含む行全体の合計を維持しながら、テーブル内の特定の列のみを表示する場合もあります。 これらは、合計が表示部分と非表示部分の両方の値から取得されることから `Non Visual Totals` と呼ばれます。  
  
 次のシナリオは、非表示部分の合計の動作を示します。 最初のステップで表示部分の合計の既定の動作を示します。  
  
 次の例では、製品カテゴリが列、再販業者の業種が行であるテーブルから [Reseller Sales Amount] の数値を取得するための [Adventure Works] のクエリを示します。 次の SELECT ステートメントが発行されると、製品と再販業者の両方について合計が示されることに注意してください。  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 結果は、次のようになります。  
  
|||||||  
|-|-|-|-|-|-|  
||**すべての製品**|**Accessories**|**Bikes**|**Clothing**|**Components**|  
|**すべてのリセラー**|**$80450596.98**|**$571297.93**|**$66302381.56**|**$1777840.84**|**$11799076.66**|  
|**特別自転車ショップ**|**$6756166.18**|**$65125.48**|**$6080117.73**|**$252933.91**|**$357989.07**|  
|**付加価値再販業者**|**$34,967,517.33**|**$175002.81**|**$30892354.33**|**$592,385.71**|**$3307774.48**|  
|**ウェア**|**$38726913.48**|**$331169.64**|**$29329909.50**|**$932521.23**|**$8133313.11**|  
  
## <a name="non-visual-on-rows-and-columns"></a>行および列の非表示部分  
 Accessories 製品と Clothing 製品、および Value Added Reseller 再販業者と Warehouse 再販業者のみのデータを含むテーブルを生成する場合、全体的な合計も維持するには、NON VISUAL を使用して次のように記述できます。  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 結果は、次のようになります。  
  
|||||  
|-|-|-|-|  
||**すべての製品**|**Accessories**|**Clothing**|  
|**すべてのリセラー**|**$80450596.98**|**$571297.93**|**$1777840.84**|  
|**付加価値再販業者**|**$34,967,517.33**|**$175002.81**|**$592,385.71**|  
|**ウェア**|**$38726913.48**|**$331169.64**|**$932521.23**|  
  
## <a name="non-visual-on-rows"></a>行の非表示部分  
 列の表示部分の合計を算出するが、行の合計についてはすべての [Category] の実際の合計を示すテーブルを生成するには、次のクエリを実行します。  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0`  
  
 `from ( Select {[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 0`  
  
 `from [Adventure Works])`  
  
 `)`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 NON VISUAL が [Category] のみに適用されていることに注目してください。  
  
 上記のクエリの結果は、次のようになります。  
  
|||||  
|-|-|-|-|  
||All Products|Accessories|Clothing|  
|All Resellers|$73,694,430.80|$506,172.45|$1,524,906.93|  
|Value Added Reseller|$34,967,517.33|$175,002.81|$592,385.71|  
|Warehouse|$38,726,913.48|$331,169.64|$932,521.23|  
  
 前の結果と比較すると、[All Resellers] 行は [Value Added Reseller] と [Warehouse] の表示値の合計を示していますが、[All Products] 列は表示されていない製品も含むすべての製品の合計額を示していることがわかります。  
  
## <a name="see-also"></a>参照  
 [MDX &#40;Analysis Services の主な概念&#41;](../key-concepts-in-mdx-analysis-services.md)   
 [Autoexists](autoexists.md)   
 [MDX&#41;&#40;メンバー、組、およびセットの操作](working-with-members-tuples-and-sets-mdx.md)   
 [MDX クエリの基礎 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)   
 [MDX の基本的なクエリ &#40;MDX&#41;](mdx-query-the-basic-query.md)   
 [MDX&#41;&#40;クエリ軸とスライサー軸を使用したクエリの制限](mdx-query-and-slicer-axes-restricting-the-query.md)   
 [MDX&#41;&#40;クエリでのキューブコンテキストの確立](establishing-cube-context-in-a-query-mdx.md)  
  
  
