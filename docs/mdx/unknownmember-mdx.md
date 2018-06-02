---
title: UnknownMember (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b74454c00f48a36b963e6c7f5b7b1bdf4e2ea44e
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582214"
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
  
## <a name="remarks"></a>コメント  
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
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
