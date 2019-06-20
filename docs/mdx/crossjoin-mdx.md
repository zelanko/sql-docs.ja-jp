---
title: Crossjoin (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b68dafa89f8285f532fc6e92e80f9741be239f65
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248236"
---
# <a name="crossjoin-mdx"></a>Crossjoin (MDX)


  1 つ以上のセットのクロス積を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Standard syntax  
Crossjoin(Set_Expression1 ,Set_Expression2 [,...n] )  
  
Alternate syntax  
Set_Expression1 * Set_Expression2 [* ...n]  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression1*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Set_Expression2*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="remarks"></a>コメント  
 **Crossjoin**関数は、2 つのクロス積を返しますまたは、複数の指定されたセット。 参加しているため、各セットとそのメンバーの順序の順序、結果セット内の組の順序が決まります。 たとえば、ときに、最初のセットで構成されます {x1, x2,..., x*n*}、2 番目のセットで構成されます {y1, y2,..., y*n*}、これらのセットのクロス積は。  
  
 {0} (x1, y1)、(x1, y2),..., (x1, y*n*)、(x2, y1) (x2 y2),...,  
  
 (x2, y*n*),..., (x*n*、y1)、(x*n*、y2),..., (xn、y*n*)}  
  
> [!IMPORTANT]  
>  クロス結合内のセットが同一ディメンションの異なる属性階層の組から構成されている場合、この関数は実際に存在する組のみを返します。 詳細については、次を参照してください。 [MDX の主な概念&#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)します。  
  
## <a name="examples"></a>使用例  
 次のクエリでは、クエリの列と行軸に Crossjoin 関数の使用の簡単な例を示しています。  
  
 `SELECT`  
  
 `[Customer].[Country].Members *`  
  
 `[Customer].[State-Province].Members`  
  
 `ON 0,`  
  
 `Crossjoin(`  
  
 `[Date].[Calendar Year].Members,`  
  
 `[Product].[Category].[Category].Members)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE Measures.[Internet Sales Amount]`  
  
 次の例では、同じディメンションの異なる階層がクロス結合される場合に行われる自動フィルター処理を示しています。  
  
 `SELECT`  
  
 `Measures.[Internet Sales Amount]`  
  
 `ON 0,`  
  
 `//Only the dates in Calendar Years 2003 and 2004 will be returned here`  
  
 `Crossjoin(`  
  
 `{[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]},`  
  
 `[Date].[Date].[Date].Members)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 次の 3 つの例では、米国内の州別 Internet Sales Amount と同じ結果を返します。 最初の 2 つは、2 つのクロス結合構文を使用して、3 つ目は、同じ情報を返す WHERE 句の使用を示します。  
  
### <a name="example-1"></a>例 1  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
       [Customer].[State-Province].Members  
   ) ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
### <a name="example-2"></a>例 2  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
### <a name="example-3"></a>例 3  
  
```  
SELECT   
   [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
