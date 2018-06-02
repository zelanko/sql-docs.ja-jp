---
title: CREATE SUBCUBE ステートメント (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 730d6f3b1445017cc1b1988c49bda176c6ba4ced
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580744"
---
# <a name="mdx-data-definition---create-subcube"></a>MDX データ定義のサブキューブの作成
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたキューブまたはサブキューブのキューブ空間を指定されたサブキューブに再定義します。 このステートメントを実行すると、後続の操作で使用する見かけのキューブ空間が変わります。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE SUBCUBE Cube_Name AS Select_Statement  
                                                  | NON VISUAL ( Select_Statement )  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 制限するキューブまたはパースペクティブの名前を指定する有効な文字列式です。この名前がサブキューブの名前になります。  
  
 *Select_Statement*  
 WITH 句、NON EMPTY 句、または HAVING 句が含まれておらず、ディメンションまたはセルのプロパティを要求しない有効な多次元式 (MDX) の SELECT 式です。  
  
 参照してください[SELECT ステートメント&#40;MDX&#41; ](../mdx/mdx-data-manipulation-select.md)構文の詳細については、Select ステートメントを**NON VISUAL**句。  
  
## <a name="remarks"></a>コメント  
 既定のメンバーをサブキューブの定義から除外すると、それに応じて座標も変わります。 集計が可能な属性の場合、既定のメンバーは [All] のメンバーに移動します。 集計が不可能な属性の場合、既定のメンバーはサブキューブ内に存在するメンバーに移動します。 サブキューブと既定のメンバーの組み合わせの例を以下に示します。  
  
|元の既定のメンバー|集計可能/不可能|サブセレクト|変更後の既定のメンバー|  
|-----------------------------|-----------------------|---------------|----------------------------|  
|Time.Year.All|はい|{Time.Year.2003}|変更なし|  
|Time.Year です。[1997]|はい|{Time.Year.2003}|Time.Year.All|  
|Time.Year です。[1997]|いいえ|{Time.Year.2003}|Time.Year です。[2003]|  
|Time.Year です。[1997]|はい|{Time.Year.2003, Time.Year.2004}|Time.Year.All|  
|Time.Year です。[1997]|いいえ|{Time.Year.2003, Time.Year.2004}|Time.Year.[2003] または<br /><br /> Time.Year.[2004]|  
  
 [All] のメンバーは、常にサブキューブ内に存在します。  
  
 サブキューブのコンテキストで作成されたセッション オブジェクトは、サブキューブが削除された時点で削除されます。  
  
 サブキューブの詳細については、次を参照してください。 [MDX でのサブキューブの作成&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/building-subcubes-in-mdx-mdx.md)です。  
  
## <a name="example"></a>例  
 次の例では、見かけのキューブ空間を Canada に存在するメンバーに制限したサブキューブを作成しています。 次を使用して、**メンバー**すべてのメンバーを返す、国のレベルが、Geography ユーザー定義階層の Canada という国のみを返す関数。  
  
```  
CREATE SUBCUBE [Adventure Works] AS  
   SELECT [Geography].[Country].&[Canada] ON 0  
   FROM [Adventure Works]  
  
SELECT [Geography].[Country].[Country].MEMBERS ON 0  
   FROM [Adventure Works]  
  
```  
  
 次の例では、サブキューブを作成します。このサブキューブでは、見かけのキューブ空間を制限して、Products.Category に存在する {Accessories, Clothing} メンバーおよび Resellers.[Business Type] に存在する {[Value Added Reseller], [Warehouse]} に限定します。  
  
 `CREATE SUBCUBE [Adventure Works] AS`  
  
 `Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works]`  
  
 次の MDX を使用して、Products.Category および Resellers.[Business Type] 内のすべてのメンバーのサブキューブを照会します。  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 結果は次のようになります。  
  
|||||  
|-|-|-|-|  
||All Products|Accessories|Clothing|  
|All Resellers|$2,031,079.39|$506,172.45|$1,524,906.93|  
|Value Added Reseller|$767,388.52|$175,002.81|$592,385.71|  
|Warehouse|$1,263,690.86|$331,169.64|$932,521.23|  
  
 NON VISUAL 句を使用してサブキューブを削除し、再作成すると、Products.Category および Resellers.[Business Type] に存在するすべてのメンバーについて、サブキューブに表示されているかどうかに関係なく、それらの実際の合計が維持されます。  
  
 `CREATE SUBCUBE [Adventure Works] AS`  
  
 `NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 前の例と同じ MDX クエリを実行します。  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 次のように、前の例とは異なる結果になります。  
  
|||||  
|-|-|-|-|  
||All Products|Accessories|Clothing|  
|All Resellers|$80,450,596.98|$571,297.93|$1,777,840.84|  
|Value Added Reseller|$34,967,517.33|$175,002.81|$592,385.71|  
|Warehouse|$38,726,913.48|$331,169.64|$932,521.23|  
  
 [All Products] および [All Resellers] の列と行それぞれに、表示されているメンバーだけでなく、すべてのメンバーの合計が含まれます。  
  
## <a name="see-also"></a>参照  
 [MDX での概念をキー &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)   
 [MDX スクリプト ステートメント&#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [DROP SUBCUBE ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-drop-subcube.md)   
 [SELECT ステートメント&#40;MDX&#41;](../mdx/mdx-data-manipulation-select.md)  
  
  
