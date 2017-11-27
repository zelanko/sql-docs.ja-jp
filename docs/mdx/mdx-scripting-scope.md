---
title: "SCOPE ステートメント (MDX) |Microsoft ドキュメント"
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
- SCOPE
dev_langs:
- kbMDX
helpviewer_keywords:
- scope [MDX]
- SCOPE statement
ms.assetid: ceab459d-b601-4468-b3fc-4f5bb4a1805f
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1548315744f310a1aca8756d14afee92ef8a693e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-scripting---scope"></a>MDX スクリプティングのスコープ
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>解説  
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
 [MDX スクリプト ステートメント & #40 です。MDX と #41 です。](../mdx/mdx-scripting-statements-mdx.md)  
  
  

