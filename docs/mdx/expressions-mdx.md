---
title: 式 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 77ef7250c7af3918509e38c9aa1f5350f3ac5610
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62690840"
---
# <a name="expressions-mdx"></a>式 (MDX)


  式は、識別子、値、および結果に評価される演算子の組み合わせです。 データは、さまざまな場所へのアクセスやデータを変更するときに使用できます。 たとえば、できます式を使用するクエリによって取得するデータの一部として、または検索条件として、一連の条件を満たすデータを検索します。  
  
## <a name="simple-and-complex-expressions"></a>単純および複雑な式  
 単純または MDX で複雑な式ができます。  
  
 単純式とは、次のような式です。  
  
 定数  
 定数は、MDX では、特定の 1 つの値を表す記号です。 文字列、数値、および日付値を定数としてレンダリングできます。 数値の定数とは異なり文字列と日付の定数は単一引用符 (') 文字で区切る必要があります。  
  
 スカラー関数  
 MDX のスカラー関数は、評価のコンテキスト内で単一の値を返します。 この区別は、ほとんどの MDX 式、ステートメント、およびスクリプトには、1 つのデータ要素ではなく、セルやメンバーなどのデータ要素のグループ経由で繰り返し評価されるため、MDX がスカラー関数を解決する方法を理解する必要があります。 スカラー関数の評価時点で、ただし、関数は通常を確認する 1 つのデータ要素。  
  
 オブジェクト識別子  
 MDX は、オブジェクト指向は多次元データの性質のためです。 オブジェクト識別子は、MDX での単純式と見なされます。 識別子の詳細については、次を参照してください。[識別子&#40;MDX&#41;](../mdx/identifiers-mdx.md)します。  
  
 演算子で結合してこれらのエンティティの組み合わせから、複雑な式を構築できます。  
  
## <a name="expression-results"></a>式の結果  
 1 つの定数、変数、スカラー関数、または列名に構築された単純な式のデータ型、照合順序、有効桁数、スケール、および式の値は、データ型、照合順序、有効桁数、スケール、および参照先の要素の値になります。 MDX が直接サポートするのは OLE VARIANT データ型だけなので、単純式で強制型変換が発生することはありません。  
  
 複雑な式では、強制型変換はさまざまなデータ型を 2 つ以上の単純な式を使用する場合に発生します。  
  
## <a name="expression-examples"></a>式の例  
 次のクエリでは、定義が単純式である、計算されるメジャーの例を示します。  
  
 `WITH`  
  
 `MEMBER MEASURES.CONSTANTVALUE AS 1`  
  
 `MEMBER MEASURES.SCALARFUNCTION AS [Date].[Calendar Year].CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.OBJECTIDENTIFIER AS [Measures].[Internet Sales Amount]`  
  
 `SELECT {MEASURES.CONSTANTVALUE,MEASURES.SCALARFUNCTION,MEASURES.OBJECTIDENTIFIER } ON 0,`  
  
 `[Date].[Calendar Year].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 式の計算をなどにもできる`[Measures].[Discount Amount] * 1.5`します。 次の例では、MDX の SELECT ステートメントでメンバーを定義するための計算の使用を示しています。  
  
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
  
|トピック|説明|  
|-----------|-----------------|  
|[キューブ式とサブキューブ式の使用](../mdx/using-cube-and-subcube-expressions.md)|キューブ式とサブキューブ式を定義します。|  
|[ディメンション式の使用](../mdx/using-dimension-expressions.md)|ディメンション式を定義します。|  
|[メンバー式の使用](../mdx/using-member-expressions.md)|メンバー式を定義します。|  
|[組式の使用](../mdx/using-tuple-expressions.md)|組式を定義します。|  
|[セット式の使用](../mdx/using-set-expressions.md)|セット式を定義します。|  
|[スカラー関数の使用](../mdx/using-scalar-expressions.md)|スカラー式を定義します。|  
|[空の値の操作](../mdx/working-with-empty-values.md)|空の値とは何か、そのような値がどのように処理されるかを説明します。|  
  
## <a name="see-also"></a>参照  
 [MDX 言語リファレンス &#40;MDX&#41;](../mdx/mdx-language-reference-mdx.md)   
 [MDX クエリの基礎 &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
