---
title: Order (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ORDER
dev_langs:
- kbMDX
helpviewer_keywords:
- Order function
ms.assetid: 84acff52-2443-4424-a09e-694e6f14c109
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: f951c681b205ff9cfbc2b99c3935931811585186
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="order-mdx"></a>Order (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたセットのメンバーを整列します。必要に応じて、階層を保持するか、解除するかを指定できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
Numeric expression syntax  
Order(Set_Expression, Numeric_Expression   
[ , { ASC | DESC | BASC | BDESC } ] )  
  
String expression syntax  
Order(Set_Expression, String_Expression   
[ , { ASC | DESC | BASC | BDESC } ] )  
  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *String_Expression*  
 有効な文字列式です。通常は、文字列として表された数値を返すセル座標の有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **順序**関数は階層型にするか、(を使用して指定されたとおり、 **ASC**または**DESC**フラグ) または非階層型 (を使用して指定されたとおり、 **BASC**または**BDESC**フラグ;、 **B** 「break 階層」の略)。 場合**ASC**または**DESC**を指定すると、**順序**関数、階層内の位置に基づいてメンバーが整列され、各レベル。 場合**BASC**または**BDESC**を指定すると、**順序**階層を無視してセット内のメンバーが整列します。 フラグが指定しない、 **ASC**既定値です。  
  
 場合、**順序**関数は 2 つ以上の階層が、クロス結合はセットで使用され、 **DESC**フラグを使用すると、セット内の最後の階層のメンバーのみの順序。 この点が Analysis Services 2000 とは異なります。Analysis Services 2000 では、セットのすべての階層が並べ替えられます。  
  
## <a name="examples"></a>使用例  
 次の例を返しますから、 **Adventure Works**キューブの Date ディメンションの Calendar 階層からのすべての Calendar Quarters の再販業者の注文の数。**順序**関数は ROWS 軸のセットを並べ替えます。 **順序**関数が、セットを並べ替えます`[Reseller Order Count]`によって決定される階層の順序を降順で、`[Calendar]`階層。  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,DESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 通知方法については、この例でときに、 **DESC**フラグを変更**BDESC**階層が切断され、Calendar Quarters のリストが、階層に関係なく返されます。  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,BDESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 次の例では、階層とは無関係に、Reseller Gross Profit に基づいて、売上が上位 5 番目までの製品のサブカテゴリに対応する Reseller Sales メジャーを返しています。 **サブセット**関数を使用してを使用して結果を並べ替えてから、セットの最初の 5 つの組のみを返す、**順序**関数。  
  
 `SELECT Subset`  
  
 `(Order`  
  
 `([Product].[Product Categories].[SubCategory].members`  
  
 `,[Measures].[Reseller Gross Profit]`  
  
 `,BDESC`  
  
 `)`  
  
 `,0`  
  
 `,5`  
  
 `) ON 0`  
  
 `FROM [Adventure Works]`  
  
 次の例では、**ランク**City 階層のメンバーにランクの関数は Reseller Sales Amount メジャーに基づいており、ランクの順序で表示されます。 使用して、**順序**City 階層のメンバーのセットを関数の最初の注文を 1 回だけ行われ、その後で線形スキャン並べ替えた順で表示される前に並べ替えを行います。  
  
```  
WITH   
SET OrderedCities AS Order  
   ([Geography].[City].[City].members  
   , [Measures].[Reseller Sales Amount], BDESC  
   )  
MEMBER [Measures].[City Rank] AS Rank  
   ([Geography].[City].CurrentMember, OrderedCities)  
SELECT {[Measures].[City Rank],[Measures].[Reseller Sales Amount]}  ON 0   
,Order  
   ([Geography].[City].[City].MEMBERS  
   ,[City Rank], ASC)  
    ON 1  
FROM [Adventure Works]  
```  
  
 次の例では、製品の数を返しますを使用して、一意のセットで、**順序**関数を使用する前に空の組を順序付ける、**フィルター**関数。 **CurrentOrdinal**を比較し、関係を排除する関数を使用します。  
  
```  
WITH MEMBER [Measures].[PrdTies] AS Count  
   (Filter  
      (Order  
        (NonEmpty  
          ([Product].[Product].[Product].Members  
          , {[Measures].[Reseller Order Quantity]}  
          )  
       , [Measures].[Reseller Order Quantity]  
       , BDESC  
       ) AS OrdPrds  
    , (OrdPrds.CurrentOrdinal < OrdPrds.Count   
       AND [Measures].[Reseller Order Quantity] =   
          ( [Measures].[Reseller Order Quantity]  
            , OrdPrds.Item  
               (OrdPrds.CurrentOrdinal  
               )  
            )  
         )  
         OR (OrdPrds.CurrentOrdinal > 1   
            AND [Measures].[Reseller Order Quantity] =   
               ([Measures].[Reseller Order Quantity]  
               , OrdPrds.Item  
                  (OrdPrds.CurrentOrdinal-2)  
                )  
             )  
          )  
       )  
SELECT {[Measures].[PrdTies]} ON 0  
FROM [Adventure Works]  
```  
  
 理解する方法、 **DESC**フラグの組のセットが、最初に、次のクエリの結果を検討します。  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 ROWS 軸では、Sales Territory Groups が 北米、ヨーロッパ、太平洋、NA のように Tax Amount の降順に並べ替えられます。 ここでは、どうを参照してください。 お crossjoin Sales Territory Groups のセットを Product Subcategories のセットを適用し、**順序**次のように、同じ方法で機能。  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
*  
{[Product].[Product Categories].[subCategory].Members}  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 Product Subcategories のセットは階層順 (降順) に並べ替えられますが、Sales Territory Groups の並べ替えは行われず、ヨーロッパ、NA、北米、太平洋のように階層に表示された順になります。 これは、Product Subcategories の組のセットで最後の階層のみが並べ替えられているためです。 Analysis Services 2000 の動作の再現、一連を使用する入れ子になった**生成**関数など、クロス結合される前に各セットの並べ替えに。  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
GENERATE(  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
,  
ORDER(  
[Sales Territory].[Sales Territory].CURRENTMEMBER  
*  
{[Product].[Product Categories].[subCategory].Members}  
,[Measures].[Tax Amount], DESC))  
ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
