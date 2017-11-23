---
title: "軸 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: AXIS
dev_langs: kbMDX
helpviewer_keywords: Axis function
ms.assetid: a3a60a1e-e266-4fa1-ae13-bae73544de33
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f996b2f9cf090a8b126de5ab349eb13dd0e46485
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="axis-mdx"></a>Axis (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定された軸上の組のセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Axis(Axis_Number)  
```  
  
## <a name="arguments"></a>引数  
 *Axis_Number*  
 軸番号を指定する有効な数値式です。  
  
## <a name="remarks"></a>解説  
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
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
