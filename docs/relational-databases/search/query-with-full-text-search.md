---
title: "フルテキスト検索でのクエリ | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-search
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [full-text search], about full-text queries
- queries [full-text search], predicates
- full-text queries [SQL Server], about full-text queries
- full-text search [SQL Server], querying SQL Server
- full-text queries [SQL Server]
- queries [full-text search], functions
ms.assetid: 7624ba76-594b-4be5-ac10-c3ac4a3529bd
caps.latest.revision: 80
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5034ce123455c63718fb41b02450c14ca2f68a0b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="query-with-full-text-search"></a>フルテキスト検索でのクエリ

フルテキスト述語の **CONTAINS** および **FREETEXT** と、行セット値関数の **CONTAINSTABLE** と **FREETEXTTABLE** を **SELECT** ステートメントと使用し、フルテキスト クエリを記述します。 このトピックでは、各述語と関数の例と、使用に最適なものを選択する方法を説明します。

-   単語や語句と一致させるには、**CONTAINS** と **CONTAINSTABLE** を使用します。
-   単語そのものではなく意味と一致させるには、**FREETEXT** と **FREETEXTTABLE** を使用します。

## <a name="examples_simple"></a> 各述語と関数の簡単な例

### <a name="example---contains"></a>例: CONTAINS  
 次の例では、 `$80.99` という単語を含み、価格が `"Mountain"`であるすべての製品を検索します。  
  
```tsql
USE AdventureWorks2012  
GO  
  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain')  
GO  
```  
  
### <a name="example---freetext"></a>例: FREETEXT 
 次の例では、vital、safety、components に関連する単語を含むドキュメントをすべて検索します。  
  
```tsql
USE AdventureWorks2012  
GO  
  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components')  
GO  
```

### <a name="example---containstable"></a>例: CONTAINSTABLE  
 次の例では、 **Description** 列の "light" または "lightweight" という語の近くに "aluminum" という語があるすべての製品の説明 ID と説明を返します。 また、順位値が 2 以上の行だけを返します。  
  
```tsql
USE AdventureWorks2012  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)'  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 2  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
### <a name="example--freetexttable"></a>例: FREETEXTTABLE  
 次の例では、FREETEXTTABLE クエリを拡張して、順位の高いものから順に行を返し、各行の順位を選択リストに追加します。 クエリを指定するには、 **ProductDescriptionID** が **ProductDescription** テーブルの一意なキー列であることを知っている必要があります。  
  
```tsql 
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
以下に、同じクエリを拡張して、順位の値が 10 以上の行だけを返す例を示します。  
  
