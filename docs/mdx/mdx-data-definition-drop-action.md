---
title: DROP ACTION ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f47eaad9a13966abd1d08b0121fdd9c0a64a7438
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63285060"
---
# <a name="mdx-data-definition---drop-action"></a>MDX データ操作 - DROP ACTION


  指定されたキューブから、指定したアクションを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP ACTION CURRENTCUBE | Cube_Name  
   .Action_Name   
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 キューブ名を提供する有効な文字列式。  
  
 *Action_Name*  
 削除するアクションの名前を指定する有効な文字列式です。  
  
## <a name="see-also"></a>参照  
 [CREATE ACTION ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-create-action.md)   
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
