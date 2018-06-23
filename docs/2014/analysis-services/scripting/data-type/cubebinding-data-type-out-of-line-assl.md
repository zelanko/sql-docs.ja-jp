---
title: CubeBinding データ型 (の不一致) (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CubeBinding Data Type (out-of-line)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeBinding
helpviewer_keywords:
- CubeBinding data type
ms.assetid: 5e1ee8ef-855c-4f3d-ae21-a33360d00d66
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b919e8f28d5cb102268ed3338aa0309e45a738c2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165917"
---
# <a name="cubebinding-data-type-out-of-line-assl"></a>CubeBinding データ型 (不一致) (ASSL)
  間のリレーションシップを表すプリミティブ データ型を定義、[キューブ](../objects/cube-element-assl.md)要素、および[データソース](../objects/datasource-element-assl.md)要素。  
  
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
|子要素|[DataSource](../objects/datasource-element-assl.md)、 [DataSourceID](../properties/id-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [MeasureGroup](../objects/group-element-assl.md)|  
|派生要素|[バインド](../../xmla/xml-elements-properties/binding-element-xmla.md)([バインド](../../xmla/xml-elements-properties/bindings-element-xmla.md)のコレクション[プロセス](../../xmla/xml-elements-commands/process-element-xmla.md)または[バッチ](../../xmla/xml-elements-commands/batch-element-xmla.md)コマンド)|  
  
## <a name="remarks"></a>コメント  
 アウトオブ ライン バインドの詳細については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)です。  
  
## <a name="see-also"></a>参照  
 [Binding データ型&#40;ASSL&#41;](binding-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  