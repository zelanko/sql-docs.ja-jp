---
title: "抽出 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: EXTRACT
dev_langs: kbMDX
helpviewer_keywords: Extract function
ms.assetid: c0d27d31-e36e-4b7f-bb86-1e4707351392
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 4a92701862d0cfcf3881c493c7e062c73fbd9aa6
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="extract-mdx"></a>Extract (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  抽出された階層要素から組のセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Extract(Set_Expression, Hierarchy_Expression1 [,Hierarchy_Expression2, ...n] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Hierarchy_Expression1*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
 *Hierarchy_Expression2*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>Remarks  
 **抽出**関数、抽出された階層要素から組で構成されるセットを返します。 指定したセット内の組ごとに、指定した階層のメンバーが結果セット内の新しい組に抽出されます。 この関数は、重複する組を常に削除します。  
  
 **抽出**関数は逆の操作を実行する、 [Crossjoin](../mdx/crossjoin-mdx.md)関数。  
  
## <a name="examples"></a>使用例  
 次のクエリを使用する方法を示しています、**抽出**関数によって返される組のセットに対して、 **NonEmpty**関数。  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `//Returns the distinct combinations of Customer and Date for all purchases`  
  
 `//of Bike Racks or Bike Stands`  
  
 `EXTRACT(`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `*`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `*`  
  
 `{[Product].[Product Categories].[Subcategory].&[26],[Product].[Product Categories].[Subcategory].&[27]}`  
  
 `*`  
  
 `{[Measures].[Internet Sales Amount]}`  
  
 `)`  
  
 `,  [Customer].[Customer], [Date].[Date])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
