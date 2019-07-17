---
title: メンバー式の使用 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 41ff63d47a62b9b83fb583c55ff2405638de22cf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097113"
---
# <a name="using-member-expressions"></a>メンバー式の使用


  メンバー式には、メンバー識別子、メンバー関数の場合、またはメンバーに変換できる式が含まれています。  
  
 メンバー識別子には、さまざまな形式があります。 メンバー識別子の最も単純な形式は、メンバーの名前で構成されます。 例:  
  
```  
SELECT Amount ON 0  
FROM [Adventure Works]  
  
```  
  
 ただし、異なる階層に同じ名前のいくつかのメンバーがある場合は、クエリを返しますメンバーを決定する方法はありません。 たとえば、次のクエリでは、[CY 2004] という名前のメンバーに関するデータを要求します。 クエリが正常には、Adventure Works キューブ内には、その名前を持つ 6 個以上のメンバーには。  
  
```  
SELECT [CY 2004] ON 0  
FROM [Adventure Works]  
  
```  
  
 したがって、メンバー識別子の最も信頼性の高い形式はメンバーの一意な名前です。これにより、キューブ内の特定のメンバーが識別されるようになります。 Analysis Services は、いくつかの方法で一意の名前を生成できますが、一意の名前は常に少なくとも 2 つの識別子ので構成されます。 ディメンション名およびメンバー名またはメンバー キー。 一意の名前の形式は次のとおりです。  
  
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
  
 MDX 関数には、メンバーを返すものが多数存在します。 完全な一覧についてを参照してください[MDX 関数リファレンス&#40;MDX。&#41;](../mdx/mdx-function-reference-mdx.md)  
  
> [!NOTE]  
>  メンバー名およびメンバー キーの詳細については、次を参照してください。[メンバー、組、およびセットの操作&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)します。  
  
## <a name="see-also"></a>関連項目  
 [式&#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
