---
title: 軸 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fa65c1531be29273c0a838b978109bbd1c8a2b18
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68016978"
---
# <a name="axis-mdx"></a>Axis (MDX)


  指定された軸上の組のセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Axis(Axis_Number)  
```  
  
## <a name="arguments"></a>引数  
 *Axis_Number*  
 軸番号を指定する有効な数値式です。  
  
## <a name="remarks"></a>Remarks  
 Axis**関数は、軸**の0から始まる位置を使用して、軸上の組のセットを返します。 たとえば、は`Axis(0)` COLUMNS 軸を返し、 `Axis(1)`は ROWS 軸を返します。 **軸**関数は、フィルター軸では使用できません。 この関数を使用すると、実行されているクエリのコンテキストを計算されるメンバーに認識させることができます。 たとえば、ROWS 軸上で選択されたメンバーのみの合計を提供する、計算されるメンバーが必要になる場合があります。 また、この関数を使用すると、一方の軸の定義をもう一方の軸の定義に依存させることもできます。 たとえば、COLUMNS 軸の最初の項目の値に応じて ROWS 軸の内容を並べ替えます。  
  
> [!NOTE]  
>  軸は、前の軸だけを参照できます。 たとえば、行`Axis(0)`またはページの軸のように、列の軸を評価した後にを実行する必要があります。  
  
## <a name="examples"></a>使用例  
 次のクエリの例では、軸関数を使用する方法を示します。  
  
 `WITH MEMBER MEASURES.AXISDEMO AS`  
  
 `SETTOSTR(AXIS(1))`  
  
 `SELECT MEASURES.AXISDEMO ON 0,`  
  
 `[Date].[Calendar Year].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 次の例では、計算されるメンバー内での Axis 関数の使用方法を示しています。  
  
 `WITH MEMBER MEASURES.AXISDEMO AS`  
  
 `SUM(AXIS(1), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.AXISDEMO} ON 0,`  
  
 `{[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
