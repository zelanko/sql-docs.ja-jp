---
title: SELECT ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 83a381e36a31542d6ad39ed9d26864350004af5c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68891151"
---
# <a name="mdx-data-manipulation---select"></a>MDX データ操作 - SELECT


  指定されたキューブからデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
[ WITH <SELECT WITH clause>   
   [ , <SELECT WITH clause>...n ]   
]   
SELECT   
     [ *   
    | ( <SELECT query axis clause>   
                  [ , <SELECT query axis clause>,...n ]   
            )   
            ]  
FROM   
   <SELECT subcube clause>   
      [ <SELECT slicer axis clause> ]  
      [ <SELECT cell property list clause> ]  
  
<SELECT WITH clause> ::=  
     ( CELL CALCULATION <CREATE CELL CALCULATION body clause> )   
   | ( [ CALCULATED ] MEMBER <CREATE MEMBER body clause>)   
   | ( SET <CREATE SET body clause>)  
   | ( MEASURE = <measure body clause> )  
  
<SELECT query axis clause> ::=  
   [ NON EMPTY ] Set_Expression  
   [ <SELECT dimension property list clause> ]   
      ON   
            Integer_Expression   
       | AXIS(Integer)   
       | COLUMNS   
       | ROWS   
       | PAGES   
       | SECTIONS   
       | CHAPTERS   
  
<SELECT subcube clause> ::=  
      Cube_Name   
   | [NON VISUAL] (SELECT   
                  [ *   
       | ( <SELECT query axis clause> [ ,   
           <SELECT query axis clause>,...n ] )   
         ]   
            FROM   
         <SELECT subcube clause>   
         <SELECT slicer axis clause> )  
  
<SELECT slicer axis clause> ::=   
      WHERE Tuple_Expression  
  
<SELECT cell property list clause> ::=   
   [ CELL ] PROPERTIES CellProperty_Name   
      [ , CellProperty_Name,...n ]  
  
