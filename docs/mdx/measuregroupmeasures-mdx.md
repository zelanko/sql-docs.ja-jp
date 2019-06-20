---
title: MeasureGroupMeasures (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 55e00420ad3f941d50d9179dcd4a87d678cc28a0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63267942"
---
# <a name="measuregroupmeasures-mdx"></a>MeasureGroupMeasures (MDX)


  指定されたメジャー グループに属しているメジャーのセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
MEASUREGROUPMEASURES(MeasureGroupName)  
```  
  
## <a name="arguments"></a>引数  
 *MeasureGroupName*  
 メジャーのセットの取得元となるメジャー グループの名前が格納されている有効な文字列式です。  
  
## <a name="remarks"></a>コメント  
 指定する文字列は、メジャー グループの名前と正確に一致する必要があります。 スペースを含むメジャー グループ名を角かっこで囲む必要はありません。  
  
## <a name="example"></a>例  
 次の例では、Adventure Works キューブ内の Internet Sales メジャー グループ内のすべてのメジャーを返します。  
  
```  
SELECT MeasureGroupMeasures('Internet Sales') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
