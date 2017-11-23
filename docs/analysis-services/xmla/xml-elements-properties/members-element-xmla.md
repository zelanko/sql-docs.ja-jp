---
title: "Members 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Members Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Members
- urn:schemas-microsoft-com:xml-analysis#Members
- microsoft.xml.analysis.members
helpviewer_keywords: Members element
ms.assetid: 55f9ec3a-5a41-4b3a-acd6-c07598868c46
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2d2b4f8a9c466fa85bdd1131a58c2c11fc232967
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="members-element-xmla"></a>Members 要素 (XMLA)
  コレクションを格納[メンバー](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)親に含まれる要素[CrossProduct](../../../analysis-services/xmla/xml-elements-properties/crossproduct-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CrossProduct>  
   <Members Hierarchy="string">  
      <Member>...</Member>  
   </Members>  
   ...  
</CrossProduct>  
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
|親要素|[CrossProduct](../../../analysis-services/xmla/xml-elements-properties/crossproduct-element-xmla.md)|  
|子要素|[メンバー](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|Description|  
|---------------|-----------------|  
|階層|必要な**文字列**属性。 格納されているメンバーの階層の名前、**メンバー**要素が属しています。|  
  
## <a name="remarks"></a>解説  
 クライアント アプリケーションを設定した場合、 **AxisFormat**プロパティを*ClusterFormat*、各軸上のメンバーはこれでは、各クラスターは順序付けされたセットの間のクロス積を表しますクラスターに分割。各階層のメンバーです。 各**軸**要素は、1 つ以上の**CrossProduct**要素。 各**CrossProduct**要素が含まれています、**メンバー**軸上の各階層の要素。 **メンバー**要素がさらに、1 つ**メンバー**クロス積に含まれる指定された階層の各メンバーの要素。  
  
## <a name="example"></a>例  
 次の例の構造を示しています、**メンバー**クライアントを指定すると要素*ClusterFormat*の**AxisFormat** XMLA プロパティ、次の軸のメンバー。  
  
||||||  
|-|-|-|-|-|  
|**Time** 階層|1999|1999|2000|2001|  
|**Category** 階層|Actual|Budget|Budget|Budget|  
|Clusters|クラスター 1|クラスター 1|クラスター 1|Cluster 2|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <CrossProduct Size = "4">  
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
      <CrossProduct Size = "1">  
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
  
  
