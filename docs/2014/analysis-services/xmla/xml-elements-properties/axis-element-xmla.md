---
title: Axis 要素 (XMLA) |Microsoft Docs
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
- Axis Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.axis
- http://schemas.microsoft.com/analysisservices/2003/engine#Axis
helpviewer_keywords:
- Axis element
ms.assetid: 336895e1-4a57-4b43-9a53-e31569866e6c
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e3e68903dc828f4b14ac60892d1b6fc2baed2f30
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263228"
---
# <a name="axis-element-xmla"></a>Axis 要素 (XMLA)
  含まれる多次元データセット内の 1 つの軸を表すために使用する組のセットを含む、[軸](axes-element-xmla.md)を使用する要素、 [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md)によって返されるデータ型、 [Execute](../xml-elements-methods-execute.md)メソッド。  
  
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
|親要素|[軸](axes-element-xmla.md)|  
|子要素|[CrossProduct](crossproduct-element-xmla.md)または[タプル](tuples-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Axis` 要素の内容は、`AxisFormat` メソッドによって使用される XMLA プロパティ `Execute` の値に応じて異なります。  
  
## <a name="tupleformat"></a>TupleFormat  
 クライアント アプリケーションを設定した場合、`AxisFormat`プロパティを*TupleFormat*軸は組のセットとして表されます。 各 `Axis` 要素には、その軸上の組のセットを表す 1 つの `Tuples` 要素が含まれます。 それぞれの組は `Tuple` 要素を使用して表され、この要素には軸上の各階層に属する `Member` 要素が含まれます。  
  
## <a name="clusterformat"></a>ClusterFormat  
 クライアント アプリケーションを設定した場合、`AxisFormat`プロパティを*ClusterFormat*、各軸のメンバーは、各クラスターは各階層のメンバーの順序付けされたセット間のクロス積を表します。 クラスターに分けられます。 各 `Axis` 要素は、1 つ以上の `CrossProduct` 要素から成っています。 それぞれの `CrossProduct` 要素には、軸上の各階層に対する 1 つの `Members` 要素が含まれます。  
  
## <a name="customformat"></a>CustomFormat  
 クライアント アプリケーションを設定した場合、`AxisFormat`プロパティを*CustomFormat*、値の処理と同じ、 *TupleFormat* Analysis Services インスタンスによっての値。  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>説明  
 次の例の構造を示しています、`Axis`クライアントを指定する場合に要素*TupleFormat*または*CustomFormat*の`AxisFormat`次を指定された、XMLA プロパティ軸のメンバー:  
  
|||||  
|-|-|-|-|  
|`Time` 階層|1999|1999|2000|  
|`Category` 階層|Actual|Budget|Budget|  
  
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
  
### <a name="description"></a>説明  
 次の例の構造を示しています、`Axis`クライアントを指定する場合に要素*ClusterFormat*の`AxisFormat`軸の次のメンバーが指定の XMLA プロパティ。  
  
||||||  
|-|-|-|-|-|  
|`Time` 階層|1999|1999|2000|2001|  
|`Category` 階層|Actual|Budget|Budget|Budget|  
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
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
