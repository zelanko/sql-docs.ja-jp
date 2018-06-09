---
title: CLEAR CALCULATIONS ステートメント (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cdc4b2d3e948f0123eb15e38a6140e63009907bc
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742391"
---
# <a name="mdx-data-manipulation---clear-calculations"></a>MDX データ操作 - CLEAR CALCULATIONS 


  キューブからすべての計算を削除して、キューブの計算パスを 0 に戻します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CLEAR CALCULATIONS [FROMCube_Expression]  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Expression*  
 有効な多次元式 (MDX) キューブ式です。  
  
## <a name="remarks"></a>コメント  
 **FROM**キューブのコンテキストが MDX スクリプトなど、既知の場合、句を省略できます。  
  
> [!NOTE]  
>  このステートメントは、サーバー管理者やデータベース管理者、またはキューブのソース データにアクセスできるロールのメンバー (つまり、ReadSourceData=true) のみが実行できます。  
  
## <a name="see-also"></a>参照  
 [MDX データ操作ステートメント&#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
