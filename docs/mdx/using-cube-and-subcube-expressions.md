---
title: キューブ式とサブキューブ式を使用して |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0b3e6cd4a38d45f2b63fa5333526832ba31e1ce9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097189"
---
# <a name="using-cube-and-subcube-expressions"></a>キューブ式とサブキューブ式の使用


  多次元式 (MDX) ステートメントでは、キューブまたはサブキューブのデータを定義、操作、または取得するために、キューブ式やサブキューブ式を使用します。  
  
## <a name="cube-expressions"></a>キューブ式  
 キューブ式は、キューブ識別子または CURRENTCUBE キーワードのいずれかが含まれていて、単純な式にしかできません。 多くの MDX ステートメントでは、キューブ識別子を要求する代わりに、現在のキューブ コンテキストを識別するために CURRENTCUBE キーワードを使用します。  
  
 キューブ識別子*Cube_Name*の MDX ステートメントの BNF 表記の説明。  
  
 キューブ式は、複数の場所で表示されます。 MDX の SELECT ステートメントでは、キューブ式は、データの取得元のキューブを指定します。 次のクエリ例では、式 [Adventure Works] は、その名前のキューブを参照します。  
  
 `SELECT [Measures].[Internet Sales Amount] ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 CREATE MEMBER ステートメントでは、キューブ式は、作成中の計算されるメンバーが表示されるキューブを指定します。 次の例では、ステートメントには、Adventure Works キューブのメジャー ディメンションに、計算されるメジャーが作成されます。  
  
 `CREATE MEMBER [Adventure Works].[Measures].[Test] AS 1`  
  
 Followingexamp で示すように、計算されるメンバーが作成されるキューブが MDX スクリプトが属する同じキューブをする必要がありますので、キューブの名前を CURRENTCUBE キーワードに置き換えることが MDX スクリプト内の CREATE MEMBER ステートメントを使用する場合le:  
  
 `CREATE MEMBER CURRENTCUBE.[Measures].[Test] AS 1;`  
  
 これを行う簡単にコピーして、キューブの名前が不要になったハード コーディングされたために、1 つのキューブから別の計算されるメンバーの定義を貼り付けます。  
  
## <a name="subcube-expressions"></a>サブキューブ式  
 サブキューブ式には、サブキューブ識別子、またはサブキューブを返す MDX ステートメントを含めることができます。 サブキューブ式にサブキューブ識別子が含まれている場合、単純な式がなります。 サブキューブを返す MDX ステートメントがある場合は、複雑なステートメント。 たとえば、次の例に示すように、MDX の SELECT ステートメントは、サブキューブを返すので、サブキューブ式が許可されている場所で使用できます。  
  
 `SELECT [Measures].MEMBERS ON COLUMNS,`  
  
 `[Date].[Calendar Year].MEMBERS ON ROWS`  
  
 `FROM`  
  
 `(SELECT [Measures].[Internet Sales Amount] ON COLUMNS,`  
  
 `[Date].[Calendar Year].&[2004] ON ROWS`  
  
 `FROM [Adventure Works])`  
  
 この FROM 句で SELECT ステートメントの使用は、サブセレクトとも呼ばれます。  
  
 サブキューブ式が発生したもう 1 つの一般的なシナリオでは、MDX スクリプトでスコープ割り当てを行う場合です。 次の例では、スコープ ステートメントを使用して、[Measures] で構成されるサブキューブに割り当てを制限します。[Internet Sales Amount]:  
  
 `SCOPE([Measures].[Internet Sales Amount]);`  
  
 `This=1;`  
  
 `END SCOPE;`  
  
 サブキューブ識別子*Subcube_Name*します。 MDX ステートメントの BNF 表記の説明。  
  
## <a name="see-also"></a>関連項目  
 [MDX の基本的なクエリ &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-query-the-basic-query.md)   
 [MDX でのサブキューブの構築&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/building-subcubes-in-mdx-mdx.md)   
 [CREATE SUBCUBE ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-create-subcube.md)   
 [式&#40;MDX&#41;](../mdx/expressions-mdx.md)   
 [SCOPE ステートメント &#40;MDX&#41;](../mdx/mdx-scripting-scope.md)  
  
  
