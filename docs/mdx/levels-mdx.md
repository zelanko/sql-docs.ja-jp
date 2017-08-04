---
title: "レベル (MDX) |Microsoft ドキュメント"
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
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2b465db3999a950c4ae78997fc66215e72215ed2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="levels-mdx"></a>Levels (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
### <a name="string"></a>文字列  
 次の例では、Country レベルが返されます。  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

