---
description: Except (MDX) 関数
title: Except (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6e4cd8dcf3a8c3100a064e8ba5888060477de979
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341508"
---
# <a name="except-mdx-function"></a>Except (MDX) 関数


  2 つのセットを評価し、2 番目のセットにも存在する組を 1 番目のセットから削除します。必要に応じて、重複部分を保持します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Except(Set_Expression1, Set_Expression2 [, ALL ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression1*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
 *Set_Expression2*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **ALL**を指定した場合、関数は、1番目のセットで見つかった重複部分を保持します。2番目のセットで見つかった重複部分は削除されます。 メンバーは、最初のセットに出現する順序で返されます。  
  
## <a name="examples"></a>例  
 この関数の使用例を次に示します。  
  
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
  
## <a name="see-also"></a>参照  
 [-&#41; &#40;MDX&#41;を除く &#40;](../mdx/except-mdx-operator.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
