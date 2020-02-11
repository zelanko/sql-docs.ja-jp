---
title: レベル (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 24e15602593f9116d499345ffca093f86ecfa135
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905644"
---
# <a name="levels-mdx"></a>レベル (MDX)


  ディメンションまたは階層内の位置が数値式で指定されているか、文字列式で指定された名前を持つレベルを返します。  
  
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
  
## <a name="remarks"></a>解説  
 レベル番号が指定されている場合、 **Levels**関数は、指定された0から始まる位置に関連付けられているレベルを返します。  
  
 レベル名が指定されている場合、 **Levels**関数は指定されたレベルを返します。  
  
> [!NOTE]  
>  ユーザー定義関数については、文字列式の構文を使用してください。  
  
## <a name="examples"></a>例  
 次の例では、各**レベル**の関数の構文について説明します。  
  
### <a name="numeric"></a>数値  
 次の例では、国のレベルが返されます。  
  
```  
SELECT [Geography].[Geography].Levels(1) ON 0  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>String  
 次の例では、国のレベルが返されます。  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
