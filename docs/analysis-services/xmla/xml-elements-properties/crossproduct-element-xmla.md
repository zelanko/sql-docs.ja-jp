---
title: "CrossProduct 要素 (XMLA) |Microsoft ドキュメント"
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
apiname: CrossProduct Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#CrossProduct
- microsoft.xml.analysis.crossproduct
- urn:schemas-microsoft-com:xml-analysis#CrossProduct
helpviewer_keywords: CrossProduct element
ms.assetid: a9a1584e-d2dd-45db-a918-d694c20d8189
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 76d36d6f020ecfca7984a35ae36148273c38d0d0
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="crossproduct-element-xmla"></a>CrossProduct 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]各階層のメンバーの順序付けされたセットの間のクロス積を含む、[軸](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)を使用する要素、 [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)によって返されるデータ型、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Axis>  
   ...  
   <CrossProduct Size="integer">  
      <Members>...</Members>  
   </CrossProduct>  
   ...  
</Axis>  
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
|親要素|[Axis](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
|子要素|[メンバー](../../../analysis-services/xmla/xml-elements-properties/members-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|Description|  
|---------------|-----------------|  
|サイズ|必要な**整数**属性。 によって表されるクロス積に含まれる組の数を示す、 **CrossProduct**要素。|  
  
## <a name="remarks"></a>解説  
 クライアント アプリケーションを設定した場合、 **AxisFormat**プロパティを*ClusterFormat*、各軸上のメンバーはこれでは、各クラスターは順序付けされたセットの間のクロス積を表しますクラスターに分割。各階層のメンバーです。 各クラスターで表される、 **CrossProduct**要素。 各**CrossProduct**要素が含まれています、**メンバー**軸上の各階層の要素。 A **CrossProduct**要素が 1 つの階層からメンバーを含めることができます。  
  
## <a name="example"></a>例  
 次の例の構造を示しています、 **CrossProduct**クライアントを指定すると要素*ClusterFormat*の**AxisFormat** XMLA プロパティ、次の軸のメンバー。  
  
||||||  
|-|-|-|-|-|  
|**Time** 階層|1999|1999|2000|2001|  
|**Category** 階層|Actual|Budget|Budget|Budget|  
|Clusters|クラスター 1|クラスター 1|クラスター 1|Cluster 2|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <CrossProduct Size="4">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
      <CrossProduct Size="1">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[2001]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
