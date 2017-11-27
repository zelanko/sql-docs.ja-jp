---
title: "DrilldownMemberTop (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DRILLDOWNMEMBERTOP
dev_langs:
- kbMDX
helpviewer_keywords:
- DrilldownMemberTop function
ms.assetid: b6575544-1fd3-4fa1-aa2e-272d307c7750
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: da7f8a1c315d9ff3eb60c69e88726b521a59d17d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="drilldownmembertop-mdx"></a>DrilldownMemberTop (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  2 番目に指定されたセット内に存在する、指定されたセットのメンバーをドリル ダウンします。結果セットは、指定された数のメンバーに限定されます。 または、最初の組階層または必要に応じて指定した階層を使用して、この関数が組のセットをドリル ダウンします。  
  
## <a name="syntax"></a>構文  
  
```  
  
DrillDownMemberTop(<Set_Expression1>, <Set_Expression2>, <Count> [,[<Numeric_Expression>] [,[<Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]]])  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression1*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Set_Expression2*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Count*  
 返す組の数を指定する有効な数値式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *階層*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
 *再帰*  
 セットの再帰的な比較を示すキーワードです。  
  
 *Include_Calc_Members*  
 計算されるメンバーがドリルダウン結果に含まれるようにするキーワードです。  
  
## <a name="remarks"></a>解説  
 数値式が指定されている場合、 **DrilldownMemberTop**関数、子メンバーのセットに対して評価された数値式の値に基づいて最初のセット内の各メンバーの子の順序を降順で並べ替えます。 クエリ コンテキストから判別した子メンバーのセットで、セルの値に基づいて最初のセット内の各メンバーの子の順序を降順で並べ替えますが表される数値式が指定されていない場合。 この動作は、並べ替えを行わずに自然な順序でメンバーのセットを返す、TopCount および Head (MDX) 関数に似ています。  
  
 並べ替えの後に、 **DrilldownMemberTop**関数には、親メンバーと指定された子メンバーの数を含むセットが返されます。*カウント、*最高値とは、両方のセットに含まれています。  
  
 場合**再帰**が指定されて、関数は、前述のように最初のセットを並べ替え、再帰的には 2 番目のセットに対して、階層に編成されている最初のセットのメンバーを比較*です。* 関数では、各メンバーの子も、2 番目のセットに存在する 1 番目のセット内の最上位の数を取得します。  
  
 1 番目のセットには、メンバーではなく組を含めることもできます。 組のドリル ダウンは、OLE DB の拡張機能であり、メンバーではなく組のセットを返します。  
  
 **DrilldownMemberTop**関数がに似ていますが、 [DrilldownMember](../mdx/drilldownmember-mdx.md)関数が 2 番目のセットに存在するも、最初のセット内の各メンバーのすべての子ではなく、 **DrilldownMemberTop**関数は、各メンバーの子メンバーの最上位の数を返します。  
  
 XMLA プロパティの mdpropmdxdrillfunctions にクエリを使用すると、サーバーがドリル関数以外が提供するサポートのレベルを確認するには参照してください[サポートされる XMLA プロパティ & #40 です。XMLA &#41;](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)詳細についてはします。  
  
## <a name="example"></a>例  
 次の例では、衣料のカテゴリをドリル ダウンして、出荷する数量が最も多い注文で衣料の 3 つのサブカテゴリを返します。  
  
```  
SELECT DrilldownMemberTop   ({[Product].[Product Categories].[All Products],        
[Product].[Product Categories].[Category].Bikes,        
[Product].[Product Categories].[Category].Clothing},     
{[Product].[Product Categories].[Category].Clothing},     
3,     
[Measures].[Reseller Order Quantity])     
ON 0     
FROM [Adventure Works]     
WHERE [Measures].[Reseller Order Quantity]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

