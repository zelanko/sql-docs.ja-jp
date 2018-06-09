---
title: PropertyList 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3e773de16e65aa9c7f1be521214088aa9f06b369
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34577834"
---
# <a name="propertylist-element-xmla"></a>PropertyList 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  使用される Analysis (XMLA) プロパティの XML のコレクションを格納、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)と[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Properties>  
   <PropertyList>  
      <!-- Zero or more XMLA properties -->  
   </PropertyList>  
</Properties>  
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
|親要素|[Properties](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)|  
|子要素|XMLA プロパティ (「解説」を参照)|  
  
## <a name="remarks"></a>コメント  
 **PropertyList** 要素は、XMLA プロパティのコレクションを含みます。 ユーザーはそれぞれのプロパティを使用して、 **Discover** または **Execute** メソッドのいくつかの側面を制御できます。たとえば、データ ソースへの接続に必要な情報の定義、返される結果セットの形式の指定、データを書式設定する際のロケールの指定などを制御できます。 **PropertyList** 要素内のそれぞれの XMLA プロパティは、個別の XML 要素によって定義されます。 XMLA プロパティの値は XML 要素に含まれるデータで、XMLA プロパティの名前は XML 要素の名前に対応します。  
  
 使用可能なプロパティとその値は、 **Discover** メソッドで要求の種類として DISCOVER_PROPERTIES を使用することによって取得できます。 **PropertyList** 要素内に一覧表示されるプロパティの順序は任意です。  
  
 Analysis Services でサポートされる XMLA プロパティの詳細については、次を参照してください。[サポートされる XMLA プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)です。  
  
## <a name="example"></a>例  
  
```  
<Properties>  
   <PropertyList>  
      <DataSourceInfo>  
         Provider=MSOLAP;Data Source=local;  
      </DataSourceInfo>  
      <Catalog>  
         Foodmart 2000  
      </Catalog>  
      <Format>  
         Multidimensional  
      </Format>  
   </PropertyList>  
</Properties>  
```  
  
## <a name="see-also"></a>参照
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
