---
title: "(TRANSACT-SQL) が含まれています |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONTAINS_TSQL
- CONTAINS
dev_langs: TSQL
helpviewer_keywords:
- precise or fuzzy (less precise) matches [full-text search]
- CONTAINS predicate (Transact-SQL)
- conditions [SQL Server], CONTAINS
- fuzzy (less precise) word or phrase search [full-text search]
- word weighting values [full-text search]
- word searches [full-text search]
- weighted values [full-text search]
- LANGUAGE option
- word inflectionally generated from another [full-text search]
- NEAR option [full-text search]
- phrase searches [full-text search]
- word near another word search [full-text search]
- full-text search [SQL Server], searching on a property
- proximity searches [full-text search]
- less precise (fuzzy) searches [full-text search]
- property searching [SQL Server], searching on a property
- inflectional forms [full-text search]
- prefix searches [full-text search]
ms.assetid: 996c72fc-b1ab-4c96-bd12-946be9c18f84
caps.latest.revision: "117"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 6c2f2f2f6bca2048ead7dc9565b5338bc2505c8e
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="contains-transact-sql"></a>CONTAINS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、単語または語句との完全一致検索やあいまい一致検索、特定の範囲内での検索、または重み付き検索を行います。 使用される述語は、 [WHERE 句](../../t-sql/queries/where-transact-sql.md)の[!INCLUDE[tsql](../../includes/tsql-md.md)]SELECT ステートメントを実行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フルテキスト検索をフルテキスト インデックス文字ベースのデータ型を含む列を作成します。  
  
 次に CONTAINS の検索対象を示します。  
  
-   単語または語句。  
  
-   単語または語句のプレフィックス。  
  
-   別の単語の近くにある単語。  
  
-   他の単語を語形変化して生成した単語。たとえば、drive という単語からは、drives、drove、driving、driven などの単語が生成されます。  
  
