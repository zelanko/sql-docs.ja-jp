---
title: 軸 (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2802422f7d50c0a504a0c42eec940d81e89e66b8
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739631"
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
  
## <a name="remarks"></a>コメント  
 **軸**関数では、軸の 0 から始まる位置を使用して、軸の組のセットを返します。 たとえば、 `Axis(0)` 、COLUMNS 軸を返します`Axis(1)`と ROWS 軸で返されます。 **軸**フィルター軸に対して関数を使用することはできません。 この関数を使用すると、計算されるメンバーに、実行中のクエリのコンテキストを認識させることができます。 たとえば、ROWS 軸上で選択されたメンバーのみの合計を提供する、計算されるメンバーが必要になる場合があります。 また、この関数を使用すると、一方の軸の定義をもう一方の軸の定義に依存させることもできます。 たとえば、COLUMNS 軸の最初の項目の値に応じて ROWS 軸の内容を並べ替えます。  
  
> [!NOTE]  
>  軸で参照できるのは、先行する軸だけです。 たとえば、 `Axis(0)` COLUMNS 軸が評価された後などを行う必要があります行またはページの軸にします。  
  
## <a name="examples"></a>使用例  
 次のクエリでは、Axis 関数の使用方法を示しています。  
  
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
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
