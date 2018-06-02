---
title: DataSource 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6f46c53f082b89bb54fe82c7ccaa74e8b31c9b26
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574834"
---
# <a name="datasource-element-xmla"></a>DataSource 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親の行外のデータ ソース バインドを含む[バッチ](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)または[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Batch> <!-- or Process>  
...  
   <DataSource>  
      <DatabaseID>...</DatabaseID>  
      <DataSourceID>...</DataSourceID>  
   </DataSource>  
...  
</Batch>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[バッチ](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)、[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|子要素|[DatabaseID](../../../analysis-services/xmla/xml-elements-properties/databaseid-element-xmla.md)、 [DataSourceID](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 **データソース**要素がによって使用される、データ ソースへの不一致のバインドを表す、**バッチ**または**プロセス**のデータ ソースのバインドを一時的にオーバーライドするコマンドAnalysis Services のオブジェクトは、コマンドによって処理されます。  
  
 アウトオブ ライン バインドの詳細については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)です。  
  
## <a name="see-also"></a>参照
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
