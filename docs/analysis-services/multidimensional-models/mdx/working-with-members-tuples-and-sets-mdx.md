---
title: "メンバー、組、およびセットの操作 (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MDX [Analysis Services], 組"
  - "メンバー キー [MDX]"
  - "MDX [Analysis Services], セット"
  - "計算されるメンバー [MDX]"
  - "メンバー [MDX]"
  - "多次元式 [Analysis Services], メンバー"
  - "名前付きセット [MDX]"
  - "多次元式 [Analysis Services], 組"
  - "メンバー関数 [MDX]"
  - "セット [MDX]"
  - "MDX [Analysis Services], メンバー"
  - "メンバー名 [MDX]"
  - "多次元式 [Analysis Services], セット"
  - "組関数"
  - "組"
  - "集合関数 [MDX]"
ms.assetid: b6ec2439-caef-46d3-9fd7-5f4526cee334
caps.latest.revision: 41
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 41
---
# メンバー、組、およびセットの操作 (MDX)
  MDX には、1 つ以上のメンバー、組、またはセットを返す操作や、メンバー、組、またはセットに対する操作を行うための関数が各種用意されています。  
  
## メンバー関数  
 MDX には、ディメンション、レベル、セット、組などの他の MDX エンティティからメンバーを取得するための関数がいくつかあります。 たとえば、[FirstChild](../../../mdx/firstchild-mdx.md) 関数はメンバーに対して操作を実行してメンバーを返す関数です。  
  
 時間ディメンションの最初の子メンバーを取得するには、次の例のように、明示的にメンバーを指定できます。  
  
```  
SELECT [Date].[Calendar Year].[CY 2001] on 0  
FROM [Adventure Works]  
  
```  
  
 または、次の例のように、**FirstChild** 関数を使用して同じメンバーを返すこともできます。  
  
```  
SELECT [Date].[Calendar Year].FirstChild on 0  
FROM [Adventure Works]  
  
```  
  
 MDX メンバー関数の詳細については、「[MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## 組関数  
 MDX には、組を返す関数がいくつかあります。これらの関数は、組を使用できる任意の箇所で使用できます。 たとえば、[Item &#40;組&#41; &#40;MDX&#41;](../../../mdx/item-tuple-mdx.md) 関数はセットから最初の組を抽出するために使用できます。これは、セットに含まれているのが単一の組であるとわかっており、組を 1 つ必要とする関数にその組を渡す場合に非常に便利です。  
  
 次の例では、列軸上の組のセット内から最初の組を返します。  
  
```  
SELECT {  
   ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2003]  
   )  
, ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2004]  
   )  
}.Item(0)  
ON COLUMNS   
FROM [Adventure Works]  
```  
  
 組関数の詳細については、「[MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## 集合関数  
 MDX には、セットを返す関数がいくつかあります。 セットを取得する方法は、明示的に組を入力して中かっこで囲むだけではありません。 セットを返すメンバー関数の詳細については、「[MDX の主な概念 &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)」をご覧ください。 他にも多くのセット関数があります。  
  
 コロン演算子を使用すれば、メンバーの順序を指定してセットを作成できます。 たとえば、次の例のセットには、2002 年度の第 1 四半期から第 4 四半期までの組が含まれます。  
  
```  
SELECT   
   {[Calendar Quarter].[Q1 CY 2002]:[Calendar Quarter].[Q4 CY 2002]}   
ON 0  
FROM [Adventure Works]  
```  
  
 コロン演算子を使用してセットを作成しない場合は、次の例のような組を指定することで、同じメンバー セットを作成できます。  
  
```  
SELECT {  
   [Calendar Quarter].[Q1 CY 2002],   
   [Calendar Quarter].[Q2 CY 2002],   
   [Calendar Quarter].[Q3 CY 2002],   
   [Calendar Quarter].[Q4 CY 2002]  
   } ON 0  
FROM [Adventure Works]  
  
```  
  
 コロン演算子は内包的な関数です。 コロン演算子の両側のメンバーはどちらも結果セットに含まれます。  
  
 セット関数の詳細については、「[MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## 配列関数  
 配列関数は、セットに対して操作を実行して配列を返します。 配列関数の詳細については、「[MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## 階層関数  
 階層関数は、メンバー、レベル、階層、または文字列に対して操作を実行して、階層を返します。 階層関数の詳細については、「[MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## レベル関数  
 レベル関数は、メンバー、レベル、または文字列に対して操作を実行して、レベルを返します。 レベル関数の詳細については、「[MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## 論理関数  
 論理関数は、MDX 式に対して操作を実行し、その式の組、メンバー、またはセットに関する情報を返します。 たとえば、[IsEmpty &#40;MDX&#41;](../../../mdx/isempty-mdx.md) 関数は、式から空のセル値が返されるかどうかを評価します。 論理関数の詳細については、「[MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## 数値関数  
 数値関数は、MDX 式に対して操作を実行してスカラー値を返します。 たとえば、[Aggregate &#40;MDX&#41;](../../../mdx/aggregate-mdx.md) 関数は、指定されたセットの組に対し、メジャーを集計することで計算されるスカラー値を返します。 数値関数の詳細については、「[MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## 文字列関数  
 文字列関数は、MDX 式に対して操作を実行して文字列を返します。 たとえば、[UniqueName &#40;MDX&#41;](../../../mdx/uniquename-mdx.md) 関数は、ディメンション、階層、レベル、メンバーの一意の名前を格納した文字列値を返します。 文字列関数の詳細については、「[MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)」をご覧ください。  
  
## 参照  
 [MDX の主な概念 &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)   
 [MDX クエリの基礎 &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)  
  
  