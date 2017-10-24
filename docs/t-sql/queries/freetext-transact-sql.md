---
title: "FREETEXT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FREETEXT
- FREETEXT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], meaning matches
- meaning matches [full-text search]
- FREETEXT predicate (Transact-SQL)
- words in predicate [full-text search]
- column searches [full-text search]
ms.assetid: 2f199d3c-440e-4bcf-bdb5-82bb3994005d
caps.latest.revision: 44
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 48c7ce4788a0c5da0b22e80ab1dc366091c25f97
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="freetext-transact-sql"></a>FREETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  使用される述語である、 [!INCLUDE[tsql](../../includes/tsql-md.md)] [WHERE 句](../../t-sql/queries/where-transact-sql.md)の[!INCLUDE[tsql](../../includes/tsql-md.md)]SELECT ステートメントを実行する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フルテキスト検索をフルテキスト インデックス文字ベースのデータ型を含む列を作成します。 この述語は、検索条件の文字列の並びと正確に一致しなくても意味が合っている値を検索できます。 フルテキスト クエリ エンジンが、上、次の操作を内部で実行する FREETEXT を使用する場合、 *freetext_string*各語に重みを割り当てます、および一致を検索します。  
  
-   単語の区切りに基づいて、文字列を個々の単語に分割。  
  
-   単語の語尾変化形を生成 (語幹への分割)。  
  
-   類義語との一致に基づいて、語の拡張と置き換えの一覧を決定。  
  
