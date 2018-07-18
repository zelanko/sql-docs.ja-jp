---
title: Collation 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Collation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Collation
helpviewer_keywords:
- Collation element
ms.assetid: 9b6dbe19-543e-43e6-abe9-1e8b4dfaa275
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 92e4e7eaa9eb4d994fc225c9d3d1c9a0c941b1b0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213932"
---
# <a name="collation-element-assl"></a>Collation 要素 (ASSL)
  親要素によって使用される照合順序を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Database> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Collation>...</Collation>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[キューブ](../objects/cube-element-assl.md)、[データベース](../objects/database-element-assl.md)、 [DataItem](../data-type/dataitem-data-type-assl.md)、[ディメンション](../objects/dimension-element-assl.md)、 [MiningModel](../objects/miningmodel-element-assl.md)、 [MiningStructure](../objects/miningstructure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 アンダースコアで区切られたロケール識別子 (LCID) と比較フラグで構成される `Collation` 文字列。 たとえば、Latin1_General_CI_AS のような文字列が使用されます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで `Collation` の親に対応する要素は、<xref:Microsoft.AnalysisServices.Cube>、<xref:Microsoft.AnalysisServices.Database>、<xref:Microsoft.AnalysisServices.DataItem>、<xref:Microsoft.AnalysisServices.Dimension>、<xref:Microsoft.AnalysisServices.MiningModel>、および <xref:Microsoft.AnalysisServices.MiningStructure> です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
