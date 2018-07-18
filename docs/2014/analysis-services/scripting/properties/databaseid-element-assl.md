---
title: DatabaseID 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DatabaseID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DatabaseID element
ms.assetid: 6bcf2bd5-b037-4964-bc72-42e0c89f9716
caps.latest.revision: 8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec07be8832ef048ac6ddc2b6cc92a945ba9e2c2e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161133"
---
# <a name="databaseid-element-assl"></a>DatabaseID 要素 (ASSL)
  識別、[データベース](../objects/database-element-assl.md)の行外に関連付けられている要素[バインド](../data-type/binding-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttributeBinding> <!-- or MeasureGroupAttributeBinding -->  
   ...  
   <DatabaseID>...</DatabaseID>  
   ...  
</DimensionAttributeBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttributeBinding](../data-type/dimensionattributebinding-data-type-out-of-line-assl.md)、 [MeasureGroupAttributeBinding](../data-type/measuregroupattributebinding-data-type-out-of-line-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 アウトオブ ライン バインドの詳細については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
