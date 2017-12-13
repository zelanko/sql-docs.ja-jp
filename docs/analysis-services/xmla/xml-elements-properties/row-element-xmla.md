---
title: "row 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: row Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#row
- microsoft.xml.analysis.row
- http://schemas.microsoft.com/analysisservices/2003/engine#row
helpviewer_keywords: row element
ms.assetid: 4d9977a0-c396-44c7-9fd4-97f4c3d643aa
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 31ce205d17095d2a6df40adb7ce0be64f883b5f4
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="row-element-xmla"></a>row 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]データの 1 つの行が含まれています、[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)によって返される表形式のデータを含む要素、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)または[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出しです。  
  
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
  
 詳細とスキーマについては表形式のデータの列の名前付けに関する詳細については、次を参照してください。[行セットのデータ型 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md).  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
