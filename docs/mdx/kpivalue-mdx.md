---
title: KPIValue (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: baa1b95e9eda32bc20e08b61ddd38c130a373050
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740401"
---
# <a name="kpivalue-mdx"></a>KPIValue (MDX)


  指定された主要業績評価指標 (KPI) の値を計算するメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
KPIValue(KPI_Name)  
```  
  
## <a name="arguments"></a>引数  
 *Kpi 名*  
 KPI の名前を指定する有効な文字列式です。  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
 次の例では、Fiscal Year 属性階層の 3 つのメンバーの子孫について、Channel Revenue メジャーの KPI の値、KPI の目標、KPI の状態、および KPI の傾向を返しています。  
  
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
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
