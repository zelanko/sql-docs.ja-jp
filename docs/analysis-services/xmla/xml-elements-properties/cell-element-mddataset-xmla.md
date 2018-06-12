---
title: セルの要素 (MDDataSet) (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ba73a6ea5926de6f445c5ca5cec8142b3e196bd
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34576274"
---
# <a name="cell-element-mddataset-xmla"></a>Cell 要素 (MDDataSet) (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  1 つの親が含まれているセルに関する情報を格納[CellData](../../../analysis-services/xmla/xml-elements-properties/celldata-element-xmla.md)要素。  
  
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
|親要素|[CellData](../../../analysis-services/xmla/xml-elements-properties/celldata-element-xmla.md)|  
|子要素|0 個以上のセル プロパティの値または[エラー](../../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|CellOrdinal|必要な**unsignedInt**属性。 多次元データセット内におけるセルの位置を表す序数です。|  
  
## <a name="remarks"></a>コメント  
 親の**ルート**要素、**軸**要素が続く、 **CellData**要素では、一連の**セル**を含む要素多次元データセットで返される各セルのプロパティ値。 **セル**要素が含まれています、 **CellOrdinal**属性は、多次元データセット、およびセル プロパティの値ごとに 1 つの要素内のセルの 0 から始まる序数位置を示しますセルに関連付けられています。 各セル プロパティの値を**セル**要素が、個別の XML 要素によって定義されています。 セル プロパティの値は、XML 要素、およびセル プロパティの名前に含まれるデータで定義されて、 **CellInfo**親ルート要素の要素は XML 要素の名前に対応します。  
  
 セル プロパティ値の構文は次のとおりです。  
  
```  
<CellProperty xsi:type="string">value</CellProperty>  
```  
  
 セル プロパティ値のデータ型は、VALUE セル プロパティについてのみ指定できます。 その他のセル プロパティのデータ型に含まれるセル プロパティ定義で決まります、 **CellInfo**要素。 既定値が指定されている場合は、セル プロパティ値の要素を除外することができます (を含めることによって、**既定**要素に含まれるセル プロパティ定義を**CellInfo**要素) のセル プロパティ既定値が指定されていないと、セル プロパティの値が null 場合またはします。  
  
## <a name="cell-property-errors"></a>セル プロパティのエラー  
 場合は、値が指定されたセルの返されることを防止する計算エラーなど、Analysis Services のインスタンス上で発生するエラーのためにセル プロパティを返すことはできません、**エラー**要素の内容に置き換えられます、該当するセル プロパティです。 次の XML の例は、セル プロパティのエラーを示しています。  
  
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
 軸参照セルを計算するために基づく、 **CellOrdinal**属性の値。 概念的には、セルの番号付けはデータセット内にデータセットが、 *p*の次元の配列を*p*軸の数です。 セルは、行優先順で指定されます。  
  
 たとえば、列に関して 4 つのメジャーと、行に関して 3 つの州と 4 つの四半期のクロス積を要求するクエリがあるとします。 データセットの結果を次に、 **CellOrdinal**太字で表示データセットの結果の一部のプロパティは、セット {9、10、11、13、14、15、17、18, 19}。 これは、セルが行優先順に番号付けためにのセットで始まる、 **CellOrdinal**の左上のセルの場合は 0 です。  
  
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
  
 I = 0、Ei = 1、そのためすれば = 0 合計が 1 * 1 = 1 とのすれば = 1, 合計は 2 (組の序数) 4 時間 (Ei の値は 1 として計算\*4)、または 8 です。 1 + 8 の合計は 9 であり、これが目的のセルの序数になります。  
  
## <a name="example"></a>例  
 次の例での構造、**セル**要素、VALUE、FORMATTED_VALUE、および FORMAT_STRING を含むセルの各セルのプロパティの値。  
  
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
 [MDDataSet データ型&#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
