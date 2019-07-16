---
title: DROP SET ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 201072b1b0e371e1f22ee9e32b009ebcea47b2b2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038170"
---
# <a name="mdx-data-definition---drop-set"></a>MDX データ操作 - DROP SET


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
 キューブの名前を指定する有効な文字列式を指定します。  
  
 *Set_Name*  
 削除する名前付きセットの名前を提供する有効な文字列式。  
  
## <a name="remarks"></a>コメント  
 名前付きセットの詳細については、「[MDX での名前付きセットの作成 &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
