---
title: 比較演算子 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ae175665c2a62caa2d3b7b845c68fefebcfd4c32
ms.sourcegitcommit: 5d6e1c827752c3aa2d02c4c7653aefb2736fffc3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2018
ms.locfileid: "49071663"
---
# <a name="comparison-operators"></a>比較演算子


  比較演算子は、スカラー データと共に使用します。 比較演算子は、任意の多次元式 (MDX) 式で使用できます。  
  
 条件を確認するには、MDX ステートメントや MDX などの関数で比較演算子も使用できます[IIf](../mdx/iif-mdx.md)関数。 ただし、条件を満たしているかどうかを調べるために比較演算子を使用する場合は、その条件に基づいてデータの変更を試みる前に、適切な権限を持っていることを確認してください。 実際のデータにアクセスし、そのデータに対してクエリを実行できるユーザーはだれでも、他のクエリで比較演算子を使用できます。 しかし、このようにアクセスできることは、それらのユーザーがデータを変更するための適切な権限を持っている、あるいは持つ必要があるという意味ではありません。 また、データの整合性を維持するためにも、データに対してクエリを実行してデータを変更できるユーザーの数は制限してください。  
  
 比較演算子はブール型に評価され、条件がテストされた結果に基づいて TRUE または FALSE を返します。  
  
 MDX では、以下の表に示す比較演算子がサポートされます。  
  
|演算子|説明|  
|--------------|-----------------|  
|[= (等しい)](../mdx/equal-to-mdx.md)|NULL 以外の引数について、左の引数が右の引数に等しい場合に TRUE を返します。そうでない場合は、FALSE を返します。<br /><br /> 一方または両方の引数が NULL 値に評価される場合は、NULL 値が返されます。ただし、`0=null` の比較が行われる場合、ブール値は TRUE になります。|  
|[<> (等しくない)](../mdx/not-equal-to-mdx.md)|NULL 以外の引数について、左の引数が右の引数に等しくない場合に TRUE を返します。そうでない場合は、FALSE を返します。<br /><br /> 一方または両方の引数が NULL 値に評価される場合は、NULL 値が返されます。|  
|[> (より大きい)](../mdx/greater-than-mdx.md)|NULL 以外の引数について、左の引数の値が右の引数の値より大きい場合に TRUE を返します。そうでない場合は、FALSE を返します。<br /><br /> 一方または両方の引数が NULL 値に評価される場合は、NULL 値が返されます。|  
|[>= (以上)](../mdx/greater-than-or-equal-to-mdx.md)|NULL 以外の引数について、左の引数の値が右の引数の値以上である場合に TRUE を返します。そうでない場合は、FALSE を返します。<br /><br /> 一方または両方の引数が NULL 値に評価される場合は、NULL 値が返されます。|  
|[< (より小さい)](../mdx/less-than-mdx.md)|Null 以外の引数の左辺の引数が右辺の引数より小さい値を持つ場合に TRUE を返しますそれ以外の場合、FALSE です。<br /><br /> 一方または両方の引数が NULL 値に評価される場合は、NULL 値が返されます。|  
|[<= (以下)](../mdx/less-than-or-equal-to-mdx.md)|NULL 以外の引数について、左の引数の値が右の引数の値以下である場合に TRUE を返します。そうでない場合は、FALSE を返します。<br /><br /> 一方または両方の引数が NULL 値に評価される場合は、NULL 値が返されます。|  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [演算子&#40;MDX 構文&#41;](../mdx/operators-mdx-syntax.md)  
  
  
