---
title: KPIStatus (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2c0824a9235aa7fd949910800d1e8ce20eab709e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63272902"
---
# <a name="kpistatus-mdx"></a>KPIStatus (MDX)


  指定された主要業績評価指標 (KPI) の [状態] 領域を表す正規化された値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
KPIStatus(KPI_Name)  
```  
  
## <a name="arguments"></a>引数  
 *KPI_Name*  
 KPI の名前を指定する有効な文字列式。  
  
## <a name="remarks"></a>コメント  
 状態値は-1 ~ 1 の正規化された値では一般にします。  
  
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
  
  
