---
title: Tuples 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c0578c541c39bdaceede6bff8afdea3d642abcef
ms.sourcegitcommit: cfe5b2af733e7801558b441b4b9427cfe4c26435
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2018
ms.locfileid: "34576864"
---
# <a name="tuples-element-xmla"></a>Tuples 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  セットを含む[組](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md)オブジェクトに対する、[軸](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)を使用する要素、 [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)によって返されるデータ型、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
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
|親要素|[Axis](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
|子要素|[組](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 クライアント アプリケーションが **AxisFormat** プロパティを *TupleFormat* に設定した場合、軸は複数の組のセットとして表されます。 各 **Axis** 要素には、その軸上の組のセットを表す 1 つの **Tuples** 要素が含まれます。 それぞれの組は **Tuple** 要素を使って表され、そこには軸上の各階層に属する [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) 要素が含まれます。  
  
## <a name="example"></a>例  
 次の例の構造を示しています、**組**クライアントを指定すると要素*TupleFormat*または*CustomFormat*の**AxisFormat** XML for Analysis (XMLA) プロパティ、軸の次のメンバーを指定します。  
  
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
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
