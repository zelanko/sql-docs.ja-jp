---
title: "DataSourceViewID 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DataSourceViewID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DataSourceViewID
helpviewer_keywords:
- DataSourceViewID element
ms.assetid: dcf617fe-0bf6-4767-af35-07c0c7fd96e5
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ecf937676d947103f6ad5e8a5d327592e0fb69d4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="datasourceviewid-element-assl"></a>DataSourceViewID 要素 (ASSL)
  識別、 [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)要素に関連付けられた、[バインド](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)親要素です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataSourceViewBinding> <!-- or DSVTableBinding -->  
   ...  
   <DataSourceViewID>...</DataSourceViewID>  
   ...  
</DataSourceViewBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataSourceViewBinding](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md)、 [DSVTableBinding](../../../analysis-services/scripting/data-type/dsvtablebinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**DataSourceViewID**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.DataSourceViewBinding>と<xref:Microsoft.AnalysisServices.DSVTableBinding>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

