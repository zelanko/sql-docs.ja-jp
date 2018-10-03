---
title: 要素 (ASSL) の値 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Value Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Value
helpviewer_keywords:
- Value element
ms.assetid: a2fad411-73fd-42df-b4e1-df2cb8454182
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d338b8607d8515bf89183eeadd24252c55af8fc5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218192"
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
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
|先祖または親|データ型|  
|------------------------|---------------|  
|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|任意の simpleType|  
|[ServerProperty](../objects/serverproperty-element-assl.md)|任意の simpleType|  
|他のすべて|String|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)、[注釈](../objects/annotation-element-assl.md)、 [Kpi](../objects/kpi-element-assl.md)、 [ReportFormatParameter](../objects/reportformatparameter-element-asl.md)、 [ReportParameter](../objects/reportparameter-element-assl.md)、 [ServerProperty](../objects/serverproperty-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Value` 要素には、親オブジェクトに関連付けられた値が含まれています。 `Value` の期待値は、次の表で説明するように、その親要素に応じて変わります。  
  
|親要素|期待値|  
|--------------------|--------------------|  
|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|アルゴリズム パラメーターの値|  
|[注釈](../objects/annotation-element-assl.md)|注釈の値|  
|[Kpi](../objects/kpi-element-assl.md)|主要業績評価指標 (KPI) の値を計算するために使用する多次元式 (MDX)|  
|[ReportFormatParameter](../objects/reportformatparameter-element-asl.md)|レポート形式パラメーターの値|  
|[ReportParameter](../objects/reportparameter-element-assl.md)|レポート パラメーターの値を計算するために使用する MDX 式|  
|[ServerProperty](../objects/serverproperty-element-assl.md)|現在実行中のインスタンスのサーバー プロパティの値|  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで `Value` の親に対応する要素は、<xref:Microsoft.AnalysisServices.AlgorithmParameter>、<xref:Microsoft.AnalysisServices.Annotation>、<xref:Microsoft.AnalysisServices.Kpi>、<xref:Microsoft.AnalysisServices.ReportParameter>、および <xref:Microsoft.AnalysisServices.ServerProperty> です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
