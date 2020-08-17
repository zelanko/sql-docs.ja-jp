---
description: Unorder (MDX)
title: Unorder (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 192f320ebc5257f2e6829e15fc40b8144208a521
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341179"
---
# <a name="unorder-mdx"></a>Unorder (MDX)


  指定したセットから適用される順序を削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Unorder(Set_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **Unorder**関数は、 [order](../mdx/order-mdx.md)関数など、他の関数またはステートメントによってセットに含まれる組に適用される順序を削除します。 **Unorder**関数によって返されるセット内の組の順序は不確定です。  
  
 **Unorder**関数は、セット処理のクエリ最適化のヒントとして使用されます。 セット内の組の順序が計算またはクエリにとって重要でない場合、 **Unorder** 関数を使用すると、このような場合にパフォーマンス上の利点が得られます。 たとえば、空でない [(MDX)](../mdx/nonempty-mdx.md) 関数は、この関数に対して指定されたセットが順序を維持する必要がある場合とは異なる場合に、パフォーマンスが向上することがあり [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。ただし、では、 [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] **Sum** や **Aggregate**など多くの関数に対して、クエリプロセッサがこの関数を自動的に実行しようとします。 **Unorder**を使用した場合のパフォーマンス上の利点は、数百万の組から成る非常に大きなセットでのみ顕著になる可能性があります。  
  
## <a name="example"></a>例  
 次の擬似コードは、この関数の構文を示しています。  
  
```  
NonEmpty (UnOrder (<set_expression>))  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
