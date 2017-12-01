---
title: "ルート (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Root
dev_langs: kbMDX
helpviewer_keywords: Root function
ms.assetid: f6c42e87-5a52-4e43-9dd1-ca757f2db79c
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a444fe658eae3d84af4ee320f57a182c4d100f75
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="root-mdx"></a>Root (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  構成される組を返します、**すべて**キューブ、ディメンション、または組の現在のスコープ内の各属性階層のメンバーです。 スコープの詳細については、次を参照してください。 [SCOPE ステートメント &#40;です。MDX と #41 です;](../mdx/mdx-scripting-scope.md)。  
  
> [!NOTE]  
>  属性階層がない場合、**すべて**メンバー、組には、その階層の既定のメンバーが含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
  
Cube syntax  
Root ()  
Dimension syntax  
Root( Dimension_Name )  
Tuple syntax  
Root( Tuple_Expression )  
```  
  
## <a name="arguments"></a>引数  
 *Dimension_Name*  
 ディメンション名を指定する有効な文字列式です。  
  
 *Tuple_Expression*  
 組を返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 ディメンション名も組式が指定されている場合、**ルート**関数を含む組を返します、**すべて**メンバー (または既定のメンバー場合、**すべて**メンバーが存在しない)、キューブ内の各属性階層からです。 組の中のメンバーの順序は、キューブ内で属性階層が定義されている順序に基づきます。  
  
 ディメンション名が指定されている場合、**ルート**関数を含む組を返します、**すべて**メンバー (または既定のメンバー場合、**すべて**メンバーが存在しない)、現在のメンバーのコンテキストに基づいて、指定されたディメンション内の各属性階層からです。 組の中のメンバーの順序は、ディメンション内で属性階層が定義されている順序に基づきます。  
  
> [!NOTE]  
>  階層名が指定されている場合、**組**関数は、指定された階層名からディメンション名を取得します。  
  
 組式が指定されている場合、**ルート**関数を指定された組の積集合を含む組を返しますと**すべて**明示的に指定された組に含まれている他のすべてのディメンション属性のメンバーです。  
  
## <a name="examples"></a>使用例  
 次の例を含む組を返します、**すべて**メンバー (または既定の場合、**すべて**メンバーが存在しない)、Adventure Works キューブ内の各階層からです。  
  
```  
SELECT Root()ON 0  
FROM [Adventure Works]  
```  
  
 次の例を含む組を返します、**すべて**メンバー (または既定の場合、**すべて**メンバーが存在しない) とこれらの既定のメンバーと交差するメジャー ディメンションの指定されたメンバーの値の Adventure Works キューブの Date ディメンション内の各階層からです。  
  
```  
SELECT Root([Date]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
 次の例は、指定された組のメンバーを含む組を返します (2001 年 7 月 1 日と共に、**すべて**メンバー (または既定の場合、**すべて**メンバーが存在しない)、その日付では、非指定の各階層からこれらのメンバーと交差するメジャー ディメンションの指定されたメンバーの Adventure Works キューブと値をディメンションです。  
  
```  
SELECT Root([Date].[July 1, 2001]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
