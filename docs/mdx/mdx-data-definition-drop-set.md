---
title: DROP SET ステートメント (MDX) |Microsoft ドキュメント
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
- SET
- DROP
- DROP SET
- DROP_SET
dev_langs:
- kbMDX
helpviewer_keywords:
- DROP SET statement
- deleting named sets
- named sets [MDX]
- removing named sets
- dropping named sets
ms.assetid: bbc37afb-af8c-41df-ba81-12771beb1c41
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: ac82ecca32cb43492dea9dc2f7cac07b81e786e9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-definition---drop-set"></a>MDX データ定義にドロップ セット
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  名前付きセットを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP [SESSION] SET   
   <Cube_Reference>.Set_Name   
               [,<Cube_Reference>.Set_Name ...n]  
  
<Cube_Reference> ::= {CURRENTCUBE | Cube_Name}  
  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブの名前を指定する有効な文字列式です。  
  
 *Set_Name*  
 削除する名前付きセットの名前を指定する有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 名前付きセットの詳細については、「[MDX での名前付きセットの作成 (MDX)](../analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