-   別の単語のシノニムになっている単語 (類義語を使用)。たとえば、"金属" という単語には、"アルミニウム" や "スチール" などのシノニムがあります。  
  
 サポートされているフルテキスト検索の形式について[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[、フルテキスト検索でのクエリ](../../relational-databases/search/query-with-full-text-search.md)です。  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CONTAINS (   
     {   
        column_name | ( column_list )   
      | *   
      | PROPERTY ( { column_name }, 'property_name' )    
     }   
     , '<contains_search_condition>'  
     [ , LANGUAGE language_term ]  
   )   
  
<contains_search_condition> ::=   
  {   
      <simple_term>   
    | <prefix_term>   
    | <generation_term>   
    | <generic_proximity_term>   
    | <custom_proximity_term>   
    | <weighted_term>   
    }   
  |   
    { ( <contains_search_condition> )   
        [ { <AND> | <AND NOT> | <OR> } ]   
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
   ( {   
        {   
          <simple_term>   
        | <prefix_term>   
        | <generation_term>   
        | <proximity_term>   
        }   
      [ WEIGHT ( weight_value ) ]   
      } [ ,...n ]   
   )   
  
<AND> ::=   
  { AND | & }  
  
<AND NOT> ::=   
  { AND NOT | &! }  
  
<OR> ::=   
  { OR | | }  
  
```  
  
## <a name="arguments"></a>引数  
 *column_name*  
 FROM 句で指定されたテーブルのフルテキスト インデックス付き列の名前です。 型の列を指定できます**char**、 **varchar**、 **nchar**、 **nvarchar**、**テキスト**、 **ntext**、**イメージ**、 **xml**、 **varbinary**、または**varbinary (max)**です。  
  
 *column_list*  
 複数の列をコンマで区切って指定します。 *column_list*かっこで囲む必要があります。 しない限り、 *language_term*が指定されているすべての列の言語*column_list*同じである必要があります。  
  
 \*  
 クエリでは、指定した検索条件の FROM 句で指定されたテーブルのすべてのフルテキスト インデックス付き列が検索を指定します。 CONTAINS 句内の列は、フルテキスト インデックスがある単一テーブルから取得する必要があります。 しない限り、 *language_term*を指定すると、テーブルのすべての列の言語は同じである必要があります。  
  
 プロパティ ( *column_name* 、'*property_name*')  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 
  
 指定した検索条件を検索するドキュメント プロパティを指定します。  
  
> [!IMPORTANT]  
>  クエリをどの行を返す*property_name*指定する必要があります、フルテキスト インデックスおよびフルテキスト インデックスの一覧、検索プロパティのプロパティに固有のエントリを含める必要があります*property_name*です。 詳細については、「 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)」を参照してください。  
  
 言語*language_term*  
 単語区切り、語幹検索、類義語の拡張と置換、およびノイズ ワードを使用する言語を (または[ストップ ワード](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md))、クエリの一部として削除します。 このパラメーターはオプションです。  
  
 1 つの列に複数の異なる言語のドキュメントが BLOB (Binary Large Object) として格納されている場合、インデックスの作成に使用される言語は、各ドキュメントのロケール識別子 (LCID) によって決まります。 このような列を照会する際に、言語を指定する*language_term*とよく一致の確率を高めることができます。  
  
 *language_term*文字列、整数、または、言語の LCID に対応する 16 進数の値として指定できます。 場合*language_term*を指定すると、その言語は、検索条件のすべての要素に適用します。 値を指定しなかった場合は、列のフルテキストの言語が使用されます。  
  
 文字列として指定されている場合*language_term*に対応する、**エイリアス**列の値、 [sys.syslanguages &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)互換性ビューです。 文字列は、ように、単一引用符で囲む必要があります '*language_term*' です。 整数として指定すると*language_term*言語を識別する実際の LCID です。 16 進数の値として指定する*language_term*は 0 x 後に LCID の 16 進数の値。 16 進数の値は、先頭の 0 を含め、8 桁以内で指定してください。  
  
 値が 2 バイト文字セット (DBCS) の形式である場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Unicode に変換します。  
  
 無効であるかが、指定された言語がない場合リソースがインストールされていません、その言語に対応している[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はエラーを返します。 ニュートラル言語リソースを使用するには、「0x0」を指定*language_term*です。  
  
 \<*contains_search_condition*>  
 内で検索するテキストを示す*column_name*と一致するための条件。  
  
*\<contains_search_condition>* is **nvarchar**. 入力に他の文字データ型が使用された場合は、暗黙の変換が行われます。 大きな文字列データ型 nvarchar (max) および varchar (max) は使用できません。 次の例で、`@SearchWord`として定義されている変数`varchar(30)`で暗黙的な変換により、`CONTAINS`述語。
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord varchar(30)  
SET @SearchWord ='performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
```  
  
 「パラメーターを見つけ出す」は、変換では機能しません、ので使用**nvarchar**パフォーマンスが向上します。 例では、宣言`@SearchWord`として`nvarchar(30)`です。  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
```  
  
 最適化されていないプランが生成される場合には、OPTIMIZE FOR クエリ ヒントを使用することもできます。  
  
 *word*  
 スペースまたは句読点なしの文字列を指定します。  
  
 *phrase*  
 単語の間をスペースで区切った 1 つ以上の単語を指定します。  
  
> [!NOTE]  
>  一部のアジア言語など、言語の中には、語句を構成するときに単語の間にスペースを挿入しないものがあります。  
  
\<simple_term>  
単語または語句に対する完全一致を指定します。 有効な単純語の例として、"blue berry"、blueberry、および "Microsoft SQL Server" などがあります。 語句は二重引用符 ("") で囲みます。 指定されていると同じ順序で語句内の単語が表示する必要があります *\<contains_search_condition >*データベース列に表示されます。 単語または語句内の文字の検索では、大文字と小文字は区別されません。 ノイズ ワード (または[ストップ ワード](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)) (など、または)、フルテキスト インデックス化された列がフルテキスト インデックスに格納されません。 1 つの単語の検索にノイズ ワードを使用した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではクエリにノイズ ワードだけが指定されていることを示すエラーが返されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各インスタンスのディレクトリ \Mssql\Binn\FTERef にノイズ ワードの標準リストがあります。  
  
 句読点は無視されます。 したがって、 `CONTAINS(testing, "computer failure")` "Where is my computer の値を持つ行が一致? Failure to find it would be expensive." がある行に一致します。 ワード ブレーカーの動作の詳細については、次を参照してください。[構成と管理ワード ブレーカーとステマーの検索](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)です。  
  
 \<prefix_term>  
 指定のテキストで始まる単語または語句の照合を指定します。 プレフィックス語句を二重引用符で囲みます ("")、アスタリスクを追加し、(\*) 終了の引用符の前に、単純語句で始まるすべてのテキストを指定する前にアスタリスクが一致します。 こうすると、句を指定する必要があります:`CONTAINS (column, '"text*"')`です。 アスタリスクは、一致する文字がないか、1 つまたはそれ以上の文字に一致します。その単語または語句を語根とする文字も対象になります。 テキストとアスタリスクが二重引用符で区切られていないと、述語が読み取る内容は `CONTAINS (column, 'text*')` となり、フルテキスト検索でアスタリスクが文字と見なされ、`text*` への完全一致が検索されます。 フルテキスト エンジンには、ワードがアクタリスクは見つかりません (\*) 文字のため、ワード ブレーカーは、通常、このような文字を無視します。  
  
 ときに *\<prefix_term >*句の場合は、語句に含まれている各単語が独立したプレフィックスであると見なされます。 したがって、"local wine *" というプレフィックスを指定しているクエリでは、"local winery"、"locally wined and dined"などの行が一致します。  
  
 \<generation_term>  
 指定されている原形の語または語句が、検索対象である元の単語の変形を含んでいる場合に、これらの単語も照合の対象であることを指定します。  
  
 INFLECTIONAL  
 言語依存の語幹検索が、指定した単純語に対して使用されます。 語幹検索の動作は、特定の各言語の語幹ルールに基づいて定義されます。 ニュートラル言語には、関連する語幹検索がありません。 クエリの対象となっている列の列言語は、必要な語幹検索を参照する場合に使用されます。 場合*language_term*が指定されている言語が使用されることに対応する語幹検索します。  
  
 指定された *\<simple_term >*内で、  *\<generation_term >*は名詞と動詞の両方と一致しません。  
  
 THESAURUS  
 列のフルテキスト言語に対応する類義語、またはクエリで指定された言語が使用されます。 最も長いパターンまたはからパターン、  *\<simple_term >*類義語辞典の照合とを展開または元のパターンを置き換える追加の条件が生成されます。 一部またはすべての一致が見つからない場合、  *\<simple_term >*、一致しない部分として扱われます、 *simple_term*です。 フルテキスト検索の類義語辞典の詳細については、次を参照してください。 [、フルテキスト検索の類義語辞典ファイルの管理と構成](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)です。  
  
 \<generic_proximity_term>  
 検索対象のドキュメントに含まれている必要がある単語または語句の照合を指定します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用することをお勧め\<custom_proximity_term >。  
  
 NEAR | ~  
 一致が返されるためには、NEAR (~) 演算子の両側の単語または語句がドキュメントに含まれている必要があります。 2 つの検索語句を指定する必要があります。 特定の検索用語には、1 つの単語または語句を二重引用符によって区切られているのいずれかを指定できます ("*語句*") です。  
  
 複数の近接語句を連結するなどで`a NEAR b NEAR c`または`a ~ b ~ c`です。 一致が返されるためには、指定したすべての近接語句がドキュメントに含まれている必要があります。  
  
 たとえば、`CONTAINS(*column_name*, 'fox NEAR chicken')`と`CONTAINSTABLE(*table_name*, *column_name*, 'fox ~ chicken')`を返すは両方のすべてのドキュメント"について fox"と"chicken"の両方を含む指定された列にします。 CONTAINSTABLE ではさらに、"fox" と "chicken" の近接度に基づく各ドキュメントのランクも返されます。 たとえば、"The fox ate the chicken" という文が含まれているドキュメントのランクは高くなります。これは、他のドキュメントよりも語句が近接しているためです。  
  
 汎用近接語句の詳細については、次を参照してください。[語句閉じるには、NEAR による他の単語の検索](../../relational-databases/search/search-for-words-close-to-another-word-with-near.md)です。  
  
 \<custom_proximity_term>  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 単語または語句の照合と、必要に応じて検索語句間の許容最大距離を指定します。 指定する正確な順序で検索語句を検索することを指定することも (\<match_order >)。  
  
 特定の検索用語には、1 つの単語または語句を二重引用符によって区切られているのいずれかを指定できます ("*語句*") です。 一致が返されるためには、指定したすべての語句がドキュメントに含まれている必要があります。 2 つ以上の検索語句を指定する必要があります。 検索語句の最大数は 64 です。  
  
 既定では、カスタム近接語句の場合、語句の間の距離やその順序に関係なく、指定した語句が含まれているすべての行が返されます。 たとえば、次のクエリを照合するドキュメントは単にする必要がありますが含まれて`term1`と"`term3 term4`"任意の順序で、任意の場所。  
  
```  
CONTAINS(column_name, 'NEAR(term1,"term3 term4")')  
```  
  
 省略可能なパラメーターは次のとおりです。  
  
 \<maximum_distance>  
 文字列と一致すると見なされるための、その文字列の先頭と末尾にある検索語句間の許容最大距離を指定します。  
  
 *整数 (integer)*  
 0 ～ 4294967295 の正の整数を指定します。 この値により、指定した他の検索用語を除く最初と最後の検索語句間にある非検索語句の数を制御します。  
  
 たとえば、次のクエリの検索`AA`と`BB`、最大距離が 5 語以内の任意の順序で。  
  
```  
CONTAINS(column_name, 'NEAR((AA,BB),5)')  
```  
  
 文字列`AA one two three four five BB`一致するものになります。 3 つの検索用語を次の例では、クエリで指定`AA`、 `BB`、および`CC`最大距離が 5 語以内。  
  
```  
CONTAINS(column_name, 'NEAR((AA,BB,CC),5)')  
```  
  
 このクエリでは、総距離が 5 語の次の文字列と一致します。  
  
 `BB   one two   CC   three four five A  A`  
  
 内部の検索用語、通知`CC`はカウントされません。  
  
 **MAX**  
 距離に関係なく、指定した語句が含まれているすべての行を返します。 これは既定値です。  
  
 \<match_order>  
 検索クエリによって返されるためには、語句が指定した順序で含まれている必要があるかどうかを指定します。 指定する\<match_order > を指定する必要がありますも\<maximum_distance >。  
  
 \<match_order > は、次の値のいずれか。  
  
 **TRUE**  
 語句を指定した順序が適用されます。 たとえば、`NEAR(A,B)`のみが一致する`A … B`です。  
  
 **FALSE**  
 指定した順序を無視します。 たとえば、`NEAR(A,B)`両方に一致する、`A … B`と`B … A`です。  
  
 これは既定値です。  
  
 たとえば、次の近接語句が単語を検索"`Monday`「,」`Tuesday`"、および"`Wednesday`"両者間の距離に関係なくで指定した順序で。  
  
```  
CONTAINS(column_name, 'NEAR ((Monday, Tuesday, Wednesday), MAX, TRUE)')  
```  
  
 カスタム近接語句の使用に関する詳細については、次を参照してください。[語句閉じるには、NEAR による他の単語の検索](../../relational-databases/search/search-for-words-close-to-another-word-with-near.md)です。  
  
 \<weighted_term>  
 クエリによって取得された一致する行と、単語または語句のリストが照合されます。このリストの単語や語句のそれぞれには、オプションで重み付け値が指定されます。  
  
 ISABOUT  
 指定します、  *\<weighted_term >*キーワード。  
  
 WEIGHT(*weight_value*)  
 0.0 ～ 1.0 の間で重み値を指定します。 内の各コンポーネント *\<weighted_term >*含めることができます、 *weight_value*です。 *weight_value*をさまざまなクエリの一部に影響を与える、クエリに一致するそれぞれの行に割り当てられる順位値を変更する方法を示します。 重み付けでは CONTAINS クエリが重みのランクに影響の結果には影響しません[CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)クエリ。  
  
> [!NOTE]  
>  小数点区切り文字は、オペレーティング システムのロケールにかかわらず常にピリオドです。  
  
 { AND | & } | { AND NOT | &! } | { OR | | }   
 2 つの contains 検索条件の間の論理演算を指定します。  
  
 {と | (& A)}  
 一致条件として、2 つの contains 検索条件を満たすことを指定します。 アンパサンド記号 (&) は、AND キーワードの代わりに使用して、AND 演算子を表すことができます。  
  
 {なく | &! }  
 2 番目の検索条件が存在しないことを、一致条件として指定します。 アンパサンドとその次の感嘆符 (&!) は、AND NOT キーワードの代わりに使用して、AND NOT 演算子を表すことができます。  
  
 { OR | | }  
 一致条件として、2 つの contains 検索条件のいずれかを満たすことを指定します。 垂直バー記号 (|) は、OR キーワードの代わりに使用して、OR 演算子を表すことができます。  
  
 ときに *\<contains_search_condition >*かっこで囲まれたグループ、グループが最初に評価のこれらのかっこで囲んだが含まれています。 かっこで囲まれたグループを評価した後は、contains 検索条件で使用される論理演算子に対して次の規則が適用されます。  
  
-   NOT は AND より先に適用されます。  
  
-   NOT は AND NOT のように、AND の後にだけ指定できます。 OR NOT 演算子は使用できません。 NOT は最初の条件の前に指定できません。 たとえば、`CONTAINS (mycolumn, 'NOT "phrase_to_search_for" ' )`が無効です。  
  
-   AND は OR より先に適用されます。  
  
-   同じタイプの論理演算子 (AND、OR) は結合されるので、任意の順番で適用できます。  
  
 *n*  
 複数の CONTAINS 検索条件と、条件内の複数の語を指定できることを示すプレースホルダーです。  
  
## <a name="general-remarks"></a>全般的な解説  
 フルテキストの述語と関数の対象は、FROM 述語で示される 1 つのテーブルです。 複数のテーブルを検索するには、FROM 句で結合テーブルを使用して、複数のテーブルが組み合わされた結果セットを検索します。  
  
 フルテキスト述語は使用できません、 [OUTPUT 句](../../t-sql/queries/output-clause-transact-sql.md)データベースの互換性レベルを 100 に設定するとします。  
  
## <a name="querying-remote-servers"></a>リモート サーバーのクエリ  
 4 部構成の名前を使用するには、CONTAINS でまたは[FREETEXT](../../t-sql/queries/freetext-transact-sql.md)フルテキスト クエリ述語には、リンク サーバー上の対象テーブルの列がインデックス付きです。 フルテキスト クエリを受け取るようリモート サーバーを準備するには、リモート サーバー上の検索対象のテーブルおよび列にフルテキスト インデックスを作成し、リモート サーバーをリンク サーバーとして追加します。  
  
## <a name="comparison-of-like-to-full-text-search"></a>フルテキスト検索に LIKE の比較  
 フルテキスト検索とは異なり、[LIKE](../../t-sql/language-elements/like-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] 述語は、文字パターンにのみで動作します。 また、フォーマットされたバイナリ データのクエリには LIKE 述語を使用できません。 さらに、構造化されていない大量のテキスト データに対して LIKE クエリを実行すると、同じデータに対して同等のフルテキスト検索を実行する場合に比べてはるかに時間がかかります。 数百万行のテキスト データに対して LIKE クエリを実行すると、結果が得られるまでに数分かかる場合があります。一方、同じデータに対してフルテキスト クエリを実行すると、返される行数とサイズにもよりますが、数秒以内で結果を取得できます。 もう 1 つの注意事項は、LIKE ではテーブル全体の単純なパターンのスキャンしか実行されないことです。 これに対し、フルテキスト クエリでは、言語が識別され、インデックスの作成時やクエリの実行時に、ストップワードのフィルター処理、類義語辞典と変化形の拡張の作成など、特定の変換が適用されます。 これらの変換により、フルテキスト クエリの再呼び出しの精度および結果の最終的なランク付けを向上させることができます。  
  
## <a name="querying-multiple-columns-full-text-search"></a>複数列のクエリ (フルテキスト検索)  
 検索する列のリストを指定することで、複数の列に対してクエリを実行できます。 クエリを実行する列は同じテーブルに含まれている必要があります。  
  
 次の CONTAINS クエリ語句を検索など、`Red`で、`Name`と`Color`の列、`Production.Product`のテーブル、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]サンプル データベース。  
  
```sql  
Use AdventureWorks2012;  
GO  
SELECT Name, Color   
FROM Production.Product  
WHERE CONTAINS((Name, Color), 'Red');  
```  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-contains-with-simpleterm"></a>A. CONTAINS を使用して\<simple_term >  
 次の例では、 `$80.99` という単語を含み、価格が `Mountain`であるすべての製品を検索します。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain');  
GO  
```  
  
### <a name="b-using-contains-and-phrase-with-simpleterm"></a>B. CONTAINS と語句を使用して\<simple_term >  
 次の例は、いずれかが含まれているすべての製品の文字列を返します`Mountain`または`Road`です。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, ' Mountain OR Road ')  
GO  
```  
  
### <a name="c-using-contains-with-prefixterm"></a>C. CONTAINS を使用して\<prefix_term >  
 次の例では、すべての製品名を返しますで、chain というプレフィックスで始まる単語を少なくとも 1 つで、`Name`列です。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, ' "Chain*" ');  
GO  
```  
  
### <a name="d-using-contains-and-or-with-prefixterm"></a>D. CONTAINS を使用して and または or で\<prefix_term >  
 次の例では、`chain` または `full` のいずれかのプレフィックスを持つ文字列が含まれている、すべてのカテゴリ説明を返します。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, '"chain*" OR "full*"');  
