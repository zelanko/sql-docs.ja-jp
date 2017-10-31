---
title: "挿入 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- INSERT_TSQL
- INSERT
dev_langs:
- TSQL
helpviewer_keywords:
- inserting multiple rows
- user-defined types [SQL Server], inserting values
- DML [SQL Server], INSERT statement
- bulk load [SQL Server]
- row additions [SQL Server], INSERT statement
- inserting rows
- table value constructor [SQL Server]
- adding data
- INSERT statement [SQL Server], about INSERT statement
- INSERT statement [SQL Server]
- UDTs [SQL Server], inserting values
- adding rows
- INSERT INTO statement
- data manipulation language [SQL Server], INSERT statement
- inserting data
ms.assetid: 1054c76e-0fd5-4131-8c07-a6c5d024af50
caps.latest.revision: 136
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ef8387c2bbbc109ad7ec325e4faf632a983d96c9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="insert-transact-sql"></a>INSERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  テーブルまたはビューの 1 つに 1 つまたは複数の行を追加[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 例については、次を参照してください。[例](#InsertExamples)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  

[ WITH <common_table_expression> [ ,...n ] ]  
INSERT   
{  
        [ TOP ( expression ) [ PERCENT ] ]   
        [ INTO ]   
        { <object> | rowset_function_limited   
          [ WITH ( <Table_Hint_Limited> [ ...n ] ) ]  
        }  
    {  
        [ ( column_list ) ]   
        [ <OUTPUT Clause> ]  
        { VALUES ( { DEFAULT | NULL | expression } [ ,...n ] ) [ ,...n     ]   
        | derived_table   
        | execute_statement  
        | <dml_table_source>  
        | DEFAULT VALUES   
        }  
    }  
}  
[;]  
  
<object> ::=  
{   
    [ server_name . database_name . schema_name .   
      | database_name .[ schema_name ] .   
      | schema_name .   
    ]  
  table_or_view_name  
}  
  
<dml_table_source> ::=  
    SELECT <select_list>  
    FROM ( <dml_statement_with_output_clause> )   
      [AS] table_alias [ ( column_alias [ ,...n ] ) ]  
    [ WHERE <search_condition> ]  
        [ OPTION ( <query_hint> [ ,...n ] ) ]  
```  
  
```  
-- External tool only syntax  

INSERT   
{  
    [BULK]  
    [ database_name . [ schema_name ] . | schema_name . ]  
    [ table_name | view_name ]  
    ( <column_definition> )  
    [ WITH (  
        [ [ , ] CHECK_CONSTRAINTS ]  
        [ [ , ] FIRE_TRIGGERS ]  
        [ [ , ] KEEP_NULLS ]  
        [ [ , ] KILOBYTES_PER_BATCH = kilobytes_per_batch ]  
        [ [ , ] ROWS_PER_BATCH = rows_per_batch ]  
        [ [ , ] ORDER ( { column [ ASC | DESC ] } [ ,...n ] ) ]  
        [ [ , ] TABLOCK ]  
    ) ]  
}  
  
[; ] <column_definition> ::=  
 column_name <data_type>  
    [ COLLATE collation_name ]  
    [ NULL | NOT NULL ]  
  
<data type> ::=   
[ type_schema_name . ] type_name   
    [ ( precision [ , scale ] | max ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

INSERT INTO [ database_name . [ schema_name ] . | schema_name . ] table_name   
    [ ( column_name [ ,...n ] ) ]  
    {   
      VALUES ( { NULL | expression } )  
      | SELECT <select_criteria>  
    }  
    [ OPTION ( <query_option> [ ,...n ] ) ]  
[;]  
```  
  
## <a name="arguments"></a>引数  
 \<Common_table_expression >  
 INSERT ステートメントのスコープ内で定義された、一時的な名前付き結果セット (共通テーブル式とも呼ばれる) を指定します。 結果セットは SELECT ステートメントから派生します。 詳細については、次を参照してください。[で common_table_expression と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 上部 (*式*) [PERCENT]  
 挿入するランダムな行の数または比率 (%) を指定します。 *expression* は行数または行の比率 (%) にすることができます。 詳細については、次を参照してください。 [TOP & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/top-transact-sql.md).  
  
 INTO  
 INSERT キーワードと対象のテーブルとの間で使用できるキーワードで、省略可能です。  
  
 *サーバー名*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 テーブルまたはビューが配置されているリンク サーバーの名前です。 *server_name*として指定することができます、[リンク サーバー](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)名、またはを使用して、 [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md)関数。  
  
 ときに*server_name* 、リンク サーバーとして指定された*database_name*と*schema_name*が必要です。 ときに*server_name* 、OPENDATASOURCE で指定された*database_name*と*schema_name*がすべてのデータ ソースに適用されると、OLE DB の機能はリモート オブジェクトにアクセスするプロバイダーです。  
  
 *database_name*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 データベースの名前です。  
  
 *schema_name*  
 テーブルまたはビューが属するスキーマの名前を指定します。  
  
 *table_or view_name*  
 データを受け取るテーブルまたはビューの名前を指定します。  
  
 A[テーブル](../../t-sql/data-types/table-transact-sql.md)、そのスコープ内の変数は、INSERT ステートメントでテーブル ソースとして使用できます。  
  
 によって参照されるビュー *table_or_view_name*可能にし、ビューの FROM 句内のただ 1 つのベース テーブルを参照する必要があります。 たとえば、複数のテーブル ビューに INSERT を使用する必要があります、 *column_list* 1 つのベース テーブルから列のみを参照します。 更新可能なビューの詳細については、次を参照してください。 [CREATE VIEW & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-view-transact-sql.md).  
  
 *rowset_function_limited*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 いずれかが、 [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md)または[OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)関数。 これらの関数の使用は、リモート オブジェクトにアクセスする OLE DB プロバイダーの機能により制限されます。  
  
 使用 ( \<table_hint_limited > [.*n* ] )  
 対象のテーブルに設定可能なテーブル ヒントを 1 つ以上指定します。 キーワード WITH とかっこが必要です。  
  
 READPAST、NOLOCK、および READUNCOMMITTED は指定できません。 テーブル ヒントの詳細については、次を参照してください。[テーブル ヒント & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/hints-transact-sql-table.md).  
  
> [!IMPORTANT]  
>  INSERT ステートメントの対象になっているテーブルで HOLDLOCK、SERIALIZABLE、READCOMMITTED、REPEATABLEREAD、または UPDLOCK のヒントを指定する機能は、将来のバージョンで削除される予定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 これらのヒントは、INSERT ステートメントのパフォーマンスに影響を与えません。 新しい開発作業では、これらのオプションの使用は避け、現在これらを使用しているアプリケーションは修正するようにしてください。  
  
 INSERT ステートメントの対象であるテーブルに対して TABLOCK ヒントを指定すると、TABLOCKX ヒントを指定した場合と同じ効果を得られます。 テーブルに対して、排他ロックが取得されます。  
  
 (*column_list*)  
 データを挿入する、1 つ以上の列で構成されるリストを指定します。 *column_list*をかっこで囲むしてコンマで区切る必要があります。  
  
 場合は、列がない*column_list*、[!INCLUDE[ssDE](../../includes/ssde-md.md)]を提供できる必要があります、列の定義に基づく値です。 それ以外の場合、行を読み込むことができません。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]場合に、列の値を自動的に提供された列。  
  
-   IDENTITY プロパティを持っている。 増分された次の ID 値が使用されます。  
  
-   既定値を持っている。 列の既定値が使用されます。  
  
-   **タイムスタンプ**データ型。 現在のタイムスタンプ値が使用されます。  
  
-   NULL 値が許可されます。 NULL 値が使用されます。  
  
-   計算列である。 計算値が使用されます。  
  
*column_list*明示的な値は、id 列に挿入され、テーブルの SET IDENTITY_INSERT オプションが ON をする必要があるときに使用する必要があります。  
  
OUTPUT 句  
 挿入操作の一部として、挿入された行を返します。 処理中のアプリケーションに結果を返すことも、テーブルまたはテーブル変数に結果を挿入して処理を続行することもできます。  
  
 [OUTPUT 句](../../t-sql/queries/output-clause-transact-sql.md)は、ローカル パーティション ビュー、分散パーティション ビュー、またはリモート テーブルを参照する DML ステートメントまたはを含む INSERT ステートメントではサポートされていません、 *execute_statement*. 含む INSERT ステートメントで OUTPUT INTO 句はサポートされていません、 \<dml_table_source > 句。 
  
 VALUES  
 追加するデータ値のリストを 1 つ以上指定します。 各列に対して 1 つのデータ値である必要があります*column_list*指定される場合、またはテーブル内のします。 値リストは、かっこで囲む必要があります。  
  
 値リスト内の値が含まれない場合と同じ順序、テーブル内の列またはテーブルの各列の値はありません*column_list*各入力値を格納する列を明示的に指定するために使用する必要があります。  
  
 使用することができます、[!INCLUDE[tsql](../../includes/tsql-md.md)]コンス トラクター (テーブル値コンス トラクターとも呼ばれます) を行、単一の INSERT ステートメントで複数の行を指定します。 行コンストラクターは、かっこで囲まれ、コンマで区切られた複数の値リストを含む単一の VALUES 句で構成されています。 詳細については、次を参照してください。[テーブル値コンス トラクターと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/table-value-constructor-transact-sql.md).  
  
 DEFAULT  
 強制的に実行、[!INCLUDE[ssDE](../../includes/ssde-md.md)]列に対して定義されている既定値を読み込みます。 既定値がなく、列に対して NULL が許可されている場合は、NULL が挿入されます。 定義された列の**タイムスタンプ**データ型の次のタイムスタンプ値が挿入されます。 DEFAULT は ID 列には有効ではありません。  
  
 *式 (expression)*  
 定数、変数、または式を指定します。 式には EXECUTE ステートメントを含めることができません。  
  
 Unicode 文字データ型を参照するときに**nchar**、 **nvarchar**、および**ntext**、'*式*' を付ける必要があります、大文字の 'N' です。 場合 'n' が指定されていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースまたは列の既定の照合順序に対応するコード ページに文字列に変換します。 文字列がこのコード ページにない場合は、失われます。  
  
 *derived_table*  
 テーブルに読み込まれるデータの行を返す、有効な SELECT ステートメントを指定します。 SELECT ステートメントには、共通テーブル式 (CTE) を含めることはできません。  
  
 *execute_statement*  
 SELECT ステートメントまたは READTEXT ステートメントでデータを返す有効な EXECUTE ステートメントです。 詳細については、「 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)」を参照してください。  
  
 INSERT…EXEC ステートメントでは、EXECUTE ステートメントの RESULT SETS オプションを指定することができません。  
  
 場合*execute_statement*使用は、INSERT では、各結果セットをテーブルまたは列との互換性にする必要があります*column_list*です。  
  
 *execute_statement*同じサーバーまたはリモート サーバーでストアド プロシージャを実行するために使用できます。 リモート サーバーのプロシージャが実行されると、結果セットがローカル サーバーに返され、ローカル サーバーのテーブルに読み込まれます。 分散トランザクションに*execute_statement*接続がある複数のアクティブな結果セット (MARS) は有効になっているときに、ループバック リンク サーバーに対して発行されることはできません。  
  
 場合*execute_statement*データを返す、READTEXT ステートメントでは、各 READTEXT ステートメントは、最大で 1 mb (1024 KB) のデータを返すことができます。 *execute_statement*拡張プロシージャで使用することもできます。 *execute_statement*拡張プロシージャのメイン スレッドによって返されるデータを挿入します。 ただし、メイン スレッド以外のスレッドからの出力は挿入しません。  
  
 テーブル値パラメーターは、INSERT EXEC ステートメントの対象として指定できませんが、INSERT EXEC 文字列またはストアド プロシージャにソースとして指定できます。 詳細については、「[テーブル値パラメーターの使用 &#40;Database Engine&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)」を参照してください。  
  
 \<dml_table_source >  
 INSERT、UPDATE、DELETE、または MERGE ステートメントの OUTPUT 句で返された行 (WHERE 句でフィルター処理される場合もあります) を対象のテーブルに挿入するように指定します。 場合\<dml_table_source > を指定すると、外部の INSERT ステートメントの対象は、次の制限を満たす必要があります。 
  
-   ビューではなくベース テーブルである必要があります。  
  
-   リモート テーブルは使用できません。  
  
-   トリガーが定義されているテーブルは使用できません。  
  
-   主キー/外部キーのリレーションシップに加えることはできません。  
  
-   マージ レプリケーションや、トランザクション レプリケーションの更新可能なサブスクリプションに加えることはできません。  
  
 データベース互換性レベルを 100 以上に設定する必要があります。 詳細については、次を参照してください。 [OUTPUT 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/output-clause-transact-sql.md).  
  
 \<select_list >  
 Output 句から返された列のどれを挿入するかを指定するコンマ区切りのリストです。 内の列\<select_list > 値の挿入先の列と互換である必要があります。 \<select_list > 集計関数または TEXTPTR を参照することはできません。 
  
> [!NOTE]  
>  選択リストに表示されている任意の変数でそれらに加えられた変更に関係なく、元の値を参照して\<dml_statement_with_output_clause >。  
  
 \<dml_statement_with_output_clause >  
 影響を受ける行を OUTPUT 句で返す有効な INSERT、UPDATE、DELETE、または MERGE ステートメントです。 このステートメントには WITH 句を指定できず、リモート テーブルまたはパーティション ビューを対象にすることもできません。 UPDATE または DELETE を指定する場合、カーソルベースの UPDATE または DELETE は指定できません。 ソース行を、入れ子になった DML ステートメントとして参照することはできません。  
  
 ここで\<search_condition >  
 いずれかの WHERE 句を含む有効な\<search_condition > によって返される行のフィルター処理する\<dml_statement_with_output_clause >。 詳細については、次を参照してください。[検索条件 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/search-condition-transact-sql.md). このコンテキストで使用すると\<search_condition > サブクエリ、スカラー ユーザー定義関数は、データ アクセス、集計関数、TEXTPTR、または、フルテキスト検索の述語を含めることはできません。 
  
 DEFAULT VALUES  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 新しい行が、各列に対して定義されている既定値で構成されることを指定します。  
  
 BULK  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 外部ツールでバイナリ データ ストリームをアップロードする際に使用されます。 このオプションはありませんツールで使用するように[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、SQLCMD、OSQL、またはデータ アクセス アプリケーション プログラミング インターフェイスなど[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client です。  
  
 FIRE_TRIGGERS  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 バイナリ データ ストリームのアップロード処理中に、変換先テーブルで定義されている挿入トリガーを実行することを指定します。 詳細については、「[BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)」を参照してください。  
  
 CHECK_CONSTRAINTS  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 バイナリ データ ストリームのアップロード処理中に、対象テーブルまたはビューに対するすべての制約を検証します。 詳細については、「[BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)」を参照してください。  
  
 KEEPNULLS  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 バイナリ データ ストリームのアップロード処理中に、空の列の NULL 値を保持します。 詳細については、「[一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)」をご覧ください。  
  
 KILOBYTES_PER_BATCH = kilobytes_per_batch  
 バッチごとのデータのキロバイト (KB) のおおよその数を指定*kilobytes_per_batch*です。 詳細については、「[BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)」を参照してください。  
  
 ROWS_PER_BATCH =*rows_per_batch*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 バイナリ データ ストリーム内のデータ行の概算数を指定します。 詳細については、「[BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)」を参照してください。  
  
>  [!NOTE]
>  列リストが指定されていない場合、構文エラーが発生します。  

## <a name="remarks"></a>解説  
グラフの SQL テーブルにデータを挿入する固有の情報を参照してください。 [INSERT (SQL グラフ)](../../t-sql/statements/insert-sql-graph.md)です。 

## <a name="best-practices"></a>ベスト プラクティス  
 使用して、@@ROWCOUNT関数の数を返しますが、クライアント アプリケーションに行を挿入します。 詳細については、次を参照してください。 [@@ROWCOUNT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/rowcount-transact-sql.md).  
  
### <a name="best-practices-for-bulk-importing-data"></a>データの一括インポートに関するベスト プラクティス  
  
#### <a name="using-insert-intoselect-to-bulk-import-data-with-minimal-logging"></a>INSERT INTO...SELECT を使用したデータ一括インポート時の最小ログ記録  
 使用することができます`INSERT INTO <target_table> SELECT <columns> FROM <source_table>`を最小ログ記録の別のテーブルにステージング テーブルなどの 1 つのテーブルから大量の行を効率的に転送します。 最小ログ記録を行うと、ステートメントのパフォーマンスが向上します。また、トランザクションの実行中に、使用可能なトランザクション ログ領域がこの操作でいっぱいになる可能性を低減します。  
  
 このステートメントの最小ログ記録には、次の要件があります。  
  
-   データベース復旧モデルが単純復旧モデルまたは一括ログ復旧モデルに設定されている。  
  
-   対象テーブルが、空のヒープか、空でないヒープである。  
  
-   対象テーブルがレプリケーションで使用されない。  
  
-   対象テーブルに TABLOCK ヒントが指定されている。  
  
MERGE ステートメントでの挿入操作の結果としてヒープに挿入される行についても、最小ログ記録が行われる場合があります。  
  
 より制限の少ない一括更新ロックを保持する BULK INSERT ステートメントとは異なり、TABLOCK ヒントが指定された INSERT INTO...SELECT は、テーブルに対する排他的な (X) ロックを保持します。 したがって、並列挿入操作を使用して行を挿入することはできません。  
  
#### <a name="using-openrowset-and-bulk-to-bulk-import-data"></a>OPENROWSET および BULK によるデータの一括インポート  
 OPENROWSET 関数では次のテーブル ヒントを使用できます。これらのテーブル ヒントにより、一括読み込みの最適化を INSERT ステートメントで利用できます。  
  
-   TABLOCK ヒントを使用すると、挿入操作のログ レコード数を最小化できます。 データベース復旧モデルが単純復旧モデルまたは一括ログ復旧モデルに設定されている必要があります。また、対象テーブルはレプリケーションで使用できません。 詳細については、次を参照してください。[一括インポートで最小ログ記録の前提条件](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)です。  
  
-   IGNORE_CONSTRAINTS ヒントを使用すると、FOREIGN KEY および CHECK の制約チェックを一時的に無効にできます。  
  
-   IGNORE_TRIGGERS ヒントを使用すると、トリガーの実行を一時的に無効にできます。  
  
-   KEEPDEFAULTS ヒントを使用すると、データ レコードにテーブルの列値が含まれていない場合に、NULL の代わりにテーブル列の既定値を挿入できます。  
  
-   KEEPIDENTITY ヒントを使用すると、インポートしたデータ ファイルの ID 値を対象テーブルの ID 列に使用できます。  
  
これらは、BULK INSERT コマンドで使用可能な最適化と似ています。 詳細については、「[テーブル ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md)」を参照してください。  
  
## <a name="data-types"></a>データ型  
 行の挿入時には、次のデータ型の動作を考慮してください。  
  
-   値を持つ列が読み込まれる場合、 **char**、 **varchar**、または**varbinary**データ型、余白または後続の空白の切り捨て (のスペース**char**と**varchar**、0 **varbinary**) は、テーブルが作成されたときに、列に対して定義された SET ANSI_PADDING の設定によって決まります。 詳細については、「[SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)」を参照してください。  
  
     次の表は、SET ANSI_PADDING OFF の既定の操作を示します。  
  
    |データ型|既定の操作|  
    |---------------|-----------------------|  
    |**char**|定義された列幅になるように値に空白を埋めます。|  
    |**varchar**|空白以外の最終文字に達するまで、後続の空白を削除します。文字列が空白だけで構成されている場合は、1 つのスペース文字を残して、後続の空白を削除します。|  
    |**varbinary**|後続の 0 を削除します。|  
  
-   空文字列 (' ') を持つ列に読み込まれ、 **varchar**または**テキスト**データ型の既定の操作は、長さ 0 の文字列を読み込めません。  
  
-   Null 値を挿入する、**テキスト**または**イメージ**列では、有効なテキスト ポインターは作成されず、また、8 KB のテキスト ページもあらかじめ割り当てされません。  
  
-   作成される列、 **uniqueidentifier**特別にフォーマットされた 16 バイトのバイナリ値をデータ型のストア。 異なり id 列を持つ、[!INCLUDE[ssDE](../../includes/ssde-md.md)]列の値を自動的に生成しない、 **uniqueidentifier**データ型。 変数に、データ型を挿入操作中に**uniqueidentifier**形式の文字列定数と*xxxxxxxx xxxx-xxxx-* (ハイフンを含む 36 文字で。*x*は 0 ~ 9 または a ~ f の 16 進数字) のために使用する**uniqueidentifier**列です。 たとえば、6F9619FF-8B86-D011-B42D-00C04FC964FF は有効な値を**uniqueidentifier**変数または列。 使用して、 [NEWID()](../../t-sql/functions/newid-transact-sql.md)グローバルに一意の ID (GUID) を取得します。  
  
### <a name="inserting-values-into-user-defined-type-columns"></a>ユーザー定義型の列への値の挿入  
 ユーザー定義型の列に値を挿入するには、次のようにします。  
  
-   そのユーザー定義型の値を指定します。  
  
-   値を指定して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム データ型、ユーザー定義型は、その型から暗黙的または明示的な変換をサポートしている限り、します。 次の例は、ユーザー定義型の列に値を挿入する方法を示しています。 `Point`、文字列から明示的に変換することで。  
  
    ```  
    INSERT INTO Cities (Location)  
    VALUES ( CONVERT(Point, '12.3:46.2') );  
    ```  
  
     明示的な変換を実行することなく、バイナリ値を指定することもできます。これは、すべてのユーザー定義型が、バイナリからの暗黙的な変換が可能であるためです。  
  
-   そのユーザー定義型の値を返すユーザー定義関数を呼び出します。 次の例は、ユーザー定義関数を使用して`CreateNewPoint()`ユーザー定義型の新しい値を作成する`Point`に値を挿入し、`Cities`テーブル。  
  
    ```  
    INSERT INTO Cities (Location)  
    VALUES ( dbo.CreateNewPoint(x, y) );  
    ```  
  
## <a name="error-handling"></a>エラー処理  
 TRY…CATCH 構造でステートメントを指定することで、INSERT ステートメントのエラー処理を実装できます。  
  
 INSERT ステートメントが制約やルールに違反していたり、その値が列のデータ型と互換性を持たない場合は、ステートメントが失敗し、エラー メッセージが返されます。  
  
 INSERT が SELECT または EXECUTE で複数の行を読み込んでいる場合、読み込まれている値でルールや制約の違反が発生すると、ステートメントが停止し、行は読み込まれません。  
  
 INSERT ステートメントの中で、式の評価中に算術エラー (オーバーフロー、0 による除算、またはドメイン エラー) が発生すると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では、SET ARITHABORT が ON に設定されている場合と同様に、これらのエラーが処理されます。 バッチは停止し、エラー メッセージが返されます。 式の評価中に SET ARITHABORT と SET ANSI_WARNINGS を OFF に、INSERT、DELETE または UPDATE ステートメントが発生し、算術エラー、オーバーフロー、0 による除算、またはドメイン エラー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を挿入します。 または、NULL 値を更新します。 出力先の列で NULL 値が許容されない場合は、挿入または更新処理は失敗し、エラーが返されます。  
  
## <a name="interoperability"></a>相互運用性  
 テーブルやビューを対象とする INSERT 操作で INSTEAD OF トリガーが定義されている場合は、INSERT ステートメントの代わりにトリガーが実行されます。 INSTEAD of トリガーの詳細については、次を参照してください。 [CREATE TRIGGER & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-trigger-transact-sql.md).  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 リモート テーブルに値を挿入するとき、すべての列のすべての値が指定されている場合を除いて、指定された値をどの列に挿入するかをユーザーが指定する必要があります。  
  
 TOP を INSERT と共に使用する場合、参照される行は任意の順序に並べられません。また、このステートメントで、ORDER BY 句を直接指定することはできません。 TOP を使用して意味のある順序で行を挿入する必要がある場合は、サブセレクト ステートメントで ORDER BY 句を指定して TOP を使用する必要があります。 例については、後の「例」のセクションを参照してください。
 
使用する挿入クエリは、行の保証が id 値の計算方法は、行が挿入される順序を設定する ORDER BY でを選択します。    
  
## <a name="logging-behavior"></a>ログ記録の動作  
 INSERT ステートメントが常に完全にログに記録を除く、OPENROWSET 関数を BULK キーワードを使用する場合、またはを使用して`INSERT INTO <target_table> SELECT <columns> FROM <source_table>`です。 これらの操作のログへの記録は最小限にできます。 詳細については、前の「データの一括読み込みの推奨事項」を参照してください。  
  
## <a name="security"></a>セキュリティ  
 リンク サーバーに接続する場合、送信側サーバーは受信側サーバーに接続するためにログイン名とパスワードをリンク サーバーに代わって提供します。 この接続を機能させるを使用してリンク サーバー間でログイン マッピングを作成する必要があります[sp_addlinkedsrvlogin](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)です。  
  
 OPENROWSET(BULK…) を使用するにあたっては、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で権限借用がどのように処理されるかを理解しておくことが重要です。 詳細については、「セキュリティの考慮事項」を参照してください[を使用して BULK INSERT または OPENROWSET &#40; した一括データのインポートBULK..."&"#41;& #40 です。SQL Server &#41;](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).  
  
### <a name="permissions"></a>Permissions  
 対象のテーブルに対する INSERT 権限が必要です。  
  
 メンバーにアクセス許可の既定値の挿入、 **sysadmin**固定サーバー ロール、 **db_owner**と**db_datawriter**固定データベース ロール、およびテーブル所有者です。 メンバー、 **sysadmin**、 **db_owner**、および**db_securityadmin**ロール、およびテーブル所有者は、他のユーザーに権限を譲渡できます。  
  
 OPENROWSET 関数の BULK オプションで、挿入を実行するには、メンバーである、 **sysadmin**固定サーバー ロールまたはの**bulkadmin**固定サーバー ロール。  
  
##  <a name="InsertExamples"></a> 使用例  
  
|カテゴリ|主な構文要素|  
|--------------|------------------------------|  
|[基本構文](#BasicSyntax)|INSERT • テーブル値コンストラクター|  
|[列値の処理](#ColumnValues)|IDENTITY • NEWID • 既定値 • ユーザー定義型|  
|[他のテーブルからデータを挿入します。](#OtherTables)|INSERT...SELECT • INSERT...EXECUTE • WITH 共通テーブル式 • TOP • OFFSET FETCH|  
|[標準的なテーブル以外の対象オブジェクトを指定します。](#TargetObjects)|ビュー • テーブル変数|  
|[リモート テーブルに行を挿入します。](#RemoteTables)|リンク サーバー、OPENQUERY 行セット関数、OPENDATASOURCE 行セット関数|  
|[データの一括読み込みのテーブルまたはデータ ファイルから](#BulkLoad)|INSERT…SELECT • OPENROWSET 関数|  
|[ヒントを使用して、クエリ オプティマイザーの既定の動作を上書きする.](#TableHints)|テーブル ヒント|  
|[INSERT ステートメントの結果をキャプチャ](#CaptureResults)|OUTPUT 句|  
  
###  <a name="BasicSyntax"></a>基本構文  
 このセクションの例では、最低限必要な構文を使用して INSERT ステートメントの基本機能を示します。  
  
#### <a name="a-inserting-a-single-row-of-data"></a>A. 1 行のデータを挿入する  
 次の例に 1 つの行の挿入、`Production.UnitMeasure`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。 このテーブルの列は、`UnitMeasureCode`、`Name`、および `ModifiedDate` です。 すべての列の値が指定され、テーブル内の列と同じ順序で並んでいる、ため、列名を列リストで指定するのにはありません*です。*  
  
```  
INSERT INTO Production.UnitMeasure  
VALUES (N'FT', N'Feet', '20080414');  
```  
  
#### <a name="b-inserting-multiple-rows-of-data"></a>B. 複数行のデータを挿入する  
 次の例では、[テーブル値コンス トラクター](../../t-sql/queries/table-value-constructor-transact-sql.md)に 3 つの行を挿入する、`Production.UnitMeasure`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]単一の INSERT ステートメント内のデータベースです。 すべての列の値が指定され、テーブルの列と同じ順序で並んでいるため、列名を列リストで指定する必要はありません。  
  
```  
INSERT INTO Production.UnitMeasure  
VALUES (N'FT2', N'Square Feet ', '20080923'), (N'Y', N'Yards', '20080923')
    , (N'Y3', N'Cubic Yards', '20080923');  
```  
  
#### <a name="c-inserting-data-that-is-not-in-the-same-order-as-the-table-columns"></a>C. テーブルの列と順序が異なるデータを挿入する  
 次の例では、列リストを使用して、各列に挿入する値を明示的に指定します。 列の順序、`Production.UnitMeasure`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース`UnitMeasureCode`、 `Name`、 `ModifiedDate`。 ただし、列がその順序で並んでいません*column_list*です。  
  
```  
INSERT INTO Production.UnitMeasure (Name, UnitMeasureCode,  
    ModifiedDate)  
VALUES (N'Square Yards', N'Y2', GETDATE());  
```  
  
###  <a name="ColumnValues"></a>列値の処理  
 このセクションの例の既定値は、IDENTITY プロパティを持つが定義されてかなどのデータ型で定義された列に値を挿入する方法を示します**uniqueidentifer**またはユーザー定義型列です。  
  
#### <a name="d-inserting-data-into-a-table-with-columns-that-have-default-values"></a>D. 列が既定値に設定されているテーブルにデータを挿入する  
 次の例では、値が自動生成される列や既定値が設定される列を使用して、テーブルに行を挿入します。 `Column_1`挿入された値を持つ文字列を連結して値を自動的に生成する計算列である`column_2`です。 `Column_2` は、既定の制約で定義されています。 この列の値が指定されていない場合、既定値が使用されます。 `Column_3`定義された、 **rowversion**データ型は、一意の増分するバイナリ番号を自動的に生成されます。 `Column_4` は、値の自動生成を行いません。 この列の値が指定されていない場合、NULL が挿入されます。 INSERT ステートメントでは、すべての列ではなく一部の列の値を含む行を挿入します。 最後の INSERT ステートメントでは、どの列も指定されていないため、DEFAULT VALUES 句を使用して既定値のみが挿入されます。  
  
```  
CREATE TABLE dbo.T1   
(  
    column_1 AS 'Computed column ' + column_2,   
    column_2 varchar(30)   
        CONSTRAINT default_name DEFAULT ('my column default'),  
    column_3 rowversion,  
    column_4 varchar(40) NULL  
);  
GO  
INSERT INTO dbo.T1 (column_4)   
    VALUES ('Explicit value');  
INSERT INTO dbo.T1 (column_2, column_4)   
    VALUES ('Explicit value', 'Explicit value');  
INSERT INTO dbo.T1 (column_2)   
    VALUES ('Explicit value');  
INSERT INTO T1 DEFAULT VALUES;   
GO  
SELECT column_1, column_2, column_3, column_4  
FROM dbo.T1;  
GO  
```  
  
#### <a name="e-inserting-data-into-a-table-with-an-identity-column"></a>E. ID 列を持つテーブルにデータを挿入する  
 次の例では、ID 列にデータを挿入する方法をいくつか示します。 最初の 2 つの INSERT ステートメントで、新規の行に対して ID 値が生成されます。 3 番目の INSERT ステートメントは、SET IDENTITY_INSERT ステートメントで設定された列の IDENTITY プロパティを上書きし、ID 列に値を明示的に挿入します。  
  
```  
CREATE TABLE dbo.T1 ( column_1 int IDENTITY, column_2 VARCHAR(30));  
GO  
INSERT T1 VALUES ('Row #1');  
INSERT T1 (column_2) VALUES ('Row #2');  
GO  
SET IDENTITY_INSERT T1 ON;  
GO  
INSERT INTO T1 (column_1,column_2)   
    VALUES (-99, 'Explicit identity value');  
GO  
SELECT column_1, column_2  
FROM T1;  
GO  
```  
  
#### <a name="f-inserting-data-into-a-uniqueidentifier-column-by-using-newid"></a>F. NEWID() を使用して uniqueidentifier 列にデータを挿入する  
 次の例では、 [NEWID](../../t-sql/functions/newid-transact-sql.md)の GUID を取得する関数`column_2`です。 異なり id 列に、[!INCLUDE[ssDE](../../includes/ssde-md.md)]列の値を自動的に生成しない、 [uniqueidentifier](../../t-sql/data-types/uniqueidentifier-transact-sql.md)データ型、2 番目に示すように`INSERT`ステートメントです。  
  
```  
CREATE TABLE dbo.T1   
(  
    column_1 int IDENTITY,   
    column_2 uniqueidentifier,  
);  
GO  
INSERT INTO dbo.T1 (column_2)   
    VALUES (NEWID());  
INSERT INTO T1 DEFAULT VALUES;   
GO  
SELECT column_1, column_2  
FROM dbo.T1;  
  
```  
  
#### <a name="g-inserting-data-into-user-defined-type-columns"></a>G. ユーザー定義型の列にデータを挿入する  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントに次の 3 つの行を挿入、`PointValue`の列、`Points`テーブル。 この列を使用して、 [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)(UDT)。 `Point` データ型は、UDT のプロパティとして公開されている整数値 X と Y で構成されます。 CAST または CONVERT のいずれかの関数をコンマ区切りのキャストを使用する必要があります X と Y 値を`Point`型です。 最初の 2 つのステートメントでは、CONVERT 関数を使用して、文字列値を変換、`Point`型、および 3 番目のステートメントは、CAST 関数を使用します。 詳細については、次を参照してください。 [UDT データを操作する](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-manipulating-udt-data.md)です。  
  
```  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '3,4'));  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '1,5'));  
INSERT INTO dbo.Points (PointValue) VALUES (CAST ('1,99' AS Point));  
```  
  
###  <a name="OtherTables"></a>他のテーブルからデータを挿入します。  
 このセクションの例では、あるテーブルの行を別のテーブルに挿入する方法を示します。  
  
#### <a name="h-using-the-select-and-execute-options-to-insert-data-from-other-tables"></a>H. SELECT および EXECUTE オプションを使用して他のテーブルのデータを挿入する  
 次の例では、INSERT…SELECT または INSERT…EXECUTE を使用して、あるテーブルのデータを別のテーブルに挿入する方法を示します。 各方法は、列リストに式とリテラル値を含む複数のテーブルを参照する SELECT ステートメントに基づきます。  
  
 最初の INSERT ステートメントでは、SELECT ステートメントを使用して、元のテーブルからデータを派生させます (`Employee`、 `SalesPerson`、および`Person`) で、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]で結果セットの格納データベースにあり、`EmployeeSales`テーブル。 2 番目の INSERT ステートメントは、EXECUTE 句を使用して SELECT ステートメントを含むストアド プロシージャを呼び出します。3 番目の INSERT ステートメントは、EXECUTE 句を使用して SELECT ステートメントをリテラル文字列として参照します。  
  
```  
CREATE TABLE dbo.EmployeeSales  
( DataSource   varchar(20) NOT NULL,  
  BusinessEntityID   varchar(11) NOT NULL,  
  LastName     varchar(40) NOT NULL,  
  SalesDollars money NOT NULL  
);  
GO  
CREATE PROCEDURE dbo.uspGetEmployeeSales   
AS   
    SET NOCOUNT ON;  
    SELECT 'PROCEDURE', sp.BusinessEntityID, c.LastName,   
        sp.SalesYTD   
    FROM Sales.SalesPerson AS sp    
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.BusinessEntityID LIKE '2%'  
    ORDER BY sp.BusinessEntityID, c.LastName;  
