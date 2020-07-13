---
title: DROP MEMBER ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4e8e38a3ff3f40f44c911a277f99ab9b629c7c87
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68038194"
---
# <a name="mdx-data-definition---drop-member"></a>MDX データ操作 - DROP MEMBER


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
 メンバー名またはメンバーキーを提供する有効な文字列式です。  
  
## <a name="see-also"></a>参照  
 [CREATE MEMBER ステートメント &#40;MDX&#41;](../mdx/mdx-data-definition-create-member.md)   
 [Mdx&#41;&#40;mdx データ定義ステートメント](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
