---
title: "PerspectiveKpi データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PerspectiveKpi Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: PerspectiveKpi
helpviewer_keywords: PerspectiveKpi data type
ms.assetid: e8d19ec8-70d3-4947-904a-fb81fcac9afd
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 99540f2d29c0ae2d40d07b6ef66b8b7bc036026e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="perspectivekpi-data-type-assl"></a>PerspectiveKpi データ型 (ASSL)
  主要業績評価指標 (KPI) に関する情報を表すプリミティブ データ型を定義、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<PerspectiveKpi>  
   <KpiID>...</KpiID>  
   <Annotations>...</Annotations>  
</PerspectiveKpi>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [KpiID](../../../analysis-services/scripting/properties/kpiid-element-assl.md)|  
|派生要素|[Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md) ([Kpi](../../../analysis-services/scripting/collections/kpis-element-assl.md)のコレクション[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.PerspectiveKpi>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
