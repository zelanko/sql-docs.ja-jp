---
title: "値の要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Value Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Value
helpviewer_keywords:
- Value element
ms.assetid: a2fad411-73fd-42df-b4e1-df2cb8454182
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5b31ced28db41575887a07ccf6c6e303aea5aaf1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="value-element-assl"></a>Value 要素 (ASSL)
  親要素の値を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AlgorithmParameter> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Value>...</Value>  
   ...  
</AlgorithmParameter>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|次の表を参照してください。|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
|先祖または親|データ型|  
|------------------------|---------------|  
|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)|任意の simpleType|  
|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|任意の simpleType|  
|他のすべて|文字列|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)、[注釈](../../../analysis-services/scripting/objects/annotation-element-assl.md)、 [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)、 [ReportFormatParameter](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md)、 [ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md)、 [ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **値**要素には、親オブジェクトに関連付けられている値が含まれています。 予想される値、**値**次の表に示すように、要素が親要素によって異なります。  
  
|親要素|期待値|  
|--------------------|--------------------|  
|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)|アルゴリズム パラメーターの値|  
|[注釈](../../../analysis-services/scripting/objects/annotation-element-assl.md)|注釈の値|  
|[Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)|主要業績評価指標 (KPI) の値を計算するために使用する多次元式 (MDX)|  
|[ReportFormatParameter](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md)|レポート形式パラメーターの値|  
|[ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md)|レポート パラメーターの値を計算するために使用する MDX 式|  
|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|現在実行中のインスタンスのサーバー プロパティの値|  
  
 親に対応する要素**値**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.AlgorithmParameter>、 <xref:Microsoft.AnalysisServices.Annotation>、 <xref:Microsoft.AnalysisServices.Kpi>、 <xref:Microsoft.AnalysisServices.ReportParameter>、および<xref:Microsoft.AnalysisServices.ServerProperty>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