```tsql  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK >= 10  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  

## <a name="pick-the-best-predicate-or-function"></a>最適な述語または関数を選択する

`CONTAINS`/`CONTAINSTABLE` と `FREETEXT`/`FREETEXTTABLE` は、別種の照合に役立ちます。 次の表では、クエリに適した述語または関数の選択方法を説明します。

例については、「[各述語と関数の簡単な例](#examples_simple)」と「[特定の種類の検索の例](#examples_specific)」を参照してください。 「[検索対象](#supported)」も参照してください。

| |CONTAINS/CONTAINSTABLE|FREETEXT/FREETEXTTABLE|
|---|---|---|
|**クエリの種類**|完全一致またはあいまい一致 (より低い精度での一致) する単語または語句を照合できます。|指定した単語、語句、または文章 ( *freetext 文字列*) の正確な文字列の並びではなく、意味を照合できます。<br/><br/>指定した列のフルテキスト インデックスに、用語または一定の形式の用語が見つかった場合は、一致すると判断されます。|
|**その他のクエリ オプション**|単語が互いに特定の範囲内でどれくらい近いか指定できます。<br/><br/>一致するものを重み付きで返すことができます。<br/><br/>検索条件の結合に、論理演算を使用できます。 詳細については、このトピックの後半の「[ブール演算子 AND、OR、および NOT の使用](#Using_Boolean_Operators)」を参照してください。|該当なし|

## <a name="compare-predicates-and-functions"></a>述語と関数を比較する

述語 `CONTAINS`/`FREETEXT` と行セット値関数 `CONTAINSTABLE`/`FREETEXTTABLE` の構文とオプションは異なります。 次の表では、クエリに適した述語または関数の選択方法を説明します。

例については、「[各述語と関数の簡単な例](#examples_simple)」と「[特定の種類の検索の例](#examples_specific)」を参照してください。 「[検索対象](#supported)」も参照してください。

| |述語<br/>CONTAINS/FREETEXT|関数<br/>CONTAINSTABLE/FREETEXTTABLE|
|---|---|---|
|**使用方法**|CONTAINS と FREETEXT のフルテキスト**述語**は、SELECT ステートメントの WHERE 句または HAVING 句で使用します。|CONTAINSTABLE 関数と FREETEXTTABLE 関数のフルテキスト**関数**は、SELECT ステートメントの FROM 句で通常のテーブル名と同じように使用します。|
|**その他のクエリ オプション**|これらは、LIKE や BETWEEN など他の [!INCLUDE[tsql](../../includes/tsql-md.md)] 述語と組み合わせて使用できます。<br/><br/>テーブルの単一の列、一連の列、すべての列のいずれかを検索対象として指定できます。<br/><br/>また、フルテキスト クエリで単語区切りとステミング、類義語辞典の検索、およびノイズ ワードの削除を行うために使用されるリソースの言語を指定することもできます。|これらのいずれかの関数を使用する場合には、検索するベース テーブルを指定する必要があります。 述語と同様に、検索するテーブルの単一の列、一連の列、またはすべての列を指定できます。また、必要に応じて、指定したフルテキスト クエリで使用される言語リソースの言語を指定することもできます。<br/><br/>通常、CONTAINSTABLE または FREETEXTTABLE の結果をベース テーブルと結合する必要があります。 これを実行するには、キー列の一意の名前を把握している必要があります。 この列は、フルテキスト処理に対応する各テーブルに含まれ、テーブルの行を一意にするために使用されます ( *一意な**キー列*)。 キー列の詳細については、「[フルテキスト インデックスの作成と管理](../../relational-databases/search/create-and-manage-full-text-indexes.md)」をご覧ください。|
|**[結果]**|CONTAINS 述語と FREETEXT 述語では、特定の行がフルテキスト クエリと一致するかどうかを示す TRUE または FALSE の値が返されます。 一致する行は結果セットで返されます。|これらの関数では、フルテキスト クエリと一致する 0 行、1 行、または 2 行以上で構成されるテーブルが返されます。 返されたテーブルには、ベース テーブルの行のうち、関数のフルテキスト検索条件に指定した選択基準に一致する行のみが含まれます。<br/><br/>このいずれかの関数を使用するクエリでは、次のように、返される各行の関連順位値 (RANK) とフルテキスト キー (KEY) も返されます。<br/><ul><li>**KEY** 列。 KEY 列には、返された行の一意の値が格納されます。 KEY 列は、選択基準を指定する際に使用できます。</li><li>**RANK** 列。 RANK 列は、各行が選択条件にどの程度一致しているかを示す *順位値* を返します。 行内のテキストまたはドキュメントの順位値が高いほど、指定したフルテキスト クエリとその行との関連性が高いことを示します。 複数の行に同じ順位が付けられる可能性もあるので注意してください。 *top_n_by_rank* パラメーター (省略可能) を指定して、返される一致の数を制限することもできます。 詳細については、「 [RANK を使用して検索結果を制限する方法](../../relational-databases/search/limit-search-results-with-rank.md)」を参照してください。</li></ul>|
|**その他のオプション**|この作業を終えると、CONTAINS または FREETEXT 述語に 4 つの要素で構成される名前を使用して、リンク サーバー上の対象のテーブルのフルテキスト インデックス列にクエリを実行できます。 フルテキスト クエリを受け取るようリモート サーバーを準備するには、リモート サーバー上の検索対象のテーブルおよび列にフルテキスト インデックスを作成し、リモート サーバーをリンク サーバーとして追加します。|該当なし|
|**詳細**|これらの述語の構文および引数の詳細については、「[CONTAINS](../../t-sql/queries/contains-transact-sql.md)」と「[FREETEXT](../../t-sql/queries/freetext-transact-sql.md)」を参照してください。|これらの関数の構文および引数の詳細については、「[CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)」と「[FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md)」を参照してください。|

##  <a name="supported"></a> 検索対象

次の表では、検索できる単語や語句の種類について説明します。
  
|クエリ用語の形式|Description|Supported by|  
|----------------------|-----------------|------------------|  
|1 つ以上の語または句<br/>(*単純語句*)|たとえば、"croissant" は語、"café au lait" は句です。 このような語や句は単純語句と呼ばれています。<br /><br /> フルテキスト検索において、*語* (または *トークン*) とは、指定された言語の規則に従って適切なワード ブレーカーによって境界が識別された文字列です。 有効な*句*は、複数の語から構成されます。句読点を含む場合も含まない場合もあります。<br /><br /> 詳細については、このトピックの後の「 [特定の語または句 (単純語句) の検索](#Simple_Term)」を参照してください。|[CONTAINS](../../t-sql/queries/contains-transact-sql.md) および [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) は、句に完全一致するものを検索します。<br /><br /> [FREETEXT](../../t-sql/queries/freetext-transact-sql.md) および [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) は、句を個々の語に分解します。|  
|指定したテキストで始まる語または句<br/>(*プレフィックス語句*)|1 つのプレフィックス語句の場合、指定したプレフィックス語句で始まるすべての語が、結果セットに含まれます。 たとえば、"auto*" は、"automatic"、"automobile" などに一致します。<br /><br /> 句の場合、句を構成する各語がプレフィックス語句と見なされます。 たとえば、"auto tran\*" は "automatic transmission" や "automobile transducer" に一致しますが、"automatic motor transmission" には一致しません。<br /><br /> *プレフィックス語句*とは、派生語または変化形を生成するために語の前に付けられる文字列です。<br /><br /> 詳細については、このトピックの後の「 [プレフィックス検索 (プレフィックス語句) の実行](#Prefix_Term)」を参照してください。|[CONTAINS](../../t-sql/queries/contains-transact-sql.md) および [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)|  
|特定の語の変化形<br/>(*生成語: 変化形*)|たとえば、"drive" という語の変化形を検索します。 テーブルのさまざまな行に、"drive"、"drives"、"drove"、"driving"、および "driven" が含まれている場合、これらはどれも drive という語から変化して生成されているので結果セットに入ります。<br /><br /> *変化形*は、動詞のさまざまな時制および活用、または名詞の単数形と複数形です。 <br /><br /> 詳細については、このトピックの後の「 [特定の語の変化形 (生成語) の検索](#Inflectional_Generation_Term)」を参照してください。|[FREETEXT](../../t-sql/queries/freetext-transact-sql.md) および [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) は、指定されたすべての語の変化形の語句を既定で検索します。<br /><br /> [CONTAINS](../../t-sql/queries/contains-transact-sql.md) および [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) は、省略可能な INFLECTIONAL 引数をサポートしています。|  
|特定の語のシノニム形<br/>(*生成語: 類義語*)|たとえば、エントリ "{car, automobile, truck, van}" が類義語辞典に追加されると、"car" という語の類義語形式を検索できます。 "automobile"、"truck"、"van"、または "car" という語は、"car" という語を含むシノニムの拡張セットに属しているため、クエリ処理されるテーブルの行のうち、これらのいずれかの語を含むすべての行が結果セットに表示されます。<br /><br />*類義語辞典*は、ユーザー指定の用語のシノニムを定義します。<br /><br />  類義語辞典ファイルの構造の詳細については、「 [フルテキスト検索に使用する類義語辞典ファイルの構成と管理](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)」を参照してください。|[FREETEXT](../../t-sql/queries/freetext-transact-sql.md) と [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) は、類義語辞典を既定で使用します。<br /><br /> [CONTAINS](../../t-sql/queries/contains-transact-sql.md) および [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) は、省略可能な THESAURUS 引数をサポートしています。|  
|他の語または句に近接する語または句<br/>(*近接語句*)|たとえば、"ice" という語の近くに "hockey" という語がある行や、"ice skating" という句の近くに "ice hockey" という句がある行を検索できます。<br /><br /> *近接語句*とは、互いに近接する語または句を表します。最初の検索語句と最後の検索語句を分離する非検索用語の最大数を指定することもできます。 さらに、任意の順序で語や句を検索したり、指定した順序で語や句を検索したりすることができます。<br /><br /> 詳細については、「 [NEAR による他の単語の近くにある単語の検索](../../relational-databases/search/search-for-words-close-to-another-word-with-near.md)」を参照してください。|[CONTAINS](../../t-sql/queries/contains-transact-sql.md) および [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)|  
|重み付け値を使用している語または句<br/>(*重み付け語句*)|たとえば、複数の語句を検索するクエリでは、検索条件の各検索語に、他の語との相対的な重要性を示す重み付け値を割り当てることができます。 この種のクエリ結果では、検索語に割り当てた相対的な重みに従って、最も関連性の高い行が最初に返されます。 結果セットには、指定した語句 (またはそれらの間のコンテンツ) のいずれかを含むドキュメントまたは行が含まれます。ただし、各検索語句に関連付けられている重み付け値の違いにより、一部の結果が他の結果より関連性が高いと見なされます。<br /><br /> 一連の語句内における各語句の重要度を示す*重み付け値*です。 重み付け値 0.0 は最低値であり、重み付け値 1.0 は最高値です。<br /><br /> 詳細については、このトピックの後の「 [重み付け値を使用する語または句 (重み付け語句) の検索](#Weighted_Term)」を参照してください。|[CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)|  

## <a name="examples_specific"></a> 特定の種類の検索の例

###  <a name="Simple_Term"></a> 特定の語または句 (単純語句) の検索  
 [CONTAINS](../../t-sql/queries/contains-transact-sql.md)、 [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)、 [FREETEXT](../../t-sql/queries/freetext-transact-sql.md)、または [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) を使用すると、テーブルで特定の句を検索できます。 たとえば、 **データベースの** ProductReview [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] テーブルで、製品に関する記述から "learning curve" という句が含まれるすべてのコメントを検索するには、次のように CONTAINS 述語を使用します。  
  
```tsql
USE AdventureWorks2012  
GO  
  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments, '"learning curve"')  
