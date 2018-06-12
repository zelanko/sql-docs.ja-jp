---
title: DROP CELL CALCULATION ステートメント (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 509717221a51ac790b92969ff052d0a8a5d0143d
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741461"
---
# <a name="mdx-data-definition---drop-cell-calculation"></a>MDX データ定義の DROP CELL CALCULATION


  指定されたセル計算を削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP [ SESSION ] CELL CALCULATION CURRENTCUBE | Cube_Name.CellCalc_Name  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブ式の名前を指定する有効な文字列式です。  
  
 *CellCalc_Name*  
 削除するセル計算の名前を指定する有効な文字列式です。  
  
## <a name="see-also"></a>参照  
 [CREATE CELL CALCULATION ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-create-cell-calculation.md)   
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
