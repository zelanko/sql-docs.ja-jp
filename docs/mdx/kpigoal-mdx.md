---
title: KPIGoal (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c6b85136e5fde72635f5691b5172232e7d601a24
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63272824"
---
# <a name="kpigoal-mdx"></a>KPIGoal (MDX)


  指定された主要業績評価指標 (KPI) の部分では目標値を計算するメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
KPIGoal(KPI_Name)  
```  
  
## <a name="arguments"></a>引数  
 *KPI_Name*  
 KPI の名前を指定する有効な文字列式。  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
 次の例では、KPI の値、KPI 目標、KPI の状態、および、Fiscal Year 属性階層の 3 つのメンバーの子孫に対する、channel revenue メジャーの KPI の傾向を返します。  
  
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
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
