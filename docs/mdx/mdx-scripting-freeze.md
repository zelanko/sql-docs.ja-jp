---
title: "FREEZE ステートメント (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: FREEZE
dev_langs: kbMDX
helpviewer_keywords:
- FREEZE statement
- locking cell values [MDX]
ms.assetid: 59f1e860-6f37-41af-97d6-7708bdaac933
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b447ef6b4c4699e652b6093c5d0a10e44ecb4d41
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
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
 [MDX スクリプト ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-scripting-statements-mdx.md)  
  
  
