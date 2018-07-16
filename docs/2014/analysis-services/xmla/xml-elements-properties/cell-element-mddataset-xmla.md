---
title: セル要素 (MDDataSet) (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Cell Element (MDDataSet)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cell
- http://schemas.microsoft.com/analysisservices/2003/engine#Cell
- urn:schemas-microsoft-com:xml-analysis#Cell
helpviewer_keywords:
- Cell element
ms.assetid: c4ea08a4-f653-4ade-be07-b91eb5b1ef32
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f07798a28c59597575de08bf5d0f3ea1d7087c8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37269508"
---
# <a name="cell-element-mddataset-xmla"></a>Cell 要素 (MDDataSet) (XMLA)
  親に含まれる 1 つのセルに関する情報を格納[CellData](celldata-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CellData>  
   <Cell CellOrdinal="unsignedInt">  
      <!-- Zero or more cell property values -->  
      <!-- or -->  
      <Error>...</Error>  
   </Cell>  
</CellData>  
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
|親要素|[CellData](celldata-element-xmla.md)|  
|子要素|0 個以上のセル プロパティの値または[エラー](error-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|CellOrdinal|必要な`unsignedInt`属性。 多次元データセット内におけるセルの位置を表す序数です。|  
  
## <a name="remarks"></a>コメント  
 親の `root` 要素の中では、`Axes` 要素の後に `CellData` 要素が続きます。これは、多次元データセットに返される各セルのプロパティ値を含む `Cell` 要素のコレクションです。 `Cell` 要素には、`CellOrdinal` 属性 (多次元データセット内におけるセルの位置を表す 0 から始まる序数を示します)、およびセルに関連付けられている各セル プロパティ値に対応する要素が含まれます。 `Cell` 要素のセル プロパティ値は、それぞれ個別の XML 要素によって定義されます。 セル プロパティの値は XML 要素に含まれる値であり、セル プロパティの名前は、親のルート要素の `CellInfo` 要素で定義されるとおり、XML 要素の名前に対応します。  
  
 セル プロパティ値の構文は次のとおりです。  
  
```  
<CellProperty xsi:type="string">value</CellProperty>  
```  
  
 セル プロパティ値のデータ型は、VALUE セル プロパティについてのみ指定できます。 他のセル プロパティのデータ型は、`CellInfo` 要素に含まれるセル プロパティ定義によって決まります。 セル プロパティ値の要素は、セル プロパティの既定値が指定されている場合 (`Default` 要素に含まれるセル プロパティ定義に `CellInfo` 要素を含めることによって)、あるいは既定値が指定されておらずセル プロパティが NULL の場合、除外することができます。  
  
## <a name="cell-property-errors"></a>セル プロパティのエラー  
 計算エラーのために特定のセルの値を返すことができない場合など、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスで発生するエラーのためにセル プロパティを返すことができない場合は、該当するセル プロパティの内容が `Error` 要素に置き換えられます。 次の XML の例は、セル プロパティのエラーを示しています。  
  
```  
<Cell CellOrdinal="0">  
   <Value xsi:type="xsd:double">  
      <Error>  
         <ErrorCode>2148497527</ErrorCode>  
         <Description>Unknown error</Description>  
      </Error>  
   </Value>  
</Cell>  
```  
  
## <a name="calculating-cell-ordinal-values"></a>セルの序数値の計算  
 セルの軸参照は、`CellOrdinal` 属性値に基づいて計算することができます。 概念的には、セルの番号付けは、データセット内のデータセットが、 *p*の次元の配列を*p*軸の数です。 セルは、行優先順で指定されます。  
  
 たとえば、列に関して 4 つのメジャーと、行に関して 3 つの州と 4 つの四半期のクロス積を要求するクエリがあるとします。 以下のデータセットの結果では、結果セットのうち太字で示した部分の `CellOrdinal` プロパティは、{9, 10, 11, 13, 14, 15, 17, 18, 19} というセットになります。 これは、セルの番号付けが、左上のセルの `CellOrdinal` を 0 として行優先順で行われるためです。  
  
|状態|Quarter|Unit sales|Store cost|Store sales|Sales count|  
|-----------|-------------|----------------|----------------|-----------------|-----------------|  
|California|第 1 四半期|16890|14431.09|36175.2|5498|  
||第 2 四半期|18052|15332.02|38396.75|5915|  
||第 3 四半期|18370|**15672.83**|**39394.05**|**6014**|  
||第 4 四半期|21436|**18094.5**|**45201.84**|**7015**|  
|Oregon|第 1 四半期|19287|**16081.07**|**40170.29**|**6184**|  
||第 2 四半期|15079|12678.96|31772.88|4799|  
||第 3 四半期|16940|14273.78|35880.46|5432|  
||第 4 四半期|16353|13738.68|34453.44|5196|  
|Washington|第 1 四半期|30114|25240.08|63282.86|9906|  
||第 2 四半期|29479|24953.25|62496.64|9654|  
||第 3 四半期|30538|25958.26|64997.38|10007|  
||第 4 四半期|34235|29172.72|73016.34|11217|  
  
 図に示されている公式を適用する場合、軸 k = 0 のメンバーの数は Uk = 4 で、軸 k = 1 の組の数は Uk = 8 です。 クエリ内の軸の総数は P = 2 です。 {California, Q3, Store Cost} のセルを S0 とすると、最初の合計は i = 0 ～ 1 です。 i = 0 の場合、軸 0 の組 {Store Cost} の序数は 1 です。 i = 1 の場合、組 {CA, Q3} の序数は 2 です。  
  
 0、Ei = = 1、ためは 0 を = 合計が 1 * 1 = 1 とは = 1、合計は 4 回 2 (組の序数) (1 として計算された Ei の値\*4)、または 8。 1 + 8 の合計は 9 であり、これが目的のセルの序数になります。  
  
## <a name="example"></a>例  
 次の例は、各セルの VALUE、FORMATTED_VALUE、および FORMAT_STRING セル プロパティ値を含む `Cell` 要素の構造を示しています。  
  
```  
<CellData>  
   <Cell CellOrdinal="0">  
      <Value xsi:type="xsd:double">16890</Value>  
      <FmtValue>16,890.00</FmtValue>  
      <FormatString>Standard</FormatString>  
   </Cell>  
   <Cell CellOrdinal="1">  
      <Value xsi:type="xsd:int">50</Value>  
      <FmtValue>50</FmtValue>  
      <FormatString>Standard</FormatString>  
   </Cell>  
   <Cell CellOrdinal="2">  
      <Value xsi:type="xsd:double">36175.2</Value>  
      <FmtValue>$36,175.20</FmtValue>  
      <FormatString>Currency</FormatString>  
   </Cell>  
</CellData>  
```  
  
## <a name="see-also"></a>参照  
 [MDDataSet データ型&#40;XMLA&#41;](../xml-data-types/mddataset-data-type-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
