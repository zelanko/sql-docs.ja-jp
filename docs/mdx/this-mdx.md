---
title: この (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 77db403ee016283a565a6bc86d2f6857de0eff45
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63259029"
---
# <a name="this-mdx"></a>This (MDX)


  多次元式 (MDX) 計算スクリプトでは、割り当てで使用するため、現在のサブキューブを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
This   
```  
  
## <a name="remarks"></a>コメント  
 **この**MDX 計算スクリプト内の現在のスコープ内で現在のサブキューブを提供する任意のサブキューブ式の代わりに関数を使用できます。 **この**を代入式の左側にある関数を使用する必要があります。  
  
## <a name="examples"></a>使用例  
 次の MDX スクリプトでは、This キーワードを SCOPE ステートメントと共に使用してサブキューブに代入する方法を示します。  
  
 `Scope`  
  
 `(`  
  
 `[Date].[Fiscal Year].&[2005],`  
  
 `[Date].[Fiscal].[Fiscal Quarter].Members,`  
  
 `[Measures].[Sales Amount Quota]`  
  
 `) ;`  
  
 `This = ParallelPeriod`  
  
 `(`  
  
 `[Date].[Fiscal].[Fiscal Year], 1,`  
  
 `[Date].[Fiscal].CurrentMember`  
  
 `) * 1.35 ;`  
  
 `/*-- Allocate equally to months in FY 2002 -----------------------------*/`  
  
 `Scope`  
  
 `(`  
  
 `[Date].[Fiscal Year].&[2002],`  
  
 `[Date].[Fiscal].[Month].Members`  
  
 `) ;`  
  
 `This = [Date].[Fiscal].CurrentMember.Parent / 3 ;`  
  
 `End Scope ;`  
  
 `End Scope;`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [計算](../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  
