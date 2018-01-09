---
title: "識別子 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- formats [Analysis Services]
- Multidimensional Expressions [Analysis Services], identifiers
- identifiers [MDX]
- MDX [Analysis Services], identifiers
- delimited identifiers [MDX]
- regular identifiers [MDX]
- formats [Analysis Services], identifiers
ms.assetid: 739a8a67-bef3-4b56-961d-ee96cfc36b5b
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 9b45b45da18ea7c9047609ffb47bc5a698e43a21
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="identifiers-mdx"></a>識別子 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  識別子の名前は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]オブジェクト。 各[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]オブジェクトができるし、識別子を持つ必要があります。 これには、キューブ、ディメンション、階層、レベル、メンバーなどが含まれます。 多次元式 (MDX) ステートメントの中でオブジェクトを参照するには、オブジェクトの識別子を使用します。  
  
 オブジェクトの名前を付ける方法に応じて、オブジェクト識別子の識別子は、標準識別子または区切られた識別子になります。  
  
> [!NOTE]  
>  正規され、区切られた識別子は、1 ～ 100 文字を含める必要があります。  
  
## <a name="using-regular-identifiers"></a>標準識別子の使用  
 標準識別子は、以下に挙げる標準識別子の形式の規則に従うオブジェクト名です。 標準識別子では区切り記号は任意に使用できます。  
  
### <a name="formatting-rules-for-regular-identifiers"></a>標準識別子の形式の規則  
  
1.  最初の文字が次のいずれかである必要があります。  
  
    -   Unicode 規格 &#xa0;2.0 で定義されている文字。 Unicode の文字定義には、各国言語の文字のほかに、ラテン文字 a ～ z と A ～ Z も含まれます。  
  
    -   アンダー スコア (_)。  
  
2.  名前の先頭以外では、次の文字を使用できます。  
  
    -   Unicode 規格 &#xa0;2.0 で定義されているようになりました。  
  
    -   Basic Latin スクリプトまたはその他の各国スクリプトの 10 進数  
  
    -   アンダー スコア (_)。  
  
3.  MDX の予約されたキーワードを識別子にすることはできません。 MDX の予約されたキーワードには大文字小文字の区別がありません。 詳細については、次を参照してください。[予約済みキーワード &#40;です。MDX 構文 &#41;](../mdx/reserved-keywords-mdx-syntax.md).  
  
4.  埋め込み型スペースおよび特殊文字は使用できません。  
  
### <a name="examples-of-regular-identifiers"></a>標準識別子の例  
 以下の MDX ステートメントで、`Measures`、`Product`、および `Style` 識別子は、標準識別子の形式の規則に従っています。 これらの標準識別子に区切り記号は不要です。  
  
 `SELECT Measures.MEMBERS ON COLUMNS,`  
  
 `Product.Style.CHILDREN ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 ``  
  
 必須ではありませんが、標準識別子に区切り記号を使用することもできます。 次の MDX ステートメントで、 `Measures`、 `Product`、および`Style`標準識別子を角かっこで正しく区切られています。  
  
 `SELECT [Measures].MEMBERS ON COLUMNS,`  
  
 `[Product].[Style].CHILDREN ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 ``  
  
## <a name="using-delimited-identifiers"></a>区切られた識別子の使用  
 標準識別子の形式の規則に従わない識別子は、必ず角かっこ ([]) で区切る必要があります。  
  
> [!NOTE]  
>  区切り記号は識別子のみに使用します。 キーワードが予約でマークされているかどうか、キーワード、区切り記号を使用できません[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]です。  
  
 区切られた識別子は以下の場合に使用します。  
  
-   オブジェクトの名前または名前の一部に予約語を使用する場合。  
  
     予約されたキーワードはオブジェクト名として使用しないことをお勧めします。 以前のバージョンからアップグレードしたデータベース[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]を以前のバージョンでない予約語を含む識別子を含めることがありますが、予約語[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]です。 オブジェクトの識別子を変更できるようになるまでの間は、区切られた識別子を使ってオブジェクトを参照できます。  
  
-   オブジェクトの名前に、修飾された識別子として示されていない文字を使用する場合。  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]現在のコード ページ内の任意の文字を使用する区切られた識別子を使用できます。 しかし、むやみにオブジェクト名に特殊文字を使用すると、MDX ステートメントやスクリプトが読みにくくなり、メンテナンスが困難になります。  
  
### <a name="formatting-rules-for-delimited-identifiers"></a>区切られた識別子の形式の規則  
 区切られた識別子の本体は、区切り記号を含め、現在のコード ページ内にある文字の任意の組み合わせで構成されます。 区切られた識別子の本体に区切り記号が含まれている場合、特殊な処理が必要です。  
  
-   識別子の本体に左角かっこ ([) しか含まれていない場合、追加の処理は不要です。  
  
-   識別子の本体に右角かっこ (]) が含まれている場合、右角かっこを 2 つ (]]) 指定する必要があります。  
  
### <a name="examples-of-delimited-identifiers"></a>区切られた識別子の例  
 次の MDX ステートメントで`Sales Volume`、 `Sales Cube`、および`select`区切られた識別子には。  
  
 `-- The [Sales Volume] and [Sales Cube] identifiers contain a space.`  
  
 `SELECT Measures.[Sales Volume]`  
  
 `FROM [Sales Cube]`  
  
 `WHERE Product.[select]`  
  
 `-- The [select] identifier is a reserved keyword.`  
  
 次の例のオブジェクトの名前は `Total Profit [Domestic]` です。 このオブジェクトを参照するには、以下の区切られた識別子を使用する必要があります。  
  
 `[Total Profit [Domestic]]]`  
  
 `Domestic` の前の左角かっこを変更せずに、区切られた識別子を作成できることに注意してください。 しかし、`Domestic` の後の右角かっこは、2 つの右角かっこに置き換える必要があります。  
  
### <a name="delimiting-identifiers-with-multiple-parts"></a>複数の部分に区切られた識別子  
 修飾されたオブジェクト名を使用する際に、場合によってはオブジェクト名を構成している複数の識別子を区切る必要があります。 たとえば、次のコードの Front Brakes 識別子は区切らなければなりません。  
  
 SELECT [Measures].MEMBERS ON COLUMNS,  
  
 [Product].[Product].[Front Brakes] ON ROWS  
  
 FROM [Adventure Works]  
  
 さらに、上の例の場合、複数の識別子を区切るようすを示すために Measures 識別子が区切られています。  
  
## <a name="see-also"></a>参照  
 [MDX 言語リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-language-reference-mdx.md)   
 [MDX クエリの基礎と #40 です。Analysis Services &#41;](../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [MDX 構文の要素 &#40;です。MDX と #41 です。](../mdx/mdx-syntax-elements-mdx.md)  
  
  
