---
title: "MeasureGroupMeasures (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- MeasureGroupMeasures function
ms.assetid: 69d9b205-1ca7-4741-9ca9-c7926bc87ead
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 17f8ba22b30fbfe925ae219a9f13bbdc5a9f1be0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="measuregroupmeasures-mdx"></a>MeasureGroupMeasures (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたメジャー グループに属するメジャーのセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
MEASUREGROUPMEASURES(MeasureGroupName)  
```  
  
## <a name="arguments"></a>引数  
 *MeasureGroupName*  
 メジャーのセットの取得元となるメジャー グループの名前が格納されている有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 指定する文字列は、メジャー グループの名前と正確に一致する必要があります。 スペースを含むメジャー グループ名を角かっこで囲む必要はありません。  
  
## <a name="example"></a>例  
 次の例では、Adventure Works キューブの Internet Sales メジャー グループ内のメジャーがすべて返されます。  
  
```  
SELECT MeasureGroupMeasures('Internet Sales') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

