---
title: PropertyList 要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PropertyList Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#PropertyList
- microsoft.xml.analysis.propertylist
- urn:schemas-microsoft-com:xml-analysis#PropertyList
helpviewer_keywords:
- PropertyList element
ms.assetid: 58e63bd9-8aac-438d-adba-1868b4d123f5
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e4f337d96be6d9fe960a70953b27413b2f5aedb1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="propertylist-element-xmla"></a>PropertyList 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]使用される Analysis (XMLA) プロパティの XML のコレクションを格納、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)と[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Properties>  
   <PropertyList>  
      <!-- Zero or more XMLA properties -->  
   </PropertyList>  
</Properties>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[プロパティ](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)|  
|子要素|XMLA プロパティ (「解説」を参照)|  
  
## <a name="remarks"></a>Remarks  
 **PropertyList** 要素は、XMLA プロパティのコレクションを含みます。 ユーザーはそれぞれのプロパティを使用して、 **Discover** または **Execute** メソッドのいくつかの側面を制御できます。たとえば、データ ソースへの接続に必要な情報の定義、返される結果セットの形式の指定、データを書式設定する際のロケールの指定などを制御できます。 **PropertyList** 要素内のそれぞれの XMLA プロパティは、個別の XML 要素によって定義されます。 XMLA プロパティの値は XML 要素に含まれるデータで、XMLA プロパティの名前は XML 要素の名前に対応します。  
  
 使用可能なプロパティとその値は、 **Discover** メソッドで要求の種類として DISCOVER_PROPERTIES を使用することによって取得できます。 **PropertyList** 要素内に一覧表示されるプロパティの順序は任意です。  
  
 サポートされる XMLA プロパティに関する詳細については[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を参照してください[サポートされる XMLA プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
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
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
