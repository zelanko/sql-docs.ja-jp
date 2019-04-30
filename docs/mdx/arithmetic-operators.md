---
title: 算術演算子 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c422df08152eaf9266a6ca3408bfce12e023c2a3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63284515"
---
# <a name="arithmetic-operators"></a>算術演算子


  加算、減算、乗算、および除算を含め、算術演算を行うには、多次元式 (MDX) で算術演算子を使用できます。  
  
 MDX では、以下の表に示す算術演算子がサポートされます。  
  
|演算子|説明|  
|--------------|-----------------|  
|[+ (加算)](../mdx/add-mdx.md)|2 つの値を加算します。|  
|[/ (除算)](../mdx/divide-mdx-operator-reference.md)|1 つの数値を別の数値を除算します。|  
|[* (乗算)](../mdx/multiply-mdx.md)|2 つの値を乗算します。|  
|[- (減算)](../mdx/subtract-mdx.md)|2 つの値の間で減算をします。|  
|^ (累乗)|1 つの数値を別の数値を生成します。|  
  
> [!NOTE]  
>  MDX には、数値の平方根を取得する関数は含まれていません。 数値の平方根を取得するには、^ 演算子を使用してその数値を 0.5 で累乗してください。  
  
## <a name="order-of-precedence"></a>優先順位の順序  
 MDX 式内での算術演算子の優先順位は、以下の規則によって決まります。  
  
-   式では、複数の算術演算子がある場合は、MDX 実行乗算と除算最初に、後に減算と加算します。  
  
-   式のすべての算術演算子の優先順位の同じレベルとは、実行の順序を左右から。  
  
-   かっこの中の式は、他のどの操作よりも優先されます。  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [演算子&#40;MDX 構文&#41;](../mdx/operators-mdx-syntax.md)  
  
  
