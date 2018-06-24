---
title: PropertyList 要素 (XMLA) |Microsoft ドキュメント
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
- PropertyList Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#PropertyList
- microsoft.xml.analysis.propertylist
- urn:schemas-microsoft-com:xml-analysis#PropertyList
helpviewer_keywords:
- PropertyList element
ms.assetid: 58e63bd9-8aac-438d-adba-1868b4d123f5
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 4b49ad0cf03ce331a00a7eefc9f1302176d89e74
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071539"
---
# <a name="propertylist-element-xmla"></a>PropertyList 要素 (XMLA)
  使用される Analysis (XMLA) プロパティの XML のコレクションを格納、 [Discover](../xml-elements-methods-discover.md)と[Execute](../xml-elements-methods-execute.md)メソッドです。  
  
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
|親要素|[Properties](properties-element-xmla.md)|  
|子要素|XMLA プロパティ (「解説」を参照)|  
  
## <a name="remarks"></a>コメント  
 `PropertyList`要素には、XMLA プロパティのコレクションが含まれています。 ユーザーはそれぞれのプロパティを使用して、`Discover` または `Execute` メソッドのいくつかの側面を制御できます。たとえば、データ ソースへの接続に必要な情報の定義、返される結果セットの形式の指定、データを書式設定する際のロケールの指定などを制御できます。 それぞれの XMLA プロパティで、`PropertyList`要素が、個別の XML 要素によって定義されています。 XMLA プロパティの値は XML 要素に含まれるデータで、XMLA プロパティの名前は XML 要素の名前に対応します。  
  
 DISCOVER_PROPERTIES 要求の種類を使用して、使用可能なプロパティとその値を取得できます、`Discover`メソッドです。 `PropertyList` 要素内に一覧表示されるプロパティの順序は任意です。  
  
 サポートされる XMLA プロパティに関する詳細については[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](propertylist-element-supported-xmla-properties.md)です。  
  
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
  
  