---
title: IF ステートメント (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e7426c609de80ab249cd71e4364979ff07165598
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579864"
---
# <a name="mdx-scripting---if"></a>MDX スクリプトの場合
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  条件が満たされる場合、ステートメントを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IF expression THEN assignment END IF  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 true または false のブール値に評価される多次元式 (MDX) 式です。  
  
 *割り当て*  
 サブキューブまたは計算されるプロパティに値を割り当てる MDX 式です。  
  
## <a name="remarks"></a>コメント  
 異なり、制御フローは、IF ステートメントを使用して、 [IIf &#40;MDX&#41; ](../mdx/iif-mdx.md)関数および[CASE ステートメント&#40;MDX&#41; ](../mdx/case-statement-mdx.md)を戻り値またはオブジェクトにのみ使用できます。  
  
## <a name="examples"></a>使用例  
 次の例では、Customers ディメンション内の Customers Geography 階層の Country レベルにスコープを限定します。 現在のメジャーが Internet Sales Amount の場合、Internet Sales Amount が 10 に設定されます。  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
