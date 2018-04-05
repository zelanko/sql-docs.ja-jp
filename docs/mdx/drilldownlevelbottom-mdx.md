---
title: DrilldownLevelBottom (MDX) |Microsoft ドキュメント
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
- DRILLDOWNLEVELBOTTOM
dev_langs:
- kbMDX
helpviewer_keywords:
- DrilldownLevelBottom function
ms.assetid: c00a6a02-e618-4713-805a-870e042f2d51
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 0811bbd1e0f3cf81ebe87ff200906e2489036092
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="drilldownlevelbottom-mdx"></a>DrilldownLevelBottom (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  セットの最下位メンバーを、指定されたレベルから 1 レベル下にドリル ダウンします。  
  
## <a name="syntax"></a>構文  
  
```  
DrilldownLevelBottom(Set_Expression, Count [,[<Level_Expression>] [,[<Numeric_Expression>][,INCLUDE_CALC_MEMBERS]]])  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *カウント*  
 返す組の数を指定する有効な数値式です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
 *Numeric_Expression*  
 省略可。 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *Include_Calc_Members*  
 省略可。 ドリルダウン結果に計算されるメンバーを追加するキーワードです。  
  
## <a name="remarks"></a>解説  
 数値式が指定されている場合、 **DrilldownLevelBottom**関数、子メンバーのセットに対して評価された指定の値に基づいて、指定されたセット内の各メンバーの子の順序の昇順で並べ替えます。 数値式が指定されていない場合、指定されたセット内の各メンバーの子を、クエリ コンテキストから判別した子メンバーのセットが表すセルの値に基づいて、昇順で並べ替えます。この動作は、並べ替えを行わずに自然な順序でメンバーのセットを返す、BottomCount および Tail (MDX) 関数に似ています。  
  
 並べ替えの後に、 **DrilldownLevelBottom**関数には、親メンバーと指定された子メンバーの数を含むセットが返されます。*カウント*、最小値でします。  
  
 **DrilldownLevelBottom**関数がに似ていますが、 [DrilldownLevel](../mdx/drilldownlevel-mdx.md)関数が、指定されたレベルでは、各メンバーのすべての子ではなく、 **DrilldownLevelBottom**関数は、最下位の子メンバーの数を返します。  
  
 XMLA プロパティの mdpropmdxdrillfunctions にクエリを使用すると、サーバーがドリル関数以外が提供するサポートのレベルを確認するには参照してください[サポートされる XMLA プロパティ &#40;です。XMLA &#41;](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)詳細についてはします。  
  
## <a name="examples"></a>使用例  
 次の例では、既定のメジャーに基づいて Product Category レベルの子を最小のものから 3 つ返します。 Adventure Works サンプル キューブでは、Accessories の最下位の 3 つの子は、Tires and Tubes、Pumps、Panniers です。 Management Studio の MDX クエリ ウィンドウで、[Products]、[Product Categories]、[Members]、[All Products]、[Accessories] にナビゲートして完全なリストを参照できます。 Count 引数を大きくして、返されるメンバーを増やすことができます。  
  
```  
SELECT DrilldownLevelBottom   
   ([Product].[Product Categories].children,  
   3,  
   [Product].[Product Categories].[Category])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 次の例を使用して、 **include_calc_members**フラグをドリル ダウン レベルで計算されるメンバーを含めるために使用します。 [Reseller Order Count] メジャーを追加、 **DrilldownLevelBottom**ステートメントをそのメジャーによって結果が並べ替えられていることを確認します。 計算されるメンバーを表示するには、Count を 9 以上にする必要があります。  
  
```  
WITH MEMBER   
[Product].[Product Categories].[Category].&[3].[Premium Clothes] AS  
[Product].[Product Categories].[Subcategory].&[18] +  
[Product].[Product Categories].[Subcategory].&[21]  
SELECT [Measures].[Reseller Order Count] ON 0,  
DRILLDOWNLEVELBOTTOM(  
  [Product].[Product Categories].children ,  
  9,  
  [Product].[Product Categories].[Category] ,  
  [Measures].[Reseller Order Count],  
  INCLUDE_CALC_MEMBERS ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [DrilldownLevel &#40;です。MDX と #41 です。](../mdx/drilldownlevel-mdx.md)   
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
