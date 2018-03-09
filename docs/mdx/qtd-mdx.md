---
title: "Qtd (MDX) |Microsoft ドキュメント"
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
f1_keywords: QTD
dev_langs: kbMDX
helpviewer_keywords: Qtd function
ms.assetid: c1fe47e0-9c2b-466f-8d6d-e2b1c16a69cb
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 767da32ea9001be53b4418fae2cfecb26d3cc842
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="qtd-mdx"></a>Qtd (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  以降では最初の兄弟、制約の中で指定されたメンバーで終わると、特定のメンバーと同じレベルからメンバーの兄弟のセットを返します、*四半期*時間ディメンション内のレベルです。  
  
## <a name="syntax"></a>構文  
  
```  
  
Qtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>Remarks  
 メンバー式が指定されていない、既定値は、現在の最初の階層のレベルを持つメンバー型の*四半期*型の最初の次元の*時間*メジャー グループにします。  
  
 **Qtd**関数のショートカット関数では、 [PeriodsToDate (& a) #40 です。MDX と #41 です。](../mdx/periodstodate-mdx.md) 、レベル式引数に設定されている関数*四半期*です。 つまり、`Qtd(Member_Expression)` と `PeriodsToDate(Quarter_Level_Expression, Member_Expression)` は機能的に等価です。  
  
## <a name="example"></a>例  
 次の例は、の合計を返して、`Measures.[Order Quantity]`メンバーを集計した、最初の 2 か月の 2003 年第 3 四半期に含まれている、`Date`ディメンションから、 **Adventure Works**キューブ。  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        QTD([Date].[Calendar].[Month].[August 2003])  
    )  
SELECT   
    [Date].[Calendar].[First2MonthsSecondSemester2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
