---
title: TimeBinding データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- TimeBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TimeBinding
helpviewer_keywords:
- TimeBinding data type
ms.assetid: f3c06978-c181-4a73-9b57-8fc30358faab
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d5d8b1ea5b0b7350fdba80d5ea99b7f3c0cc9ee1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095582"
---
# <a name="timebinding-data-type-assl"></a>TimeBinding データ型 (ASSL)
  期間へのバインドを表す派生データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<TimeBinding>  
   <!-- The following elements extend Binding -->  
      <CalendarStartDate>...</CalendarStartDate>  
      <CalendarEndDate>...</CalendarEndDate>  
      <FirstDayOfWeek>...</FirstDayOfWeek>  
   <CalendarLanguage>...</CalendarLanguage>  
   <FiscalFirstMonth>...</FiscalFirstMonth>  
   <FiscalFirstDayOfMonth>...</FiscalFirstDayOfMonth>  
   <FiscalYearName>...</FiscalYearName>  
   <ReportingFirstMonth>...</ReportingFirstMonth>  
   <ReportingFirstWeekOfMonth>...</ReportingFirstWeekOfMonth>  
   <ReportingWeekToMonthPattern>...</ReportingWeekToMonthPattern>  
   <ManufacturingFirstMonth>...</ManufacturingFirstMonth>  
   <ManufacturingFirstWeekOfMonth>...</ManufacturingFirstWeekOfMonth>  
   <ManufacturingExtraMonthQuarter>...</ManufacturingExtraMonthQuarter>  
</TimeBinding>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[バインド](binding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[CalendarEndDate](../properties/calendarenddate-element-assl.md)、 [CalendarLanguage](../properties/language-element-assl.md)、 [CalendarStartDate](../properties/calendarstartdate-element-assl.md)、 [FirstDayOfWeek](../properties/firstdayofweek-element-assl.md)、 [FiscalFirstDayOfMonth](../properties/fiscalfirstdayofmonth-element-assl.md)、 [FiscalFirstMonth](../properties/fiscalfirstmonth-element-assl.md)、 [FiscalYearName](../properties/name-element-assl.md)、 [ManufacturingExtraMonthQuarter](../properties/manufacturingextramonthquarter-element-assl.md)、 [ManufacturingFirstMonth](../properties/manufacturingfirstmonth-element-assl.md)、[ManufacturingFirstWeekOfMonth](../properties/manufacturingfirstweekofmonth-element-assl.md)、 [ReportingFirstMonth](../properties/reportingfirstmonth-element-assl.md)、 [ReportingFirstWeekOfMonth](../properties/reportingfirstweekofmonth-element-assl.md)、 [ReportingWeekToMonthPattern](../properties/reportingweektomonthpattern-element-assl.md)|  
|派生要素|参照してください[バインド](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 詳細については、`Binding`の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む、型、`Binding`型との継承階層`Binding`型を参照してください[データ型のバインド&#40;ASSL&#41;](binding-data-type-assl.md).  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.TimeBinding>します。  
  
## <a name="see-also"></a>関連項目  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
