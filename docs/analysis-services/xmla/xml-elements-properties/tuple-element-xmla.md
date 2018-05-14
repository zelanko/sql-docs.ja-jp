---
title: Tuple 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9f7f7d21f64c502e60ee0f6c95d2b6cbfd09c1b7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="tuple-element-xmla"></a>Tuple 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親要素 [Tuples](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md) に含まれる、[Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) 要素のコレクションを含みます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Tuples>  
   <Tuple>  
      <Member>...</Member>  
   </Tuple>  
   ...  
</Tuples>  
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
|親要素|[組](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md)|  
|子要素|[メンバー](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 クライアント アプリケーションが **AxisFormat** プロパティを *TupleFormat* に設定した場合、軸は複数の組のセットとして表されます。 各 **Axis** 要素には、その軸上の組のセットを表す 1 つの **Tuples** 要素が含まれます。 それぞれの組は **Tuple** 要素を使って表され、そこには軸上の各階層に属する **Member** 要素が含まれます。  
  
## <a name="example"></a>例  
 次の例は、クライアントが **AxisFormat** XMLA プロパティに *TupleFormat* または *CustomFormat* を指定した場合の **Tuple** 要素の構造を示しています。ここで、軸のメンバーは以下のとおりです。  
  
|||||  
|-|-|-|-|  
|**Time** 階層|1999|1999|2000|  
|**Category** 階層|Actual|Budget|Budget|  
  
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
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
