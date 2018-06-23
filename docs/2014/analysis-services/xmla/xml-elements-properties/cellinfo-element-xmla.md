---
title: CellInfo 要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CellInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cellinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#CellInfo
- urn:schemas-microsoft-com:xml-analysis#CellInfo
helpviewer_keywords:
- CellInfo element
ms.assetid: 8b6420f1-e9a7-4975-b580-1439fa11f5ca
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 803640fe83ccc3137b4597b8c1b78850abeb55c1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085952"
---
# <a name="cellinfo-element-xmla"></a>CellInfo 要素 (XMLA)
  親に含まれるセル メタデータを表す[OlapInfo](olapinfo-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<OlapInfo>  
   ...  
   <CellInfo>  
      <!-- One or more cell property definitions -->  
   </CellInfo>  
   ...  
</OlapInfo>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[OlapInfo](olapinfo-element-xmla.md)|  
|子要素|1 つ以上のセル プロパティ定義|  
  
## <a name="remarks"></a>コメント  
 `CellInfo` 要素は、`root` データ型を使用する `MDDataSet` 要素によって返される多次元データセット内に含まれる、セルのプロパティのコレクションを含みます。 `CellInfo` 要素内のそれぞれのセル プロパティは別個の XML 要素によって定義され、それぞれに `name` 属性と `type` 属性が指定されています。 セル プロパティの `name` 属性は、XML 要素によって表される OLE DB for OLAP セル プロパティの名前に対応します。`type` 属性は、セル プロパティの XML データ型を表します。 XML 要素の名前は、`CellData` 要素の `root` 要素に含まれるセルのセル プロパティの値を識別するために使用されます。  
  
 セル プロパティ定義の構文は次のとおりです。  
  
```  
<CellPropertyDefinition name="string" type"string" />  
```  
  
 DISCOVER_PROPERTIES 要求の種類を使用して、使用可能なプロパティとその値を取得できます、`Discover`メソッドです。 `PropertyList` 要素内に一覧表示されるプロパティの順序は任意です。  
  
 オプションで、プロバイダーは `AxisInfo` または `CellInfo` セクション内の個々のメンバーまたはセル プロパティの既定値を指定できます。 プロパティの値が常に同じ、あるいはほとんど同じ場合、既定値を使用すると結果を小さくすることができます。 プロパティの既定値を示すために、`Default`要素は、セル プロパティ定義要素の 1 つの子要素として必要に応じて指定できます。 したがって、結果の中にメンバーまたはセル プロパティが存在しない場合、指定された既定値がセル プロパティの値になります。  
  
## <a name="example"></a>例  
 次の例は、`CellInfo` 要素内で、セル プロパティ VALUE、FORMATTED_VALUE、および FORMAT_STRING がどのように表されるかを示しています。  
  
```  
<OlapInfo>  
   ...  
      <CellInfo>  
         <Value name="VALUE"></Value>  
         <FmtValue name="FORMATTED_VALUE"></FmtValue>  
         <FormatString name="FORMAT_STRING"></FormatString>  
      </CellInfo>  
</OlapInfo>  
```  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  