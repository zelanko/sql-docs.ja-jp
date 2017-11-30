---
title: "Crossjoin (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: CROSSJOIN
dev_langs: kbMDX
helpviewer_keywords: Crossjoin function
ms.assetid: 503b8376-d244-4855-8f44-a749764162e4
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: fdbb56e7cbb7f02610d4763241707404835bdc9a
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="crossjoin-mdx"></a>Crossjoin (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>解説  
 **Crossjoin**関数が 2 つのクロス積を返しますまたは、複数の指定されたセットです。 結果セット内の組の順序は、クロス積を求める各セットの順序と各セット内のメンバーの順序によって決まります。 たとえば、ときに、最初のセットで構成されます {x1, x2,..., x*n*}、2 番目のセットで構成される {y1, y2,..., y*n*}、これらのセットのクロス積は。  
  
 {(x1, y1), (x1, y2),...,(x1, y*n*), (x2, y1), (x2, y2),...,  
  
 (x2, y*n*),..., (x*n*, y1), (x*n*, y2),..., (xn, y*n*)}  
  
> [!IMPORTANT]  
>  クロス結合内のセットが同一ディメンションの異なる属性階層の組から構成されている場合、この関数は実際に存在する組のみを返します。 詳細については、次を参照してください[MDX &#40; の主な概念。Analysis Services &#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md).  
  
## <a name="examples"></a>使用例  
 次のクエリでは、クエリの列軸と行軸での Crossjoin 関数の使用例を示しています。  
  
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
  
 次の例では、同じディメンションの異なる階層がクロス結合の対象となる場合に行われる自動フィルター処理を示しています。  
  
 `SELECT`  
  
 `Measures.[Internet Sales Amount]`  
  
 `ON 0,`  
  
 `//Only the dates in Calendar Years 2003 and 2004 will be returned here`  
  
 `Crossjoin(`  
  
 `{[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]},`  
  
 `[Date].[Date].[Date].Members)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 次の 3 つの例はいずれも、米国内の州の州別 Internet Sales Amount を返します。 最初の 2 例では 2 種類のクロス結合の構文を使用し、3 つ目の例では WHERE 句を使用して同じ結果を返しています。  
  
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
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
