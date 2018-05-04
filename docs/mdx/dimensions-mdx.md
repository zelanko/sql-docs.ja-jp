---
title: ディメンション (MDX) |Microsoft ドキュメント
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
- Dimensions
dev_langs:
- kbMDX
helpviewer_keywords:
- Dimensions function
ms.assetid: 64f63aa0-ef74-4415-a0c9-8acc6cd81739
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 493a17424410155be360828e7c998335c2f11aad
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="dimensions-mdx"></a>Dimensions (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  数値式や文字列式で指定された階層を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Numeric expression syntax  
Dimensions(Hierarchy_Number)  
  
String expression syntax  
Dimensions(Hierarchy_Name)  
```  
  
## <a name="arguments"></a>引数  
 *Hierarchy_Number*  
 階層番号を指定する有効な数値式です。  
  
 *Hierarchy_Name*  
 階層名を指定する有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 階層番号が指定されている場合、**ディメンション**関数は、キューブ内の 0 から始まる位置を階層に指定された階層数を返します。  
  
 階層名が指定されている場合、**ディメンション**関数は、指定された階層を返します。 通常、この文字列バージョンの使用、**ディメンション**ユーザー定義関数と関数。  
  
> [!NOTE]  
>  **メジャー**ディメンションは常に表される`Dimensions(0)`です。  
  
## <a name="examples"></a>使用例  
 次の例を使用して、**ディメンション**関数の名前、レベル数、および数の数値式と文字列式の両方を使用して、指定した階層のメンバーを返します。  
  
```  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Levels.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Members.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
