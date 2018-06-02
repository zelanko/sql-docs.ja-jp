---
title: レベル (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2fba58261bb0ba8f91e8127b1d33b847accf0dc7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579514"
---
# <a name="levels-mdx"></a>Levels (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  数値式でディメンション内または階層内の位置を指定されたレベル、または文字列式で名前を指定されたレベルを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Numeric expression syntax  
Hierarchy_Expression.Levels( Level_Number )  
  
String expression syntax  
Hierarchy_Expression.Levels( Level_Name )  
```  
  
## <a name="arguments"></a>引数  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
 *Level_Number*  
 レベル番号を指定する有効な数値式です。  
  
 *Level_Name*  
 レベル名を指定する有効な文字列式です。  
  
## <a name="remarks"></a>コメント  
 レベル番号が指定されている場合、**レベル**関数は、指定した 0 から始まる位置に関連付けられているレベルを返します。  
  
 レベル名が指定されている場合、**レベル**関数は、指定されたレベルを返します。  
  
> [!NOTE]  
>  ユーザー定義関数については、文字列式の構文を使用してください。  
  
## <a name="examples"></a>使用例  
 次の例の各、**レベル**関数の構文。  
  
### <a name="numeric"></a>数値  
 次の例では、Country レベルが返されます。  
  
```  
SELECT [Geography].[Geography].Levels(1) ON 0  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>String  
 次の例では、Country レベルが返されます。  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