GO  
```  
  
 検索条件 (この場合は "learning curve") には、1 つ以上の語で構成される複雑な条件を指定できます。  
  
###  <a name="Prefix_Term"></a> プレフィックス付きの語 (プレフィックス語句) の検索  
 [CONTAINS](../../t-sql/queries/contains-transact-sql.md) または [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) を使用すると、指定したプレフィックスを持つ語または句を検索することができます。 指定したプレフィックスで始まるテキストが含まれる列のすべてのエントリが返されます。 たとえば、 `top`というプレフィックス ( `top``ple`、 `top``ping`、 `top`など) が含まれるすべての行を検索する場合、 クエリは次のようになります。  
  
```tsql  
USE AdventureWorks2012  
GO  
  
SELECT Description, ProductDescriptionID  
FROM Production.ProductDescription  
WHERE CONTAINS (Description, '"top*"' )  
GO  
```  
  
 アスタリスク (*) より前のテキストに一致するすべてのテキストが返されます。 `CONTAINS (DESCRIPTION, 'top*')`のように、テキストとアスタリスクを二重引用符で囲まなかった場合、フルテキスト検索ではアスタリスクはワイルドカードとして認識されません。  
  
 プレフィックス語句が句の場合、句を構成する各トークンは、それぞれ独立したプレフィックス語句と見なされます。 それらのプレフィックス語句で始まる語を持つすべての行が返されます。 たとえば、"light bread*" というプレフィックス語句を使用すると、"light breaded"、"lightly breaded"、または "light bread" というテキストを含む行が検索されますが、"lightly toasted bread" は対象から除外されます。  
  
###  <a name="Inflectional_Generation_Term"></a> 特定の語の変化形 (生成語) の検索  
[CONTAINS](../../t-sql/queries/contains-transact-sql.md)、 [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)、 [FREETEXT](../../t-sql/queries/freetext-transact-sql.md)、または [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) を使用すると、動詞のさまざまな時制および活用、または名詞の単数形と複数形 (変化形検索)、または特定の語のシノニム形 (類義語辞典検索) を検索できます。  
  
次の例は `Comments` データベースの `ProductReview` テーブルの `AdventureWorks` 列にある "foot" のすべての語形 ("foot"、"feet" など) を検索します。  
  
```tsql  
USE AdventureWorks2012  
GO  
  