GO  
```  
  
### <a name="e-using-contains-with-proximityterm"></a>E. CONTAINS を使用して\<proximity_term >  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 
  
 次の検索の例、`Production.ProductReview`という単語が含まれているすべてのコメントをテーブル`bike`within 10 の語句、単語の"`control`"と指定した順序で (つまり、"`bike`「の前に」`control`") です。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments , 'NEAR((bike,control), 10, TRUE)');  
GO  
```  
  
### <a name="f-using-contains-with-generationterm"></a>F. CONTAINS を使用して\<generation_term >  
 次の例では、`ride` を原型とする riding、ridden などの単語が含まれている、すべての製品を検索します。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE CONTAINS(Description, ' FORMSOF (INFLECTIONAL, ride) ');  
GO  
```  
  
### <a name="g-using-contains-with-weightedterm"></a>G. CONTAINS を使用して\<weighted_term >  
 次の例は、すべての製品名、単語を含む検索`performance`、 `comfortable`、または`smooth`、各単語に異なる重みが割り当てられています。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE CONTAINS(Description, 'ISABOUT (performance weight (.8),   
comfortable weight (.4), smooth weight (.2) )' );  
GO  
```  
  
### <a name="h-using-contains-with-variables"></a>H. CONTAINS を変数と共に使用する  
 次の例では、特定の検索語ではなく変数を使用します。  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'Performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
