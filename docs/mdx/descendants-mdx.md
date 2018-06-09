---
title: 子孫 (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 013b7a7a2124788f3f1bcaa6d09b8ef7b10562e4
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740751"
---
# <a name="descendants-mdx"></a>Descendants (MDX)


  メンバーの子孫のうち、指定されたレベルまたは距離にある子孫のセットを返します。他のレベルの子孫を含めたり除外したりすることも可能です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member expression syntax using a level expression  
Descendants(Member_Expression [ , Level_Expression [ ,Desc_Flag ] ] )  
  
Member expression syntax using a numeric expression  
Descendants(Member_Expression [ , Distance [ ,Desc_Flag ] ] )  
  
Set expression syntax using a level expression  
Descendants(Set_Expression [ , Level_Expression [ ,Desc_Flag ] ] )  
  
Member expression syntax using a numeric expression  
Descendants(Set_Expression [ , Distance [ ,Desc_Flag ] ] )  
  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
 *距離*  
 指定されたメンバーからの距離を指定する有効な数値式です。  
  
 *Desc_Flag*  
 子孫のセットを区別するための説明フラグを指定する有効な文字列式です。  
  
## <a name="remarks"></a>コメント  
 レベルが指定されている場合、**子孫**関数を指定されたメンバーまたはで指定されたフラグによって調整必要に応じて、指定したレベルにおいて、指定されたセットのメンバーの子孫を含むセットを返します*Desc_Flag*です。  
  
 場合*距離*を指定すると、**子孫**関数を指定されたメンバーまたは指定された数のレベルで指定されたフラグによって調整必要に応じて、指定されたメンバーの階層では、指定されたセットのメンバーの子孫を含むセットを返します*Desc_Flag*です。 この関数は、不規則階層を対象とする場合に Distance 引数と共に使用されるのが一般的です。 距離に 0 が指定された場合は、指定されたメンバーのみで構成されるセットまたは指定されたセットを返します。  
  
 セット式が指定されている場合、**子孫**関数は、セットのメンバーごとに個別に解決されると、セットを再作成します。 つまり、使用する構文、**子孫**関数は、機能的には、MDX[生成](../mdx/generate-mdx.md)関数。  
  
 関数が使用するレベルの既定値を呼び出すことによって決まりますレベルまたは距離が指定されていない場合、[レベル](../mdx/level-mdx.md)関数 (<\<メンバー >> です。レベル) (メンバーが指定されている場合、指定されたメンバーのまたは呼び出すことによって、**レベル**(セットが指定した) 場合に、指定されたセットの各メンバーに対して機能します。 レベル式、距離、フラグがいずれも指定されていない場合は、次の構文の動作になります。  
  
 `Descendants`  
  
 `(`  
  
 `Member_Expression ,`  
  
 `Member_Expression.Level ,`  
  
 `SELF_BEFORE_AFTER`  
  
 `)`  
  
 レベルが指定されており、説明フラグが指定されていない場合は、次の構文の動作になります。  
  
 `Descendants`  
  
 `(`  
  
 `Member_Expression ,`  
  
 `Level_Expression,`  
  
 `SELF`  
  
 `)`  
  
 説明フラグの値を変更することで、指定したレベルまたは距離にある子孫、指定したレベルまたは距離の前後の子 (リーフ ノードまで)、あるいは指定したレベルまたは距離に関係なくリーフ メンバーすべてについて、含めるか除外するかを制御できます。 次の表に指定できるフラグ、 *Desc_Flag*引数。  
  
|フラグ|説明|  
|----------|-----------------|  
|SELF|指定されたレベルまたは指定された距離にある子孫メンバーのみを返します。 指定されたレベルが、指定されたメンバーのレベルである場合は、指定されたメンバーを含めます。|  
|AFTER|指定されたレベルまたは距離のすべての下位レベルにある子孫メンバーを返します。|  
|BEFORE|指定されたメンバーと指定されたレベルの間、または指定された距離のすべてのレベルにある子孫メンバーを返します。 指定されたメンバーは含めますが、指定されたレベルまたは距離にあるメンバーは含めません。|  
|BEFORE_AND_AFTER|指定されたメンバーのレベルのすべての下位レベルにある子孫メンバーを返します。 指定されたメンバーは含めますが、指定されたレベルまたは指定された距離にあるメンバーは含めません。|  
|SELF_AND_AFTER|指定されたレベルまたは指定された距離にある子孫メンバーと、指定されたレベルまたは指定された距離のすべての下位レベルにある子孫メンバーを返します。|  
|SELF_AND_BEFORE|指定されたレベルまたは指定された距離にある子孫メンバーと、指定されたメンバーと指定されたレベルの間または指定された距離にあるすべてのレベルの子孫メンバーを返します (指定されたメンバーを含みます)。|  
|SELF_BEFORE_AFTER|指定されたメンバーのレベルのすべての下位レベルにある子孫メンバーを返します (指定メンバーを含みます)。|  
|LEAVES|指定されたメンバーと指定されたレベルの間、または指定された距離にある、リーフ子孫メンバーを返します。|  
  
## <a name="examples"></a>使用例  
 次の例では、指定されたメンバー (United States)、および指定されたメンバー (United States) と指定されたレベル (City) の前のレベルのメンバー間にあるメンバーを返しています。この例では、指定されたメンバー自体 (United States)、および State-Province レベル (City レベルの前のレベル) のメンバーが返されます。 この例には、この関数の他の引数を容易にテストできるように、コメント アウトした引数も含まれています。  
  
```  
SELECT Descendants  
   ([Geography].[Geography].[Country].&[United States]  
      //, [Geography].[Geography].[Country]  
   , [Geography].[Geography].[City]  
      //, [Geography].[Geography].Levels (3)  
      //, SELF   
      //, AFTER  
      , BEFORE  
      // BEFORE_AND_AFTER  
      //, SELF_AND_AFTER  
      //, SELF_AND_BEFORE  
      //,SELF_BEFORE_AFTER  
      //,LEAVES   
   ) ON 0  
FROM [Adventure Works]   
```  
  
 次の例は、の日次平均を返します、`Measures.[Gross Profit Margin]`から、2003年会計年度の各月の日間にわたって計算、メジャー、 **Adventure Works**キューブ。 **子孫**関数の現在のメンバーから判別される日のセットを返します、`[Date].[Fiscal]`階層。  
  
```  
WITH MEMBER Measures.[Avg Gross Profit Margin] AS Avg  
   (  
      Descendants( [Date].[Fiscal].CurrentMember,   
           [Date].[Fiscal].[Date]  
          ),   
        Measures.[Gross Profit Margin]  
   )  
SELECT  
   Measures.[Avg Gross Profit Margin] ON COLUMNS,  
   [Date].[Fiscal].[Month].Members ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Fiscal Year].&[2003])  
```  
  
 次の例では、レベル式を使用して、Australia の State-Province ごとに Internet Sales Amount を返し、State-Province ごとに Australia の Internet Sales Amount の合計に対する割合を返しています。 この例では、Item 関数を使用して、によって返されるセットから最初の (そして唯一の) 組を抽出、**先祖**関数。  
  
```  
WITH MEMBER Measures.x AS   
   [Measures].[Internet Sales Amount] /   
   ( [Measures].[Internet Sales Amount],  
      Ancestors   
         ( [Customer].[Customer Geography].CurrentMember,   
           [Customer].[Customer Geography].[Country]  
         ).Item (0)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{Descendants   
   ( [Customer].[Customer Geography].[Country].&[Australia],   
     [Customer].[Customer Geography].[State-Province], SELF   
   )    
} ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
