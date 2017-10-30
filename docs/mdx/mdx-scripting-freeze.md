---
title: "FREEZE ステートメント (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FREEZE
dev_langs:
- kbMDX
helpviewer_keywords:
- FREEZE statement
- locking cell values [MDX]
ms.assetid: 59f1e860-6f37-41af-97d6-7708bdaac933
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ff9fab5df513cea71db43f5ca26f08ccae93d553
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-scripting---freeze"></a>MDX スクリプティングの固定
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたサブキューブのセル値を現在の値にロックします。 セル値をロックしておくと、他のセルに変更が加えられても、ロックしたセルには影響しません。  
  
## <a name="syntax"></a>構文  
  
```  
  
FREEZE Subcube_Expression   
```  
  
## <a name="arguments"></a>引数  
 *Subcube_Expression*  
 サブキューブを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
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
 [MDX スクリプト ステートメント & #40 です。MDX と #41 です。](../mdx/mdx-scripting-statements-mdx.md)  
  
  