GO  
```  
  
### <a name="i-using-contains-with-a-logical-operator-and"></a>I. CONTAINS を論理演算子 (AND) と共に使用する  
 次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの ProductDescription テーブルを使用します。 クエリでは、CONTAINS 述語を使用する、説明 ID が 5 と等しくない説明を検索し、説明には、両方の単語が含まれています。`Aluminum`と単語`spindle`です。 検索条件では、AND ブール演算子を使用します。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'Aluminum AND spindle');  
GO  
```  
  
### <a name="j-using-contains-to-verify-a-row-insertion"></a>J. CONTAINS を使用して行の挿入を確認する  
 次の例では、SELECT サブクエリ内で CONTAINS を使用します。 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用して、クエリは特定の自転車の ProductReview テーブルですべてのコメントのコメント値を取得します。 検索条件では、AND ブール演算子を使用します。  
  
```sql  
USE AdventureWorks2012;  
GO  
INSERT INTO Production.ProductReview   
  (ProductID, ReviewerName, EmailAddress, Rating, Comments)   
VALUES  
  (780, 'John Smith', 'john@fourthcoffee.com', 5,   
'The Mountain-200 Silver from AdventureWorks2008 Cycles meets and exceeds expectations. I enjoyed the smooth ride down the roads of Redmond');  
  
-- Given the full-text catalog for these tables is Adv_ft_ctlg,   
-- with change_tracking on so that the full-text indexes are updated automatically.  
WAITFOR DELAY '00:00:30';     
-- Wait 30 seconds to make sure that the full-text index gets updated.  
  
SELECT r.Comments, p.Name  
FROM Production.ProductReview AS r  
JOIN Production.Product AS p   
    ON r.ProductID = p.ProductID  
    AND r.ProductID = (SELECT ProductID  
FROM Production.ProductReview  
WHERE CONTAINS (Comments,   
    ' AdventureWorks2008 AND   
    Redmond AND   
    "Mountain-200 Silver" '));  
GO  
```  
  
