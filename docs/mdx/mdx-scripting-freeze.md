---
title: FREEZE ステートメント (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9b7eb3a3939ce8525dc57d27a24ac005ecb2cf2d
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579904"
---
# <a name="mdx-scripting---freeze"></a>MDX スクリプティングの固定
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたサブキューブのセル値を現在の値にロックします。 セル値をロックしておくと、他のセルに変更が加えられても、ロックしたセルには影響しません。  
  
## <a name="syntax"></a>構文  
  
```  
  
FREEZE Subcube_Expression   
```  
  
## <a name="arguments"></a>引数  
 *Subcube_Expression*  
 サブキューブを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **凍結**ステートメントで指定されているサブキューブのセルの値をロック、MDX での後続のステートメントをによる後続の計算で値が変更からスクリプト パスです。  
  
 以下の例では、A と B は MDX 計算スクリプト内のサブキューブを表しています。  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 この時点では、A も B も 3 に等しくなっています。  
  
 挿入ようになりました、**凍結**して A サブキューブ内のセルをロックする関数。  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 A は 2 に、B は 3 に等しくなりました。  
  
## <a name="see-also"></a>参照  
 [MDX スクリプト ステートメント&#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
