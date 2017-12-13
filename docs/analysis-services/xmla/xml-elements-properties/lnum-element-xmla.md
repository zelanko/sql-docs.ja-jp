---
title: "LNum 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
apiname: LNum Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.lnum
- urn:schemas-microsoft-com:xml-analysis#LNum
- http://schemas.microsoft.com/analysisservices/2003/engine#LNum
helpviewer_keywords: LNum element
ms.assetid: 7b9cc143-0c5e-4a8c-a288-8921bfcfd103
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1c5d42bebd4740b7a4c741cfffa9d7762cd2a6bc
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="lnum-element-xmla"></a>LNum 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]親のレベルの序数位置に関する情報を格納[HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md)または[メンバー](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <LNum>...</LNum>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|int|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md)、[メンバー](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **HierarchyInfo** 、要素、 **LNum**要素には、階層のレベルの序数位置を表すプロパティの名前が含まれています。 値は、OLE DB for OLAP 仕様で軸行セットに関して定義されている、LEVEL_NUMBER プロパティと同等です。  
  
 **メンバー** 、要素、 **LNum**要素には、0 から始まる序数の位置、階層のルート レベルから親によって表されるメンバーにはが含まれています[メンバー](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)。要素。 値 0 は、階層のルート レベルを表します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
