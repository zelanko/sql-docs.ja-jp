---
title: "MeasureGroupBinding データ型 (の不一致) (ASSL) |Microsoft ドキュメント"
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
- MeasureGroupBinding Data Type (out-of-line)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MeasureGroupBinding
helpviewer_keywords:
- MeasureGroupBinding data type
ms.assetid: e6c65597-89ac-457e-a0e5-01d85449a1b7
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2db6edd7c86ad9d233aa6002c77b4c2b2371d7dc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="measuregroupbinding-data-type-out-of-line-assl"></a>MeasureGroupBinding データ型 (不一致) (ASSL)
  メジャー グループへのバインドを表すプリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureGroupBinding>  
   <ID>...</ID>  
   <Source>...</Source>  
   <EstimatedRows>...</EstimatedRows>  
   <Dimensions>...</Dimensions>  
   <Measures>...</Measures>  
      <Partitions>...</Partitions>  
</MeasureGroupBinding>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[ディメンション](../../../analysis-services/scripting/collections/dimensions-element-assl.md)、 [EstimatedRows](../../../analysis-services/scripting/properties/estimatedrows-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、[メジャー](../../../analysis-services/scripting/collections/measures-element-assl.md)、[パーティション](../../../analysis-services/scripting/collections/partitions-element-assl.md)、[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|  
|派生要素|参照してください[バインド](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>解説  
 詳細についてを参照して、不一致バインドのうち、[データ ソースとのバインド & #40 です。SSAS 多次元 &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