SELECT Comments, ReviewerName  
FROM Production.ProductReview  
WHERE CONTAINS (Comments, 'FORMSOF(INFLECTIONAL, "foot")')  
GO  
```  
  
フルテキスト検索では、動詞のさまざまな時制および活用または名詞の単数形と複数形の検索を可能にする*ステマー*が使用されます。 ステマーの詳細については、「 [検索用のワード ブレーカーとステミング機能の構成と管理](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)」を参照してください。  
   
###  <a name="Weighted_Term"></a> 重み付け値を使用する語または句 (重み付け語句) の検索  
[CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) を使用すると、重み付け値を指定して語または句を検索することができます。 重みは 0.0 ～ 1.0 の数値で指定し、一連の語句内における各語句の重要度を示します。 重み 0.0 は最低値であり、重み 1.0 は最高値です。  
  
次の例のクエリは、重みを使用して、文字列 "Bay" で始まるテキストに "Street" または "View" が含まれる顧客住所をすべて検索します。 結果では、指定した語が多く含まれている行ほど高い順位が付けられます。  
  
```tsql  
USE AdventureWorks2012  
GO  
  
SELECT AddressLine1, KEY_TBL.RANK   
FROM Person.Address AS Address INNER JOIN  
CONTAINSTABLE(Person.Address, AddressLine1, 'ISABOUT ("Bay*",   
         Street WEIGHT(0.9),   
         View WEIGHT(0.1)  
         ) ' ) AS KEY_TBL  
