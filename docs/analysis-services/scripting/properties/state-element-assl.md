---
title: "要素 (ASSL) の状態 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: State Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: State
helpviewer_keywords: State element
ms.assetid: b6ee1144-89f7-4ced-bc87-c2e33ca25f73
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 90ea8e843513e7cdf677585c274ff5fd803127a6
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="state-element-assl"></a>State 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]親要素の現在の処理状態を説明する読み取り専用の値が含まれています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, MiningModel, MiningStructure, Partition -->  
      ...  
   <State>...</State>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)、[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*処理*|要素は完全に処理されました。|  
|*Partiallyprocessed であります。*|要素の一部が処理されました ([キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)と[MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)のみ)。|  
|*まだ処理されていません*|要素は処理されませんでした。|  
  
 許可される値に対応する列挙**状態**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.AnalysisState>します。  
  
 親に対応する要素**状態**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.Cube>、 <xref:Microsoft.AnalysisServices.Dimension>、 <xref:Microsoft.AnalysisServices.MeasureGroup>、 <xref:Microsoft.AnalysisServices.MiningModel>、 <xref:Microsoft.AnalysisServices.MiningStructure>、および<xref:Microsoft.AnalysisServices.Partition>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
