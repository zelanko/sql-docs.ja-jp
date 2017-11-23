---
title: "されません (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: NOT
dev_langs: kbMDX
helpviewer_keywords: NOT operator [MDX]
ms.assetid: c11bd3b0-54b3-4a6d-babc-6067722194db
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 513dcff2862aa024684702017b9281b6163fcf5f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="not-mdx"></a>NOT (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  1 つの数値式の論理否定を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Expression1*  
 数値を返す有効な多次元式 (MDX) 式です。  
  
## <a name="return-value"></a>戻り値  
 ブール値を返す**false**に引数が評価された場合**true**、それ以外の**true**です。  
  
## <a name="remarks"></a>解説  
 **いない**演算子はブール値として式を処理 (つまり、0 として**false**、それ以外の**true**) 論理否定演算を実行する前にします。 次の表に示す方法、**いない**演算子が論理否定演算を実行します。  
  
|*Expression1*|戻り値|  
|-------------------|------------------|  
|**true**|**オプション**|  
|**オプション**|**true**|  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)  
  
  
