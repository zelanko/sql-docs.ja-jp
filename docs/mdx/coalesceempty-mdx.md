---
title: CoalesceEmpty (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- COALESCEEMPTY
dev_langs:
- kbMDX
helpviewer_keywords:
- CoalesceEmpty function
ms.assetid: c00dd739-44bc-4af6-9871-c7e1e3f3e5ba
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 14a972a7f79039e46ded92f62c748c6cd9577a6e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>解説  
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
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