> [!NOTE]  
>  サポートされているフルテキスト検索の形式について[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[、フルテキスト検索でのクエリ](../../relational-databases/search/query-with-full-text-search.md)です。  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
FREETEXT ( { column_name | (column_list) | * }   
          , 'freetext_string' [ , LANGUAGE language_term ] )  
```  
  
## <a name="arguments"></a>引数  
 *column_name*  
 FROM 句で指定したテーブルのフルテキスト インデックス付きの列の名前を指定します。 型の列を指定できます**char**、 **varchar**、 **nchar**、 **nvarchar**、**テキスト**、 **ntext**、**イメージ**、 **xml**、 **varbinary**、または**varbinary (max)**です。  
  
 *column_list*  
 コンマ区切りで複数の列を指定できます。 *column_list*かっこで囲む必要があります。 しない限り、 *language_term*が指定されているすべての列の言語*column_list*同じである必要があります。  
  
 \*  
 検索するフルテキスト検索に登録されているすべての列を使用することを示す、指定された*freetext_string*です。 複数のテーブルが FROM 句の場合\*テーブル名で修飾する必要があります。 しない限り、 *language_term*を指定すると、テーブルのすべての列の言語は同じである必要があります。  
  
 *freetext_string*  
 内で検索するテキスト、 *column_name*です。 単語、フレーズ、文など、あらゆるテキストを入力できます。 用語または一定の形式になっている用語がフルテキスト インデックス内に見つかった場合、一致するものと判断されます。  
  
 異なり、CONTAINS および CONTAINSTABLE で検索条件では AND で使用されている場合は、キーワード*freetext_string*単語 'と'、ノイズ ワードと見なされますまたは[ストップ ワード](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)、され破棄されます。  
  
 WEIGHT、FORMSOF、ワイルドカード、NEAR、およびその他の構文は使用できません。 *freetext_string*は単語、語幹に分割され、類義語辞典を通過します。  
  
 *freetext_string*は**nvarchar**です。 入力に他の文字データ型が使用された場合は、暗黙の変換が行われます。 次の例で、`@SearchWord`として定義されている変数`varchar(30)`で暗黙的な変換により、`FREETEXT`述語。  
  
```  
  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord varchar(30)  
SET @SearchWord ='performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
  
```  
  
 「パラメーターを見つけ出す」は、変換では機能しません、ので使用**nvarchar**パフォーマンスが向上します。 例では、宣言`@SearchWord`として`nvarchar(30)`です。  
  
```  
  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
  
```  
  
 また、最適でないプランを生成する場合に OPTIMIZE FOR クエリ ヒントを使用することができます。  
  
 言語*language_term*  
 クエリにおいて、単語区切り、語幹への分割、類義語のチェック、およびストップワードの破棄を行うときに使用する言語リソースの言語を指定します。 このパラメーターは省略可能で、言語のロケール識別子 (LCID) に対応する文字列、整数、または 16 進数の値を指定できます。 場合*language_term*を指定すると、その言語は検索条件のすべての要素に適用されます。 値を指定しなかった場合は、列のフルテキストの言語が使用されます。  
  
 1 つの列に言語の異なる複数のドキュメントが BLOB (Binary Large Object) として格納されている場合、そのインデックスの作成に使用される言語は、そのドキュメントのロケール識別子 (LCID) によって決まります。 このような列のクエリを実行する場合を指定して*言語**language_term*とよく一致の確率を高めることができます。  
  
 文字列として指定されている場合*language_term*に対応する、**エイリアス**彼は列の値[sys.syslanguages & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)互換性ビューです。  文字列は、ように、単一引用符で囲む必要があります '*language_term*' です。 整数として指定すると*language_term*言語を識別する実際の LCID です。 16 進数の値として指定する*language_term*は 0 x 後に LCID の 16 進数の値。 16 進数の値は、先頭の 0 を含め、8 桁以内で指定してください。  
  
 値が 2 バイト文字セット (DBCS) の形式である場合[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Unicode に変換されます。  
  
 無効であるかが、指定された言語がない場合リソースがインストールされていません、その言語に対応している[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はエラーを返します。 ニュートラル言語リソースを使用するには、「0x0」を指定*language_term*です。  
  
## <a name="general-remarks"></a>全般的な解説  
 フルテキストの述語と関数の対象は、FROM 述語で示される 1 つのテーブルです。 複数のテーブルを検索するには、FROM 句で結合テーブルを使用して、複数のテーブルが組み合わされた結果セットを検索します。  
  
FREETEXT を使用するフルテキスト クエリは、CONTAINS を使用するフルテキスト クエリほど正確ではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フルテキスト検索エンジンは、重要な単語や語句を識別します。 予約済みキーワードやワイルドカード通常意味を持つ文字で指定するときに特別な意味を指定しない、 \<contains_search_condition > CONTAINS 述語のパラメーターです。
  
 フルテキスト述語は使用できません、 [OUTPUT 句](../../t-sql/queries/output-clause-transact-sql.md)データベースの互換性レベルを 100 に設定するとします。  
  
> [!NOTE]  
>  FREETEXTTABLE 関数は、FREETEXT 述語と同様の検索に役立ちます。 通常のテーブル名のようにこの関数を参照することができます、[句から](../../t-sql/queries/from-transact-sql.md)SELECT ステートメントのです。 詳細については、次を参照してください。 [FREETEXTTABLE & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/freetexttable-transact-sql.md).  
  
## <a name="querying-remote-servers"></a>リモート サーバーのクエリ  
 4 部構成の名前を使用することができます、 [CONTAINS](../../t-sql/queries/contains-transact-sql.md)または FREETEXT 述語をフルテキスト クエリには、リンク サーバー上の対象テーブルの列がインデックス付きです。 フルテキスト クエリを受け取るようリモート サーバーを準備するには、リモート サーバー上の検索対象のテーブルおよび列にフルテキスト インデックスを作成し、リモート サーバーをリンク サーバーとして追加します。  
  
## <a name="comparison-of-like-to-full-text-search"></a>フルテキスト検索に LIKE の比較  
 フルテキスト検索とは異なり、[LIKE](../../t-sql/language-elements/like-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] 述語は、文字パターンにのみで動作します。 また、フォーマットされたバイナリ データのクエリには LIKE 述語を使用できません。 さらに、構造化されていない大量のテキスト データに対して LIKE クエリを実行すると、同じデータに対して同等のフルテキスト検索を実行する場合に比べてはるかに時間がかかります。 数百万行のテキスト データに対して LIKE クエリを実行すると、結果が得られるまでに数分かかる場合があります。一方、同じデータに対してフルテキスト クエリを実行すると、返される行数にもよりますが、数秒以内で結果を取得できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-freetext-to-search-for-words-containing-specified-character-values"></a>A. FREETEXT を使用して、指定した文字値を含む単語を検索する  
 次の例では、vital、safety、components に関連する単語を含むすべてのドキュメントを検索します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components' );  
GO  
```  
  
### <a name="b-using-freetext-with-variables"></a>B. FREETEXT で変数を使用する  
 次の例では、特定の検索語ではなく変数を使用します。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30);  
SET @SearchWord = N'high-performance';  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
GO  
```  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索の概要](../../relational-databases/search/get-started-with-full-text-search.md)   
 [作成し、フルテキスト カタログの管理](../../relational-databases/search/create-and-manage-full-text-catalogs.md)   
 [フルテキスト カタログ &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [フルテキスト インデックスの作成と管理](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [フルテキスト検索でのクエリ](../../relational-databases/search/query-with-full-text-search.md)   
 [フルテキスト検索クエリの作成 &#40;Visual Database Tools&#41;](http://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [ここで & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)  
  
  

