---
title: Collation 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Collation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Collation
helpviewer_keywords:
- Collation element
ms.assetid: 9b6dbe19-543e-43e6-abe9-1e8b4dfaa275
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: db1cdb33f9fffe6c9a28269a12cc83ca9419bd8e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="collation-element-assl"></a>Collation 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]親要素によって使用される照合順序を決定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Database> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Collation>...</Collation>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)、 [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)、[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **照合**ロケール識別子 (LCID) と比較フラグをアンダー スコア文字で区切られた文字列で構成されます。 たとえば、Latin1_General_CI_AS のような文字列が使用されます。  
  
 親に対応する要素**照合**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.Cube>、 <xref:Microsoft.AnalysisServices.Database>、 <xref:Microsoft.AnalysisServices.DataItem>、 <xref:Microsoft.AnalysisServices.Dimension>、 <xref:Microsoft.AnalysisServices.MiningModel>、および<xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
