---
title: レベル (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Levels
dev_langs:
- kbMDX
helpviewer_keywords:
- Levels function
ms.assetid: 1a989cc9-8aa8-4ec3-b5e9-795d6fa84983
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 1898b87749b8ae2921e71d391f8bbae3374d893b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
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
  
## <a name="remarks"></a>解説  
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
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
