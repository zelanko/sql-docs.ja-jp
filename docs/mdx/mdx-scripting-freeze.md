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
ms.openlocfilehash: 4738dab411fe55808034a6d9d81a16994089ea74
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138288"
---
# <a name="mdx-scripting---freeze"></a>MDX スクリプティング - FREEZE


  指定したサブキューブのセル値を現在の値にロックします。 セル値がロックされている場合、他のセルに対する変更は、ロックされているセルには影響しません。  
  
## <a name="syntax"></a>構文  
  
```  
  
FREEZE Subcube_Expression   
```  
  
## <a name="arguments"></a>引数  
 *Subcube_Expression*  
 サブキューブを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **FREEZE**ステートメントは、指定されたサブキューブ内のセルの値をロックします。これにより、MDX スクリプト内の後続のステートメントは、後続の計算パスで値を変更できなくなります。  
  
 次の例では、A と B は MDX 計算スクリプト内のサブキューブを表します。  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 この時点で、A と B はどちらも3と等しくなります。  
  
 ここで、サブキューブ内のセルをロックする**Freeze**関数を挿入します。  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 A は 2 に、B は 3 に等しくなりました。  
  
## <a name="see-also"></a>参照  
 [Mdx&#41;&#40;MDX スクリプトステートメント](../mdx/mdx-scripting-statements-mdx.md)  
  
  
