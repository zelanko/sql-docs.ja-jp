---
title: "CacheMode 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- CacheMode Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- CacheMode element
ms.assetid: bfb8f7bb-ccd3-4dfe-a36a-1cea15edfe40
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4a5af62efbab01b78a68af1ec7f94caeaaaea22a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="cachemode-element-assl"></a>CacheMode 要素 (ASSL)
  マイニング構造の処理中に取得したトレーニング データに使用するキャッシュ メカニズムを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningStructure>  
   ...  
   <CacheMode>...</CacheMode>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*KeepTrainingCases*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*KeepTrainingCases*|トレーニング ケースは処理中および処理後にキャッシュされます。|  
|*ClearAfterProcessing*|トレーニング ケースは処理中にキャッシュされますが、処理後に削除されます。|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**CacheMode**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningStructure>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

