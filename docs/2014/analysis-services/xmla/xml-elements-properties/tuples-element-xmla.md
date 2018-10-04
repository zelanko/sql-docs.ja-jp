---
title: Tuples 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Tuples Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Tuples
- microsoft.xml.analysis.tuples
- urn:schemas-microsoft-com:xml-analysis#Tuples
helpviewer_keywords:
- Tuples element
ms.assetid: 5494bbaa-c1aa-43fa-b3e0-83befb2bccdd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 36f29edb149ab6a5c7c22dfe87c4d630289f29cd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128022"
---
# <a name="tuples-element-xmla"></a>Tuples 要素 (XMLA)
  セットを含む[タプル](tuple-element-xmla.md)オブジェクトに対する、[軸](axis-element-xmla.md)を使用する要素、 [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md)によって返されるデータ型、 [Execute](../xml-elements-methods-execute.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Axis>  
   ...  
   <Tuples>  
      <Tuple>...</Tuple>  
   </Tuples>  
   ...  
</Axis>  
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
|親要素|[Axis](axis-element-xmla.md)|  
|子要素|[タプル](tuple-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 クライアント アプリケーションを設定した場合、`AxisFormat`プロパティを*TupleFormat*軸は組のセットとして表されます。 各`Axis`要素が含まれています、`Tuples`その軸上の組のセットを表す要素。 使用して表されるそれぞれの組を`Tuple`要素を含む[メンバー](member-element-xmla.md)軸上の各階層の要素。  
  
## <a name="example"></a>例  
 次の例の構造を示しています、`Tuples`要素をクライアントが指定したときに*TupleFormat*または*CustomFormat*の`AxisFormat`XML for Analysis (XMLA) のプロパティ軸の次のメンバーを指定します。  
  
|||||  
|-|-|-|-|  
|`Time` 階層|1999|1999|2000|  
|`Category` 階層|Actual|Budget|Budget|  
  
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
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
