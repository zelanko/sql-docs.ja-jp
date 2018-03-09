---
title: "FREETEXTTABLE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FREETEXTTABLE_TSQL
- FREETEXTTABLE
dev_langs:
- TSQL
helpviewer_keywords:
- search conditions [SQL Server], meaning matches
- meaning matches [full-text search]
- FREETEXTTABLE function (Transact-SQL)
- ranked results [full-text search]
- column searches [full-text search]
ms.assetid: 4523ae15-4260-40a7-a53c-8df15e1fee79
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 412de75f061da97a82e8494c442e17ba00b03ab7
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="freetexttable-transact-sql"></a>FREETEXTTABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  使用される関数、[句から](../../t-sql/queries/from-transact-sql.md)の[!INCLUDE[tsql](../../includes/tsql-md.md)]SELECT ステートメントを実行する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フルテキスト検索をフルテキスト インデックス文字ベースのデータ型を含む列を作成します。 この関数は、0、1、または複数の行を意味し、正確な表現だけでなく、指定したテキストの一致する値を格納している列のテーブルを返します*freetext_string*です。 FREETEXTTABLE は、通常のテーブル名のように参照されます。  
  
 FREETEXTTABLE は、同じ種類と一致するのに役立つ、 [FREETEXT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/freetext-transact-sql.md),  
  
 FREETEXTTABLE を使用するクエリでは、各行の関連順位値 (RANK) とフルテキスト キー (KEY) が取得されます。  
  
