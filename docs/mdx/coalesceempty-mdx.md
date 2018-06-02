---
title: CoalesceEmpty (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cbd5928e859436b90b986e9e0ea0d09e91ccd664
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577314"
---
# <a name="coalesceempty-mdx"></a>CoalesceEmpty (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  空のセル値を、指定された空でないセル値 (数値または文字列) に変換します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Numeric syntax  
CoalesceEmpty( Numeric_Expression1 [ ,Numeric_Expression2,...n] )  
  
String syntax  
CoalesceEmpty(String_Expression1 [ ,String_Expression2,...n] )  
```  
  
## <a name="arguments"></a>引数  
 *Numeric_Expression1*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *Numeric_Expression2*  
 有効な数値式です。通常は、指定された数値です。  
  
 *String_Expression1*  
 有効な文字列式です。通常は、文字列を返すセル座標の多次元式 (MDX) 式です。  
  
 *String_Expression2*  
 有効な文字列式です。通常は、1 番目の文字列式から返された NULL 値を置き換える、指定された文字列です。  
  
## <a name="remarks"></a>コメント  
 1 つ以上の数値式が指定されている場合、 **CoalesceEmpty**関数の最初の数値式 (左から右へ) から空でない値に解決される数値の値を返します。 指定されている数値式に、空でない値に解決される式がない場合、この関数は、空のセル値を返します。 通常、2 番目の数値式に対応する値が、1 番目の数値式から返された NULL 値を置き換える数値です。  
  
 1 つ以上の文字列式が指定されている場合、この関数は、左から右の順に見て、空でない値に解決される最初の文字列式の文字列値を返します。 指定されている文字列式に、空でない値に解決される式がない場合、この関数は、空のセル値を返します。 通常、2 番目の文字列式に対応する値が、1 番目の文字列式から返された NULL 値を置き換える文字列値です。  
  
 **CoalesceEmpty**関数は、同じ型の値のみを取得できます。 つまり、指定した値式は、すべて 1 つの数値データ型または空のセル値に評価されるか、すべて 1 つの文字列データ型または空のセル値に評価される必要があります。 この関数の 1 回の呼び出しで、数値式と文字列式を両方含めることはできません。  
  
 空のセルの詳細については、OLE DB のドキュメントを参照してください。  
  
## <a name="example"></a>例  
 次の例のクエリ、 **Adventure Works**キューブ。 この例では、各製品の注文数量とカテゴリ別の注文数量の割合を返します。 **CoalesceEmpty**関数により、計算されるメンバーをフォーマットするときに、null 値がゼロ (0) として表されることです。  
  
```  
WITH   
   MEMBER [Measures].[Order Percent by Category] AS  
   CoalesceEmpty(   
      ([Product].[Product Categories].CurrentMember,  
        Measures.[Order Quantity]) /   
          (  
           Ancestor  
           ( [Product].[Product Categories].CurrentMember,   
             [Product].[Product Categories].[Category]  
           ), Measures.[Order Quantity]  
       ), 0  
   ), FORMAT_STRING='Percent'  
SELECT   
   {Measures.[Order Quantity],  
      [Measures].[Order Percent by Category]} ON COLUMNS,  
{[Product].[Product].Members} ON ROWS  
FROM [Adventure Works]  
WHERE {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
