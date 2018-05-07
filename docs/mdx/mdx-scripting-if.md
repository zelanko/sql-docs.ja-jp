---
title: IF ステートメント (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- statements [MDX], IF
ms.assetid: 8830cce5-9e06-4f89-a555-295bb0d0a8a1
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: ffe88aae91e19f0f4e55d104a323870caf4e67b7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>解説  
 異なり、制御フローは、IF ステートメントを使用して、 [IIf &#40;MDX&#41; ](../mdx/iif-mdx.md)関数および[CASE ステートメント&#40;MDX&#41; ](../mdx/case-statement-mdx.md)を戻り値またはオブジェクトにのみ使用できます。  
  
## <a name="examples"></a>使用例  
 次の例では、Customers ディメンション内の Customers Geography 階層の Country レベルにスコープを限定します。 現在のメジャーが Internet Sales Amount の場合、Internet Sales Amount が 10 に設定されます。  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
