---
title: "DROP SET ステートメント (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e4138e926a72af94389df15c924cf6bbcfb6e8e1
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-definition---drop-set"></a>MDX データ定義にドロップ セット
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [MDX データ定義ステートメント & #40 です。MDX と #41 です。](../mdx/mdx-data-definition-statements-mdx.md)  
  
  

