---
title: "軸の要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
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
apiname: Axes Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- Axes
- http://schemas.microsoft.com/analysisservices/2003/engine#Axes
- microsoft.xml.analysis.axes
- urn:schemas-microsoft-com:xml-analysis#Axes
helpviewer_keywords: Axes element
ms.assetid: 2005d06a-f8a2-4b4f-8c0d-2f7f73eb6f5c
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: facdfe5f8f4a03c5fcacff459dac78cb330f8f3b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="axes-element-xmla"></a>Axes 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]コレクションを格納[軸](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)要素に含まれる軸データを表す、[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)を使用する要素、 [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)データ型。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <Axes>  
      <Axis>...</Axis>  
   </Axes>  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Any|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|子要素|[Axis](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 下にある、**軸**要素、**軸**要素は、0 から始まる、データセット内の出現順序で一覧表示されます。 **AxisFormat** XMLA プロパティの設定の決定方法**軸**要素が書式設定します。 詳細については、 **AxisFormat**プロパティを参照してください[サポートされる XMLA プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 軸は、次元が同じである複数の組から成るセットを表します。 1 つのセットを表す方法はいくつかあり、それぞれの方法に利点があります。 たとえば、次のような 4 つの組から成るセットは、2 次元の組のコレクションとして表すことも、2 つの 1 次元セットのデカルト積として表すこともできます。  
  
|1999|1999|2000|2000|  
|----------|----------|----------|----------|  
|Actual|Budget|Actual|Budget|  
  
 この組のセットは、2 次元の組のコレクションとして次のように表すことができます。  
  
```  
{ ( 1999, Actual ), ( 1999, Budget ), ( 2000, Actual ), ( 2000, Budget ) }  
```  
  
 このセットは、2 つの 1 次元セットのデカルト積として次のように表すこともできます。  
  
```  
{ 1999, 2000 } x { Actual, Budget }  
```  
  
 クライアント ツールにとって、最初の表記方法 (2 次元の組) の方が簡単に使用できます。 2 番目の表記方法 (1 次元のセットのデカルト積) はスペース使用量がより少なく、セットの多次元的な性質を保持しています。  
  
 次の表は、軸の構造とメンバーを定義して特徴付けるために使用できる操作の一覧です。  
  
|操作|Description|  
|---------------|-----------------|  
|メンバー|ディメンション階層のメンバーを表す軸の最小単位です。|  
|メンバー|コレクション**メンバー**オブジェクトから同じディメンション階層。|  
|組|異なるディメンション階層に属するメンバーのコレクションです。|  
|組|コレクション**組**同じ次元を持つオブジェクト。|  
|Union|複数のセットの和集合です。|  
|CrossJoin|複数のセットのデカルト積です。|  
  
 これらの操作は、2 次元の組および 1 次元セットのデカルト積を次のように変換します。  
  
## <a name="two-dimensional-tuples"></a>2 次元の組  
  
```  
Tuples (  
   Tuple( Member(1999), Member(Actual) ),  
   Tuple( Member(1999), Member(Budget) ),  
   Tuple( Member(2000), Member(Actual) ),  
   Tuple( Member(2000), Member(Budget) )  
```  
  
## <a name="cartesian-product-of-one-dimensional-sets"></a>1 次元セットのデカルト積  
  
```  
CrossProduct (  
   Members( Member(1999), Member(2000) ),  
   Members( Member(Actual), Member(Budget) )  
```  
  
 クライアントが使用できる、 **AxisFormat**プロパティを特定の表現を要求します。  
  
## <a name="see-also"></a>参照  
 [MDDataSet データ型 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)   
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
