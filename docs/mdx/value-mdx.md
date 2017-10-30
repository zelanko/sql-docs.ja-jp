---
title: "値 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Value
dev_langs:
- kbMDX
helpviewer_keywords:
- Value function
ms.assetid: ff76628e-2d49-49f6-a6cb-f6da07d83d65
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 63e24e0f701332747e3129a57768bfe1b6fbb45d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="value-mdx"></a>Value (MDX)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  クエリのコンテキストで属性階層の現在のメンバーと交差する、メジャー ディメンションの現在のメンバーの値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression[.Value]   
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **値**関数を文字列として指定されたメンバーの値を返します。 **値**メンバーの値は、メンバーの既定のプロパティであり、他の値が指定されていない場合、メンバーに関して返される値は、ために、引数は省略可能です。 メンバーのプロパティの詳細については、次を参照してください。[固有メンバー プロパティ & #40 です。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md)と[ユーザー定義メンバー プロパティ & #40 です。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md).  
  
## <a name="examples"></a>使用例  
 次の例では、明示的にメンバーの名前を返すだけでなく、メンバーの値も返します。  
  
```  
WITH MEMBER [Date].[Calendar].NumericValue as [Date].[Calendar].[July 1, 2001].Value  
MEMBER [Date].[Calendar].MemberName AS [Date].[Calendar].[July 1, 2001].Name  
  
SELECT {[Date].[Calendar].NumericValue, [Date].[Calendar].MemberName} ON 0  
from [Adventure Works]  
```  
  
 次の例では、軸上のメンバーに関して返される既定の値としてメンバーの値を返します。  
  
```  
SELECT {[Date].[Calendar].[July 1, 2001]} ON 0  
from [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MemberValue & #40 です。MDX と #41 です。](../mdx/membervalue-mdx.md)   
 [プロパティ & #40 です。MDX と #41 です。](../mdx/properties-mdx.md)   
 [名前と #40 です。MDX と #41 です。](../mdx/name-mdx.md)   
 [UniqueName & #40 です。MDX と #41 です。](../mdx/uniquename-mdx.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

