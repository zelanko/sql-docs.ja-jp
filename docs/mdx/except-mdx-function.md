---
title: "(MDX) を除く |Microsoft ドキュメント"
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
f1_keywords: EXCEPT
dev_langs: kbMDX
helpviewer_keywords: Except function
ms.assetid: 5d832c82-1e6d-4308-9c26-7edb8afe11dd
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 36e19418f982542318da340664182526c2b00070
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="except-mdx-function"></a>Except (MDX) 関数
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Remarks  
 場合**すべて**が指定すると、関数は、最初のセットで検出された重複部分を保持は 2 番目のセットで検出された重複部分は削除されます。 メンバーは、1 番目のセット内に出現する順序で返されます。  
  
## <a name="examples"></a>使用例  
 この関数の使用例を以下に示します。  
  
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
 [-(& a) #40 です。除く (& a) #41;&#40;です。MDX と #41 です。](../mdx/except-mdx-operator.md)   
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
