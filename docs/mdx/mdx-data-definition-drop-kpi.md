---
title: DROP KPI ステートメント (MDX) |Microsoft ドキュメント
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
- KPI
- DROP
- DROP KPI
- DROP_KPI
helpviewer_keywords:
- DROP KPI statement
- key performance indicators [MDX]
ms.assetid: d19c6809-b8a6-459d-8554-b41854f7cc45
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: e6e885e486033b0234841523b8193f37fe2e7563
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-definition---drop-kpi"></a>MDX データ定義、DROP KPI
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたキューブから、指定された主要業績評価指標 (KPI) を削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP KPI CURRENTCUBE | Cube_Name.KPI_Name   
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブ名を指定する有効な文字列です。  
  
 *Kpi 名*  
 削除する KPI の名前を指定する有効な文字列です。  
  
## <a name="see-also"></a>参照  
 [CREATE KPI ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-create-kpi.md)   
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
