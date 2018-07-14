---
title: Binding 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Binding Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.binding
- http://schemas.microsoft.com/analysisservices/2003/engine#Binding
- urn:schemas-microsoft-com:xml-analysis#Binding
helpviewer_keywords:
- Binding element
ms.assetid: d5acd8d4-8551-449a-ae30-d0ba828cc02d
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec223f5a56ea32388a3485f39db0bbbc494fda85
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37203972"
---
# <a name="binding-element-xmla"></a>Binding 要素 (XMLA)
  アウトオブ ライン バインドを定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]オブジェクト、ディメンションでは、属性など、[バインド](bindings-element-xmla.md)のコレクションを[バッチ](../xml-elements-commands/batch-element-xmla.md)または[プロセス](../xml-elements-commands/process-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Bindings>  
   <Binding xsi:type="DimensionAttributeBinding">...</Binding>  
   <!-- or -->  
   <Binding xsi:type="MeasureGroupAttributeBinding">...</Binding>  
   <!-- or -->  
   <Binding xsi:type="PartitionBinding">...</Binding>  
</Bindings>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[DimensionAttributeBinding](../../scripting/data-type/dimensionattributebinding-data-type-out-of-line-assl.md)、 [MeasureGroupAttributeBinding](../../scripting/data-type/measuregroupattributebinding-data-type-out-of-line-assl.md)、 [PartitionBinding](../../scripting/data-type/binding-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[バインド](bindings-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Binding` 要素は、`Batch` または `Process` コマンドによって処理される [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] オブジェクトに対して不一致バインドを定義します (データ ソースおよびデータ ソース ビューを除きます)。 オブジェクトの処理の詳細については、次を参照してください。[オブジェクトの処理&#40;XMLA&#41;](../xml-elements-objects.md)します。  
  
 アウトオブ ライン バインドの詳細については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
