---
title: "および (MDX) |Microsoft ドキュメント"
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
- AND
dev_langs:
- kbMDX
helpviewer_keywords:
- AND, MDX
ms.assetid: 398fd483-d010-4524-b115-0becad66f25c
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e905bdd62e876240d0178dc337ed61665ac2699f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="and-mdx"></a>AND (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  2 つの数値式の論理積演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Expression1 AND Expression2  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Expression1*  
 数値を返す有効な多次元式 (MDX) 式です。  
  
 *Expression2*  
 数値を返す有効な MDX 式です。  
  
## <a name="return-value"></a>戻り値  
 両方のパラメーターを評価する場合に true を返すブール値**true**、それ以外の**false**です。  
  
## <a name="remarks"></a>解説  
 **AND**演算子はブール値として両方の式を処理 (つまり、0 として**false**、それ以外の**true**) 論理積の演算を実行する前にします。 次の表に示しますが、どのように**AND**論理積演算を実行します。  
  
|*Expression1*|*Expression2*|戻り値|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**true**|  
|**true**|**false**|**false**|  
|**false**|**true**|**false**|  
|**false**|**false**|**false**|  
  
## <a name="example"></a>例  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for clothing sales where the GPM is between 20% and 30%.  
With Member [Measures].[LowGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] <= .3 AND   
      [Measures].[Gross Profit Margin] >= .2,  
      [Measures].[Gross Profit Margin],  
      null)  
SELECT NON EMPTY  
    [Sales Territory].[Sales Territory Country].Members ON 0,  
    [Product].[Category].[Clothing] ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[LowGPM])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)  
  
  

