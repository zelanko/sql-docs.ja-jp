---
title: この (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- THIS
dev_langs:
- kbMDX
helpviewer_keywords:
- This function [MDX]
ms.assetid: 87acddee-ae54-49ee-8923-1b760606e8b7
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 7065d192cf9b02f827753b8e0b50191d6daf30b8
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="this-mdx"></a>This (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  多次元式 (MDX) 計算スクリプト内の代入で使用するために現在のサブキューブを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
This   
```  
  
## <a name="remarks"></a>解説  
 **この**関数は、MDX 計算スクリプト内の現在のスコープ内で現在のサブキューブを指定する任意のサブキューブ式の代わりに使用できます。 **この**関数は、代入の左辺で使用する必要があります。  
  
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
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)   
 [計算](../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  
