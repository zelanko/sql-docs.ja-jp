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
ms.openlocfilehash: b419cbb05aa616f163f5878bda83c9d68203575d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905659"
---
# <a name="level-mdx"></a>Level (MDX)


  メンバーのレベルを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Level  
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを返す有効な多次元式 (MDX) です。  
  
### <a name="examples"></a>例  
 次の例では、**レベル**関数を使用して、Adventure works キューブ内のすべての月を返します。  
  
```  
SELECT[Date].[Fiscal].[Month].[February 2002].Level.Members ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 次の例では、**レベル**関数を使用して、Adventure works キューブの Model name 属性階層にあるすべての目的の自転車ショップのレベル名を返します。  
  
```  
WITH MEMBER Measures.x AS   
   [Product].[Model Name].[All-Purpose Bike Stand].Level.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
