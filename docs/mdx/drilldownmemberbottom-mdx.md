---
title: DrilldownMemberBottom (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 854f880cf9cb4f06ee4fc44fd18cec5f0ab99ca8
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145117"
---
# <a name="drilldownmemberbottom-mdx"></a>DrilldownMemberBottom (MDX)


  2 番目に指定されたセット内に存在する、指定されたセットのメンバーをドリル ダウンします。結果セットは、指定された数のメンバーに限定されます。 または、最初の組階層または必要に応じて指定した階層を使用して、この関数が組のセットもドリル ダウンします。  
  
## <a name="syntax"></a>構文  
  
```  
  
DrillDownMemberBottom(<Set_Expression1>, <Set_Expression2>, <Count> [,[<Numeric_Expresion>] [,[<Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]]])  
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
  
 *Hierarchy*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
 *再帰*  
 セットの再帰的な比較を示すキーワードです。  
  
 *Include_Calc_Members*  
 計算されるメンバーがドリルダウン結果に含まれるようにするキーワード。  
  
## <a name="remarks"></a>コメント  
 数値式が指定されている場合、 **DrilldownMemberBottom**関数、子のセットに対して評価された数値式の値に基づいて、最初のセット内の各メンバーの子の順序の昇順で並べ替えますメンバー。 数値式が指定されていない場合、1 番目のセット内の各メンバーの子を、クエリ コンテキストから判別した子メンバーのセットが表すセルの値に基づいて、昇順で並べ替えます。 この動作は、並べ替えを行わずに自然な順序でメンバーのセットを返す、BottomCount および Tail (MDX) 関数に似ています。  
  
 並べ替えの後、 **DrilldownMemberBottom**関数が、親メンバーと指定された子メンバーの数を含むセットを返します*数、* 両方に含まれる最小値とは設定します。  
  
 場合**再帰**が指定されて、関数は、前述のように最初のセットを並べ替え、再帰的に 2 番目のセットに対して、階層に編成されている最初のセットのメンバーを比較します。 この関数は、最初のセットのメンバーのうち、2 番目のセット内にも存在する各メンバーの子を、最小のものから指定されている数だけ取得します。  
  
 1 番目のセットには、メンバーではなく組を含めることもできます。 組のドリル ダウンは、OLE DB の拡張機能であり、メンバーではなく組のセットを返します。  
  
 **DrilldownMemberBottom**機能に似ています、 [DrilldownMember](../mdx/drilldownmember-mdx.md)も最初のセット内の各メンバーのすべての子ではなく、 、2番目のセット内に存在しますが、機能**DrilldownMemberBottom**関数は、最下位の子メンバーの各メンバーの数を返します。  
  
 XMLA プロパティの MdpropMdxDrillFunctions にクエリを実行、サーバーがドリル関数; が提供するサポートのレベルを確認することができます。参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)詳細についてはします。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
