---
title: CurrentStorageMode 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fd14d8a08253a85ff0cd14a33036806a4b008e53
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032393"
---
# <a name="currentstoragemode-element-assl"></a>CurrentStorageMode 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  親要素の現在のストレージ モードを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Dimension> <!-- or Partition -->  
   <CurrentStorageMode>...</CurrentStorageMode>  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*ROLAP*|  
|Cardinality|0-1 : 省略可能な要素で、出現しないか、出現する場合は 1 回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **CurrentStorageMode**要素プロアクティブ キャッシュの目的、使用されているストレージ モードを示し、親要素のすべての属性に適用されます。  
  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*MOLAP*|親は多次元 OLAP (MOLAP) ストレージを使用します。|  
|*ROLAP*|親はリレーショナル OLAP (ROLAP) ストレージを使用します。|  
|*HOLAP*|親はハイブリッド OLAP (HOLAP) ストレージを使用します。<br /><br /> 注: この値はに対してのみ有効[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)要素の親です。|  
  
 有効な値に対応する列挙**CurrentStorageMode**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.StorageMode>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