### <a name="k-querying-on-a-document-property"></a>K. ドキュメント プロパティに対してクエリを実行する  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 
  
 次のクエリは、インデックス付きプロパティに検索`Title`で、`Document`の列、`Production.Document`テーブル。 このクエリは、`Title` または `Maintenance` という文字列が `Repair` プロパティに含まれているドキュメントのみを返します。  
  
> [!NOTE]  
>  プロパティ検索で行が返されるためには、インデックスの作成中に列を解析するフィルターによって、指定されたプロパティが抽出される必要があります。 また、指定されたテーブルのフルテキスト インデックスが、プロパティを含めるように構成されている必要があります。 詳細については、「 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)」を参照してください。  
  
```sql  
Use AdventureWorks2012;  
GO  
SELECT Document 
FROM Production.Document  
WHERE CONTAINS(PROPERTY(Document,'Title'), 'Maintenance OR Repair');  
GO  
```  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索の概要](../../relational-databases/search/get-started-with-full-text-search.md)   
 [作成し、フルテキスト カタログの管理](../../relational-databases/search/create-and-manage-full-text-catalogs.md)   
 [フルテキスト カタログ &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [フルテキスト インデックスの作成と管理](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [フルテキスト検索でのクエリ](../../relational-databases/search/query-with-full-text-search.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/freetext-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [フルテキスト検索でのクエリ](../../relational-databases/search/query-with-full-text-search.md)   
 [フル テキスト検索](../../relational-databases/search/full-text-search.md)   
 [フルテキスト検索クエリの作成 &#40;Visual Database Tools&#41;](http://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [ここで &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)   
 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
