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
ms.openlocfilehash: 41bd34fbd3d296f4aa38877e6d26e25eba9ae726
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138690"
---
# <a name="mdx-scripting---if"></a>MDX スクリプティング - IF


  条件が true の場合、ステートメントを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IF expression THEN assignment END IF  
```  
  
## <a name="arguments"></a>引数  
 *条件*  
 true または false のブール値に評価される多次元式 (MDX) 式です。  
  
 *割り当て*  
 サブキューブまたは計算されるプロパティに値を割り当てる MDX 式です。  
  
## <a name="remarks"></a>解説  
 制御フローには IF ステートメントを使用します。これは、 [IIf &#40;mdx&#41;](../mdx/iif-mdx.md)関数および[CASE ステートメント &#40;](../mdx/case-statement-mdx.md) 、値またはオブジェクトを返すためだけに使用できる mdx&#41;とは異なります。  
  
## <a name="examples"></a>例  
 次の例では、scope は Customers ディメンションの Customers Geography 階層の国レベルに制限されています。 現在のメジャーが Internet Sales Amount の場合、Internet Sales Amount は10に設定されます。  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
