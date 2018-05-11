---
title: CrossProduct 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f67968b92fe879a6675222ed57306fca9a317b31
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="crossproduct-element-xmla"></a>CrossProduct 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  各階層のメンバーの順序付けされたセットの間のクロス積を含む、[軸](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)を使用する要素、 [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)によって返されるデータ型、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
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
|親要素|[軸](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
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
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
