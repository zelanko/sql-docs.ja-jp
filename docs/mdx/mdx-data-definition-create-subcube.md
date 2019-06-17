---
title: CREATE SUBCUBE ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2b505de916ba274ebb69137aa3f61fe384386829
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248313"
---
# <a name="mdx-data-definition---create-subcube"></a>MDX データ操作 - CREATE SUBCUBE


  指定したキューブまたはサブキューブを指定されたサブキューブのキューブ空間を再定義します。 このステートメントは、後続の操作の見かけのキューブ空間を変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE SUBCUBE Cube_Name AS Select_Statement  
                                                  | NON VISUAL ( Select_Statement )  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 サブキューブの名前になりますキューブまたはパースペクティブの名前を提供する有効な文字列式を制限されているです。  
  
 *Select_Statement*  
 WITH 句、NON EMPTY 句、または HAVING 句が含まれておらず、ディメンションまたはセルのプロパティを要求しない有効な多次元式 (MDX) の SELECT 式です。  
  
 参照してください[SELECT ステートメント&#40;MDX&#41; ](../mdx/mdx-data-manipulation-select.md) Select ステートメントの構文の詳細については、 **NON VISUAL**句。  
  
## <a name="remarks"></a>コメント  
 サブキューブの定義では、既定のメンバーが除外されているとき、座標それに応じて変更されます。 集計可能な属性の場合は、既定のメンバーは、[All] メンバーに移動されます。 集計が不可能な属性の場合、既定のメンバーはサブキューブ内に存在するメンバーに移動します。 次の表には、例サブキューブと既定のメンバーの組み合わせが含まれています。  
  
|元の既定のメンバー|集計可能/不可能|サブセレクト|変更後の既定のメンバー|  
|-----------------------------|-----------------------|---------------|----------------------------|  
|Time.Year.All|はい|{Time.Year.2003}|変更なし|  
|Time.Year です。[1997]|はい|{Time.Year.2003}|Time.Year.All|  
|Time.Year です。[1997]|いいえ|{Time.Year.2003}|Time.Year です。[2003]|  
|Time.Year です。[1997]|はい|{Time.Year.2003、Time.Year.2004}|Time.Year.All|  
|Time.Year です。[1997]|いいえ|{Time.Year.2003、Time.Year.2004}|いずれかの Time.Year です。[2003] または<br /><br /> Time.Year.[2004]|  
  
 [All] のメンバーは、常にサブキューブ内に存在します。  
  
 サブキューブのコンテキストで作成されたセッション オブジェクトは、サブキューブが削除されるときに削除されます。  
  
 サブキューブの詳細については、次を参照してください。 [MDX でのサブキューブの作成&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/building-subcubes-in-mdx-mdx.md)します。  
  
## <a name="example"></a>例  
 次の例では、カナダの国または地域に存在するメンバーに見かけのキューブ空間を制限したサブキューブを作成します。 次を使用して、**メンバー**を国のすべてのメンバーの Geography ユーザー定義階層の Canada という国のみを返すのレベルを返す関数。  
  
```  
CREATE SUBCUBE [Adventure Works] AS  
   SELECT [Geography].[Country].&[Canada] ON 0  
   FROM [Adventure Works]  
  
SELECT [Geography].[Country].[Country].MEMBERS ON 0  
   FROM [Adventure Works]  
  
```  
  
 次の例は、products.category {Accessories, Clothing} メンバーに見かけのキューブ空間を制限したサブキューブを作成し、{[Value Added Reseller]、[Warehouse]} 再販業者に。[Business Type] です。  
  
 `CREATE SUBCUBE [Adventure Works] AS`  
  
 `Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works]`  
  
 次の MDX を使用して、Products.Category および Resellers.[Business Type] 内のすべてのメンバーのサブキューブを照会します。  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 次の結果が得られます。  
  
|||||  
|-|-|-|-|  
||All Products|Accessories|Clothing|  
|All Resellers|$2,031,079.39|$506,172.45|$1,524,906.93|  
|Value Added Reseller|$767,388.52|$175,002.81|$592,385.71|  
|Warehouse|$1,263,690.86|$331,169.64|$932,521.23|  
  
 削除して、NON VISUAL 句を使用してサブキューブを再作成には、Products.Category および Resellers 内のすべてのメンバーの実際の合計を維持するサブキューブを作成します。[Business Type]、表示されるかどうか、またはサブキューブではなく。  
  
 `CREATE SUBCUBE [Adventure Works] AS`  
  
 `NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 前述のと同じ MDX クエリを発行するには。  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 次の異なる結果が得られます。  
  
|||||  
|-|-|-|-|  
||All Products|Accessories|Clothing|  
|All Resellers|$80,450,596.98|$571,297.93|$1,777,840.84|  
|Value Added Reseller|$34,967,517.33|$175,002.81|$592,385.71|  
|Warehouse|$38,726,913.48|$331,169.64|$932,521.23|  
  
 [All Products] および [All Resellers] の列と行それぞれに、表示されているメンバーだけでなく、すべてのメンバーの合計が含まれます。  
  
## <a name="see-also"></a>参照  
 [MDX の主な概念 (Analysis Services)](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)   
 [MDX スクリプト ステートメント&#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [DROP SUBCUBE ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-drop-subcube.md)   
 [SELECT ステートメント (MDX)](../mdx/mdx-data-manipulation-select.md)  
  
  