GO  
--INSERT...SELECT example  
INSERT INTO dbo.EmployeeSales  
    SELECT 'SELECT', sp.BusinessEntityID, c.LastName, sp.SalesYTD   
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.BusinessEntityID LIKE '2%'  
    ORDER BY sp.BusinessEntityID, c.LastName;  
GO  
--INSERT...EXECUTE procedure example  
INSERT INTO dbo.EmployeeSales   
EXECUTE dbo.uspGetEmployeeSales;  
GO  
--INSERT...EXECUTE('string') example  
INSERT INTO dbo.EmployeeSales   
EXECUTE   
('  
SELECT ''EXEC STRING'', sp.BusinessEntityID, c.LastName,   
    sp.SalesYTD   
    FROM Sales.SalesPerson AS sp   
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.BusinessEntityID LIKE ''2%''  
    ORDER BY sp.BusinessEntityID, c.LastName  
');  
GO  
--Show results.  
SELECT DataSource,BusinessEntityID,LastName,SalesDollars  
FROM dbo.EmployeeSales;  
```  
  
#### <a name="i-using-with-common-table-expression-to-define-the-data-inserted"></a>I. WITH 共通テーブル式を使用して挿入するデータを定義する  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースに `NewEmployee` テーブルを作成します。 共通テーブル式 (`EmployeeTemp`) で、`NewEmployee` テーブルに挿入する 1 つ以上のテーブルの行を定義します。 INSERT ステートメントは、共通テーブル式の列を参照します。  
  
```  
CREATE TABLE HumanResources.NewEmployee  
(  
    EmployeeID int NOT NULL,  
    LastName nvarchar(50) NOT NULL,  
    FirstName nvarchar(50) NOT NULL,  
    PhoneNumber Phone NULL,  
    AddressLine1 nvarchar(60) NOT NULL,  
    City nvarchar(30) NOT NULL,  
    State nchar(3) NOT NULL,   
    PostalCode nvarchar(15) NOT NULL,  
    CurrentFlag Flag  
);  
GO  
WITH EmployeeTemp (EmpID, LastName, FirstName, Phone,   
                   Address, City, StateProvince,   
                   PostalCode, CurrentFlag)  
AS (SELECT   
       e.BusinessEntityID, c.LastName, c.FirstName, pp.PhoneNumber,  
       a.AddressLine1, a.City, sp.StateProvinceCode,   
       a.PostalCode, e.CurrentFlag  
    FROM HumanResources.Employee e  
        INNER JOIN Person.BusinessEntityAddress AS bea  
        ON e.BusinessEntityID = bea.BusinessEntityID  
        INNER JOIN Person.Address AS a  
        ON bea.AddressID = a.AddressID  
        INNER JOIN Person.PersonPhone AS pp  
        ON e.BusinessEntityID = pp.BusinessEntityID  
        INNER JOIN Person.StateProvince AS sp  
        ON a.StateProvinceID = sp.StateProvinceID  
        INNER JOIN Person.Person as c  
        ON e.BusinessEntityID = c.BusinessEntityID  
    )  
INSERT INTO HumanResources.NewEmployee   
    SELECT EmpID, LastName, FirstName, Phone,   
           Address, City, StateProvince, PostalCode, CurrentFlag  
    FROM EmployeeTemp;  
GO  
```  
  
#### <a name="j-using-top-to-limit-the-data-inserted-from-the-source-table"></a>J. TOP を使用してソース テーブルから挿入されるデータを制限する  
 次の例では、`EmployeeSales` テーブルを作成し、ランダムに選ばれた上位 5 人の従業員の名前と年度累計売り上げデータを [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースの `HumanResources.Employee` テーブルから挿入します。 INSERT ステートメントによって返される、5 行を選択する、`SELECT`ステートメントです。 OUTPUT 句に挿入される行を表示する、`EmployeeSales`テーブル。 上位 5 人の従業員を特定するために SELECT ステートメントの ORDER BY 句を使用することはありません。  
  
```  
CREATE TABLE dbo.EmployeeSales  
( EmployeeID   nvarchar(11) NOT NULL,  
  LastName     nvarchar(20) NOT NULL,  
  FirstName    nvarchar(20) NOT NULL,  
  YearlySales  money NOT NULL  
 );  
GO  
INSERT TOP(5)INTO dbo.EmployeeSales  
    OUTPUT inserted.EmployeeID, inserted.FirstName, 
        inserted.LastName, inserted.YearlySales  
    SELECT sp.BusinessEntityID, c.LastName, c.FirstName, sp.SalesYTD   
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.SalesYTD > 250000.00  
    ORDER BY sp.SalesYTD DESC;  
```  
  
 TOP を使用して意味のある順序で行を挿入する必要がある場合は、次の例に示すように、サブセレクト ステートメントで ORDER BY を指定して TOP を使用する必要があります。 OUTPUT 句に挿入される行を表示する、`EmployeeSales`テーブル。 ランダムな行の代わりに、ORDER BY 句の結果に基づいて、上位 5 人の従業員が挿入されます。  
  
```  
INSERT INTO dbo.EmployeeSales  
    OUTPUT inserted.EmployeeID, inserted.FirstName, 
        inserted.LastName, inserted.YearlySales  
    SELECT TOP (5) sp.BusinessEntityID, c.LastName, c.FirstName, sp.SalesYTD   
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.SalesYTD > 250000.00  
    ORDER BY sp.SalesYTD DESC;  
```  
  
###  <a name="TargetObjects"></a>標準的なテーブル以外の対象オブジェクトを指定します。  
 このセクションの例では、ビューまたはテーブル変数を指定して行を挿入する方法を示します。  
  
#### <a name="k-inserting-data-by-specifying-a-view"></a>K. ビューを指定してデータを挿入する  
 次の例では、対象オブジェクトとしてビュー名を指定します。しかし、新しい行は基になるベース テーブルに挿入されます。 内の値の順序、`INSERT`ステートメントは、ビューの列の順序と一致する必要があります。 詳細については、次を参照してください。[変更データ ビューを経由した](../../relational-databases/views/modify-data-through-a-view.md)です。  
  
```  
CREATE TABLE T1 ( column_1 int, column_2 varchar(30));  
GO  
CREATE VIEW V1 AS   
SELECT column_2, column_1   
FROM T1;  
GO  
INSERT INTO V1   
    VALUES ('Row 1',1);  
GO  
SELECT column_1, column_2   
FROM T1;  
GO  
SELECT column_1, column_2  
FROM V1;  
GO  
```  
  
#### <a name="l-inserting-data-into-a-table-variable"></a>L. テーブル変数を指定してデータを挿入する  
 次の例では、テーブル変数を指定の対象オブジェクトとして、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
-- Create the table variable.  
DECLARE @MyTableVar table(  
    LocationID int NOT NULL,  
    CostRate smallmoney NOT NULL,  
    NewCostRate AS CostRate * 1.5,  
    ModifiedDate datetime);  
  
-- Insert values into the table variable.  
INSERT INTO @MyTableVar (LocationID, CostRate, ModifiedDate)  
    SELECT LocationID, CostRate, GETDATE() 
    FROM Production.Location  
    WHERE CostRate > 0;  
  
-- View the table variable result set.  
SELECT * FROM @MyTableVar;  
GO  
```  
  
###  <a name="RemoteTables"></a>リモート テーブルに行を挿入します。  
 このセクションの例を使用してリモートの対象テーブルに行を挿入する方法を示します、[リンク サーバー](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)または[行セット関数](../../t-sql/functions/rowset-functions-transact-sql.md)リモート テーブルを参照します。  
  
#### <a name="m-inserting-data-into-a-remote-table-by-using-a-linked-server"></a>M. リンク サーバーを使用してリモート テーブルにデータを挿入する  
 次の例では、リモート テーブルに行を挿入します。 使用してリモート データ ソースへのリンクを作成した後、 [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)です。 リンク サーバー名、 `MyLinkServer`、形式で 4 部構成のオブジェクト名の一部として指定しています*server.catalog.schema.object*です。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
USE master;  
GO  
-- Create a link to the remote data source.   
-- Specify a valid server name for @datasrc as 'server_name' 
-- or 'server_nameinstance_name'.  
  
EXEC sp_addlinkedserver @server = N'MyLinkServer',  
    @srvproduct = N' ',  
    @provider = N'SQLNCLI',   
    @datasrc = N'server_name',  
    @catalog = N'AdventureWorks2012';  
GO  
```  
  
```  
-- Specify the remote data source in the FROM clause using a four-part name   
-- in the form linked_server.catalog.schema.object.  
  
INSERT INTO MyLinkServer.AdventureWorks2012.HumanResources.Department (Name, GroupName)  
VALUES (N'Public Relations', N'Executive General and Administration');  
GO  
```  
  
#### <a name="n-inserting-data-into-a-remote-table-by-using-the-openquery-function"></a>N. OPENQUERY 関数を使用してリモート テーブルにデータを挿入する  
 次の例では、リモート テーブルに行を挿入を指定して、 [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md)行セット関数。 この例では、前の例で作成したリンク サーバー名を使用します。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
INSERT OPENQUERY (MyLinkServer, 
    'SELECT Name, GroupName 
     FROM AdventureWorks2012.HumanResources.Department')  
VALUES ('Environmental Impact', 'Engineering');  
GO  
```  
  
#### <a name="o-inserting-data-into-a-remote-table-by-using-the-opendatasource-function"></a>O.  OPENDATASOURCE 関数を使用してリモート テーブルにデータを挿入する  
 次の例では、リモート テーブルに行を挿入を指定して、 [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md)行セット関数。 形式を使用して、データ ソースの有効なサーバー名を指定*server_name*または*server_name \instance_name*です。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
-- Use the OPENDATASOURCE function to specify the remote data source.  
-- Specify a valid server name for Data Source using the format 
-- server_name or server_nameinstance_name.  
  
INSERT INTO OPENDATASOURCE('SQLNCLI',  
    'Data Source= <server_name>; Integrated Security=SSPI')  
    .AdventureWorks2012.HumanResources.Department (Name, GroupName)  
    VALUES (N'Standards and Methods', 'Quality Assurance');  
GO  
```  
  
#### <a name="p-inserting-into-an-external-table-created-using-polybase"></a>P. PolyBase を使用して作成された外部のテーブルに挿入します。  
 Hadoop または Azure ストレージに SQL Server からのデータをエクスポートします。 最初に、変換先ファイルまたはディレクトリを指す外部テーブルを作成します。 次に、ローカルの SQL Server テーブルからのデータを外部データ ソースをエクスポートするのに INSERT INTO 使用します。 INSERT INTO ステートメントでは、存在しないと、SELECT ステートメントの結果は、指定されたファイルの形式で指定した場所にエクスポートする場合、変換先ファイルまたはディレクトリを作成します。  詳細については、「 [PolyBase 入門](../../relational-databases/polybase/get-started-with-polybase.md)」を参照してください。  
  
**適用対象**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
-- Create an external table.   
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] (  
        [FirstName] char(25) NOT NULL,   
        [LastName] char(25) NOT NULL,   
        [YearlyIncome] float NULL,   
        [MaritalStatus] char(1) NOT NULL  
)  
WITH (  
        LOCATION='/old_data/2009/customerdata.tbl',  
        DATA_SOURCE = HadoopHDP2,  
        FILE_FORMAT = TextFileFormat,  
        REJECT_TYPE = VALUE,  
        REJECT_VALUE = 0  
);  
  
-- Export data: Move old data to Hadoop while keeping 
-- it query-able via external table.  

INSERT INTO dbo.FastCustomer2009  
SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
ON (T1.CustomerKey = T2.CustomerKey)  
WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
```  
  
###  <a name="BulkLoad"></a>データ テーブルまたはデータ ファイルを一括読み込み  
 このセクションの例では、INSERT ステートメントを使用してテーブルにデータを一括読み込みする 2 つの方法を示します。  
  
#### <a name="q-inserting-data-into-a-heap-with-minimal-logging"></a>Q.  最小ログ記録を行ってヒープにデータを挿入する  
 次の例では、新しいテーブル (ヒープ) を作成し、最小ログ記録を使用して、別のテーブルのデータをそのテーブルに挿入します。 例では、復旧モデル、`AdventureWorks2012`データベースが FULL に設定します。 したがって、最小ログ記録が使用されるようにするために、行を挿入する前に `AdventureWorks2012` データベースの復旧モデルを BULK_LOGGED に設定し、INSERT INTO...SELECT ステートメントの後に FULL に戻しています。 さらに、ターゲット テーブルには、TABLOCK ヒントが指定`Sales.SalesHistory`です。 これにより、ステートメントが使用するトランザクション ログの領域が最小化され、ステートメントが効率的に実行されるようになります。  
  
```  
-- Create the target heap.  
CREATE TABLE Sales.SalesHistory(  
    SalesOrderID int NOT NULL,  
    SalesOrderDetailID int NOT NULL,  
    CarrierTrackingNumber nvarchar(25) NULL,  
    OrderQty smallint NOT NULL,  
    ProductID int NOT NULL,  
    SpecialOfferID int NOT NULL,  
    UnitPrice money NOT NULL,  
    UnitPriceDiscount money NOT NULL,  
    LineTotal money NOT NULL,  
    rowguid uniqueidentifier ROWGUIDCOL  NOT NULL,  
    ModifiedDate datetime NOT NULL );  
GO  
-- Temporarily set the recovery model to BULK_LOGGED.  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY BULK_LOGGED;  
GO  
-- Transfer data from Sales.SalesOrderDetail to Sales.SalesHistory  
INSERT INTO Sales.SalesHistory WITH (TABLOCK)  
    (SalesOrderID,   
     SalesOrderDetailID,  
     CarrierTrackingNumber,   
     OrderQty,   
     ProductID,   
     SpecialOfferID,   
     UnitPrice,   
     UnitPriceDiscount,  
     LineTotal,   
     rowguid,   
     ModifiedDate)  
SELECT * FROM Sales.SalesOrderDetail;  
GO  
-- Reset the recovery model.  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY FULL;  
GO  
```  
  
#### <a name="r-using-the-openrowset-function-with-bulk-to-bulk-load-data-into-a-table"></a>R.  OPENROWSET 関数を BULK を指定して使用し、テーブルにデータを一括読み込みする  
 次の例は、OPENROWSET 関数を指定することによって、テーブルにデータ ファイルからの行を挿入します。 パフォーマンスを最適化するために、IGNORE_TRIGGERS テーブル ヒントを指定しています。 例については、次を参照してください[を使用して BULK INSERT または OPENROWSET &#40; した一括データのインポート。BULK..."&"#41;& #40 です。SQL Server &#41;](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
INSERT INTO HumanResources.Department WITH (IGNORE_TRIGGERS) (Name, GroupName)  
SELECT b.Name, b.GroupName   
FROM OPENROWSET (  
    BULK 'C:SQLFilesDepartmentData.txt',  
    FORMATFILE = 'C:SQLFilesBulkloadFormatFile.xml',  
    ROWS_PER_BATCH = 15000)AS b ;  
```  
  
###  <a name="TableHints"></a>ヒントを使用して、クエリ オプティマイザーの既定の動作を上書きする.  
 このセクションの例を使用する方法をデモンストレーション[テーブル ヒント](../../t-sql/queries/hints-transact-sql-table.md)INSERT ステートメントを処理するときに、クエリ オプティマイザーの既定の動作を一時的に無効にします。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]通常、クエリ オプティマイザーがクエリの最適な実行プランを選択、ヒントは、経験を積んだ開発者やデータベース管理者が、最後の手段としてのみ使用することをお勧めします。  
  
#### <a name="s-using-the-tablock-hint-to-specify-a-locking-method"></a>S.  TABLOCK ヒントを使用してロック手法を指定する  
 次の例では、Production.Location テーブルに対して排他 (X) ロックを使用することと、このロックを INSERT ステートメントの終了まで保持することを指定します。  
  
**適用されます**: [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]です。  
  
```  
INSERT INTO Production.Location WITH (XLOCK)  
(Name, CostRate, Availability)  
VALUES ( N'Final Inventory', 15.00, 80.00);  
```  
  
###  <a name="CaptureResults"></a>INSERT ステートメントの結果をキャプチャ  
 このセクションの例を使用する方法をデモンストレーション、 [OUTPUT 句](../../t-sql/queries/output-clause-transact-sql.md)情報や、それらに基づく式を返す、影響を受ける各行の INSERT ステートメントでします。 これらの結果は処理アプリケーションに返され、確認メッセージの表示、アーカイブ化、その他のアプリケーション要件で使用することができます。  
  
#### <a name="t-using-output-with-an-insert-statement"></a>T.  INSERT ステートメントで OUTPUT を使用します。  
 次の例では、`ScrapReason` テーブルに 1 行を挿入し、`OUTPUT` 句を使用してステートメントの結果を `@MyTableVar` テーブル変数に返します。 `ScrapReasonID` 列が `IDENTITY` プロパティで定義されているため、`INSERT` ステートメントではこの列の値を指定していません。 ただし、によって生成された値、[!INCLUDE[ssDE](../../includes/ssde-md.md)]でその列が返される、`OUTPUT`句、`INSERTED.ScrapReasonID`列です。  
  
```  
DECLARE @MyTableVar table( NewScrapReasonID smallint,  
                           Name varchar(50),  
                           ModifiedDate datetime);  
INSERT Production.ScrapReason  
    OUTPUT INSERTED.ScrapReasonID, INSERTED.Name, INSERTED.ModifiedDate  
        INTO @MyTableVar  
VALUES (N'Operator error', GETDATE());  
  
--Display the result set of the table variable.  
SELECT NewScrapReasonID, Name, ModifiedDate FROM @MyTableVar;  
--Display the result set of the table.  
SELECT ScrapReasonID, Name, ModifiedDate   
FROM Production.ScrapReason;  
```  
  
#### <a name="u-using-output-with-identity-and-computed-columns"></a>U.  ID 列と計算列で OUTPUT を使用する  
 次の例を作成、`EmployeeSales`テーブルおよびソース テーブルからデータを取得する SELECT ステートメントで、INSERT ステートメントを使用していくつかの行を挿入します。 `EmployeeSales`テーブルに id 列が含まれています (`EmployeeID`) し、計算列 (`ProjectedSales`)。 これらの値は[!INCLUDE[ssDE](../../includes/ssde-md.md)]によって挿入操作中に生成されるため、いずれの列も `@MyTableVar` で定義できません。  
  
```  
CREATE TABLE dbo.EmployeeSales  
( EmployeeID   int IDENTITY (1,5)NOT NULL,  
  LastName     nvarchar(20) NOT NULL,  
  FirstName    nvarchar(20) NOT NULL,  
  CurrentSales money NOT NULL,  
  ProjectedSales AS CurrentSales * 1.10   
);  
GO  
DECLARE @MyTableVar table(  
  LastName     nvarchar(20) NOT NULL,  
  FirstName    nvarchar(20) NOT NULL,  
  CurrentSales money NOT NULL  
  );  
  
INSERT INTO dbo.EmployeeSales (LastName, FirstName, CurrentSales)  
  OUTPUT INSERTED.LastName,   
         INSERTED.FirstName,   
         INSERTED.CurrentSales  
  INTO @MyTableVar  
    SELECT c.LastName, c.FirstName, sp.SalesYTD  
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.BusinessEntityID LIKE '2%'  
    ORDER BY c.LastName, c.FirstName;  
  
SELECT LastName, FirstName, CurrentSales  
FROM @MyTableVar;  
GO  
SELECT EmployeeID, LastName, FirstName, CurrentSales, ProjectedSales  
FROM dbo.EmployeeSales;  
```  
  
#### <a name="v-inserting-data-returned-from-an-output-clause"></a>V.  OUTPUT 句から返されたデータを挿入する  
 次の例では、MERGE ステートメントの OUTPUT 句から返されたデータをキャプチャし、別のテーブルにそのデータを挿入します。 MERGE ステートメントの更新プログラム、`Quantity`の列、`ProductInventory`テーブル内で処理される注文に基づいてでは、毎日、`SalesOrderDetail`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。 また、在庫が 0 になった製品の行を削除します。 例が削除され、別のテーブルに挿入される行はキャプチャ`ZeroInventory`、製品在庫がないを追跡します。  
  
```  
--Create ZeroInventory table.  
CREATE TABLE Production.ZeroInventory (DeletedProductID int, RemovedOnDate DateTime);  
GO  
  
INSERT INTO Production.ZeroInventory (DeletedProductID, RemovedOnDate)  
SELECT ProductID, GETDATE()  
FROM  
(   MERGE Production.ProductInventory AS pi  
    USING (SELECT ProductID, SUM(OrderQty) FROM Sales.SalesOrderDetail AS sod  
           JOIN Sales.SalesOrderHeader AS soh  
           ON sod.SalesOrderID = soh.SalesOrderID  
           AND soh.OrderDate = '20070401'  
           GROUP BY ProductID) AS src (ProductID, OrderQty)  
    ON (pi.ProductID = src.ProductID)  
    WHEN MATCHED AND pi.Quantity - src.OrderQty <= 0  
        THEN DELETE  
    WHEN MATCHED  
        THEN UPDATE SET pi.Quantity = pi.Quantity - src.OrderQty  
    OUTPUT $action, deleted.ProductID) AS Changes (Action, ProductID)  
WHERE Action = 'DELETE';  
IF @@ROWCOUNT = 0  
PRINT 'Warning: No rows were inserted';  
GO  
SELECT DeletedProductID, RemovedOnDate FROM Production.ZeroInventory;  
```  

#### <a name="w-inserting-data-using-the-select-option"></a>W. [選択] オプションを使用してデータを挿入します。  
 次の例では、複数行の選択 オプションを使用して、INSERT ステートメントを使用してデータを挿入する方法を示します。 最初の`INSERT`ステートメントは、 `SELECT` 、ソース テーブルからデータを取得するには、直接のステートメントし、結果を格納する設定、`EmployeeTitles`テーブル。  
  
```  
CREATE TABLE EmployeeTitles  
( EmployeeKey   INT NOT NULL,  
  LastName     varchar(40) NOT NULL,  
  Title      varchar(50) NOT NULL  
);  
INSERT INTO EmployeeTitles  
    SELECT EmployeeKey, LastName, Title   
    FROM ssawPDW.dbo.DimEmployee  
    WHERE EndDate IS NULL;  
```  
  
#### <a name="x-specifying-a-label-with-the-insert-statement"></a>X です。 INSERT ステートメントとラベルを指定します。  
 次の例では、INSERT ステートメントとラベルの使用を示します。  
  
```  
-- Uses AdventureWorks  
  
INSERT INTO DimCurrency   
VALUES (500, N'C1', N'Currency1')  
OPTION ( LABEL = N'label1' );  
```  
  
#### <a name="y-using-a-label-and-a-query-hint-with-the-insert-statement"></a>Y です。 INSERT ステートメントでラベルとクエリ ヒントの使用  
 このクエリは、INSERT ステートメントを使用して、ラベルとクエリの結合ヒントを使用するための基本構文を示しています。 クエリは、コントロール ノードに送信された後[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、コンピューティング ノードで実行されている、生成するときに、ハッシュ結合の方法を適用、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クエリ プラン。 結合ヒントや、OPTION 句を使用する方法の詳細については、次を参照してください。[オプション (SQL Server PDW)](http://msdn.microsoft.com/en-us/72bbce98-305b-42fa-a19f-d89620621ecc)です。  
  
```  
-- Uses AdventureWorks  
  
INSERT INTO DimCustomer (CustomerKey, CustomerAlternateKey, 
    FirstName, MiddleName, LastName )   
SELECT ProspectiveBuyerKey, ProspectAlternateKey, 
    FirstName, MiddleName, LastName  
FROM ProspectiveBuyer p JOIN DimGeography g ON p.PostalCode = g.PostalCode  
WHERE g.CountryRegionCode = 'FR'  
OPTION ( LABEL = 'Add French Prospects', HASH JOIN);  
```  
  
## <a name="see-also"></a>参照  
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql-identity-property.md)   
 [NEWID & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/newid-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [マージ & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/merge-transact-sql.md)   
 [OUTPUT 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/output-clause-transact-sql.md)   
 [inserted テーブルと deleted テーブルの使用](../../relational-databases/triggers/use-the-inserted-and-deleted-tables.md)  
  
  




