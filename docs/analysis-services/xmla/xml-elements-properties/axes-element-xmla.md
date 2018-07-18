---
title: 軸の要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3a8dfff1c8a551157661bcb1de5700bf51a7f914
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38038020"
---
# <a name="axes-element-xmla"></a>Axes 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  コレクションを格納 [Axis](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) 要素に含まれる軸データを表す、[root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) を使用する要素、[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) データ型。  
  
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
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|子要素|[Axis](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 下にある、**Axis** 要素、**Axis** 要素は、0 から始まる、データセット内の出現順序で一覧表示されます。 **AxisFormat** XMLA プロパティの設定の決定方法 **Axis** 要素が書式設定します。 詳細については、 **AxisFormat**プロパティを参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)です。  
  
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
|Members|同じディメンション階層に属する **Member** オブジェクトのコレクションです。|  
|Tuple|異なるディメンション階層に属するメンバーのコレクションです。|  
|Tuples|同じ次元を持つ **Tuple** オブジェクトのコレクションです。|  
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
 [MDDataSet データ型&#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
