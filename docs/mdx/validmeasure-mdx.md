---
title: ValidMeasure (MDX) |Microsoft ドキュメント
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
- VALIDMEASURE
dev_langs:
- kbMDX
helpviewer_keywords:
- ValidMeasure function
ms.assetid: ecf20a86-c45e-4521-84ce-3a466e0c1136
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: c3c2bb7aa20794d7de9a3eeaa208377736af653e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="validmeasure-mdx"></a>ValidMeasure (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定された組に対応する結果を返す際に、適用できないディメンションを All レベル (集計可能でない場合は既定のメンバー) にすることにより、キューブ内のメジャーの値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
ValidMeasure(Tuple_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Tuple_Expression*  
 組を返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **ValidMeasure**組の値、属性、メジャーのメジャー グループと関係がない値を無視組を返します。 属性にメジャーとの間のリレーションシップが存在しない理由は 2 つ考えられます。  
  
-   属性のディメンションに、組のメジャーのメジャー グループとの間のリレーションシップが存在しない。  
  
-   属性のディメンションに、メジャーのメジャー グループとの間のリレーションシップが存在しないが、粒度属性はキー属性でなく、粒度属性には組の属性との間に直接的なリレーションシップが存在しない。  
  
 この関数によって指定される動作は、既定のサーバー側の動作とによって制御されます、 **IgnoreUnrelatedDimensions**メジャー グループ オブジェクトのプロパティです。  
  
 指定された組の各属性に粒度が指定されている場合 (つまり、組のメンバーが All メンバーでない場合)、各属性の現在の座標は次のように移動されます。  
  
-   指定属性メンバーに関連していた属性は、現在のメンバーと共存するメンバーに移動されます。  
  
-   指定された属性メンバーに関連する属性は、All メンバー (階層が集計可能でない場合は既定のメンバー) に移動されます。  
  
-   関連しない属性は、(メジャーに基づいて) All メンバーに移動されます。  
  
## <a name="example"></a>例  
 次のクエリは、ValidMeasure 関数を使用して IgnoreUnrelatedDimensions プロパティの動作をオーバーライドする方法を示します。 Adventure Works キューブの Sales Targets メジャー グループでは、IgnoreUnrelatedDimensions が False に設定されます。これは、Date ディメンションが Calendar Quarter 粒度でこのメジャー グループに結合するためです。つまり、MDX スクリプトで下位の Month レベルまで値を割り当てる計算を行っても、Sales Quota メジャーにより既定で Calendar Quarter の下に NULL が返されます。 計算されるメジャーで ValidMeasure 関数を使用すると、Sales Quota メジャーは IgnoreUnrelatedDimensions が True に設定されている場合と同じように動作し、Sales Quota が現在の Calendar Quarter の値を表示するように強制できます。  
  
```  
WITH MEMBER MEASURES.VTEST AS VALIDMEASURE([Measures].[Sales Amount Quota])  
SELECT {[Measures].[Sales Amount Quota], MEASURES.VTEST} ON 0,  
[Date].[Calendar].MEMBERS ON 1  
FROM [Adventure Works]  
```  
  
 同様に、Sales Targets メジャー グループには Promotion ディメンションとの間にリレーションシップがないため、Promotion のすべての階層の All Member の下に NULL が返されます。 さらに、この動作も ValidMeasure を使用して変更できます。  
  
 `WITH MEMBER MEASURES.VTEST AS VALIDMEASURE([Measures].[Sales Amount Quota])`  
  
 `SELECT {[Measures].[Sales Amount Quota], MEASURES.VTEST} ON 0,`  
  
 `[Promotion].[Promotions].members ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
