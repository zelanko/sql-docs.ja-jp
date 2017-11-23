---
title: "DesignAggregations 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DesignAggregations Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DesignAggregations
- microsoft.xml.analysis.designaggregations
- http://schemas.microsoft.com/analysisservices/2003/engine#DesignAggregations
helpviewer_keywords: DesignAggregations command
ms.assetid: 4c419dbc-7405-40aa-8ddd-6b46685a297d
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d442725b09919ef9cbbec87cc08c0e01551bc5ae
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="designaggregations-element-xmla"></a>DesignAggregations 要素 (XMLA)
  上の集計デザインの集計を作成、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <DesignAggregations>  
      <Object>...</Object>  
      <Time>...</Time>  
      <Steps>...</Steps>  
      <Optimization>...</Optimization>  
      <Storage>...</Storage>  
      <Materialize>...</Materialize>  
      <Queries>...</Queries>  
   </DesignAggregations>  
</Command>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[具体化](../../../analysis-services/xmla/xml-elements-properties/materialize-element-xmla.md)、[オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)、[最適化](../../../analysis-services/xmla/xml-elements-properties/optimization-element-xmla.md)、[クエリ](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md)、[手順](../../../analysis-services/xmla/xml-elements-properties/steps-element-xmla.md)、[ストレージ](../../../analysis-services/xmla/xml-elements-properties/storage-element-xmla.md)、[時間](../../../analysis-services/xmla/xml-elements-properties/time-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **DesignAggregations**集計デザインによって保存される集計定義を生成するコマンドを使用します。 その後、集計デザインを使用してパーティションの集計を具体化し、複数のパーティション間で再利用することもできます。  
  
## <a name="see-also"></a>参照  
 [コマンドと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
