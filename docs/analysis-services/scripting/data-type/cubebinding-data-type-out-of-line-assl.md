---
title: "CubeBinding データ型 (の不一致) (ASSL) |Microsoft ドキュメント"
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
- CubeBinding Data Type (out-of-line)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CubeBinding
helpviewer_keywords:
- CubeBinding data type
ms.assetid: 5e1ee8ef-855c-4f3d-ae21-a33360d00d66
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c0624bd051d8534e82b608bc925236abc0153798
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="cubebinding-data-type-out-of-line-assl"></a>CubeBinding データ型 (不一致) (ASSL)
  間のリレーションシップを表すプリミティブ データ型を定義、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素、および[データソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeBinding>  
   <ID>...</ID>  
   <DataSourceID>...</DataSourceID>  
   <DataSource>...</DataSource>  
   <MeasureGroup>...</MeasureGroup>  
</CubeBinding>  
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
|子要素|[DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md)、 [DataSourceID](../../../analysis-services/scripting/properties/datasourceid-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|派生要素|[バインド](../../../analysis-services/xmla/xml-elements-properties/binding-element-xmla.md)([バインド](../../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md)のコレクション[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)または[バッチ](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)コマンド)|  
  
## <a name="remarks"></a>解説  
 アウトオブ ライン バインドの詳細については、次を参照してください。[データ ソースとのバインド & #40 です。SSAS 多次元 &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>参照  
 [バインディング データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

