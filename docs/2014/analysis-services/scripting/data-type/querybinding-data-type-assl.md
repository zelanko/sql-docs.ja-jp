---
title: QueryBinding データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- QueryBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- QueryBinding
helpviewer_keywords:
- QueryBinding data type
ms.assetid: 7b58fc89-0060-4e56-ad99-6f74fe8cfc6d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 71e00b6810d777563855f3016d9fa129010a08ac
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059652"
---
# <a name="querybinding-data-type-assl"></a>QueryBinding データ型 (ASSL)
  関連付けを表す派生データ型を定義、 [DataSource](../objects/datasource-element-assl.md)を持つ要素を[QueryDefinition](../properties/querydefinition-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<QueryBinding>  
   <!-- The following elements extend TabularBinding -->  
   <DataSourceID>...</DataSourceID>  
      <QueryDefinition>...</QueryDefinition>  
</QueryBinding>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[TabularBinding](binding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[DataSourceID](../properties/id-element-assl.md)、 [QueryDefinition](../properties/querydefinition-element-assl.md)|  
|派生要素|参照してください[バインド](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>コメント  
 詳細については、`Binding`の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む、型、`Binding`型との継承階層`Binding`型を参照してください[データ型のバインド&#40;ASSL&#41;](binding-data-type-assl.md).  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.QueryBinding>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
