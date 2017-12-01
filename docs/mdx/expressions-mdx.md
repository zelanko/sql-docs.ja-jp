---
title: "式 (MDX) |Microsoft ドキュメント"
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
dev_langs: kbMDX
helpviewer_keywords:
- identifiers [MDX]
- expressions [MDX]
- expressions [MDX], about expressions
- MDX [Analysis Services], expressions
- Multidimensional Expressions [Analysis Services], expressions
ms.assetid: e20c34bc-30fa-4ac5-b896-9d4c9925ef59
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 77f06bad91fb9b7aa60f2f4725dd79cf36f41d77
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="expressions-mdx"></a>式 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  式は、識別子、値、および演算子の組み合わせを[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]結果を得るために評価されることができます。 データにアクセスしたりデータを変更する際には、複数の異なる場所でデータを使用できます。 たとえば、クエリの取得対象データの一部分として式を使用したり、一連の基準を満たすデータを探すときの検索条件として式を使用することができます。  
  
## <a name="simple-and-complex-expressions"></a>単純式と複合式  
 MDX では、次のような単純式と複合式を使用できます。  
  
 単純式とは、次のような式です。  
  
 定数  
 定数は、MDX における 1 つの特定の値を表す記号です。 定数として、文字列値、数値、および日付値を指定できます。 文字列と日付の定数は、数値定数とは異なり、単一引用符 (') 文字で区切る必要があります。  
  
 スカラー関数  
 MDX のスカラー関数は、評価のコンテキスト内で単一の値を返します。 MDX がスカラー関数を解決する方法を理解するうえで、この違いは重要です。ほとんどの MDX 式、ステートメント、およびスクリプトは単一のデータ要素に対して評価されるのではなく、(複数のセル、メンバーなど) データ要素のグループに対して反復的に評価されます。 しかし、スカラー関数の評価時には、通常、関数は単一のデータ要素を検査します。  
  
 オブジェクト識別子  
 多次元データの性質上、MDX はオブジェクト指向です。 MDX では、オブジェクト識別子は単純式と見なされます。 識別子の詳細については、次を参照してください。[識別子 &#40;です。MDX と #41 です。](../mdx/identifiers-mdx.md).  
  
 これらのエンティティを演算子で結合して、複合式を作成することができます。  
  
## <a name="expression-results"></a>式の結果  
 1 つの定数、変数、スカラー関数、または列名から成る単純式の場合、式のデータ型、照合順序、有効桁数、小数点以下桁数、および値は、参照される要素のデータ型、照合順序、有効桁数、小数点以下桁数、および値になります。 MDX が直接サポートするのは OLE VARIANT データ型だけなので、単純式で強制型変換が発生することはありません。  
  
 複合式の場合、異なるデータ型を持つ複数の単純式を使用する際に、強制型変換が発生する可能性があります。  
  
## <a name="expression-examples"></a>式の例  
 次のクエリでは、定義が単純式である、計算されるメジャーの例を示します。  
  
 `WITH`  
  
 `MEMBER MEASURES.CONSTANTVALUE AS 1`  
  
 `MEMBER MEASURES.SCALARFUNCTION AS [Date].[Calendar Year].CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.OBJECTIDENTIFIER AS [Measures].[Internet Sales Amount]`  
  
 `SELECT {MEASURES.CONSTANTVALUE,MEASURES.SCALARFUNCTION,MEASURES.OBJECTIDENTIFIER } ON 0,`  
  
 `[Date].[Calendar Year].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 式することもできます、な計算など`[Measures].[Discount Amount] * 1.5`です。 以下の例は、MDX SELECT ステートメント内でメンバーを定義するための計算式の使用方法を示しています。  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Amount] * 1.5  
SELECT   
   [Measures].[Special Discount] on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[キューブ式とサブキューブ式の使用](../mdx/using-cube-and-subcube-expressions.md)|キューブ式とサブキューブ式を定義します。|  
|[ディメンション式の使用](../mdx/using-dimension-expressions.md)|ディメンション式 (次元式) を定義します。|  
|[メンバー式の使用](../mdx/using-member-expressions.md)|メンバー式を定義します。|  
|[組式の使用](../mdx/using-tuple-expressions.md)|組式を定義します。|  
|[セット式の使用](../mdx/using-set-expressions.md)|セット式を定義します。|  
|[スカラー関数の使用](../mdx/using-scalar-expressions.md)|スカラー式を定義します。|  
|[空の値の操作](../mdx/working-with-empty-values.md)|空の値とは何か、そのような値がどのように処理されるかを説明します。|  
  
## <a name="see-also"></a>参照  
 [MDX 言語リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-language-reference-mdx.md)   
 [MDX クエリの基礎と #40 です。Analysis Services &#41;](../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
