---
title: "キューブ式とサブキューブ式を使用して |Microsoft ドキュメント"
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
dev_langs: kbMDX
helpviewer_keywords:
- subcubes [MDX]
- cubes [Analysis Services], MDX
- CURRENTCUBE keyword
- expressions [MDX], subcubes
- expressions [MDX], cubes
ms.assetid: 95ae034d-8f88-4820-91c6-205ec424e119
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: cb1766ed1c16901bec84f735ecc2357939a65a11
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="using-cube-and-subcube-expressions"></a>キューブ式とサブキューブ式の使用
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  多次元式 (MDX) ステートメントでは、キューブまたはサブキューブのデータを定義、操作、または取得するために、キューブ式やサブキューブ式を使用します。  
  
## <a name="cube-expressions"></a>キューブ式  
 キューブ式には、キューブ識別子または CURRENTCUBE キーワードが含まれているため、単純式のみを指定できます。 多くの MDX ステートメントでは、キューブ識別子を使用する代わりに、現在のキューブ コンテキストを識別するために CURRENTCUBE キーワードを使用します。  
  
 キューブ識別子は*Cube_Name* MDX ステートメントの説明については BNF 表記でします。  
  
 キューブ式は複数の場所で使用できます。 MDX の SELECT ステートメントでは、キューブ式は、データの取得元のキューブを指定します。 次のクエリの例では、式 [Adventure Works] はその名前のキューブを参照しています。  
  
 `SELECT [Measures].[Internet Sales Amount] ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 CREATE MEMBER ステートメントでは、キューブ式は、作成中の計算されるメンバーが表示されるキューブを指定します。 次の例のステートメントでは、Adventure Works キューブの Measures ディメンションに、計算されるメジャーを作成します。  
  
 `CREATE MEMBER [Adventure Works].[Measures].[Test] AS 1`  
  
 MDX スクリプト内で CREATE MEMBER ステートメントを使用する場合は、キューブの名前を CURRENTCUBE キーワードに置き換えることができます。これは、計算されるメンバーが作成されるキューブが、MDX スクリプトが属するキューブと常に同じになるためです。次に例を示します。  
  
 `CREATE MEMBER CURRENTCUBE.[Measures].[Test] AS 1;`  
  
 これにより、キューブの名前がハードコーディングされなくなるため、計算されるメンバーの定義をキューブ間で簡単にコピーして貼り付けることができるようになります。  
  
## <a name="subcube-expressions"></a>サブキューブ式  
 サブキューブ式には、サブキューブ識別子、またはサブキューブを返す MDX ステートメントを含めることができます。 サブキューブ式にサブキューブ識別子が含まれている場合、これは単純式になります。 サブキューブを返す MDX ステートメントが含まれている場合は、複合ステートメントになります。 たとえば、次の例に示すように、MDX の SELECT ステートメントは、サブキューブを返すので、サブキューブ式が許可されている場所で使用できます。  
  
 `SELECT [Measures].MEMBERS ON COLUMNS,`  
  
 `[Date].[Calendar Year].MEMBERS ON ROWS`  
  
 `FROM`  
  
 `(SELECT [Measures].[Internet Sales Amount] ON COLUMNS,`  
  
 `[Date].[Calendar Year].&[2004] ON ROWS`  
  
 `FROM [Adventure Works])`  
  
 このように FROM 句内で使用する SELECT ステートメントは、サブセレクトとも呼ばれます。  
  
 サブキューブ式が使用される別の一般的なシナリオとして、MDX スクリプトで、スコープを指定した割り当てを実行する場合があります。 次の例では、SCOPE ステートメントを使用して、[Measures].[Internet Sales Amount] で構成されるサブキューブに割り当てを制限します。  
  
 `SCOPE([Measures].[Internet Sales Amount]);`  
  
 `This=1;`  
  
 `END SCOPE;`  
  
 サブキューブ識別子は*Subcube_Name*です。 形式で表されます。  
  
## <a name="see-also"></a>参照  
 [MDX の基本的なクエリ &#40;です。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-query-the-basic-query.md)   
 [MDX &#40; でのサブキューブの作成MDX と #41 です。](../analysis-services/multidimensional-models/mdx/building-subcubes-in-mdx-mdx.md)   
 [SUBCUBE ステートメント &#40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-subcube.md)   
 [式 &#40;です。MDX と #41 です。](../mdx/expressions-mdx.md)   
 [SCOPE ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-scripting-scope.md)  
  
  
