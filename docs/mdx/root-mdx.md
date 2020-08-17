---
description: ルート (MDX)
title: ルート (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a408250de53e3d77750d6ea9a87aa679152a86d8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341308"
---
# <a name="root-mdx"></a>ルート (MDX)


  キューブ、ディメンション、または組の現在のスコープ内の各属性階層の **すべて** のメンバーで構成される組を返します。 スコープの詳細については、「 [Scope ステートメント &#40;MDX&#41;](../mdx/mdx-scripting-scope.md)」を参照してください。  
  
> [!NOTE]  
>  属性階層に **All** メンバーが含まれていない場合、組にはその階層の既定のメンバーが含まれます。  
  
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
 ディメンション名も組式も指定されていない場合、 **ルート** 関数は、キューブ内の各属性階層から **all** メンバー (または、 **すべて** のメンバーが存在しない場合は既定のメンバー) を含む組を返します。 組の中のメンバーの順序は、キューブ内で属性階層が定義されている順序に基づきます。  
  
 ディメンション名が指定されている場合、 **ルート** 関数は、現在のメンバーのコンテキストに基づいて、指定されたディメンションの各属性階層から、 **all** メンバー (または、 **すべて** のメンバーが存在しない場合は既定のメンバー) を含む組を返します。 組のメンバーの順序は、ディメンション内で属性階層が定義されている順序に基づいています。  
  
> [!NOTE]  
>  階層名が指定されている場合、 **組** 関数は、指定された階層名からディメンション名を取得します。  
  
 組式が指定されている場合、 **ルート** 関数は、指定された組と、指定された組に明示的に含まれていない他のすべてのディメンション属性の **すべて** のメンバーの交差部分を含む組を返します。  
  
## <a name="examples"></a>例  
 次の例では、Adventure Works キューブ内の各階層から、 **all** メンバー (または **all** メンバーが存在しない場合は既定値) を含む組を返します。  
  
```  
SELECT Root()ON 0  
FROM [Adventure Works]  
```  
  
 次の例では、Adventure Works キューブの Date ディメンションの各階層と、これらの既定のメンバーと交差するメジャーディメンションの指定されたメンバーの値を含む、 **all** メンバー (または、 **all** メンバーが存在しない場合は既定値) を含む組を返します。  
  
```  
SELECT Root([Date]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
 次の例では、指定された組メンバーを含むタプルを返します (1, 2001,、日付ディメンション Adventure **All** works キューブ内の指定されていない各階層**から、これら**のメンバーと交差するメジャーディメンションの指定されたメンバーの値)。  
  
```  
SELECT Root([Date].[July 1, 2001]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
