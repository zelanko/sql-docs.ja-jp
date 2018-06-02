---
title: 算術演算子 |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4bf4a182c73acb18d649de3888f735f8842964dc
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576954"
---
# <a name="arithmetic-operators"></a>算術演算子
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  多次元式 (MDX) 内では、算術演算子を使用して、加算、減算、乗算、除算を含む算術演算を行うことができます。  
  
 MDX では、以下の表に示す算術演算子がサポートされます。  
  
|演算子|説明|  
|--------------|-----------------|  
|[+ (加算)](../mdx/add-mdx.md)|2 つの値を加算します。|  
|[/ (除算)](../mdx/divide-mdx-operator-reference.md)|ある数値を別の数値によって除算します。|  
|[* (乗算)](../mdx/multiply-mdx.md)|2 つの値を乗算します。|  
|[- (減算)](../mdx/subtract-mdx.md)|2 つの値の間で減算をします。|  
|^ (Power)|1 つの値を別の値で累乗します。|  
  
> [!NOTE]  
>  MDX には、数値の平方根を取得する関数は含まれていません。 数値の平方根を取得するには、^ 演算子を使用してその数値を 0.5 で累乗してください。  
  
## <a name="order-of-precedence"></a>優先順位の順序  
 MDX 式内での算術演算子の優先順位は、以下の規則によって決まります。  
  
-   1 つの式の中に複数の算術演算子がある場合、MDX は乗算と除算を先に実行し、その後に減算と加算を実行します。  
  
-   式のすべての算術演算子の同じレベルの優先順位の場合は、実行の順序を左から右にします。  
  
-   かっこの中の式は、他のどの操作よりも優先されます。  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [演算子&#40;MDX 構文&#41;](../mdx/operators-mdx-syntax.md)  
  
  
