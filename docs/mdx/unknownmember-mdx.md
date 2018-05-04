---
title: UnknownMember (MDX) |Microsoft ドキュメント
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
- UnknownMember
dev_langs:
- kbMDX
helpviewer_keywords:
- UnknownMember function
ms.assetid: 5ae39cbe-65c8-4a59-9548-71b28ecf6eb5
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 7fe0fe0706d6b88c19f5683a71de15516dddecec
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="unknownmember-mdx"></a>UnknownMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  レベルまたはメンバーに関連付けられている不明なメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member expression syntax  
Member_Expression.UnknownMember  
  
Hierarchy_expression syntax  
Hierarchy_Expression.UnknownMember  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 階層が不明の場合に、階層を持つファクト テーブルのデータを関連付けるには、不明なメンバーを作成します。 不明なメンバーは以下のレベルのいずれかにあります。  
  
-   集計されない属性階層の場合、最上位レベル。  
  
-   下のレベルで、**すべて**自然階層のレベルです。  
  
-   不自然階層の場合、任意のレベル。  
  
 メンバー式が指定されている場合、 **UnknownMember**関数は、指定されたメンバーの不明なメンバーの子を返します。 指定されたメンバーが存在しない場合、関数は NULL を返します。  
  
 階層式が指定されている場合、 **UnknownMember**関数が存在する場合、最上位レベルに不明なメンバーを返します。  
  
 レベルまたはメンバーに不明なメンバーが存在しない場合、 **UnknownMember**関数 null のメンバーを作成します。  
  
> [!NOTE]  
>  その階層またはメンバーに不明なメンバーが存在しない場合、エラーが生成されます。  
  
## <a name="examples"></a>使用例  
 次の例では、メジャー ディメンションのすべてのメンバーを対象に、Product 属性階層の All Products メンバーの不明なメンバーを返しています。  
  
```  
SELECT [Product].[Product].[All Products].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
 次の例では、メジャー ディメンションのすべてのメンバーを対象に、Product Categories 階層の不明なメンバーを返しています。  
  
```  
SELECT [Product].[Product Categories].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
