---
title: "DrilldownLevelTop (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: DRILLDOWNLEVELTOP
dev_langs: kbMDX
helpviewer_keywords: DrilldownLevelTop function
ms.assetid: b3b45dd6-2ade-4dd7-83dd-849231e2e517
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f4f3454f14371a7d75cf04f18ba69f11bce6d71f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="drilldownleveltop-mdx"></a>DrilldownLevelTop (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  セットの最上位メンバーを、指定されたレベルから 1 レベル下にドリル ダウンします。  
  
## <a name="syntax"></a>構文  
  
```  
  
DrilldownLevelTop(<Set_Expression>, <Count> [,[<Level_Expression>] [,[<Numeric_Expression>][,INCLUDE_CALC_MEMBERS]]])  
  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *カウント*  
 返す組の数を指定する有効な数値式です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *Include_Calc_Members*  
 ドリルダウン結果に計算されるメンバーを追加するためのキーワードです。  
  
## <a name="remarks"></a>解説  
 数値式が指定されている場合、 **DrilldownLevelTop**関数、子メンバーのセットに対して評価された数値式の値に基づいて指定されたセット内の各メンバーの子の順序を降順で並べ替えます。 数値式が指定されていない場合、指定されたセット内の各メンバーの子を、クエリ コンテキストから判別した子メンバーのセットが表すセルの値に基づいて、降順で並べ替えます。  
  
 並べ替えの後に、 **DrilldownLevelTop**関数には、親メンバーと指定された子メンバーの数を含むセットが返されます。*カウント、*値が最も高いです。  
  
 **DrilldownLevelTop**関数がに似ていますが、 [DrilldownLevel](../mdx/drilldownlevel-mdx.md)関数が、指定されたレベルでは、各メンバーのすべての子ではなく、 **DrilldownLevelTop**関数は、子メンバーの最上位の数を返します。  
  
 XMLA プロパティの mdpropmdxdrillfunctions にクエリを使用すると、サーバーがドリル関数以外が提供するサポートのレベルを確認するには参照してください[サポートされる XMLA プロパティ &#40;です。XMLA &#41;](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)詳細についてはします。  
  
## <a name="examples"></a>使用例  
 次の例では、既定のメジャーに基づいて Product Category レベルの子を最上位のものから 3 つ返します。 Adventure Works サンプル キューブでは、Accessories の最上位の 3 つの子は、Bike Racks、Bike Stands、Bottles and Cages です。 Management Studio の MDX クエリ ウィンドウで、[Products]、[Product Categories]、[Members]、[All Products]、[Accessories] にナビゲートして完全なリストを参照できます。 Count 引数を大きくして、返されるメンバーを増やすことができます。  
  
```  
SELECT DrilldownLevelTop   
   ([Product].[Product Categories].children,  
   3,  
   [Product].[Product Categories].[Category])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 次の例を使用して、 **include_calc_members**フラグをドリル ダウン レベルで計算されるメンバーを含めるために使用します。 メジャー [Reseller Order Count] に含まれる、 **DrilldownLevelTop**戻り値がそのメジャーで並べ替えられていることを確認するステートメント。  
  
```  
WITH MEMBER   
[Product].[Product Categories].[Category].&[3].[Premium Clothes] AS  
[Product].[Product Categories].[Subcategory].&[18] +  
[Product].[Product Categories].[Subcategory].&[21]  
SELECT [Measures].[Reseller Order Count] ON 0,  
DRILLDOWNLEVELTOP(  
  [Product].[Product Categories].children ,  
  2,  
  [Product].[Product Categories].[Category] ,  
  [Measures].[Reseller Order Count],  
  INCLUDE_CALC_MEMBERS ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [DrilldownLevel &#40;です。MDX と #41 です。](../mdx/drilldownlevel-mdx.md)   
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
