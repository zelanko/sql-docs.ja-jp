---
title: StorageMode 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 72b2963293c6c59338ad23f8e4f4f5c0e9d19001
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34038656"
---
# <a name="storagemode-element-assl"></a>StorageMode 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|親要素|[キューブ要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)、[要素の寸法&#40;ASSL&#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)、 [MeasureGroup 要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)、[パーティション要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*MOLAP*|親は多次元 OLAP (MOLAP) ストレージを使用します。|  
|*ROLAP*|親はリレーショナル OLAP (ROLAP) ストレージを使用します。|  
|*HOLAP*|親はハイブリッド OLAP (HOLAP) ストレージを使用します。<br /><br /> 注: この値は、有効では[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)要素の親です。|  
|*InMemory*|親は IMBI ストレージを使用します。|  
  
 許可される値に対応する列挙**StorageMode**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.StorageMode>します。  
  
 親に対応する要素**StorageMode**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.Cube>、 <xref:Microsoft.AnalysisServices.Dimension>、 <xref:Microsoft.AnalysisServices.MeasureGroup>、および<xref:Microsoft.AnalysisServices.Partition>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
