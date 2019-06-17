---
title: レベル (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8406d02e167258901c3a6ce9ed3a1d7de935df54
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048516"
---
# <a name="level-mdx"></a>Level (MDX)


  メンバーのレベルを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Level  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを返す有効な多次元式 (MDX)。  
  
### <a name="examples"></a>使用例  
 次の例では、**レベル**Adventure Works キューブ内のすべての月数を返す関数。  
  
```  
SELECT[Date].[Fiscal].[Month].[February 2002].Level.Members ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 次の例では、**レベル**All-Purpose Bike Stand の Adventure Works キューブ内の Model Name 属性階層のレベルの名前を返す関数。  
  
```  
WITH MEMBER Measures.x AS   
   [Product].[Model Name].[All-Purpose Bike Stand].Level.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
