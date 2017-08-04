---
title: "算術演算子 |Microsoft ドキュメント"
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
- arithmetic operators
ms.assetid: 1dff3e20-fe9d-4155-bf06-27d6458188e9
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bc3adf599f92a74dd996a0ef090f6f42ab1fba0d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="arithmetic-operators"></a>算術演算子
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  多次元式 (MDX) 内では、算術演算子を使用して、加算、減算、乗算、除算を含む算術演算を行うことができます。  
  
 MDX では、以下の表に示す算術演算子がサポートされます。  
  
|演算子|Description|  
|--------------|-----------------|  
|[+ (加算)](../mdx/add-mdx.md)|2 つの値を加算します。|  
|[/(除算)](../mdx/divide-mdx-operator-reference.md)|ある数値を別の数値によって除算します。|  
|[* (乗算)](../mdx/multiply-mdx.md)|2 つの値を乗算します。|  
|[-(減算)](../mdx/subtract-mdx.md)|2 つの値の間で減算をします。|  
|^ (Power)|1 つの値を別の値で累乗します。|  
  
> [!NOTE]  
>  MDX には、数値の平方根を取得する関数は含まれていません。 数値の平方根を取得するには、^ 演算子を使用してその数値を 0.5 で累乗してください。  
  
## <a name="order-of-precedence"></a>優先順位の順序  
 MDX 式内での算術演算子の優先順位は、以下の規則によって決まります。  
  
-   1 つの式の中に複数の算術演算子がある場合、MDX は乗算と除算を先に実行し、その後に減算と加算を実行します。  
  
-   式のすべての算術演算子の同じレベルの優先順位の場合は、実行の順序を左から右にします。  
  
-   かっこの中の式は、他のどの操作よりも優先されます。  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)   
 [演算子 & #40 です。MDX 構文 &#41;](../mdx/operators-mdx-syntax.md)  
  
  

