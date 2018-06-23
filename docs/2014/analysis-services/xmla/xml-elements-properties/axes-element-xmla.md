---
title: 軸の要素 (XMLA) |Microsoft ドキュメント
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
- Axes Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Axes
- http://schemas.microsoft.com/analysisservices/2003/engine#Axes
- microsoft.xml.analysis.axes
- urn:schemas-microsoft-com:xml-analysis#Axes
helpviewer_keywords:
- Axes element
ms.assetid: 2005d06a-f8a2-4b4f-8c0d-2f7f73eb6f5c
caps.latest.revision: 21
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: f508a92ca7ab8aca224c299723adddf3654c167c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163940"
---
# <a name="axes-element-xmla"></a>Axes 要素 (XMLA)
  コレクションを格納 [Axis](axis-element-xmla.md) 要素に含まれる軸データを表す、[root](root-element-xmla.md) を使用する要素、[MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) データ型。  
  
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
|親要素|[root](root-element-xmla.md)|  
|子要素|[Axis](axis-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Axes` 要素の下には、データセット内の出現順序に従って、0 から始まる複数の `Axis` 要素がリストされます。 XMLA プロパティ設定 `AxisFormat` は、`Axis` 要素の書式を決定します。 詳細については、`AxisFormat`プロパティを参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](propertylist-element-supported-xmla-properties.md)です。  
  
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
  
|演算|説明|  
|---------------|-----------------|  
|Member|ディメンション階層のメンバーを表す軸の最小単位です。|  
|Members|同じディメンション階層に属する `Member` オブジェクトのコレクションです。|  
|Tuple|異なるディメンション階層に属するメンバーのコレクションです。|  
|Tuples|同じ次元を持つ `Tuple` オブジェクトのコレクションです。|  
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
  
 クライアントは `AxisFormat` プロパティを使用して、特定の表記を要求することができます。  
  
## <a name="see-also"></a>参照  
 [MDDataSet データ型&#40;XMLA&#41;](../xml-data-types/mddataset-data-type-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  