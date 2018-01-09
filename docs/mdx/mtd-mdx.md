---
title: "Mtd (MDX) |Microsoft ドキュメント"
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
f1_keywords: MTD
dev_langs: kbMDX
helpviewer_keywords: Mtd function
ms.assetid: 07d8fd65-f9e6-42d4-868d-fccfac6bdb70
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f6969649d0ac405aca0766219b0df52b1c1ee244
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="mtd-mdx"></a>Mtd (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  時間ディメンションの年 (Year) レベルという制約の中で、指定されたメンバーと同じレベルにある兄弟メンバーのセットを返します。先頭は最初の兄弟、末尾は指定されたメンバーになります。  
  
## <a name="syntax"></a>構文  
  
```  
  
Mtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 既定値は型のレベルを持つ最初の階層の現在のメンバーではメンバー式が指定されていない場合*月*型の最初の次元の*時間*メジャー グループにします。  
  
 **Mtd**関数のショートカット関数では、 [PeriodsToDate](../mdx/periodstodate-mdx.md)レベルの基になる属性階層の Type プロパティ設定されている場合に機能*月*です。 つまり、`Mtd(Member_Expression)`は等価`PeriodsToDate(Month_Level_Expression,Member_Expression)`です。  
  
## <a name="example"></a>例  
 次の例では、July, 2002 年 7 月の 20 日からの Internet sales の運送料の日付を月の合計を返します。  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [合計 &#40;です。MDX と #41 です。](../mdx/sum-mdx.md)   
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
