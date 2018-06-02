---
title: CellInfo 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3ada531d33baf7007d08ac8a719fca2bf8f1b2e4
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574254"
---
# <a name="cellinfo-element-xmla"></a>CellInfo 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親に含まれるセル メタデータを表す[OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)要素。  
  
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
|親要素|[OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|子要素|1 つ以上のセル プロパティ定義|  
  
## <a name="remarks"></a>コメント  
 **CellInfo**要素によって返される多次元データセット内に含まれるセルのセル プロパティのコレクションを格納、**ルート**要素を使用して、 **MDDataSet**データ型。 内の各セル プロパティ、 **CellInfo**要素がそれぞれに個別の XML 要素によって定義されている、**名前**属性および**型**属性。 **名前**セル プロパティの属性は、OLE DB の XML 要素によって表される OLAP セル プロパティの名前に対応し、**型**セルの XML データ型を表す属性プロパティ。 含まれるセルのセル プロパティの値を識別する XML 要素の名前が使用される、 **CellData**の要素、**ルート**要素。  
  
 セル プロパティ定義の構文は次のとおりです。  
  
```  
<CellPropertyDefinition name="string" type"string" />  
```  
  
 使用可能なプロパティとその値は、 **Discover** メソッドで要求の種類として DISCOVER_PROPERTIES を使用することによって取得できます。 **PropertyList** 要素内に一覧表示されるプロパティの順序は任意です。  
  
 プロバイダーがで個々 のメンバーまたはセル プロパティの既定値を指定できます必要に応じて、 **AxisInfo**または**CellInfo**セクションです。 プロパティの値が常に同じ、あるいはほとんど同じ場合、既定値を使用すると結果を小さくすることができます。 プロパティの既定値を示すために、**既定**要素は、セル プロパティ定義要素の 1 つの子要素として必要に応じて指定できます。 したがって、結果の中にメンバーまたはセル プロパティが存在しない場合、指定された既定値がセル プロパティの値になります。  
  
## <a name="example"></a>例  
 次の例での VALUE、FORMATTED_VALUE、および FORMAT_STRING セル プロパティの表現方法を示しています、 **CellInfo**要素。  
  
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
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
