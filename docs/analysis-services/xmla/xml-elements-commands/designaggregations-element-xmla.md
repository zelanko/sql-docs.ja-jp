---
title: DesignAggregations 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b32a7ecaf7c8268b88d3fc417cc1e41e024bfd2f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34574134"
---
# <a name="designaggregations-element-xmla"></a>DesignAggregations 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Analysis Services インスタンスで、集計デザインの集計を作成します。  
  
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
  
## <a name="remarks"></a>コメント  
 **DesignAggregations**集計デザインによって保存される集計定義を生成するコマンドを使用します。 その後、集計デザインを使用してパーティションの集計を具体化し、複数のパーティション間で再利用することもできます。  
  
## <a name="see-also"></a>参照
 [コマンド&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
