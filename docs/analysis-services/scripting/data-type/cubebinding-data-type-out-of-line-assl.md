---
title: CubeBinding データ型 (の不一致) (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 68bc808952f85efd2056df07b8fb5d8a60561bf7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="cubebinding-data-type-out-of-line-assl"></a>CubeBinding データ型 (不一致) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 アウトオブ ライン バインドの詳細については、次を参照してください。[データ ソースとのバインド & #40 です。SSAS 多次元 & #41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>参照  
 [バインディング データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
