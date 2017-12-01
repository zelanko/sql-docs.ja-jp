---
title: "CONTAINSTABLE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONTAINSTABLE
- CONTAINSTABLE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- precise or fuzzy (less precise) matches [full-text search]
- fuzzy (less precise) word or phrase search [full-text search]
- word searches [full-text search]
- weighted values [full-text search]
- values [SQL Server], ranked
- LANGUAGE option
- NEAR option [full-text search]
- RANK column
- phrase searches [full-text search]
- conditions [SQL Server], CONTAINSTABLE
- relevance ranking values [full-text search]
- proximity searches [full-text search]
- CONTAINSTABLE function (Transact-SQL)
- ranked results [full-text search]
- rankings [full-text search]
- less precise (fuzzy) searches [full-text search]
ms.assetid: e580c210-cf57-419d-9544-7f650f2ab814
caps.latest.revision: "69"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: be9da8f4e10f299844f5ea6895f189c5c4fe4c3c
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="containstable-transact-sql"></a>CONTAINSTABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  単語または語句との完全一致検索やあいまい一致検索、特定の範囲内での近接検索、または重み付き検索を行う列に対して、0 行以上の行を含むテーブルを返します。 CONTAINSTABLE で使用、 [FROM 句](../../t-sql/queries/from-transact-sql.md)の[!INCLUDE[tsql](../../includes/tsql-md.md)]SELECT ステートメントとは、通常のテーブル名の場合と同様に参照されています。 実行、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フルテキスト検索をフルテキスト インデックス文字ベースのデータ型を含む列を作成します。  
  
 CONTAINSTABLE は、同じ種類の照合、 [CONTAINS 述語](../../t-sql/queries/contains-transact-sql.md)CONTAINS として同じ検索条件を使用しています。  
  
 ただし、CONTAINS とは異なり、CONTAINSTABLE を使用するクエリでは、各行の関連順位値 (RANK) とフルテキスト キー (KEY) が返されます。  サポートされているフルテキスト検索の形式について[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[、フルテキスト検索でのクエリ](../../relational-databases/search/query-with-full-text-search.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CONTAINSTABLE   
( table , { column_name | ( column_list ) | * } , ' <contains_search_condition> '   
     [ , LANGUAGE language_term]   
  [ , top_n_by_rank ]   
)   
  
<contains_search_condition> ::=   
    { <simple_term>   
    | <prefix_term>   
    | <generation_term>   
    | <generic_proximity_term>   
    | <custom_proximity_term>   
    |  <weighted_term>   
    }   
    | { ( <contains_search_condition> )   
    { { AND | & } | { AND NOT | &! } | { OR | | } }   
     <contains_search_condition> [ ...n ]   
    }  
  
<simple_term> ::=   
     { word | "phrase" }  
<prefix term> ::=   
     { "word*" | "phrase*" }   
<generation_term> ::=   
     FORMSOF ( { INFLECTIONAL | THESAURUS } , <simple_term> [ ,...n ] )   
  
<generic_proximity_term> ::=   
     { <simple_term> | <prefix_term> } { { { NEAR | ~ }   
     { <simple_term> | <prefix_term> } } [ ...n ] }  
  
<custom_proximity_term> ::=   
  NEAR (   
     {  
        { <simple_term> | <prefix_term> } [ ,…n ]  
     |  
        ( { <simple_term> | <prefix_term> } [ ,…n ] )   
      [, <maximum_distance> [, <match_order> ] ]  
     }  
       )   
  
      <maximum_distance> ::= { integer | MAX }  
      <match_order> ::= { TRUE | FALSE }   
  
<weighted_term> ::=   
     ISABOUT  
    ( { {   
  <simple_term>   
  | <prefix_term>   
  | <generation_term>   
  | <proximity_term>   
  }   
   [ WEIGHT ( weight_value ) ]   
   } [ ,...n ]   
    )  
  
```  
  
## <a name="arguments"></a>引数  
 *テーブル*  
 フルテキスト インデックスが作成されているテーブルの名前を指定します。 *テーブル*1 部、2 部、3、または 4 部構成のデータベース オブジェクトの名前を指定できます。 ビューに対してクエリを実行する場合は、フルテキスト インデックスが作成されたベース テーブルを 1 つだけ指定できます。  
  
 *テーブル*とサーバー名を指定できません。 リンク サーバーに対するクエリでは使用できません。  
  
 *column_name*  
 フルテキスト検索用にインデックスが作成される 1 つ以上の列の名前を指定します。 型の列を指定できます**char**、 **varchar**、 **nchar**、 **nvarchar**、**テキスト**、 **ntext**、**イメージ**、 **xml**、 **varbinary**、または**varbinary (max)**です。  
  
 *column_list*  
 コンマ区切りで複数の列を指定できます。 *column_list*かっこで囲む必要があります。 しない限り、 *language_term*が指定されているすべての列の言語*column_list*同じである必要があります。  
  
 \*  
 すべてのフルテキスト インデックス内の列を作成することを示す*テーブル*指定された検索条件の検索に使用する必要があります。 しない限り、 *language_term*を指定すると、テーブルのすべての列の言語は同じである必要があります。  
  
 言語*language_term*  
 リソースが単語区切り、語幹検索、および類義語辞典、およびノイズ ワードを使用する言語は、(または[ストップ ワード](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md))、クエリの一部として削除します。 このパラメーターは省略可能で、言語のロケール識別子 (LCID) に対応する文字列、整数、または 16 進数の値を指定できます。 場合*language_term*を指定すると、その言語は検索条件のすべての要素に適用されます。 値を指定しなかった場合は、列のフルテキストの言語が使用されます。  
  
 1 つの列に言語の異なる複数のドキュメントが BLOB (Binary Large Object) として格納されている場合、そのインデックスの作成に使用される言語は、そのドキュメントのロケール識別子 (LCID) によって決まります。 このような列のクエリを実行する場合を指定して*言語**language_term*とよく一致の確率を高めることができます。  
  
 文字列として指定すると*language_term*に対応する、**エイリアス**列の値、 [sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)互換性ビューです。  文字列は、ように、単一引用符で囲む必要があります '*language_term*' です。 整数として指定すると*language_term*言語を識別する実際の LCID です。 16 進数の値として指定する*language_term*は 0 x 後に LCID の 16 進数の値。 16 進数の値は、先頭の 0 を含め、8 桁以内で指定してください。  
  
 値が 2 バイト文字セット (DBCS) の形式である場合[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Unicode に変換されます。  
  
 無効であるかが、指定された言語がない場合リソースがインストールされていません、その言語に対応している[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はエラーを返します。 ニュートラル言語リソースを使用するには、「0x0」を指定*language_term*です。  
  
 *top_n_by_rank*  
 だけを *n* 降順で最高順位の一致が返されます。 整数値、場合にのみ適用されます *n*を指定します。 *top_n_by_rank* を他のパラメーターと組み合わせた場合、クエリから返される行数は、実際にすべての述語に一致する行数より少なくなります。 *top_n_by_rank*最も重要なヒットだけを再度呼び出すことによってクエリ パフォーマンスを向上することができます。  
  
 <contains_search_condition>  
 内で検索するテキストを示す*column_name*と一致するための条件。 検索条件については、次を参照してください。 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md).  
  
## <a name="remarks"></a>解説  
 フルテキストの述語と関数の対象は、FROM 述語で示される 1 つのテーブルです。 複数のテーブルを検索するには、FROM 句で結合テーブルを使用して、複数のテーブルが組み合わされた結果セットを検索します。  
  
 返されるテーブルがという名前の列を持つ**キー**フルテキスト キー値を格納しています。 各フルテキスト インデックス付きテーブルがあり、値を持つことが保証されます、一意である列で返される値、**キー**列で指定した選択条件に一致する行のフルテキスト キー値は、検索が含まれています条件です。 **TableFulltextKeyColumn** OBJECTPROPERTYEX 関数から取得したプロパティは、この一意のキー列の id を提供します。 フルテキスト インデックスのフルテキスト キーに関連付けられている列の ID を取得するには使用**sys.fulltext_indexes**です。 詳細については、次を参照してください。 [sys.fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md).  
  
 元のテーブルから目的の行を取得するには、CONTAINSTABLE 行との結合を指定してください。 CONTAINSTABLE を使用する場合、通常は次の形式で FROM 句を SELECT ステートメントに指定します。  
  
```  
SELECT select_list  
FROM table AS FT_TBL INNER JOIN  
   CONTAINSTABLE(table, column, contains_search_condition) AS KEY_TBL  
   ON FT_TBL.unique_key_column = KEY_TBL.[KEY];  
```  
  
 CONTAINSTABLE で生成されたテーブルには、という名前の列が含まれています。**ランク**です。 **ランク**列には、行が選択基準にどの程度一致を示す行ごと (0 ~ 1000) からの値。 通常、順位値は SELECT ステートメント内で次のいずれかの方法で使用します。  
  
-   ORDER BY 句で使用し、最も順位値の高い行をテーブルの最初の行に返す。  
  
-   選択リストで使用し、それぞれの行に割り当てられている順位値を表示する。  
  
## <a name="permissions"></a>Permissions  
 実行権限は、対象テーブルまたは参照されるテーブル内の列に対して SELECT 特権を持っているユーザーにだけ与えられます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-example"></a>A. 簡単な例  
 次の例では、作成し、3 つの郡およびそのフラグの色の一覧を表示する 2 つの列の単純なテーブルを入力します。 It では、作成し、テーブルのインデックス、フルテキスト カタログを設定します。 続いて、 **CONTAINSTABLE**構文を説明します。 この例では、検索値を複数回を満たす場合に順位値が高いに拡張する方法を示します。 前回のクエリでは、タンザニア緑と黒の両方が含まれています。 これは、順位の高いクエリの色の 1 つだけが含まれているイタリアよりもにあります。  
  
```  
CREATE TABLE Flags (Country nvarchar(30) NOT NULL, FlagColors varchar(200));  
CREATE UNIQUE CLUSTERED INDEX FlagKey ON Flags(Country);  
INSERT Flags VALUES ('France', 'Blue and White and Red');  
INSERT Flags VALUES ('Italy', 'Green and White and Red');  
INSERT Flags VALUES ('Tanzania', 'Green and Yellow and Black and Yellow and Blue');  
SELECT * FROM Flags;  
GO  
  
CREATE FULLTEXT CATALOG TestFTCat;  
CREATE FULLTEXT INDEX ON Flags(FlagColors) KEY INDEX FlagKey ON TestFTCat;  
GO   
  
SELECT * FROM Flags;  
SELECT * FROM CONTAINSTABLE (Flags, FlagColors, 'Green') ORDER BY RANK DESC;  
SELECT * FROM CONTAINSTABLE (Flags, FlagColors, 'Green or Black') ORDER BY RANK DESC;  
```  
  
### <a name="b-returning-rank-values"></a>B. 順位値を返す  
 次の例では、"frame"、"wheel"、または "tire" という単語を含むすべての製品名を検索します。各単語にはそれぞれ異なる重みが割り当てられています。 これらの検索基準に一致し、返された行に対して、相対的な近似度合い (順位値) を表示します。 また、最も順位値の高い行を最初に返します。  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.Name, KEY_TBL.RANK  
    FROM Production.Product AS FT_TBL   
        INNER JOIN CONTAINSTABLE(Production.Product, Name,   
        'ISABOUT (frame WEIGHT (.8),   
        wheel WEIGHT (.4), tire WEIGHT (.2) )' ) AS KEY_TBL  
            ON FT_TBL.ProductID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
### <a name="c-returning-rank-values-greater-than-a-specified-value"></a>C. 指定した値を超える順位値を返す  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
 次の例では、NEAR を使用して、`bracket` テーブルで、相互に近接する "`reflector`" および "`Production.Document`" を検索します。 また、順位値が 50 以上の行だけを返します。  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT DocumentNode, Title, DocumentSummary  
FROM Production.Document AS DocTable   
INNER JOIN CONTAINSTABLE(Production.Document, Document,  
  'NEAR(bracket, reflector)' ) AS KEY_TBL  
  ON DocTable.DocumentNode = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 50  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
> [!NOTE]  
>  フルテキスト クエリで最大距離の整数が指定されていない場合、論理語の間隔が 100 を超えるヒットのみが含まれるドキュメントは NEAR の要件を満たさず、その順位は 0 になります。  
  
### <a name="d-returning-top-5-ranked-results-using-topnbyrank"></a>D. top_n_by_rank を使用して上位 5 個の結果を返す  
 次の例では、`Description` 列内で "light" または "lightweight" という単語の近くに "aluminum" という語句を含んでいる、上位 5 種の製品の説明を返します。  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)',  
      5  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY];  
GO  
```  
  
 `GO`  
  
### <a name="e-specifying-the-language-argument"></a>E. LANGUAGE 引数を指定する  
 次の例を使用して、`LANGUAGE`引数。  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)',  
      LANGUAGE N'English',  
      5  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY];  
GO  
```  
  
> [!NOTE]  
>  言語*language_term*引数を使用するは必要ありません*top_n_by_rank です。*  
  
## <a name="see-also"></a>参照  
 [検索結果を制限するランクを持つ](../../relational-databases/search/limit-search-results-with-rank.md)   
 [フルテキスト検索でのクエリ](../../relational-databases/search/query-with-full-text-search.md)   
 [フルテキスト検索クエリの作成 &#40;Visual Database Tools&#41;](http://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md)   
 [フルテキスト検索でのクエリ](../../relational-databases/search/query-with-full-text-search.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)  
  
  
