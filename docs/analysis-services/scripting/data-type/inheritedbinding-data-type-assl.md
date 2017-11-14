---
title: "InheritedBinding データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
- InheritedBinding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- InheritedBinding
helpviewer_keywords:
- InheritedBinding data type
ms.assetid: a61f58c5-62d6-44e8-a02f-db2b17d1f256
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 06ba209e561310e683936e52eb55a4860efd10b1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="inheritedbinding-data-type-assl"></a>InheritedBinding データ型 (ASSL)
  示す派生データ型を定義、 [MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)要素は、属性からバインドを継承します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<InheritedBinding>...</InheritedBinding>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[バインド](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|なし|  
|派生要素|参照してください[バインド](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>解説  
 詳細については、**バインド**の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む、型、**バインド**型との継承階層**バインド**型を参照してください[バインドのデータ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)要素。  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとのバインド & #40 です。SSAS 多次元 &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.InheritedBinding>します。  
  
## <a name="see-also"></a>参照  
 [バインディング データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [データ ソースとのバインド & #40 です。SSAS 多次元 &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