ON Address.AddressID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 重み付け語句は、単純語句、プレフィックス語句、生成語、または近接語句と組み合わせて使用できます。  

##  <a name="Using_Boolean_Operators"></a> ブール演算子 AND、OR、および NOT の使用
 
CONTAINS 述語と CONTAINSTABLE 関数は、同じ検索条件を使用します。 どちらも、ブール演算子 AND、OR、AND NOT を使用して複数の検索語句を結合した論理演算をサポートします。 たとえば、AND を使用して "latte" と "New York-style bagel" の両方を含む行を検索できます。 また、AND NOT を使用して "bagel" を含み、かつ "cream cheese" を含まない行を検索することもできます。  
  
一方、FREETEXT と FREETEXTTABLE では、ブール演算子は検索対象の語として扱われます。  
  
 CONTAINS を、論理演算子 AND、OR、および NOT を使用する他の述語と組み合わせる方法については、「[検索条件 &#40;Transact-SQL&#41;](../../t-sql/queries/search-condition-transact-sql.md)」を参照してください。  
  
### <a name="example"></a>例  
 次の例では、CONTAINS 述語を使用して、説明 ID が 5 以外で、説明に "Aluminum" と "spindle" という両方の単語が含まれている説明を検索します。 検索条件では、AND ブール演算子を使用します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの ProductDescription テーブルを使用します。
  
```tsql  
USE AdventureWorks2012  
GO  
  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'aluminum AND spindle')  
GO  
```  
  
##  <a name="Additional_Considerations"></a> その他のクエリ オプション

 フルテキスト クエリを記述する場合は、次のオプションも指定できます。
  
-   **LANGUAGE** オプションを使用した **Language**。 クエリ用語の多くは、ワード ブレーカーの動作に大きく依存します。 適切なワード ブレーカー (およびステミング機能) および類義語辞典ファイルを使用するために、LANGUAGE オプションを指定することをお勧めします。 詳細については、「 [フルテキスト インデックス作成時の言語の選択](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md)」を参照してください。  

-   **大文字と小文字の区別**」を参照してください。 フルテキスト検索クエリでは大文字と小文字は区別されません。 ただし、日本語の場合は、同じ発音を複数の方法で表記できます。この表記方法を正規化することは、大文字と小文字の区別をなくすことに似ています。たとえば、「かな」で検索することで、大文字小文字を区別しない検索に近い検索を実現できます。 しかし、このような正規化はサポートされていません。  

-   **ストップワード**」を参照してください。 フルテキスト クエリを定義する際に、Full-Text Engine でストップワード (ノイズ ワードとも呼ばれます) が検索基準から除外されます。 ストップワードとは、"a"、"and"、"is"、"the" などの頻出する単語で、特定のテキストの検索には通常役立ちません。 ストップワードはストップリストに列挙されています。 各フルテキスト インデックスには特定のストップリストが関連付けられ、それによってクエリから、またはインデックス作成時にインデックスから除外されるストップワードが決まります。 詳細については、「[フルテキスト検索に使用するストップワードとストップリストの構成と管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)」を参照してください。  
  
-   **類義語辞典**。 FREETEXT クエリと FREETEXTTABLE クエリでは、類義語辞典を既定で使用します。 CONTAINS と CONTAINSTABLE では、省略可能な THESAURUS 引数をサポートしています。 詳細については、「[フルテキスト検索に使用する類義語辞典ファイルの構成と管理](configure-and-manage-thesaurus-files-for-full-text-search.md)」を参照してください。
  
##  <a name="tokens"></a> トークン化の結果の確認

特定のワード ブレーカー、類義語辞典、ストップリストの組み合わせをクエリ文字列入力に適用した後に、**sys.dm_fts_parser** 動的管理ビューを使用すると、トークン化の結果を確認できます。 詳細については、「[sys.dm_fts_parser &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/freetext-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [フルテキスト検索クエリの作成 &#40;Visual Database Tools&#41;](http://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [フルテキスト クエリのパフォーマンスの向上](../../relational-databases/search/improve-the-performance-of-full-text-queries.md)
 
