---
title: 識別子 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7562beb2cccd94853c346aaf2f1be1886a2e3ac5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63224954"
---
# <a name="identifiers-mdx"></a>識別子 (MDX)


  識別子は、Analysis Services オブジェクトの名前です。 すべてのオブジェクトは、ことができ、識別子を含める必要があります。 これには、キューブ、ディメンション、階層、レベル、メンバー、およびなどが含まれます。 多次元式 (MDX) ステートメントの中でオブジェクトを参照するには、オブジェクトの識別子を使用します。  
  
 によって、オブジェクトの名前は、オブジェクト識別子の識別子を通常、または区切られた識別子となります。  
  
> [!NOTE]  
>  正規され、区切られた識別子は、1 ~ 100 文字を含める必要があります。  
  
## <a name="using-regular-identifiers"></a>標準識別子の使用  
 標準識別子は、標準識別子の次の書式設定規則に準拠しているオブジェクト名です。 区切り記号は、通常の識別子を使用できます。  
  
### <a name="formatting-rules-for-regular-identifiers"></a>標準識別子の書式設定ルール  
  
1.  最初の文字が次のいずれかである必要があります。  
  
    -   Unicode 規格 &#xa0;2.0 で定義されている文字。 だけでなく他の言語の文字、Unicode の文字定義には、a ~ z、A ~ z のラテン文字が含まれています。  
  
    -   アンダー スコア (_)。  
  
2.  名前の先頭以外では、次の文字を使用できます。  
  
    -   Unicode 規格 &#xa0;2.0 で定義されているようになりました。  
  
    -   Basic Latin スクリプトまたはその他の各国スクリプトの 10 進数  
  
    -   アンダー スコア (_)。  
  
3.  MDX の予約されたキーワードを識別子にすることはできません。 予約済みキーワードは、MDX では大文字です。 詳細については、次を参照してください。[予約済みキーワード&#40;MDX 構文&#41;](../mdx/reserved-keywords-mdx-syntax.md)します。  
  
4.  埋め込み型スペースおよび特殊文字は使用できません。  
  
### <a name="examples-of-regular-identifiers"></a>標準識別子の例  
 以下の MDX ステートメントで、`Measures`、`Product`、および `Style` 識別子は、標準識別子の形式の規則に従っています。 これらの標準識別子では、区切り記号は必要ありません。  
  
 `SELECT Measures.MEMBERS ON COLUMNS,`  
  
 `Product.Style.CHILDREN ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 ``  
  
 必須ではありませんが、標準識別子に区切り記号を使用することもできます。 次の MDX ステートメントで、 `Measures`、 `Product`、および`Style`角かっこを使用して、標準識別子が正しく区切られているいます。  
  
 `SELECT [Measures].MEMBERS ON COLUMNS,`  
  
 `[Product].[Style].CHILDREN ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 ``  
  
## <a name="using-delimited-identifiers"></a>区切られた識別子を使用します。  
 標準識別子の形式の規則に従わない識別子は、必ず角かっこ ([]) で区切る必要があります。  
  
> [!NOTE]  
>  区切り記号は識別子のみです。 キーワードが予約でマークされているかどうか、キーワード、区切り記号を使用できません[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]します。  
  
 次の状況では、区切られた識別子を使用します。  
  
-   オブジェクトの名前または名前の一部に予約語を使用する場合。  
  
     予約済みキーワードをオブジェクト名として使用しないことをお勧めします。 以前のバージョンからアップグレードしたデータベース[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]以前のバージョンで予約されていない単語を含む識別子が含まれている可能性がありますが、ここでは予約されています。 オブジェクトの識別子を変更できるようになるまでの間は、区切られた識別子を使ってオブジェクトを参照できます。  
  
-   オブジェクトの名前に、修飾された識別子として示されていない文字を使用する場合。  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 現在のコード ページで任意の文字を使用する区切られた識別子を使用できます。 しかし、むやみにオブジェクト名に特殊文字を使用すると、MDX ステートメントやスクリプトが読みにくくなり、メンテナンスが困難になります。  
  
### <a name="formatting-rules-for-delimited-identifiers"></a>区切られた識別子の形式の規則  
 区切られた識別子の本体は、区切り文字自体を含め、現在のコード ページ内の文字の任意の組み合わせを含めることができます。 区切られた識別子の本体に区切り記号が含まれている場合、特殊な処理が必要です。  
  
-   識別子の本体に左かっこ ([) のみが含まれている場合、追加の処理の必要はありません。  
  
-   識別子の本体に右角かっこ (]) が含まれている場合は、2 つの右角かっこを指定する必要があります (])。  
  
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
 修飾オブジェクト名を使用する場合は、1 つ以上のオブジェクト名を構成する識別子を区切る必要があります。 たとえば、次のコードの Front Brakes 識別子は、区切る必要があります。  
  
 [Measures] を選択します。メンバー [列]  
  
 [Product] です。[Product] です。[Front Brakes]行に  
  
 [Adventure Works] から  
  
 さらに、前の例では、Measures 識別子が 1 つ以上の識別子を区切るを示すために区切られます。  
  
## <a name="see-also"></a>参照  
 [MDX 言語リファレンス &#40;MDX&#41;](../mdx/mdx-language-reference-mdx.md)   
 [MDX クエリの基礎 &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [MDX 構文の要素&#40;MDX&#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  
