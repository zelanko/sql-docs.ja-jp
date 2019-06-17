---
title: IF ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4975c455b942f053287b344a956a0083c8ca4e1a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63187506"
---
# <a name="mdx-scripting---if"></a>MDX スクリプティング - IF


  条件が true の場合は、ステートメントを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IF expression THEN assignment END IF  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 true または false のブール値に評価される多次元式 (MDX) 式です。  
  
 *assignment*  
 サブキューブまたは計算されるプロパティに値を割り当てる MDX 式です。  
  
## <a name="remarks"></a>コメント  
 異なり、制御フローは、IF ステートメントを使用して、 [IIf &#40;MDX&#41; ](../mdx/iif-mdx.md)関数と[CASE ステートメント&#40;MDX&#41; ](../mdx/case-statement-mdx.md)を値またはオブジェクトを返すにのみ使用できます。  
  
## <a name="examples"></a>使用例  
 次の例では、スコープは、Customers ディメンション内の Customers Geography 階層の Country レベルに限定されます。 現在のメジャーが Internet Sales Amount の場合は、Internet Sales Amount が 10 に設定されています。  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
