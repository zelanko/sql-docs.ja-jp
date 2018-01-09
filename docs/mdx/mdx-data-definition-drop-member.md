---
title: "DROP MEMBER ステートメント (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP
- Member
- DROP_MEMBER
- DROP MEMBER
dev_langs: kbMDX
helpviewer_keywords:
- deleting calculated members
- calculated members [MDX]
- DROP MEMBER statement
- dropping calculated members
- removing calculated members
ms.assetid: e9819976-a9ec-4c48-b0b5-3f6938e200f5
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: d4881eb548f1d5ccc034522e7446856ccad08d24
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-definition---drop-member"></a>MDX データ定義にドロップ メンバー
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  計算されるメンバーを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP MEMBER   
   CURRENTCUBE | Cube_Name  
      .Member_Name   
               [,CURRENTCUBE | Cube_Name.Member_Name ...n]  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブ名を提供する有効な文字列式です。  
  
 *Member_Identifier*  
 メンバー名またはメンバー キーを指定する有効な文字列式です。  
  
## <a name="see-also"></a>参照  
 [MEMBER ステートメント &#40; を作成します。MDX と #41 です。](../mdx/mdx-data-definition-create-member.md)   
 [MDX データ定義ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
