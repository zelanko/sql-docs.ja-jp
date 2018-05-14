---
title: row 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 78539bfa16bfca56cbac10a4d1d9a793f685a333
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="row-element-xmla"></a>row 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  データの 1 つの行が含まれています、[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)によって返される表形式のデータを含む要素、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)または[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出しです。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <row>  
      <!-- One or more column elements -->  
   </row>  
</root>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)(を使用して、[行セット](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)データ型)|  
|子要素|1 つ以上の列要素|  
  
## <a name="remarks"></a>解説  
 によって返される各行、**ルート**を表形式のデータを含む要素には、対応する**行**要素。 内の各列、**ルート**要素は、個別の XML 要素によって表されます。 列の値、**行**要素は XML 要素に含まれるデータと列の名前は、XML 要素の名前に対応しています。  
  
 行の中の列に NULL 値を指定する方法は、次の 2 つです。  
  
-   列要素が欠落している場合、その列が NULL であることを暗黙に意味します。  
  
-   列要素で `xsi:nil='true'` 属性を使用することにより、その列が NULL 値を持つことを示せます。  
  
 たとえば、ある行に Store_Name という単一の列が含まれ、その値が NULL の場合、以下のいずれかの方法で表せます。  
  
```  
<row>  
</row>  
```  
  
 または。  
  
```  
<row>  
   <Store_name xsi:nil='true'/>  
</row>  
```  
  
 列要素には、エラーが含まれている場合、**エラー**要素は、次の例に示すように、エラーに関する情報を提供します。  
  
```  
<row>   <Store_name>  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception">  
         <ErrorCode>3238658054</ErrorCode>  
         <Description>The object [X] was not found in the cube when [X] was parsed.</Description>  
      </Error>  
   </Store_name>  
</row>  
```  
  
 詳細とスキーマについては表形式のデータの列の名前付けに関する詳細については、次を参照してください。[行セットのデータ型 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md).  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
