---
title: DrilldownLevelTop (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8d6532998f65625bf3dacd11de2949a3478ba6ea
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2018
ms.locfileid: "50146217"
---
# <a name="drilldownleveltop-mdx"></a>DrilldownLevelTop (MDX)


  セットの最上位メンバーを、指定されたレベルから 1 レベル下にドリル ダウンします。  
  
## <a name="syntax"></a>構文  
  
```  
  
DrilldownLevelTop(<Set_Expression>, <Count> [,[<Level_Expression>] [,[<Numeric_Expression>][,INCLUDE_CALC_MEMBERS]]])  
  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Count*  
 返す組の数を指定する有効な数値式です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *Include_Calc_Members*  
 ドリルダウン結果に計算されるメンバーを追加するためのキーワードです。  
  
## <a name="remarks"></a>コメント  
 数値式が指定されている場合、 **DrilldownLevelTop**関数、子のセットに対して評価された数値式の値に基づいて指定されたセット内の各メンバーの子の順序を降順で並べ替えますメンバー。 数値式が指定されていない場合、指定されたセット内の各メンバーの子を、クエリ コンテキストから判別した子メンバーのセットが表すセルの値に基づいて、降順で並べ替えます。  
  
 並べ替えの後、 **DrilldownLevelTop**関数が、親メンバーと指定された子メンバーの数を含むセットを返します*数、* 最高値を使用します。  
  
 **DrilldownLevelTop**機能に似ています、 [DrilldownLevel](../mdx/drilldownlevel-mdx.md)関数が、指定されたレベルでは、各メンバーのすべての子ではなく、 **DrilldownLevelTop**関数は、子メンバーの最上位の数を返します。  
  
 XMLA プロパティの MdpropMdxDrillFunctions にクエリを実行、サーバーがドリル関数; が提供するサポートのレベルを確認することができます。参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)詳細についてはします。  
  
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
  
 次の例を使用して、 **include_calc_members**フラグをドリル ダウン レベルで計算されるメンバーを含めるために使用します。 含まれているメジャー [Reseller Order Count]、 **DrilldownLevelTop**戻り値がそのメジャーで並べ替えられていることを確認するステートメント。  
  
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
 [DrilldownLevel &#40;MDX&#41;](../mdx/drilldownlevel-mdx.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
