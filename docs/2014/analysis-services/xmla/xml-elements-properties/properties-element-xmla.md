---
title: Properties 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Properties Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Properties
- microsoft.xml.analysis.properties
- urn:schemas-microsoft-com:xml-analysis#Properties
- Properties
helpviewer_keywords:
- Properties element
ms.assetid: 0b5468e5-bf23-4d22-862f-72e27a9fff2f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 83234d39c39ec4e52d387f074a3f2d753ef323d8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054842"
---
# <a name="properties-element-xmla"></a>Properties 要素 (XMLA)
  によって使用される分析 (XMAL) プロパティの XML が含まれています、 [Discover](../xml-elements-methods-discover.md)と[Execute](../xml-elements-methods-execute.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Discover> <!-- or Execute -->  
...  
   <Properties>  
      <PropertyList>...</PropertyList>  
   </Properties>  
...  
</Discover>  
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
|親要素|[検出](../xml-elements-methods-discover.md)、[実行](../xml-elements-methods-execute.md)|  
|子要素|[PropertyList](propertylist-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Properties` 要素は、`Discover` および `Execute` メソッドのさまざまな側面を制御するために使用される XMLA プロパティを表します。たとえば、データ ソースへの接続に必要な情報の定義、返される結果セットの形式の指定、データを書式設定する際のロケールの指定などを制御します。  
  
 要求の種類として DISCOVER_PROPERTIES を使用して、使用可能なプロパティとその値を取得できます、`Discover`メソッド。  
  
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
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
