---
title: (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f818731fdc2d7b7b6ee6b000fd4e85b150c9f92c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68105244"
---
# <a name="kpigoal-mdx"></a>KPIGoal (MDX)


  指定された主要業績評価指標 (KPI) の目標部分の値を計算するメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
KPIGoal(KPI_Name)  
```  
  
## <a name="arguments"></a>引数  
 *KPI_Name*  
 KPI の名前を指定する有効な文字列式です。  
  
## <a name="remarks"></a>解説  
  
## <a name="example"></a>例  
 次の例では、会計年度の属性階層の3つのメンバーの子孫について、チャネル収益メジャーの KPI 値、KPI 目標、KPI の状態、および KPI の傾向を返します。  
  
```  
SELECT  
   { KPIValue("Channel Revenue"),   
     KPIGoal("Channel Revenue"),  
     KPIStatus("Channel Revenue"),   
     KPITrend("Channel Revenue")  
   } ON Columns,  
Descendants  
   ( { [Date].[Fiscal].[Fiscal Year].&[2002],  
       [Date].[Fiscal].[Fiscal Year].&[2003],  
       [Date].[Fiscal].[Fiscal Year].&[2004]   
     }, [Date].[Fiscal].[Fiscal Quarter]  
   ) ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
