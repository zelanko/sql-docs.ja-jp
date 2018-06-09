---
title: DrilldownLevelBottom (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d691efc1b8e1758f5dbacd43b2886eed75fa6dd6
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740781"
---
# <a name="drilldownlevelbottom-mdx"></a>DrilldownLevelBottom (MDX)


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
 任意。 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *Include_Calc_Members*  
 任意。 ドリルダウン結果に計算されるメンバーを追加するキーワードです。  
  
## <a name="remarks"></a>コメント  
 数値式が指定されている場合、 **DrilldownLevelBottom**関数、子メンバーのセットに対して評価された指定の値に基づいて、指定されたセット内の各メンバーの子の順序の昇順で並べ替えます。 数値式が指定されていない場合、指定されたセット内の各メンバーの子を、クエリ コンテキストから判別した子メンバーのセットが表すセルの値に基づいて、昇順で並べ替えます。この動作は、並べ替えを行わずに自然な順序でメンバーのセットを返す、BottomCount および Tail (MDX) 関数に似ています。  
  
 並べ替えの後に、 **DrilldownLevelBottom**関数には、親メンバーと指定された子メンバーの数を含むセットが返されます。*カウント*、最小値でします。  
  
 **DrilldownLevelBottom**関数がに似ていますが、 [DrilldownLevel](../mdx/drilldownlevel-mdx.md)関数が、指定されたレベルでは、各メンバーのすべての子ではなく、 **DrilldownLevelBottom**関数は、最下位の子メンバーの数を返します。  
  
 XMLA プロパティの mdpropmdxdrillfunctions にクエリを使用すると、サーバーがドリル関数以外が提供するサポートのレベルを確認するには参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)詳細についてはします。  
  
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
 [DrilldownLevel &#40;MDX&#41;](../mdx/drilldownlevel-mdx.md)   
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
