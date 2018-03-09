---
title: "メンバー式の使用 |Microsoft ドキュメント"
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
dev_langs: kbMDX
helpviewer_keywords:
- members [MDX], expressions
- expressions [MDX], members
ms.assetid: 63c7af49-8bea-47c5-9566-a961f77d2a3d
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: bc1574fc06eeaa032fb68d395106721fc33ec699
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="using-member-expressions"></a>メンバー式の使用
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  メンバー式には、メンバー識別子、メンバー関数、またはメンバーに変換可能な式が入ります。  
  
 メンバー識別子には、さまざまな形式があります。 メンバー識別子の最も単純な形式は、メンバーの名前で構成されます。 例 :  
  
```  
SELECT Amount ON 0  
FROM [Adventure Works]  
  
```  
  
 ただし、同じ名前の複数のメンバーが異なる階層に存在する場合は、クエリによって返されるメンバーを決定する方法がありません。 たとえば、次のクエリでは、[CY 2004] という名前のメンバーに関するデータを要求します。 クエリは正常に実行されますが、Adventure Works キューブには、この名前のメンバーが少なくとも 6 つ存在します。  
  
```  
SELECT [CY 2004] ON 0  
FROM [Adventure Works]  
  
```  
  
 したがって、メンバー識別子の最も信頼性の高い形式はメンバーの一意な名前です。これにより、キューブ内の特定のメンバーが識別されるようになります。 Analysis Services ではいくつかの方法で一意の名前を生成できますが、一意の名前は、常に、ディメンション名と、メンバー名またはメンバー キーという、少なくとも 2 つの識別子で構成されます。 一意の名前の形式は次のとおりです。  
  
```  
  
Dimension_Name  
.[Hierarchy_Name.] [[{Member_Name | &Member_Key}.]... ] {Member_Name | &Member_Key}  
  
```  
  
 次に、Adventure Works キューブのメンバーを表す一意の名前の例をいくつか示します。  
  
```  
[Measures].[Amount]  
[Date].[Calendar Year].&[2004]  
[Date].[Calendar].[Calendar Quarter].&[2004]&[1]  
[Employee].[Employees].&[112]  
[Product].[Product Categories].[All Products]  
  
```  
  
 MDX 関数には、メンバーを返すものが多数存在します。 一覧については、次を参照してください。 [MDX 関数リファレンス &#40;です。MDX と #41 です](../mdx/mdx-function-reference-mdx.md)  
  
> [!NOTE]  
>  メンバー名およびメンバー キーの詳細については、次を参照してください[メンバー、組、およびセット &#40; の操作。MDX と #41 です](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)。  
  
## <a name="see-also"></a>参照  
 [式 &#40;です。MDX と #41 です](../mdx/expressions-mdx.md)  
  
  
