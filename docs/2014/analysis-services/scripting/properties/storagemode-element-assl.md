---
title: StorageMode 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- StorageMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- StorageMode
helpviewer_keywords:
- StorageMode element
ms.assetid: 197e8153-1ab6-43ba-a7e9-ae9be19ac511
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 11c7c07f0373d3d271c39146509c73b11c9b7f9b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104942"
---
# <a name="storagemode-element-assl"></a>StorageMode 要素 (ASSL)
  親要素のストレージ モードを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <StorageMode>...</StorageMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*MOLAP*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[キューブ要素&#40;ASSL&#41;](../objects/cube-element-assl.md)、[ディメンション要素&#40;ASSL&#41;](../objects/dimension-element-assl.md)、 [MeasureGroup 要素&#40;ASSL&#41;](../objects/group-element-assl.md)、[パーティション要素&#40;ASSL&#41;](../objects/partition-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*MOLAP*|親は多次元 OLAP (MOLAP) ストレージを使用します。|  
|*ROLAP*|親はリレーショナル OLAP (ROLAP) ストレージを使用します。|  
|*HOLAP*|親はハイブリッド OLAP (HOLAP) ストレージを使用します。 **注:** この値は無効です[ディメンション](../objects/dimension-element-assl.md)要素の親。|  
|*InMemory*|親は IMBI ストレージを使用します。|  
  
 許容された値に対応する列挙体`StorageMode`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.StorageMode>します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで `StorageMode` の親に対応する要素は、<xref:Microsoft.AnalysisServices.Cube>、<xref:Microsoft.AnalysisServices.Dimension>、<xref:Microsoft.AnalysisServices.MeasureGroup>、および <xref:Microsoft.AnalysisServices.Partition> です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
