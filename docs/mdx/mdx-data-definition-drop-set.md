---
description: MDX データ操作 - DROP SET
title: DROP SET ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0992df0c7180c8a572fb1f8c34b99059ab118ea4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387238"
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
 キューブの名前を指定する有効な文字列式です。  
  
 *Set_Name*  
 削除する名前付きセットの名前を提供する有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 名前付きセットの詳細については、「[MDX での名前付きセットの作成 &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [Mdx&#41;&#40;mdx データ定義ステートメント ](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
