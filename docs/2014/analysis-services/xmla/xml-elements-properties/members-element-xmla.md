---
title: Members 要素 (XMLA) |Microsoft Docs
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
- Members Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Members
- urn:schemas-microsoft-com:xml-analysis#Members
- microsoft.xml.analysis.members
helpviewer_keywords:
- Members element
ms.assetid: 55f9ec3a-5a41-4b3a-acd6-c07598868c46
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 37eb0532f56fd4aff8ca760b843697f30f3c9585
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201962"
---
# <a name="members-element-xmla"></a>Members 要素 (XMLA)
  コレクションを含む[メンバー](member-element-xmla.md)親に含まれる要素[CrossProduct](crossproduct-element-xmla.md)要素。  
  
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
|親要素|[CrossProduct](crossproduct-element-xmla.md)|  
|子要素|[Member](member-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|Hieararchy|必要な`String`属性。 `Members` 要素に含まれるメンバーが属する階層の名前です。|  
  
## <a name="remarks"></a>コメント  
 クライアント アプリケーションを設定した場合、`AxisFormat`プロパティを*ClusterFormat*、各軸のメンバーは、各クラスターは各階層のメンバーの順序付けされたセット間のクロス積を表します。 クラスターに分けられます。 各 `Axis` 要素は、1 つ以上の `CrossProduct` 要素から成っています。 それぞれの `CrossProduct` 要素には、軸上の各階層に対する 1 つの `Members` 要素が含まれます。 さらに、`Members` 要素には、クロス積に含まれる指定された階層のメンバーごとに 1 つの `Member` 要素が含まれます。  
  
## <a name="example"></a>例  
 次の例の構造を示しています、`Members`要素をクライアントが指定したときに*ClusterFormat*の`AxisFormat`軸の次のメンバーが指定の XMLA プロパティ。  
  
||||||  
|-|-|-|-|-|  
|`Time` 階層|1999|1999|2000|2001|  
|`Category` 階層|Actual|Budget|Budget|Budget|  
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
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
