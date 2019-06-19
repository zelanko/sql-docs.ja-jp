---
title: (MDX) を除く |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 03d9b5140eb0cbf9d868e43c65213efe917994a9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62690882"
---
# <a name="except-mdx-function"></a>Except (MDX) 関数


  2 つのセットを評価し、2 番目のセットにも存在する組を 1 番目のセットから削除します。必要に応じて、重複部分を保持します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Except(Set_Expression1, Set_Expression2 [, ALL ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression1*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Set_Expression2*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="remarks"></a>コメント  
 場合**すべて**が指定すると、関数は、最初のセットで検出された重複部分を保持は、2 番目のセットで検出された重複部分が削除されます。 メンバーは、最初のセットに表示される順序で返されます。  
  
## <a name="examples"></a>使用例  
 次の例では、この関数の使用を示します。  
  
```  
   //This query shows the quantity of orders for all products,  
   //with the exception of Components, which are not  
   //sold.  
SELECT   
   [Date].[Month of Year].Children  ON COLUMNS,  
   Except  
      ([Product].[Product Categories].[All].Children ,  
         {[Product].[Product Categories].[Components]}  
      ) ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   ([Measures].[Order Quantity])  
```  
  
## <a name="see-also"></a>関連項目  
 [-&#40;を除く&#41; &#40;MDX&#41;](../mdx/except-mdx-operator.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
