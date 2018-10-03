---
title: LastProcessed 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- LastProcessed Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- LastProcessed
helpviewer_keywords:
- LastProcessed element
ms.assetid: df3d1f6f-705c-4408-9eb3-c550a1dec450
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d634eead7abe78e60eda98083bc6dbeb4ae932ea
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153402"
---
# <a name="lastprocessed-element-assl"></a>LastProcessed 要素 (ASSL)
  親要素が含まれているデータベースが最後に処理された時刻を示す読み取り専用のタイムスタンプを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Cube> <!-- or one of the elements listed in the Element Relationships table -->  
   ...  
      <LastProcessed>...</LastProcessed>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|DateTime|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[キューブ](../objects/cube-element-assl.md)、[データベース](../objects/database-element-assl.md)、[ディメンション](../objects/dimension-element-assl.md)、 [MeasureGroup](../objects/group-element-assl.md)、 [MiningModel](../objects/miningmodel-element-assl.md)、 [MiningStructure](../objects/miningstructure-element-assl.md)、[パーティション](../objects/partition-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスは、`LastProcessed` 要素の値を維持します。 値は、親要素が含まれているデータベースが処理された場合にのみ変更されます。 親要素を個別に処理しても、`LastProcessed` 要素の値は変わりません。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで `LastProcessed` の親に対応する要素は、<xref:Microsoft.AnalysisServices.Cube>、<xref:Microsoft.AnalysisServices.Database>、<xref:Microsoft.AnalysisServices.Dimension>、<xref:Microsoft.AnalysisServices.MeasureGroup>、<xref:Microsoft.AnalysisServices.MiningModel>、<xref:Microsoft.AnalysisServices.MiningStructure>、および <xref:Microsoft.AnalysisServices.Partition> です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