<SELECT dimension property list clause> ::=  
   [DIMENSION] PROPERTIES   
      (DimensionProperty_Name   
         [,DimensionProperty_Name,...n ] )   
    | (LevelProperty_Name   
         [, LevelProperty_Name,...n ] )   
    | (MemberProperty_Name   
         [, MemberProperty_Name,...n ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
 *以外*  
 0 ～ 127 の整数値です。  
  
 *Cube_Name*  
 キューブ名を提供する有効な文字列です。  
  
 *Tuple_Expression*  
 組を返す有効な多次元式 (MDX) 式です。  
  
 *CellProperty_Name*  
 セルプロパティを表す有効な文字列。  
  
 *DimensionProperty_Name*  
 ディメンションプロパティを表す有効な文字列です。  
  
 *LevelProperty_Name*  
 レベルプロパティを表す有効な文字列です。  
  
 *MemberProperty_Name*  
 メンバー プロパティを表す有効な文字列です。  
  
## <a name="remarks"></a>解説  
 
  `<SELECT slicer axis clause>` 式には、指定した `<SELECT query axis clause>` 式で参照されるディメンションと階層以外のメンバーを指定する必要があります。  
  
 指定した `<SELECT query axis clause>` 式と `<SELECT slicer axis clause>` 値でキューブ内の属性が省略されている場合は、属性の既定のメンバーが暗黙的にスライサー軸に追加されます。  
  
 サブセレクト ステートメントで NON VISUAL オプションを使用すると、フィルター選択された合計ではなく、実際の合計を維持しながら、メンバーを除外することができます。 これにより、上位 10 件の売上 (販売員、製品、地域) のクエリを実行するときに、返された上位 10 件の売上の合計額ではなく、クエリ対象となるすべてのメンバーに対する実際の売上合計を取得することができます。 詳細については、以下の例を参照してください。  
  
 接続文字列パラメーターサブクエリを\<使用して接続を開いたときに、計算されるメンバーを SELECT クエリ軸句> に含めることができます *= 1*;パラメーターの使用法については<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> 、「 [Xmla&#41;&#40;サポートされる xmla プロパティ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)」を参照してください。 サブセレクトの計算されるメンバーには、例が用意されています。  
  
## <a name="autoexists"></a>autoexists  
 SELECT ステートメントに特定のディメンションの属性を複数使用した場合、こうした属性のメンバーは、Analysis Services が属性の式を評価する際、それ以外のすべての属性の条件を満たすよう、適切に絞り込まれます。 たとえば、Geography ディメンションの属性を指定したとします。 一方の式で City 属性のすべてのメンバーを返し、もう一方の式で Country 属性のメンバーを、欧州内の国のみに限定した場合、結果として得られる City メンバーは、欧州の国に属する市区町村に限定されます。 Analysis Services が備えているこの特性は Autoexists と呼ばれ、同じディメンション内の属性にのみ適用されます。 Autoexists が同じディメンションの属性にのみ適用されるのは、一方の属性式で排除されたディメンション レコードが、もう一方の属性式で含められるのを防ぐように機能するためです。 ディメンション レコードに複数の属性式を適用した結果の共通集合と考えることもできます。 次の例を考えてみてください。  
  
 `//Obtain the Top 10 best reseller selling products by Name`  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 取得される結果セットは次のとおりです。  
  
|||||  
|-|-|-|-|  
||**再販業者の売上高**|**割引額**|**PCT 割引**|  
|**山地-200**|**$14356699.36**|**$19012.71**|**0.13%**|  
|**道路-250**|**$9377457.68**|**$4032.47**|**0.04%**|  
|**山地-100**|**$8568958.27**|**$139393.27**|**1.63%**|  
|**道路-650**|**$7442141.81**|**$39698.30**|**0.53%**|  
|**ツーリング-1000**|**$6723794.29**|**$166144.17**|**2.47%**|  
|**道路-550-W**|**$3668383.88**|**$1901.97**|**0.05%**|  
|**道路-350-W**|**$3665932.31**|**$20946.50**|**0.57%**|  
|**HL マウンテンフレーム**|**$3365069.27**|**$174.11**|**0.01%**|  
|**道路-150**|**$2363805.16**|**$0.00**|**0.00%**|  
|**ツーリング-3000**|**$2046508.26**|**$79582.15**|**3.89%**|  
  
 取得された製品のセットは、Preferred10Products と同じであるように見えます。そこで、Preferred10Products のセットを検証してみることにします。  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Preferred10Products on 1`  
  
 `from [Adventure Works]`  
  
 次の結果から、両方のセット (Top10SellingProducts と Preferred10Products) が同一であることがわかります。  
  
|||||  
|-|-|-|-|  
||**再販業者の売上高**|**割引額**|**PCT 割引**|  
|**山地-200**|**$14356699.36**|**$19012.71**|**0.13%**|  
|**道路-250**|**$9377457.68**|**$4032.47**|**0.04%**|  
|**山地-100**|**$8568958.27**|**$139393.27**|**1.63%**|  
|**道路-650**|**$7442141.81**|**$39698.30**|**0.53%**|  
|**ツーリング-1000**|**$6723794.29**|**$166144.17**|**2.47%**|  
|**道路-550-W**|**$3668383.88**|**$1901.97**|**0.05%**|  
|**道路-350-W**|**$3665932.31**|**$20946.50**|**0.57%**|  
|**HL マウンテンフレーム**|**$3365069.27**|**$174.11**|**0.01%**|  
|**道路-150**|**$2363805.16**|**$0.00**|**0.00%**|  
|**ツーリング-3000**|**$2046508.26**|**$79582.15**|**3.89%**|  
  
 前の例では、2つのセットを作成しました。1つは計算式、もう1つは定数式です。 これらの例は、さまざまな種類の Autoexists を示しています。  
  
 Autoexists は、式にディープまたは浅いを適用できます。 既定の設定は deep です。 次の例が示しているのは、deep Autoexists の概念です。 この例では、[Mountain] グループの製品について、[Product].[Product Line] 属性で Top10SellingProducts をフィルター処理します。 どちらの属性 (スライサーおよび軸) も同じディメンション ([Product]) に属している点に注意してください。  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `// Preferred10Products set removed for clarity`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 結果セットは、次のようになります。  
  
|||||  
|-|-|-|-|  
||**再販業者の売上高**|**割引額**|**PCT 割引**|  
|**山地-200**|**$14356699.36**|**$19012.71**|**0.13%**|  
|**山地-100**|**$8568958.27**|**$139393.27**|**1.63%**|  
|**HL マウンテンフレーム**|**$3365069.27**|**$174.11**|**0.01%**|  
|**山地-300**|**$1907249.38**|**$876.95**|**0.05%**|  
|**Mountain-500**|**$1067327.31**|**$17266.09**|**1.62%**|  
|**山地-400-W**|**$592450.05**|**$303.49**|**0.05%**|  
|**LL マウンテンフレーム**|**$521864.42**|**$252.41**|**0.05%**|  
|**ML マウンテンフレーム-W**|**$482953.16**|**$206.95**|**0.04%**|  
|**ML マウンテンフレーム**|**$343785.29**|**$161.82**|**0.05%**|  
|**Women's Mountain Shorts**|**$260304.09**|**$6675.56**|**2.56%**|  
  
 この結果セットを見ると、Top10SellingProducts のリストに、新しい製品が 7 つ出現していることがわかります。また、Mountain-200、Mountain-100、および HL Mountain Frame がリストの上位に移動しています。 その前の結果セットでは、この 3 つの値がばらばらに存在していました。  
  
 クエリのスライス条件を満たすように Top10SellingProducts のセットが評価されていることから、これを deep Autoexists といいます。 deep Autoexists では、スライサーの式、軸の下位選択式などを適用した後、可能な限り深い場所に到達するように、すべての式が評価されます。  
  
 ただし、場合によっては、次の例のように、Top10SellingProducts に対して、Preferred10Products と同等の分析を行うことができれば便利です。  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Preferred10Products on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 結果セットは、次のようになります。  
  
|||||  
|-|-|-|-|  
||**再販業者の売上高**|**割引額**|**PCT 割引**|  
|**山地-200**|**$14356699.36**|**$19012.71**|**0.13%**|  
|**山地-100**|**$8568958.27**|**$139393.27**|**1.63%**|  
|**HL マウンテンフレーム**|**$3365069.27**|**$174.11**|**0.01%**|  
  
 上の結果では、スライスによって、Preferred10Products から、[Product].[Product Line] の [Mountain] グループに属する製品だけを含む結果が得られます。Preferred10Products は定数式であるため、これは当然の結果と言えます。  
  
 この結果セットは、shallow Autoexists と考えることもできます。 式がスライス句よりも前に評価されるためです。 前の例では、概念をわかりやすく説明するために、定数式を使用しました。  
  
 Autoexists の動作は、 **Autoexists** 接続文字列プロパティを使用することにより、セッション レベルで変更できます。 次の例は、まず、新しいセッションを開いてを追加する、 *Autoexists=3* プロパティを接続文字列にします。 この例を実行するには、新しい接続を開く必要があります。 いったん Autoexist 設定で確立された接続は、その接続が解除されるまで有効です。  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `//Preferred10Products set removed for clarity`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 次の結果セットは、shallow Autoexists の動作を示しています。  
  
|||||  
|-|-|-|-|  
||**再販業者の売上高**|**割引額**|**PCT 割引**|  
|**山地-200**|**$14356699.36**|**$19012.71**|**0.13%**|  
|**山地-100**|**$8568958.27**|**$139393.27**|**1.63%**|  
|**HL マウンテンフレーム**|**$3365069.27**|**$174.11**|**0.01%**|  
  
 Autoexists の動作は、接続文字列の AUTOEXISTS = [1 | 2 | 3] パラメーターを使用して変更できます。パラメーターの使用法については<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> 、「 [Xmla&#41;&#40;サポートされる xmla プロパティ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)」を参照してください。  
  
## <a name="examples"></a>例  
 次の例では、 `Measures.[Order Quantity]` **Adventure works**キューブから、 `Date`ディメンションに含まれる2003年の最初の8か月間に集計された、メンバーの合計を返します。  
  
```  
WITH MEMBER [Date].[Calendar].[First8Months2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Year],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First8Months2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 **非ビジュアルを**理解するために、次の例は、製品カテゴリが列、再販業者のビジネスタイプが行であるテーブルの [再販業者の売上金] の数値を取得するための [Adventure Works] のクエリです。 合計は、製品と再販業者の両方に与えられていることに注意してください。  
  
 次の SELECT ステートメントを実行します。  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 結果は、次のようになります。  
  
|||||||  
|-|-|-|-|-|-|  
||**すべての製品**|**Accessories**|**Bikes**|**Clothing**|**Components**|  
|**すべてのリセラー**|**$80450596.98**|**$571297.93**|**$66302381.56**|**$1777840.84**|**$11799076.66**|  
|**特別自転車ショップ**|**$6756166.18**|**$65125.48**|**$6080117.73**|**$252933.91**|**$357989.07**|  
|**付加価値再販業者**|**$34,967,517.33**|**$175002.81**|**$30892354.33**|**$592,385.71**|**$3307774.48**|  
|**ウェア**|**$38726913.48**|**$331169.64**|**$29329909.50**|**$932521.23**|**$8133313.11**|  
  
 アクセサリと衣料製品のデータのみを含むテーブルを生成するには、販売店と倉庫の再販業者の値を追加します。ただし、次のように、非ビジュアルを使用して、全体的な合計を維持することができます。  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 結果は、次のようになります。  
  
|||||  
|-|-|-|-|  
||**すべての製品**|**Accessories**|**Clothing**|  
|**すべてのリセラー**|**$80450596.98**|**$571297.93**|**$1777840.84**|  
|**付加価値再販業者**|**$34,967,517.33**|**$175002.81**|**$592,385.71**|  
|**ウェア**|**$38726913.48**|**$331169.64**|**$932521.23**|  
  
 列の表示部分の合計を算出するが、行の合計についてはすべての [Category] の実際の合計を示すテーブルを生成するには、次のクエリを実行します。  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0`  
  
 `from ( Select {[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 0`  
  
 `from [Adventure Works])`  
  
 `)`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 NON VISUAL が [Category] のみに適用されていることに注目してください。  
  
 上記のクエリの結果は、次のようになります。  
  
|||||  
|-|-|-|-|  
||All Products|Accessories|Clothing|  
|All Resellers|$73,694,430.80|$506,172.45|$1,524,906.93|  
|Value Added Reseller|$34,967,517.33|$175,002.81|$592,385.71|  
|Warehouse|$38,726,913.48|$331,169.64|$932,521.23|  
  
 前の結果と比較すると、[All Resellers] 行は [Value Added Reseller] と [Warehouse] の表示値の合計を示していますが、[All Products] 列は表示されていない製品も含むすべての製品の合計額を示していることがわかります。  
  
 次の例は、サブセレクトで計算されるメンバーを使用してフィルター処理する方法を示しています。 このサンプルを再現するには、接続文字列パラメーターの*サブクエリ = 1*を使用して接続を確立する必要があります。  
  
 `select Measures.allmembers on 0`  
  
 `from (`  
  
 `Select { [Measures].[Reseller Sales Amount]`  
  
 `, [Measures].[Reseller Total Product Cost]`  
  
 `, [Measures].[Reseller Gross Profit]`  
  
 `, [Measures].[Reseller Gross Profit Margin]`  
  
 `} on 0`  
  
 `from [Adventure Works]`  
  
 `)`  
  
 上記のクエリの結果は、次のようになります。  
  
|||||  
|-|-|-|-|  
|Reseller Sales Amount|再販業者の製品コストの合計|Reseller Gross Profit|再販業者の売上総利益率|  
|$80,450,596.98|$79980114.38|$470482.60|0.58%|  
  
## <a name="see-also"></a>参照  
 [MDX &#40;Analysis Services の主な概念&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services)   
 [Mdx&#41;&#40;MDX データ操作ステートメント](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [MDX&#41;&#40;クエリ軸とスライサー軸を使用したクエリの制限](~/analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-restricting-the-query.md)  
  
  

