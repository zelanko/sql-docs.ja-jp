---
title: "Axis 要素 (XMLA) |Microsoft ドキュメント"
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
apiname: Axis Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.axis
- http://schemas.microsoft.com/analysisservices/2003/engine#Axis
helpviewer_keywords: Axis element
ms.assetid: 336895e1-4a57-4b43-9a53-e31569866e6c
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 790fdec7656fa1af8b273a2a3ca7941933480be4
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="axis-element-xmla"></a>Axis 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]含まれる多次元データセット内の 1 つの軸を表すために使用する組のセットが含まれています、[軸](../../../analysis-services/xmla/xml-elements-properties/axes-element-xmla.md)を使用する要素、 [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)によって返されるデータ型、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Axes>  
   ...  
   <Axis> <!-- when AxisFormat XMLA property is set to ClusterFormat -->  
      <CrossProduct>...</CrossProduct>  
   </Axis>  
   <Axis> <!-- when AxisFormat XMLA property is set to TupleFormat or CustomFormat -->  
      <Tuples>...</Tuples>  
   </Axis>  
   ...  
</Axes>  
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
|親要素|[軸](../../../analysis-services/xmla/xml-elements-properties/axes-element-xmla.md)|  
|子要素|[CrossProduct](../../../analysis-services/xmla/xml-elements-properties/crossproduct-element-xmla.md)または[組](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 内容、**軸**要素の値によって異なります、 **AxisFormat**で使用される XMLA プロパティ、 **Execute**メソッドです。  
  
## <a name="tupleformat"></a>TupleFormat  
 クライアント アプリケーションが **AxisFormat** プロパティを *TupleFormat* に設定した場合、軸は複数の組のセットとして表されます。 各**軸**要素が含まれています、**組**その軸の組のセットを表す要素。 それぞれの組は **Tuple** 要素を使って表され、そこには軸上の各階層に属する **Member** 要素が含まれます。  
  
## <a name="clusterformat"></a>ClusterFormat  
 クライアント アプリケーションを設定した場合、 **AxisFormat**プロパティを*ClusterFormat*、各軸上のメンバーはこれでは、各クラスターは順序付けされたセットの間のクロス積を表しますクラスターに分割。各階層のメンバーです。 各**軸**要素は、1 つ以上の**CrossProduct**要素。 各**CrossProduct**要素が含まれています、**メンバー**軸上の各階層の要素。  
  
## <a name="customformat"></a>CustomFormat  
 クライアント アプリケーションを設定した場合、 **AxisFormat**プロパティを*CustomFormat*、値の処理と同じ、 *TupleFormat* Analysis Services インスタンスによっての値。  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>Description  
 次の例の構造を示しています、**軸**クライアントを指定すると要素*TupleFormat*または*CustomFormat*の**AxisFormat** XMLA プロパティ、軸の次のメンバーを指定します。  
  
|||||  
|-|-|-|-|  
|**Time** 階層|1999|1999|2000|  
|**Category** 階層|Actual|Budget|Budget|  
  
### <a name="code"></a>コード  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <Tuples>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
      </Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
### <a name="description"></a>Description  
 次の例の構造を示しています、**軸**クライアントを指定すると要素*ClusterFormat*の**AxisFormat**という、XMLA プロパティ軸のメンバー:  
  
||||||  
|-|-|-|-|-|  
|**Time** 階層|1999|1999|2000|2001|  
|**Category** 階層|Actual|Budget|Budget|Budget|  
|Clusters|クラスター 1|クラスター 1|クラスター 1|Cluster 2|  
  
### <a name="code"></a>コード  
  
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
  
  
