---
title: TimeBinding データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0f97642a9b98c0fc234388d3a0baa3f6b570369b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032013"
---
# <a name="timebinding-data-type-assl"></a>TimeBinding データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|基本データ型|[バインド](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[CalendarEndDate](../../../analysis-services/scripting/properties/calendarenddate-element-assl.md)、 [CalendarLanguage](../../../analysis-services/scripting/properties/calendarlanguage-element-assl.md)、 [CalendarStartDate](../../../analysis-services/scripting/properties/calendarstartdate-element-assl.md)、 [FirstDayOfWeek](../../../analysis-services/scripting/properties/firstdayofweek-element-assl.md)、 [FiscalFirstDayOfMonth](../../../analysis-services/scripting/properties/fiscalfirstdayofmonth-element-assl.md)、 [FiscalFirstMonth](../../../analysis-services/scripting/properties/fiscalfirstmonth-element-assl.md)、 [FiscalYearName](../../../analysis-services/scripting/properties/fiscalyearname-element-assl.md)、 [ManufacturingExtraMonthQuarter](../../../analysis-services/scripting/properties/manufacturingextramonthquarter-element-assl.md)、 [ManufacturingFirstMonth](../../../analysis-services/scripting/properties/manufacturingfirstmonth-element-assl.md)、[ManufacturingFirstWeekOfMonth](../../../analysis-services/scripting/properties/manufacturingfirstweekofmonth-element-assl.md)、 [ReportingFirstMonth](../../../analysis-services/scripting/properties/reportingfirstmonth-element-assl.md)、 [ReportingFirstWeekOfMonth](../../../analysis-services/scripting/properties/reportingfirstweekofmonth-element-assl.md)、 [ReportingWeekToMonthPattern](../../../analysis-services/scripting/properties/reportingweektomonthpattern-element-assl.md)|  
|派生要素|参照してください[バインド](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>解説  
 詳細については、**バインド**の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む、型、**バインド**型との継承階層**バインド**型を参照してください[データ型のバインド&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)です。  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとのバインド & #40 です。SSAS 多次元 & #41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.TimeBinding>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
