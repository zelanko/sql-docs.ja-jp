---
title: Discover メソッド (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Discover Method
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.discover
- urn:schemas-microsoft-com:xml-analysis#Discover
- Discover
helpviewer_keywords:
- Discover method
ms.assetid: 0eb52d88-c081-416e-a229-610e4373b0b3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 91ea30a495eb76c22075007f48e3ae721504ef49
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116322"
---
# <a name="discover-method-xmla"></a>Discover メソッド (XMLA)
  インスタンスから利用可能なデータベースまたは特定のオブジェクトに関する詳細情報の一覧などの情報を取得[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]します。 `Discover` メソッドを使用して取得されるデータは、メソッドに渡されるパラメーターの値によって異なります。  
  
 **Namespace** urn: スキーマ-microsoft-'http://www.w3.org/2001/xmlschema'-分析  
  
 **SOAP アクション**"urn: スキーマ-microsoft-'http://www.w3.org/2001/xmlschema'-分析: 検出"  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Discover>  
   <RequestType>...</RequestType>  
   <Restrictions>...</Restrictions>  
   <Properties>...</Properties>  
</Discover>  
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
|親要素|なし|  
|子要素|[Properties](xml-elements-properties/properties-element-xmla.md)、 [RequestType](xml-elements-properties/type-element-xmla.md)、[Restrictions](xml-elements-properties/restrictions-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Discover` メソッドは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスとオブジェクトに関するメタデータを要求します。 XMLA を使用してメタデータが返される[行セット](xml-data-types/rowset-data-type-xmla.md)データ型。  
  
## <a name="example"></a>例  
 次のコード サンプルでは、[!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] サンプルの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースからキューブの一覧を要求するために、クライアントが `Discover` 呼び出しを送信します。  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <RequestType>MDSCHEMA_CUBES</RequestType>  
   <Restrictions>  
      <RestrictionList>  
         <CATALOG_NAME>Adventure Works DW Multidimensional 2012</CATALOG_NAME>  
      </RestrictionList>  
   </Restrictions>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Tabular</Format>  
      </PropertyList>  
   </Properties>  
</Discover>  
```  
  
## <a name="see-also"></a>参照  
 [XML データ型&#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Execute メソッド&#40;XMLA&#41;](xml-elements-methods-execute.md)   
 [メソッド&#40;XMLA&#41;](xml-elements-methods.md)   
 [XML 要素&#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [Analysis Services のスキーマ行セット](../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
