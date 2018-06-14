---
title: TopPercent (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d7de38f27d23fe11d0953553a8737a9e2f4e2db3
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743651"
---
# <a name="toppercent-mdx"></a>TopPercent (MDX)


  セットを降順で並べ替え、累積合計が指定された割合以上になるように、値の大きい方から組のセットを作成して返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
TopPercent(Set_Expression, Percentage, Numeric_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *割合*  
 返す組の割合を指定する有効な数値式です。  
  
> [!IMPORTANT]  
>  *割合*は正の値を指定する必要がある負の値がエラーを生成します。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **TopPercent**関数セットを降順で並べ替え、指定されたセットに対して評価される指定数値式の合計を計算します。 次に、合計値の累積割合が指定されている割合以上になるように、最も値の大きい方から要素を返します。 この関数は、累積合計が指定された割合以上になるセットの最小サブセットを返します。 要素は大きい方から順に返されます。  
  
> [!WARNING]  
>  場合*Numeric_Expression*し、負の値を返します**TopPercent**のみ 1 つ (1) の行を返します。  
>   
>  この動作の詳細な説明については、2 番目の例を参照してください。  
  
> [!IMPORTANT]  
>  同様に、 [BottomPercent](../mdx/bottompercent-mdx.md) 、関数、 **TopPercent**関数が常に階層を解除します。  
  
## <a name="example"></a>例  
 次の例は、Bike カテゴリで、再販業者の売上の上位 10% に最も貢献している都市を返します。 結果は、降順で並べ替えられ、売上が最高値である都市が先頭になります。  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopPercent  
   ({[Geography].[Geography].[City].Members}  
   , 10  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].[Bikes])  
```  
  
 上記の式には、次の結果が生成されます。  
  
||Reseller Sales Amount|  
|-|---------------------------|  
|Toronto|$3,508,904.84|  
|London|$1,521,530.09|  
|Seattle|$1,209,418.16|  
|Paris|$1,170,425.18|  
  
 元のデータのセットは、次のクエリで取得でき、588 行が返されます。  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
Order  
   ({[Geography].[Geography].[City].Members}  
   , [Measures].[Reseller Sales Amount]  
   , BDESC  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].[Bikes])  
  
```  
  
## <a name="example"></a>例  
 次のチュートリアルで負の値の影響を理解できますが、 *Numeric_Expression*です。 まず、この動作を実行できる、いくつかのコンテキストを構築します。  
  
 次のクエリは、Reseller の 'Sales Amount'、'Total Product Cost'、および 'Gross Profit' のテーブルを、利益で降順に並べ替えて返します。 利益には負の値しかないので、損失の少ないものが上位に表示されます。  
  
```  
SELECT { [Measures].[Reseller Sales Amount], [Measures].[Reseller Total Product Cost], [Measures].[Reseller Gross Profit] } ON columns  
     ,  ORDER( [Product].[Product Categories].[Bikes].[Touring Bikes].children, [Measures].[Reseller Gross Profit], BDESC )   ON rows  
FROM [Adventure Works]  
  
```  
  
 上記のクエリは、次の結果を返します。見やすくするために、中間部の行は削除してあります。  
  
||Reseller Sales Amount|Reseller Total Product Cost|Reseller Gross Profit|  
|-|---------------------------|---------------------------------|---------------------------|  
|Touring-2000 Blue, 50|$157,444.56|$163,112.57|($5,668.01)|  
|Touring 2000 青、46|$321,027.03|$333,021.50|($11,994.47)|  
|Touring-3000 Blue, 62|$87,773.61|$100,133.52|($12,359.91)|  
|…|…|…|…|  
|Touring 1000 の黄色の場合、46|$1,016,312.83|$1,234,454.27|($218,141.44)|  
|Touring-1000 Yellow, 60|$1,184,363.30|$1,443,407.51|($259,044.21)|  
  
 このとき、利益で上位 100% の自転車を提示するように求められた場合、クエリは次のように記述されます。  
  
```  
SELECT { [Measures].[Reseller Sales Amount], [Measures].[Reseller Total Product Cost], [Measures].[Reseller Gross Profit] } ON columns  
     ,  TOPPERCENT( [Product].[Product Categories].[Bikes].[Touring Bikes].children, 100,[Measures].[Reseller Gross Profit] )   ON rows  
FROM [Adventure Works]  
  
```  
  
 クエリで 100% が要求されていることに注意してください。つまり、すべての行が返される必要があります。 ただしで負の値があるため、 *Numeric_Expression* 、1 行のみが返されます。  
  
||Reseller Sales Amount|Reseller Total Product Cost|Reseller Gross Profit|  
|-|---------------------------|---------------------------------|---------------------------|  
|Touring-2000 Blue, 50|$157,444.56|$163,112.57|($5,668.01)|  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
