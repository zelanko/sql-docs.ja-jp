---
description: UnknownMember (MDX)
title: UnknownMember (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0489556836b943ba91d4e17b3a164aeca0c648d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341148"
---
# <a name="unknownmember-mdx"></a>UnknownMember (MDX)


  レベルまたはメンバーに関連付けられている不明なメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member expression syntax  
Member_Expression.UnknownMember  
  
Hierarchy_expression syntax  
Hierarchy_Expression.UnknownMember  
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 Analysis Services は、階層が不明な場合に、ファクトテーブルデータを階層に関連付けるための不明なメンバーを作成します。 不明なメンバーは、次のいずれかのレベルにすることができます。  
  
-   集計されない属性階層の場合、最上位レベル。  
  
-   自然階層の **すべて** のレベルの最初のレベル。  
  
-   不自然階層の場合、任意のレベル。  
  
 メンバー式が指定されている場合、 **UnknownMember** 関数は、指定されたメンバーの不明なメンバーの子を返します。 指定されたメンバーが存在しない場合、関数は NULL を返します。  
  
 階層式が指定されている場合、 **UnknownMember** 関数は、最上位レベルに不明なメンバーが存在する場合は、そのメンバーを返します。  
  
 レベルまたはメンバーに不明なメンバーが存在しない場合、 **UnknownMember** 関数は null メンバーを作成します。  
  
> [!NOTE]  
>  その階層またはメンバーに不明なメンバーが存在しない場合、エラーが生成されます。  
  
## <a name="examples"></a>例  
 次の例では、Measures ディメンションのすべてのメンバーについて、Product 属性階層の All Products メンバーの不明なメンバーを返します。  
  
```  
SELECT [Product].[Product].[All Products].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
 次の例では、Measures ディメンションのすべてのメンバーについて、Product Categories 階層の不明なメンバーを返します。  
  
```  
SELECT [Product].[Product Categories].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
