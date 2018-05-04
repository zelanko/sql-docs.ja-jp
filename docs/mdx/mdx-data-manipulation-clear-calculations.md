---
title: CLEAR CALCULATIONS ステートメント (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CLEAR CALCULATIONS
- clalculations
- clear
dev_langs:
- kbMDX
helpviewer_keywords:
- clearing calculations
- CLEAR CALCULATIONS statement
- deleting calculations
- removing calculations
- calculations [Analysis Services], clearing
- cubes [Analysis Services], calculations
ms.assetid: aebec9a1-1d1d-4697-aa3f-cc2449625603
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 84cfc46ea64b0d4fb1dd79532bc6bdba9af71ded
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-manipulation---clear-calculations"></a>CLEAR CALCULATIONS の MDX データ操作
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  キューブからすべての計算を削除して、キューブの計算パスを 0 に戻します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CLEAR CALCULATIONS [FROMCube_Expression]  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Expression*  
 有効な多次元式 (MDX) キューブ式です。  
  
## <a name="remarks"></a>解説  
 **FROM**キューブのコンテキストが MDX スクリプトなど、既知の場合、句を省略できます。  
  
> [!NOTE]  
>  このステートメントは、サーバー管理者やデータベース管理者、またはキューブのソース データにアクセスできるロールのメンバー (つまり、ReadSourceData=true) のみが実行できます。  
  
## <a name="see-also"></a>参照  
 [MDX データ操作ステートメント&#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