> [!NOTE]  
>  サポートされているフルテキスト検索の形式について[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[、フルテキスト検索でのクエリ](../../relational-databases/search/query-with-full-text-search.md)です。  
  
(http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
FREETEXTTABLE (table , { column_name | (column_list) | * }   
          , 'freetext_string'   
     [ , LANGUAGE language_term ]   
     [ , top_n_by_rank ] )  
```  
  
## <a name="arguments"></a>引数  
 *テーブル*  
 フルテキスト クエリ用に指定されているテーブルの名前を指定します。 *テーブル*または*ビュー*1 部、2 部、または 3 部構成のデータベース オブジェクトの名前を指定できます。 ビューに対してクエリを実行する場合は、フルテキスト インデックスが作成されたベース テーブルを 1 つだけ指定できます。  
  
 *テーブル*とサーバー名を指定できません。 リンク サーバーに対するクエリでは使用できません。  
  
 *column_name*  
 FROM 句で指定したテーブルのフルテキスト インデックス付きの列の名前を指定します。 型の列を指定できます**char**、 **varchar**、 **nchar**、 **nvarchar**、**テキスト**、 **ntext**、**イメージ**、 **xml**、 **varbinary**、または**varbinary (max)**です。  
  
 *column_list*  
 コンマ区切りで複数の列を指定できます。 *column_list*かっこで囲む必要があります。 しない限り、 *language_term*が指定されているすべての列の言語*column_list*同じである必要があります。  
  
 \*  
 検索するフルテキスト検索に登録されているすべての列を使用することを示す、指定された*freetext_string*です。 しない限り、 *language_term*を指定すると、テーブル内のすべてのフルテキスト インデックス付き列の言語は同じである必要があります。  
  
 *freetext_string*  
 内で検索するテキスト、 *column_name*です。 単語、フレーズ、文など、あらゆるテキストを入力できます。 用語または一定の形式になっている用語がフルテキスト インデックス内に見つかった場合、一致するものと判断されます。  
  
 異なり、CONTAINS の検索条件では AND で使用されている場合は、キーワード*freetext_string*単語 'と'、ノイズ ワードと見なされますまたは[ストップ ワード](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)、され破棄されます。  
  
 WEIGHT、FORMSOF、ワイルドカード、NEAR、およびその他の構文は使用できません。 *freetext_string*は単語、語幹に分割され、類義語辞典を通過します。  
  
 言語*language_term*  
 クエリにおいて、単語区切り、語幹への分割、類義語のチェック、およびストップワードの破棄を行うときに使用する言語リソースの言語を指定します。 このパラメーターは省略可能で、言語のロケール識別子 (LCID) に対応する文字列、整数、または 16 進数の値を指定できます。 場合*language_term*を指定すると、その言語は検索条件のすべての要素に適用されます。 値を指定しなかった場合は、列のフルテキストの言語が使用されます。  
  
 1 つの列に言語の異なる複数のドキュメントが BLOB (Binary Large Object) として格納されている場合、そのインデックスの作成に使用される言語は、そのドキュメントのロケール識別子 (LCID) によって決まります。 このような列のクエリを実行する場合を指定して*言語 * * language_term*とよく一致の確率を高めることができます。  
  
 文字列として指定されている場合*language_term*に対応する、**エイリアス**列の値、 [sys.syslanguages &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)互換性ビューです。  文字列は、ように、単一引用符で囲む必要があります '*language_term*' です。 整数として指定すると*language_term*言語を識別する実際の LCID です。 16 進数の値として指定する*language_term*は 0 x 後に LCID の 16 進数の値。 16 進数の値は、先頭の 0 を含め、8 桁以内で指定してください。  
  
 値が 2 バイト文字セット (DBCS) の形式である場合[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Unicode に変換されます。  
  
 無効であるかが、指定された言語がない場合リソースがインストールされていません、その言語に対応している[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はエラーを返します。 ニュートラル言語リソースを使用するには、「0x0」を指定*language_term*です。  
  
 *top_n_by_rank*  
 だけを *n*降順で最高順位の一致が返されます。 整数値、場合にのみ適用されます *n*を指定します。 *top_n_by_rank* を他のパラメーターと組み合わせた場合、クエリから返される行数は、実際にすべての述語に一致する行数より少なくなります。 *top_n_by_rank*最も重要なヒットだけを再度呼び出すことによってクエリ パフォーマンスを向上することができます。  
  
## <a name="remarks"></a>解説  
 フルテキストの述語と関数の対象は、FROM 述語で示される 1 つのテーブルです。 複数のテーブルを検索するには、FROM 句で結合テーブルを使用して、複数のテーブルが組み合わされた結果セットを検索します。  
  
 FREETEXTTABLE では、FREETEXT 述語と同じ検索条件が使用されます。  
  
 CONTAINSTABLE と同様、返されるテーブルがという名前の列を持つ**キー**と**ランク**、適切な行を取得し、行の順位値を使用するクエリ内で参照されます。  
  
## <a name="permissions"></a>権限  
 FREETEXTTABLE を呼び出すには、指定されるテーブルまたは参照されるテーブル列に対して適切な SELECT 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-example"></a>A. 簡単な例  
 次の例では、作成し、3 つの郡およびそのフラグの色の一覧を表示する 2 つの列の単純なテーブルを入力します。 It では、作成し、テーブルのインデックス、フルテキスト カタログを設定します。 続いて、 **FREETEXTTABLE**構文を説明します。  
  
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
SELECT * FROM FREETEXTTABLE (Flags, FlagColors, 'Blue');  
SELECT * FROM FREETEXTTABLE (Flags, FlagColors, 'Yellow');  
```  
  
### <a name="b-using-freetext-in-an-inner-join"></a>B. INNER JOIN での FREETEXT の使用  
 次の例に関連するすべてのカテゴリの説明とカテゴリの名前を返します`sweet`、 `candy`、 `bread`、 `dry`、または`meat`です。  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.Description  
    ,KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL   
    INNER JOIN FREETEXTTABLE(Production.ProductDescription,  
    Description,   
    'high level of performance') AS KEY_TBL  
ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY RANK DESC;  
GO  
```  
  
### <a name="c-specifying-language-and-highest-ranked-matches"></a>C. 言語および最高順位の一致の指定  
 次の例と同じでありの使用方法を示します、 `LANGUAGE` *language_term*と*top_n_by_rank*パラメーター。  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.Description  
    ,KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL   
    INNER JOIN FREETEXTTABLE(Production.ProductDescription,  
    Description,   
    'high level of performance',  
    LANGUAGE N'English', 2) AS KEY_TBL  
ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY RANK DESC;  
GO  
```  
  
> [!NOTE]  
>  言語*language_term* paramete*r*を使用する必要はありません、 *top_n_by_rank*パラメーター*です。*  
  
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
 [FREETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/freetext-transact-sql.md)   
 [行セット関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/rowset-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [ここで &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)   
 [precompute rank サーバー構成オプション](../../database-engine/configure-windows/precompute-rank-server-configuration-option.md)  
  
  
