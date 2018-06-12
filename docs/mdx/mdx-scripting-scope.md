---
title: SCOPE ステートメント (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 497fdfb11ec186ffba56470f2b0ede2ed2f4221a
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741771"
---
# <a name="mdx-scripting---scope"></a>MDX スクリプティングのスコープ


  指定された多次元式 (MDX) ステートメントのスコープを指定されたサブキューブに限定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SCOPE(Subcube_Expression)   
   [ MDX_Statement ]  
END SCOPE  
  
Subcube_Expression ::=(Auxiliary_Subcube [, Auxiliary_Subcube,...n])  
  
Auxiliary_Subcube ::=   
        Limited_Set   
    | Root([dimension_name])   
    | Leaves([dimension_name])  
  
Limited_Set ::=   
        single_tuple   
    | member   
    | Common_Grain_Members   
    | hierarchy.members   
    | level.members   
    | {}   
    | Descendants  
            (  
                  Member  
         , [level  
         [  
            , SELF   
             | AFTER   
                          | BEFORE   
                          | SELF_AND_AFTER   
                          | SELF_AND_BEFORE   
                          | SELF_BEFORE_AFTER   
                          | LEAVES  
                  ]  
            )   
[* <limited set>]  
```  
  
## <a name="arguments"></a>引数  
 *Subcube_Expression*  
 有効な MDX サブキューブ式です。  
  
 *MDX_Statement*  
 有効な MDX ステートメントです。  
  
 *Common_Grain_Members*  
 同じ粒度のメンバーに評価される有効な MDX ステートメントです。  
  
 *single_tuple*  
 1 つの組です。  
  
## <a name="remarks"></a>コメント  
 SCOPE ステートメントでは、1 つ以上の MDX ステートメントの実行対象のサブキューブを指定します。 MDX ステートメントを SCOPE ステートメントの中に組み込まない限り、MDX ステートメントの暗黙的なスコープは、キューブ全体になります。  
  
> [!NOTE]  
>  SCOPE ステートメントは、非表示のメンバーも公開します。  
  
 SCOPE ステートメントに関係なく「口」を公開するサブキューブを作成、 **MDX Compatibility**設定します。 たとえば、次のようなステートメントがあると、`Scope( Customer.State.members )`国や地域が含まれていない状態で、状態を含めることができますが、どのそれ以外の場合に非表示のプレース ホルダーのメンバーを挿入します。  
  
 SCOPE ステートメントの中で作成する計算されるメンバーと名前付きセットは、SCOPE ステートメントの影響を受けません。  
  
## <a name="example"></a>例  
 Adventure Works サンプル ソリューションの MDX 計算スクリプトから次の例では、2005 年会計年度と sales amount quota メジャー、会計四半期として現在のスコープを定義しを使用して現在のスコープ内のセルに値を割り当てます、 **ParallelPeriod**関数。 例では、別の SCOPE ステートメントを使用してスコープを変更しを実行別の割り当てを使用して、 [This (MDX)](../mdx/this-mdx.md)関数。  
  
```  
Scope   
 (   
    [Date].[Fiscal Year].&[2005],  
    [Date].[Fiscal].[Fiscal Quarter].Members,  
    [Measures].[Sales Amount Quota]  
 ) ;     
  
   This = ParallelPeriod                               
          (   
             [Date].[Fiscal].[Fiscal Year], 1,  
             [Date].[Fiscal].CurrentMember   
          ) * 1.35 ;  
  
/*-- Allocate equally to months in FY 2002 -----------------------------*/  
  
  Scope   
  (   
     [Date].[Fiscal Year].&[2002],  
     [Date].[Fiscal].[Month].Members   
  ) ;     
  
    This = [Date].[Fiscal].CurrentMember.Parent / 3 ;     
  
  End Scope ;     
End Scope ;     
```  
  
## <a name="see-also"></a>参照  
 [MDX スクリプト ステートメント&#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
