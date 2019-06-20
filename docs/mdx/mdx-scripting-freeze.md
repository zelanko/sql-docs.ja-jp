---
title: FREEZE ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cd652a9f308bd7a564a61d165f9c47875a900737
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63187569"
---
# <a name="mdx-scripting---freeze"></a>MDX スクリプティング - FREEZE


  現在の値を指定されたサブキューブのセルの値をロックします。 セルの値がロックされると、他のセルへの変更なしに影響を与えるロックされたセル。  
  
## <a name="syntax"></a>構文  
  
```  
  
FREEZE Subcube_Expression   
```  
  
## <a name="arguments"></a>引数  
 *Subcube_Expression*  
 サブキューブを返す有効な多次元式 (MDX) 式。  
  
## <a name="remarks"></a>コメント  
 **固定**ステートメントが指定されているサブキューブのセルの値をロック、MDX での後続のステートメントをによる後続の計算で値が変更からスクリプトのパスします。  
  
 次の例では、A と B は MDX 計算スクリプトでのサブキューブを表します。  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 この時点では、どちらも A および B は 3 と等しい。  
  
 挿入ようになりました、**固定**して A サブキューブ内のセルをロックする関数。  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 A は 2 に、B は 3 に等しくなりました。  
  
## <a name="see-also"></a>関連項目  
 [MDX スクリプト ステートメント &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
