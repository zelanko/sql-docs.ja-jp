---
title: KPIStatus (MDX) |Microsoft ドキュメント
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
dev_langs:
- kbMDX
helpviewer_keywords:
- KPIStatus function
ms.assetid: c563f3a9-5dd7-4586-9519-16a3ca58e2ec
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 2f00db6e9abf09d6ed4d02036fff11b23f9d7c42
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="kpistatus-mdx"></a>KPIStatus (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定された主要業績評価指標 (KPI) の状態を表す、正規化された値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
KPIStatus(KPI_Name)  
```  
  
## <a name="arguments"></a>引数  
 *Kpi 名*  
 KPI の名前を指定する有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 状態値は、通常、-1 ～ 1 の範囲に正規化されます。  
  
## <a name="example"></a>例  
 次の例では、Fiscal Year 属性階層の 3 つのメンバーの子孫について、Channel Revenue メジャーに対応する KPI 値、KPI 目標、KPI 状態、および KPI 傾向を返しています。  
  
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
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
