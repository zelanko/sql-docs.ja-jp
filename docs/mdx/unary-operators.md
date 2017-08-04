---
title: "単項演算子 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- unary operators
ms.assetid: bf1b5518-6040-4484-9ce8-79c0eb4373a9
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5b5aea52fb028a9c1d5345e60d4bfa400ecaa735
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="unary-operators"></a>単項演算子
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  多次元式 (MDX) において、単項演算子は単一のオペランドに対する操作を実行します (たとえば、数値式の負または正の値を返します)。  
  
 MDX では、以下の表に示す単項演算子がサポートされます。  
  
|演算子|Description|  
|--------------|-----------------|  
|[-(負号)](../mdx/negative-mdx.md)|数値式の負の値を返します。|  
|[+ (正号)](../mdx/positive-mdx.md)|数値式の正の値を返します。|  
  
 次の例では、単項演算子を使用してメジャーの負の値を返します。  
  
```  
WITH   
   MEMBER [Measures].[NegDiscountAmount] AS  
   -[Measures].[Discount Amount]  
SELECT   
   {[Measures].[Discount Amount],[Measures].[NegDiscountAmount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
 によって実行される集計操作を決定するさらに、MDX が特別な単項演算子を使用して、 [RollupChildren](../mdx/rollupchildren-mdx.md)関数。 これらの特別な単項演算子の詳細については、次を参照してください。[ディメンションへのカスタム集計の追加](../analysis-services/multidimensional-models/bi-wizard-add-a-custom-aggregation-to-a-dimension.md)です。  
  
## <a name="see-also"></a>参照  
 [演算子 & #40 です。MDX 構文 &#41;](../mdx/operators-mdx-syntax.md)  
  
  

