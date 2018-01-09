---
title: "比較演算子 |Microsoft ドキュメント"
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
dev_langs: kbMDX
helpviewer_keywords: comparison operators [MDX]
ms.assetid: 4a4bbc76-c6a2-4b19-ae75-6ac3ac14df01
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e99997bd3d87dbe949c8658ac7f866c648959430
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="comparison-operators"></a>比較演算子
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  比較演算子は、スカラー データと共に使用します。 比較演算子は、任意の多次元式 (MDX) 式で使用できます。  
  
 条件を確認するには、MDX ステートメントや MDX などの関数で比較演算子も使用できます[IIf](../mdx/iif-mdx.md)関数。 ただし、条件を満たしているかどうかを調べるために比較演算子を使用する場合は、その条件に基づいてデータの変更を試みる前に、適切な権限を持っていることを確認してください。 実際のデータにアクセスし、そのデータに対してクエリを実行できるユーザーはだれでも、他のクエリで比較演算子を使用できます。 しかし、このようにアクセスできることは、それらのユーザーがデータを変更するための適切な権限を持っている、あるいは持つ必要があるという意味ではありません。 また、データの整合性を維持するためにも、データに対してクエリを実行してデータを変更できるユーザーの数は制限してください。  
  
 比較演算子はブール型に評価され、条件がテストされた結果に基づいて TRUE または FALSE を返します。  
  
 MDX では、以下の表に示す比較演算子がサポートされます。  
  
|演算子|Description|  
|--------------|-----------------|  
|[= (等しい)](../mdx/equal-to-mdx.md)|NULL 以外の引数について、左の引数が右の引数に等しい場合に TRUE を返します。そうでない場合は、FALSE を返します。<br /><br /> しない限り、いずれかまたは両方の引数は、null 値に評価される場合、演算子は、null 値を返します比較`0=null`行われると、ブール値が TRUE を含む場合。|  
|[<> (等しくない)](../mdx/not-equal-to-mdx.md)|NULL 以外の引数について、左の引数が右の引数に等しくない場合に TRUE を返します。そうでない場合は、FALSE を返します。<br /><br /> 一方または両方の引数が NULL 値に評価される場合は、NULL 値が返されます。|  
|[> (より大きい)](../mdx/greater-than-mdx.md)|NULL 以外の引数について、左の引数の値が右の引数の値より大きい場合に TRUE を返します。そうでない場合は、FALSE を返します。<br /><br /> 一方または両方の引数が NULL 値に評価される場合は、NULL 値が返されます。|  
|[>= (以上)](../mdx/greater-than-or-equal-to-mdx.md)|NULL 以外の引数について、左の引数の値が右の引数の値以上である場合に TRUE を返します。そうでない場合は、FALSE を返します。<br /><br /> 一方または両方の引数が NULL 値に評価される場合は、NULL 値が返されます。|  
|[< (より小さい)](../mdx/less-than-mdx.md)|NULL 以外の引数について、左の引数の値が右の引数の値より小さい場合に TRUE を返します。そうでない場合は、FALSE を返します。<br /><br /> 一方または両方の引数が NULL 値に評価される場合は、NULL 値が返されます。|  
|[<= (以下)](../mdx/less-than-or-equal-to-mdx.md)|NULL 以外の引数について、左の引数の値が右の引数の値以下である場合に TRUE を返します。そうでない場合は、FALSE を返します。<br /><br /> 一方または両方の引数が NULL 値に評価される場合は、NULL 値が返されます。|  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)   
 [演算子 &#40;です。MDX 構文 &#41;](../mdx/operators-mdx-syntax.md)  
  
  
