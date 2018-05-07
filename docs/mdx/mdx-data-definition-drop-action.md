---
title: DROP ACTION ステートメント (MDX) |Microsoft ドキュメント
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
f1_keywords:
- DROP
- DROP ACTION
- Action
- DROP_ACTION
dev_langs:
- kbMDX
helpviewer_keywords:
- DROP ACTION statement
- deleting actions
- removing actions
- actions [MDX]
- dropping actions
ms.assetid: 74b3cfee-dea8-4968-a54c-1754d52ee1bd
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: f91406c2af7698067ca31760d6a3984ee1246225
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-definition---drop-action"></a>MDX データ定義の削除アクション
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたキューブから指定されたアクションを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP ACTION CURRENTCUBE | Cube_Name  
   .Action_Name   
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブ名を提供する有効な文字列式です。  
  
 *Action_Name*  
 削除するアクションの名前を指定する有効な文字列式です。  
  
## <a name="see-also"></a>参照  
 [CREATE ACTION ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-create-action.md)   
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
