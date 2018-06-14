---
title: 現在の (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e4962dfd9eba7d3a21710fef33aa39256dcfbfa
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739481"
---
# <a name="current-mdx"></a>Current (MDX)


  繰り返し処理の実行時に、セットから現在の組を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set_Expression.Current   
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="remarks"></a>コメント  
 繰り返し処理の各ステップで操作の対象になっている組が現在の組です。 **現在**関数は、その組を返します。 この関数は、セットに対する繰り返し処理の実行中のみ有効です。  
  
 セットを反復処理する MDX 関数が含まれて、[生成](../mdx/generate-mdx.md)関数。  
  
> [!NOTE]  
>  この関数は、セットの別名を使用するか名前付きセットを定義することによって名前が付けられたセットに対してのみ使用できます。  
  
## <a name="examples"></a>使用例  
 次の例を使用する方法を示しています、**現在**関数**生成**:  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of all Calendar Years crossjoined with`  
  
 `//all Product Categories`  
  
 `SET MyTuples AS CROSSJOIN(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS,`  
  
 `[Product].[Category].[Category].MEMBERS)`  
  
 `//Iterates through each tuple in the set and returns the name of the Calendar`  
  
 `//Year in each tuple`  
  
 `MEMBER MEASURES.CURRENTDEMO AS`  
  
 `GENERATE(MyTuples, MyTuples.CURRENT.ITEM(0).NAME, ", ")`  
  
 `SELECT MEASURES.CURRENTDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
