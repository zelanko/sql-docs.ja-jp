---
title: DrilldownLevel (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 99e8c47164d920ec531bf6ab51e35979b060c35d
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578004"
---
# <a name="drilldownlevel-mdx"></a>DrilldownLevel (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  セットで表される最低レベルより 1 つ下のレベルに、セットのメンバーをドリルダウンします。  
  
 レベルを指定すると、ドリル ダウン オプションですが、レベルを設定する場合は、いずれかを使用、**レベル式**または**インデックス レベル**です。 これらの引数を両方同時に指定することはできません。 最後に、計算されるメンバーがクエリに存在する場合は、引数を行セットに含めるよう指定できます。  
  
## <a name="syntax"></a>構文  
  
```  
DrilldownLevel(Set_Expression [,[Level_Expression] ,[Index]] [,INCLUDE_CALC_MEMBERS])  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Level_Expression*  
 (省略可)。 ドリルダウンするレベルを明示的に指定する MDX 式です。 レベル式を指定する場合は次のインデックスの引数をスキップします。  
  
 *Index*  
 (省略可)。 セット内のドリル ダウン先の階層番号を指定する有効な数値式です。 Level_Expression の代わりにインデックス レベルを使用して、ドリルダウンするレベルを明示的に指定することもできます。  
  
 *Include_Calc_Members*  
 (省略可)。 計算されるメンバーがドリルダウン レベルに存在する場合にそれらを含めるかどうかを示すフラグです。  
  
## <a name="remarks"></a>コメント  
 **DrilldownLevel**関数は、指定したセットに含まれるメンバーに基づいて階層の順序で子のセットにメンバーを返します。 指定したセットの元のメンバーの間の順序はそのまま保持されます。ただし、この関数の結果セットに組み込まれるすべての子メンバーは、それぞれの親メンバーの直下に組み込まれます。  
  
 複数レベルの階層データ構造の場合は、ドリルダウンするレベルを明示的に選択できます。 レベルを指定する方法は 2 つあります。両方の方法を同時に使用することはできません。 最初の方法を設定、 **level_expression**は、レベル、その他の方法を取得する MDX 式を使用して引数を指定、**インデックス**引数を番号でレベルを指定する数値式を使用します。  
  
 レベル式が指定された場合は、指定されたレベルにあるメンバーの子メンバーだけを取得し、階層の順序でセットを構築します。 レベル式が指定された場合に、そのレベルにメンバーが存在しなければ、レベル式は無視されます。  
  
 インデックス値が指定された場合、この関数は、インデックス (0 を基点とするインデックス) を基準にして、指定されたセット内で参照されている階層の最低レベルより 1 つ上のレベルにあるメンバーの子メンバーだけを取得し、階層の順序でセットを構築します。  
  
 レベル式もインデックス値も指定されていない場合、指定されたセット内で参照されている最初のディメンションの最下位レベルにあるメンバーの子メンバーだけを取得し、階層内の順序でセットを構築します。  
  
 XMLA プロパティの mdpropmdxdrillfunctions にクエリを使用すると、サーバーがドリル関数以外が提供するサポートのレベルを確認するには参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)詳細についてはします。  
  
## <a name="examples"></a>使用例  
 SSMS の MDX クエリ ウィンドウで Adventure Works キューブを使用して以下の例を試すことができます。  
  
 **例 1-最小構文をデモします。**  
  
 最初の例では、最小構文**DrilldownLevel**です。 唯一必要な引数は、セット式です。 このクエリを実行するとなる、親のすべてのカテゴリと、次のレベルのメンバーに注意してください。 [アクセサリ]、[Bikes]、具合にします。 この例では、単純の基本的な目的を示しています、 **DrilldownLevel**関数で、下のレベルまでドリルダウンします。  
  
```  
SELECT DRILLDOWNLEVEL({[Product].[Product Categories]} * {[Sales Territory].[Sales Territory]}}) ON COLUMNS  
FROM [Adventure Works]  
```  
  
 例 2 - 明示的なインデックス レベルを使用する代替構文  
  
 この例は、数値式を使用してインデックス レベルを指定する代替構文を示しています。 ここでは、インデックス レベルは 0 です。 ゼロを基準とするインデックスでは、これが最低レベルです。  
  
```  
SELECT  
DRILLDOWNLEVEL({[Product].[Product Categories]} * {[Sales Territory].[Sales Territory]},,0) ON COLUMNS  
FROM [Adventure Works]  
```  
  
 前のクエリと同じ結果セットが返されることに注意してください。 一般に、特定のレベルからドリルダウンする場合を除き、インデックス レベルを設定する必要はありません。 インデックス値に 1 を設定して前のクエリを再実行し、次に 2 を設定して再実行します。 インデックス値を 1 に設定した場合は、階層の第 2 レベルからドリルダウンされます。 インデックス値を 2 に設定した場合は、この例の最高レベル、第 3 レベルからドリルダウンされます。 数値式を大きくするほど、インデックス レベルは高くなります。  
  
 **例 3-レベル式をデモします。**  
  
 次の例は、レベル式の使用方法を示しています。 階層構造を表すセットの場合は、レベル式を使用して、ドリルダウンを開始する階層のレベルを選択できます。  
  
 この例でのドリル ダウン レベルから開始 [市区町村] の 2 番目の引数として、 **DrilldownLevel**関数。 このクエリを実行すると、ワシントン州およびオレゴン州の [City] レベルからドリルダウンされます。 ごと、 **DrilldownLevel**関数、結果セットも [Postal codes] 下のレベルのメンバーが含まれています。  
  
```  
SELECT [Measures].[Internet Sales Amount] ON COLUMNS,  
   NON EMPTY (  
   DRILLDOWNLEVEL(  
       {[Customer].[Customer Geography].[Country].[United States],  
           DESCENDANTS(  
             { [Customer].[Customer Geography].[State-Province].[Washington],    
               [Customer].[Customer Geography].[State-Province].[Oregon]},   
               [Customer].[Customer Geography].[City]) } ,  
[Customer].[Customer Geography].[City] ) )  ON ROWS  
FROM [Adventure Works]  
```  
  
 **例 4-計算されるメンバーを含む**  
  
 計算されるメンバーが含まれ、結果の下に表示される設定を追加すると、最後の例に示す、 **include_calculated_members**フラグ。 このフラグは 4 つ目のパラメーターとして指定することに注意してください。  
  
 計算されるメンバーが、計算されないメンバーと同じレベルに存在するため、この例は正常に実行されます。 計算されるメンバー [West Coast] は、[United States] のメンバーと、[United States] の 1 つ下のレベルのすべてのメンバーで構成されます。  
  
```  
WITH MEMBER   
[Customer].[Customer Geography].[Country].&[United States].[West Coast] AS  
[Customer].[Customer Geography].[State-Province].&[OR]&[US] +  
[Customer].[Customer Geography].[State-Province].&[WA]&[US] +  
[Customer].[Customer Geography].[State-Province].&[CA]&[US]  
SELECT [Measures].[Internet Order Count] ON 0,  
DRILLDOWNLEVEL([Customer].[Customer Geography].[Country].&[United States],,,INCLUDE_CALC_MEMBERS) on 1  
FROM [Adventure Works]  
```  
  
 このフラグだけを削除してクエリを再実行すると、計算されるメンバー [West Coast] が除かれた、同じ結果が返されます。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
