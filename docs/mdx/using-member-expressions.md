---
title: メンバー式の使用 |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bdf16151dac1e55e6fe41d76078b5fc409fd36d3
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581534"
---
# <a name="using-member-expressions"></a>メンバー式の使用
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  メンバー式には、メンバー識別子、メンバー関数、またはメンバーに変換可能な式が入ります。  
  
 メンバー識別子には、さまざまな形式があります。 メンバー識別子の最も単純な形式は、メンバーの名前で構成されます。 以下に例を示します。  
  
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
  
 MDX 関数には、メンバーを返すものが多数存在します。 一覧については、次を参照してください[MDX 関数リファレンス&#40;MDX。&#41;](../mdx/mdx-function-reference-mdx.md)  
  
> [!NOTE]  
>  メンバー名およびメンバー キーの詳細については、次を参照してください。[メンバー、組、およびセット&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)です。  
  
## <a name="see-also"></a>参照  
 [式&#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
