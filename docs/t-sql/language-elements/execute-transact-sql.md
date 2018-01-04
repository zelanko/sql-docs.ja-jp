---
title: "実行 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EXEC
- EXECUTE_TSQL
- EXECUTE
- EXEC_TSQL
dev_langs: TSQL
helpviewer_keywords:
- remote stored procedures [SQL Server]
- command strings [SQL Server]
- extended stored procedures [SQL Server], executing
- stored procedures [SQL Server], executing
- Transact-SQL statements, executing
- strings [SQL Server], executing
- statements [SQL Server], executing
- context switching [SQL Server], execution context
- user-defined functions [SQL Server], executing
- character strings [SQL Server], executing
- switching execution context
- EXECUTE statement
ms.assetid: bc806b71-cc55-470a-913e-c5f761d5c4b7
caps.latest.revision: "104"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 52a896293ad991509884b45979be0129bd56f287
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="execute-transact-sql"></a>EXECUTE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

コマンド文字列または文字の文字列内で実行する[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ、または、次のモジュールのいずれかの: システム ストアド プロシージャ、ユーザー定義のストアド プロシージャ、CLR ストアド プロシージャ、スカラー値ユーザー定義関数、または拡張ストアド プロシージャです。 EXECUTE ステートメントを使用して、パススルー コマンドをリンク サーバーに送信できます。 さらに、文字列またはコマンドを実行するコンテキストを、明示的に設定できるようになりました。 WITH RESULT SETS オプションを使用すると、結果セットのメタデータを定義できます。
  
> [!IMPORTANT]  
>  文字列で EXECUTE を呼び出す前には、文字列を検証してください。 また、検証されていないユーザー入力から作成されるコマンドは実行しないでください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
  
Execute a stored procedure or function  
[ { EXEC | EXECUTE } ]  
    {   
      [ @return_status = ]  
      { module_name [ ;number ] | @module_name_var }   
        [ [ @parameter = ] { value   
                           | @variable [ OUTPUT ]   
                           | [ DEFAULT ]   
                           }  
        ]  
      [ ,...n ]  
      [ WITH <execute_option> [ ,...n ] ]  
    }  
[;]  
  
Execute a character string  
{ EXEC | EXECUTE }   
    ( { @string_variable | [ N ]'tsql_string' } [ + ...n ] )  
    [ AS { LOGIN | USER } = ' name ' ]  
[;]  
  
Execute a pass-through command against a linked server  
{ EXEC | EXECUTE }  
    ( { @string_variable | [ N ] 'command_string [ ? ]' } [ + ...n ]  
        [ { , { value | @variable [ OUTPUT ] } } [ ...n ] ]  
    )   
    [ AS { LOGIN | USER } = ' name ' ]  
    [ AT linked_server_name ]  
[;]  
  
<execute_option>::=  
{  
        RECOMPILE   
    | { RESULT SETS UNDEFINED }   
    | { RESULT SETS NONE }   
    | { RESULT SETS ( <result_sets_definition> [,...n ] ) }  
}   
  
<result_sets_definition> ::=   
{  
    (  
         { column_name   
           data_type   
         [ COLLATE collation_name ]   
         [ NULL | NOT NULL ] }  
         [,...n ]  
    )  
    | AS OBJECT   
        [ db_name . [ schema_name ] . | schema_name . ]   
        {table_name | view_name | table_valued_function_name }  
    | AS TYPE [ schema_name.]table_type_name  
    | AS FOR XML   
}  
```  
  
```  
-- In-Memory OLTP   

Execute a natively compiled, scalar user-defined function  
[ { EXEC | EXECUTE } ]   
    {   
      [ @return_status = ]   
      { module_name | @module_name_var }   
        [ [ @parameter = ] { value   
                           | @variable   
                           | [ DEFAULT ]   
                           }  
        ]   
      [ ,...n ]   
      [ WITH <execute_option> [ ,...n ] ]   
    }  
<execute_option>::=  
{  
    | { RESULT SETS UNDEFINED }   
    | { RESULT SETS NONE }   
    | { RESULT SETS ( <result_sets_definition> [,...n ] ) }  
}  
```  
  
```  
-- Syntax for Azure SQL Database   
  
Execute a stored procedure or function  
[ { EXEC | EXECUTE } ]  
    {   
      [ @return_status = ]  
      { module_name  | @module_name_var }   
        [ [ @parameter = ] { value   
                           | @variable [ OUTPUT ]   
                           | [ DEFAULT ]   
                           }  
        ]  
      [ ,...n ]  
      [ WITH RECOMPILE ]  
    }  
[;]  
  
Execute a character string  
{ EXEC | EXECUTE }   
    ( { @string_variable | [ N ]'tsql_string' } [ + ...n ] )  
    [ AS {  USER } = ' name ' ]  
[;]  
  
<execute_option>::=  
{  
        RECOMPILE   
    | { RESULT SETS UNDEFINED }   
    | { RESULT SETS NONE }   
    | { RESULT SETS ( <result_sets_definition> [,...n ] ) }  
}   
  
<result_sets_definition> ::=   
{  
    (  
         { column_name   
           data_type   
         [ COLLATE collation_name ]   
         [ NULL | NOT NULL ] }  
         [,...n ]  
    )  
    | AS OBJECT   
        [ db_name . [ schema_name ] . | schema_name . ]   
        {table_name | view_name | table_valued_function_name }  
    | AS TYPE [ schema_name.]table_type_name  
    | AS FOR XML  
  
```  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

-- Execute a stored procedure  
[ { EXEC | EXECUTE } ]  
    procedure_name   
        [ { value | @variable [ OUT | OUTPUT ] } ] [ ,...n ] }  
[;]  
  
-- Execute a SQL string  
{ EXEC | EXECUTE }  
    ( { @string_variable | [ N ] 'tsql_string' } [ +...n ] )  
[;]  
```  
  
## <a name="arguments"></a>引数  
 @*return_status*  
 モジュールから返されるステータス番号を格納する整数型の変数を指定します (省略可能)。 この変数は、EXECUTE ステートメントで使う前に、バッチ、ストアド プロシージャ、または関数の中で宣言する必要があります。  
  
 スカラー値ユーザー定義関数を呼び出すために使用する場合、@*return_status*任意のスカラー データ型の変数にすることができます。  
  
 *モジュール名*  
 呼び出されるストアド プロシージャやユーザー定義のスカラー値関数の、完全修飾名または部分的な修飾名を指定します。 モジュール名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 拡張ストアド プロシージャの名前では、サーバーの照合順序に関係なく、常に大文字と小文字が区別されます。  
  
 別のデータベース内で作成されたモジュールを実行するには、実行するユーザーがモジュールを所有しているか、そのデータベース内のモジュールを実行する適切な権限がユーザーに与えられている必要があります。 モジュールを実行している別のサーバーで実行できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]モジュールを実行しているユーザーがそのサーバー (リモート アクセス) を使用して、そのデータベースにモジュールを実行するには、適切なアクセス許可を持っている場合。 サーバー名だけを指定してデータベース名を指定しない場合、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]では、ユーザーの既定のデータベース内でモジュールが検索されます。  
  
 ;*数*  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 同じ名前のプロシージャのグループ化に使用される整数です (省略可能)。 このパラメーターは、拡張ストアド プロシージャでは使用できません。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 プロシージャ グループの詳細については、次を参照してください。 [CREATE PROCEDURE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-procedure-transact-sql.md).  
  
 @*module_name_var*  
 モジュール名を表すローカル変数の名前を指定します。  
  
 ネイティブ コンパイル、スカラー ユーザー定義関数の名前を保持する変数を指定できます。  
  
 @*パラメーター*  
 パラメーターは、*モジュール名*モジュールで定義されています。 パラメーター名の先頭にはアット マーク (@) を付ける必要があります。 使用する場合、@*parameter_name*=*値*フォーム、パラメーター名と定数は、モジュールで定義されている順序で指定されることはありません。 ただし場合、@*parameter_name*=*値*任意のパラメーターの形式が使用される、すべての後続のパラメーターのために使用する必要があります。  
  
 既定では、パラメーターに NULL 値は許容されます。  
  
 *value*  
 モジュールまたはパススルー コマンドに渡すパラメーターの値を指定します。 パラメーター名を指定しない場合、パラメーター値は、モジュールで定義された順序で指定する必要があります。  
  
 リンク サーバーに対してパススルー コマンドを実行するとき、パラメーター値の順序は、リンク サーバーの OLE DB プロバイダーに依存します。 ほとんどの OLE DB プロバイダーでは、左から右へパラメーターに値がバインドされます。  
  
 パラメーターの値がオブジェクト名や文字列であったり、データベース名やスキーマ名によって修飾されている場合は、その名前全体を単一引用符で囲む必要があります。 パラメーターの値がキーワードの場合は、そのキーワードを二重引用符で囲む必要があります。  
  
 既定値がモジュール内で定義されている場合、ユーザーはパラメーターを指定せずにモジュールを実行できます。  
  
 既定値を NULL にすることもできます。 パラメーター値が NULL の場合の操作は、通常、モジュールの定義で指定します。  
  
 @*変数*  
 パラメーターと戻りパラメーターを格納する変数です。  
  
 OUTPUT  
 モジュールまたはコマンド文字列でパラメーターを返すよう指定します。 モジュールまたはコマンド文字列内で一致するパラメーターも、キーワード OUTPUT を使って作成されている必要があります。 このキーワードは、カーソル変数をパラメーターとして使用するときに指定します。  
  
 場合*値*@ 対応への変更、リンク サーバーに対して実行するモジュールの OUTPUT として定義された*パラメーター*実行の最後に、変数に、プロバイダーをコピー、OLE DB で、モジュールの実行。  
  
 出力パラメーターが使用されている、その目的は、呼び出し元のバッチまたはモジュール内の他のステートメントで戻り値を使用する場合は、パラメーターの値渡す必要がありますを変数としてなど*パラメーター* = @*変数*. モジュール内で OUTPUT パラメーターとして定義されていないパラメーターには、OUTPUT を指定してモジュールを実行することはできません。 OUTPUT を使って定数をモジュールに引き渡すことはできません。戻りパラメーターには変数名が必要です。 プロシージャを実行する前に、必ず変数のデータ型を宣言し、値を割り当ててください。  
  
 リモート ストアド プロシージャに対して EXECUTE を使用する場合や、リンク サーバーに対してパススルー コマンドを実行する場合は、OUTPUT パラメーターにラージ オブジェクト (LOB) 型を指定することはできません。  
  
 戻りパラメーターには、LOB 型以外のデータ型を指定できます。  
  
 DEFAULT  
 モジュールで定義されているパラメーターの既定値を使用します。 パラメーターに値を必要とするモジュールでパラメーターの既定値が定義されていない場合、パラメーターを指定しなかったり、DEFAULT キーワードを指定したりすると、エラーが発生します。  
  
 @*string_variable*  
 ローカル変数の名前を指定します。 @*string_variable*いずれかを指定できます**char**、 **varchar**、 **nchar**、または**nvarchar**データ型。 ように、 **(max)**データ型。  
  
 [N] '*tsql_string*'  
 定数文字列を指定します。 *tsql_string*いずれかを指定できます**nvarchar**または**varchar**データ型。 として文字列は、N が含まれる場合は、 **nvarchar**データ型。  
  
 AS \<context_specification >  
 ステートメントを実行するコンテキストを指定します。  
  
 Login  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 権限を借用するコンテキストがログインであることを指定します。 権限借用のスコープはサーバーです。  
  
 User  
 権限を借用するコンテキストが、現在のデータベース内のユーザーであることを指定します。 権限借用のスコープは、現在のデータベースに限定されます。 コンテキスト スイッチの対象がデータベース ユーザーであっても、そのユーザーのサーバー レベルの権限は継承されません。  
  
> [!IMPORTANT]  
>  データベース ユーザーのコンテキストの切り替えがアクティブな間、データベース外部のリソースにアクセスしようとするとは、ステートメントが失敗になります。 Use*データベース*ステートメント、分散クエリ、および 3 部または 4 部構成の識別子を使用して別のデータベースを参照するクエリ。  
  
 '*名前*'  
 有効なユーザーまたはログイン名を指定します。 *名前*sysadmin 固定サーバー ロールのメンバーであるかにプリンシパルとして存在している必要があります[sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)または[sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)、それぞれします。  
  
 *名前*NT authority \localservice、NT authority \networkservice、NT authority \localsystem などのビルトイン アカウントにすることはできません。  
  
 詳細については、次を参照してください。[ユーザーまたはログイン名を指定する](#_user)このトピックで後述します。  
  
 [N] '*command_string*'  
 リンク サーバーにパススルーされるコマンドを含む定数文字列を指定します。 として文字列は、N が含まれる場合は、 **nvarchar**データ型。  
  
 [?]  
 対象の値が指定されているパラメーターを示す、 \<arg リスト > EXEC('...', \<arg-list>) にで使用されているパススルー コマンドの\<linkedsrv > ステートメントです。  
  
 *Linked_server_name*  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 指定する*command_string*に対してが実行される*linked_server_name*と、結果は存在する場合、クライアントに返されます。 *linked_server_name*ローカル サーバー内の既存のリンク サーバー定義を参照する必要があります。 使用してリンク サーバーが定義されている[sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)です。  
  
 \<Execute_option >  
 実行オプションは次のとおりです。 RESULT SETS オプションは INSERT…EXEC ステートメントで指定できません。  
  
|項目|定義|  
|----------|----------------|  
|RECOMPILE|モジュール実行後に、新しいプランを強制的にコンパイル、使用、および破棄します。 モジュールに既存のクエリ プランがある場合、このプランはキャッシュに残ります。<br /><br /> 指定するパラメーターが一定しない場合であったり、データが大きく変更されたときにこのオプションを使用してください。 このオプションは、拡張ストアド プロシージャには使用しません。 このオプションは負荷を伴うので、あまり使用しないことをお勧めします。<br /><br /> **注:**は使用できません WITH RECOMPILE OPENDATASOURCE 構文を使用するストアド プロシージャを呼び出すときにします。 4 部構成のオブジェクト名が指定されている場合、WITH RECOMPILE オプションは無視されます。<br /><br /> **注:** RECOMPILE は、ネイティブ コンパイル、スカラー ユーザー定義関数ではサポートされません。 再コンパイルする必要がある場合を使用して[sp_recompile &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-recompile-transact-sql.md).|  
|**結果セットが定義されていません**|**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。<br /><br /> このオプションを使用した場合、返される結果の種類は保証されず、定義は指定されません。 ステートメントは、何かの結果が返される場合でも、結果が返されない場合でも、問題なく実行されます。 result_sets_option を指定しない場合は、RESULT SETS UNDEFINED が既定の動作となります。<br /><br /> スカラー ユーザー定義の関数では、およびネイティブ コンパイルのスカラー ユーザー定義関数を解釈された、このオプションが機能していないため、関数は、結果セットを返すことはありません。|  
|RESULT SETS NONE|**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。<br /><br /> 実行ステートメントによって結果が一切返されなくなります。 結果が返された場合、バッチは中断されます。<br /><br /> スカラー ユーザー定義の関数では、およびネイティブ コンパイルのスカラー ユーザー定義関数を解釈された、このオプションが機能していないため、関数は、結果セットを返すことはありません。|  
|*\<result_sets_definition >*|**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。<br /><br /> result_sets_definition で指定されたとおりに結果が返されるようになります。 複数の結果セットを返すステートメントが複数指定して*result_sets_definition*セクションです。 各*result_sets_definition*でかっこ、コンマで区切られます。 詳細については、次を参照してください。 \<result_sets_definition > このトピックで後述します。<br /><br /> このオプションは常には、ネイティブ コンパイル済みのスカラー ユーザー定義関数のエラーが発生するため、関数は、結果セットを返すことはありません。|
  
\<result_sets_definition >**対象**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]
  
 実行されたステートメントによって返される結果セットの定義です。 result_sets_definition の句には、次の意味があります。  
  
|項目|定義|  
|----------|----------------|  
|{<br /><br /> column_name<br /><br /> data_type<br /><br /> [ COLLATE collation_name]<br /><br /> [NULL &#124;です。NULL 以外]<br /><br /> }|次の表を参照してください。|  
|db_name|テーブル、ビュー、またはテーブル値関数を含むデータベースの名前です。|  
|schema_name|テーブル、ビュー、またはテーブル値関数を所有するスキーマの名前です。|  
|table_name &#124;です。view_name &#124;です。table_valued_function_name|名前付きのテーブル、ビュー、またはテーブル値関数で指定された列を返すように指定します。 テーブル変数、一時テーブル、およびシノニムは、AS オブジェクト構文ではサポートされていません。|  
|AS TYPE [schema_name.]table_type_name|テーブル型で指定された列を返すように指定します。|  
|AS FOR XML|これらは、SELECT によって生成されたものとしてにステートメントまたは EXECUTE ステートメントで呼び出されるストアド プロシージャから結果の XML 形式に変換することを指定しています. XML をしています. ステートメントの使用などがあります。 元のステートメントの TYPE ディレクティブからのすべての書式設定が削除され、TYPE ディレクティブが指定されなかったものとして、結果が返されます。 AS FOR XML では、実行されたステートメントまたはストアド プロシージャからの XML 以外の表形式の結果は XML に変換されません。|  
  
|項目|定義|  
|----------|----------------|  
|column_name|各列の名前です。 列の数が結果セットと異なる場合は、エラーが発生し、バッチが中断されます。 列の名前が結果セットと異なる場合は、返される列の名前は定義済みの名前に設定されます。|  
|data_type|各列のデータ型です。 データ型が異なる場合は、定義済みのデータ型への暗黙的な変換が行われます。 変換に失敗すると、バッチが中断されます。|  
|COLLATE collation_name|各列の照合順序です。 照合順序の不一致がある場合、暗黙的な照合順序が使用されます。 これに失敗した場合は、バッチが中断されます。|  
|NULL &#124;です。NOT NULL します。|各列の NULL 値の許容属性です。 定義済みの NULL 値の許容属性が NOT NULL である場合に、返されるデータに NULL が含まれていると、エラーが発生し、バッチは中断されます。 指定しない場合、既定値は ANSI_NULL_DFLT_ON および ANSI_NULL_DFLT_OFF オプションの設定に従った値になります。|  
  
 実行中に返される実際の結果セットは、結果セットの数、列の数、列の名前、NULL 値の許容属性、およびデータ型のいずれかが WITH RESULT SETS 句を使用して定義された結果とは異なる場合があります。 結果セットの数が異なる場合は、エラーが発生し、バッチが中断されます。  
  
## <a name="remarks"></a>解説  
 使用するか、パラメーターを指定することができます*値*またはを使用して*parameter_name*=*値。* パラメーターは、トランザクションの一部ではないです。そのため、トランザクションが後でロールバックの値にパラメーターが変更された場合、パラメーター戻すことはできません前の値にします。 呼び出し元に返される値は常に、モジュールから戻る時点での値になります。  
  
 1 つのモジュールで、別のモジュールが呼び出されるか、共通言語ランタイム (CLR) モジュール、ユーザー定義型、または集計の参照によりマネージ コードが実行されるとき、入れ子が発生します。 入れ子のレベルは、呼び出されたモジュールまたはマネージ コード参照の実行開始時に増加し、呼び出されたモジュールやマネージ コード参照の終了時に減少します。 入れ子のレベルが最大値 32 を超えると、呼び出しチェーン全体が失敗します。 現在の入れ子レベルは、@@NESTLEVELシステム関数です。  
  
 リモート プロシージャと拡張ストアド プロシージャは、BEGIN DISTRIBUTED TRANSACTION ステートメントの中で実行されない限り、または各種の構成オプションと共に使用されない限り、トランザクションのスコープ外となります。したがって、これらのプロシージャを呼び出して実行したコマンドはロールバックできません。 詳細については、次を参照してください。[システム ストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)と[分散トランザクション &#40; を開始TRANSACT-SQL と #41 です。](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md).  
  
 カーソル変数を使用するとき、カーソル変数にカーソルを渡すプロシージャを実行し、このカーソルがプロシージャに割り当てられているカーソルであった場合は、エラーが発生します。  
  
 ステートメントがバッチ内の最初のステートメントの場合は、モジュールを実行するときに EXECUTE キーワードを指定する必要はありません。  
  
 CLR ストアド プロシージャに固有のその他の情報については、「CLR ストアド プロシージャ」を参照してください。  
  
## <a name="using-execute-with-stored-procedures"></a>ストアド プロシージャでの EXECUTE の使用  
 ステートメントがバッチ内の最初のステートメントの場合は、ストアド プロシージャを実行するときに EXECUTE キーワードを指定する必要はありません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム ストアド プロシージャは、sp_ で始まります。 物理的に格納されている、 [Resource データベース](../../relational-databases/databases/resource-database.md)がすべてのシステムとユーザー定義のデータベースの sys スキーマに論理的に表示します。 システム ストアド プロシージャを、バッチ内、またはユーザー定義ストアド プロシージャや関数などのモジュール内で実行する場合は、ストアド プロシージャ名に sys スキーマ名を追加することをお勧めします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム拡張ストアド プロシージャは、文字 xp_ で始まり、master データベースの dbo スキーマに含まれています。 システム拡張ストアド プロシージャを、バッチ内、またはユーザー定義ストアド プロシージャや関数などのモジュール内で実行する場合は、ストアド プロシージャ名に master.dbo を追加することをお勧めします。  
  
 ユーザー定義ストアド プロシージャを、バッチ内、またはユーザー定義ストアド プロシージャや関数などのモジュール内で実行する場合は、ストアド プロシージャ名にスキーマ名を追加することをお勧めします。 ユーザー定義ストアド プロシージャに、システム ストアド プロシージャと同じ名前を付けることはお勧めしません。 ストアド プロシージャの実行の詳細については、次を参照してください。[ストアド プロシージャを実行する](../../relational-databases/stored-procedures/execute-a-stored-procedure.md)です。  
  
## <a name="using-execute-with-a-character-string"></a>文字列での EXECUTE の使用  
 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、文字列は 8,000 バイトに制限されています。 このため、動的実行では大きな文字列を連結する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 **Varchar (max)**と**nvarchar (max)**最大 2 ギガバイトのデータを指定する文字列を可能にするデータ型を指定することができます。  
  
 データベース コンテキスト内の変更が維持されるのは、EXECUTE ステートメントの終了時までです。 たとえば、次のステートメントの `EXEC` を実行すると、データベース コンテキストは master になります。  
  
```sql  
USE master; EXEC ('USE AdventureWorks2012; SELECT BusinessEntityID, JobTitle FROM HumanResources.Employee;');  
```  
  
## <a name="context-switching"></a>コンテキストの切り替え  
 `AS { LOGIN | USER } = ' name '` 句を使用して、動的ステートメントの実行コンテキストを切り替えることができます。 コンテキスト スイッチを `EXECUTE ('string') AS <context_specification>` のように指定した場合、コンテキスト スイッチは、実行するクエリのスコープでのみ有効になります。  
  
###  <a name="_user"></a>ユーザーまたはログイン名を指定します。  
 `AS { LOGIN | USER } = ' name '` で指定するユーザーまたはログイン名は、sys.database_principals または sys.server_principals の各プリンシパルとして存在する必要があります。存在しない場合、ステートメントは失敗します。 さらに、プリンシパルで IMPERSONATE 権限が許可されている必要があります。 呼び出し元がデータベース所有者または sysadmin 固定サーバー ロールのメンバーでない場合は、ユーザーが Windows グループ メンバーシップによって [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータベースやインスタンスにアクセスしているときでも、プリンシパルは存在する必要があります。 たとえば、次のような条件を想定します。  
  
-   CompanyDomain\SQLUsers グループに Sales データベースへのアクセス権がある。  
  
-   CompanyDomain\SqlUser1 は SQLUsers のメンバーであり、したがって Sales データベースへのアクセスが暗黙的に許可されている。  
  
 Companydomain \sqluser1 は SQLUsers のメンバーシップを介してデータベースへのアクセスは、ステートメントをグループ`EXECUTE @string_variable AS USER = 'CompanyDomain\SqlUser1'`ために失敗`CompanyDomain\SqlUser1`データベース内のプリンシパルとして存在しません。  
  
### <a name="best-practices"></a>ベスト プラクティス  
 ステートメントまたはモジュールで定義されている操作の実行に必要な、最小の権限が与えられているログインまたはユーザーを指定します。 たとえば、サーバー レベルの権限を持つ、のみデータベース レベルの権限が必要です。 ログイン名を指定できません。または、これらのアクセス許可が必要でない場合は、データベース所有者アカウントを指定しません。  
  
## <a name="permissions"></a>アクセス許可  
 EXECUTE ステートメントの実行に権限は必要ありませんが、 EXECUTE 文字列内で参照されるセキュリティ保護可能なリソースに対しては権限が必要です。 たとえば、この文字列に INSERT ステートメントが含まれている場合、EXECUTE ステートメントの呼び出し元は対象のテーブルに対する INSERT 権限が必要です。 EXECUTE ステートメントは、モジュール内に含まれている場合でも、検出されるたびに権限が確認されます。  
  
 モジュールの EXECUTE 権限は、既定ではモジュールの所有者に与えられており、所有者はその権限を別のユーザーに譲渡できます。 文字列を実行するモジュールが実行されるとき、権限は、モジュールを作成したユーザーのコンテキストではなく、モジュールを実行しているユーザーのコンテキストに基づいて確認されます。 ただし、呼び出すモジュールと呼び出されるモジュールを所有するユーザーが同じ場合、2 番目のモジュールに対しては EXECUTE 権限の確認は行われません。  
  
 モジュールで他のデータベース オブジェクトにアクセスする場合は、モジュールに対する EXECUTE 権限があり、次のいずれかに該当する場合にのみ、実行は成功します。  
  
-   モジュールが EXECUTE AS USER または SELF としてマークされており、モジュール所有者が、参照されるオブジェクトに対して必要な権限を保持している。 モジュール内で権限借用の詳細については、次を参照してください。 [EXECUTE AS 句 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
-   モジュールが EXECUTE AS CALLER としてマークされており、オブジェクトに対して必要な権限を保持している。  
  
-   モジュールが EXECUTE AS をマーク*user_name*と*user_name*オブジェクトに対応するアクセス許可を持っています。  
  
### <a name="context-switching-permissions"></a>コンテキスト切り替え権限  
 ログインに EXECUTE AS を指定するには、呼び出し元に、指定のログイン名に対する IMPERSONATE 権限が与えられている必要があります。 データベース ユーザーに EXECUTE AS を指定するには、呼び出し元に、指定のユーザー名に対する IMPERSONATE 権限が与えられている必要があります。 実行コンテキストを指定しない場合、または EXECUTE AS CALLER を指定する場合、IMPERSONATE 権限は必要ありません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-execute-to-pass-a-single-parameter"></a>A. EXECUTE を使用して 1 つのパラメーターを渡す  
 `uspGetEmployeeManagers`ストアド プロシージャ、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベースに 1 つのパラメーターが必要ですが (`@EmployeeID`)。 次の例では、実行、`uspGetEmployeeManagers`ストアド プロシージャを`Employee ID 6`パラメーター値として。  
  
```  
EXEC dbo.uspGetEmployeeManagers 6;  
GO  
```  
  
 実行の中で明示的に変数を指定することもできます。  
  
```  
EXEC dbo.uspGetEmployeeManagers @EmployeeID = 6;  
GO  
```  
  
 バッチの最初のステートメントを次に示すかどうかまたは**osql**または**sqlcmd**スクリプト、EXEC は必要ありません。  
  
```  
dbo.uspGetEmployeeManagers 6;  
GO  
--Or  
dbo.uspGetEmployeeManagers @EmployeeID = 6;  
GO  
```  
  
### <a name="b-using-multiple-parameters"></a>B. 複数のパラメーターを使用する  
 次の例を実行、`spGetWhereUsedProductID`ストアド プロシージャ、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。 ここでは、製品 ID (`819`) と、`@CheckDate,` 型の値をとる `datetime` の、2 つのパラメーターを引き渡します。  
  
```  
DECLARE @CheckDate datetime;  
SET @CheckDate = GETDATE();  
EXEC dbo.uspGetWhereUsedProductID 819, @CheckDate;  
GO  
```  
  
### <a name="c-using-execute-tsqlstring-with-a-variable"></a>C. EXECUTE 'tsql_string' を変数と共に使用する  
 例を次にどのように`EXECUTE`変数を含む文字列を動的に構築されるハンドル。 この例で作成、`tables_cursor`カーソル内のすべてのユーザー定義テーブルの一覧を保持するために、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース、および、テーブルのすべてのインデックスを再構築するボックスの一覧を使用します。  
  
```  
DECLARE tables_cursor CURSOR  
   FOR  
   SELECT s.name, t.name   
   FROM sys.objects AS t  
   JOIN sys.schemas AS s ON s.schema_id = t.schema_id  
   WHERE t.type = 'U';  
OPEN tables_cursor;  
DECLARE @schemaname sysname;  
DECLARE @tablename sysname;  
FETCH NEXT FROM tables_cursor INTO @schemaname, @tablename;  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN;  
   EXECUTE ('ALTER INDEX ALL ON ' + @schemaname + '.' + @tablename + ' REBUILD;');  
   FETCH NEXT FROM tables_cursor INTO @schemaname, @tablename;  
END;  
PRINT 'The indexes on all tables have been rebuilt.';  
CLOSE tables_cursor;  
DEALLOCATE tables_cursor;  
GO  
  
```  
  
### <a name="d-using-execute-with-a-remote-stored-procedure"></a>D. EXECUTE をリモート ストアド プロシージャと共に使用する  
 次の例を実行、`uspGetEmployeeManagers`リモート サーバー上のストアド プロシージャ`SQLSERVER1`の成功または失敗を示す戻り値の状態を格納および`@retstat`です。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
DECLARE @retstat int;  
EXECUTE @retstat = SQLSERVER1.AdventureWorks2012.dbo.uspGetEmployeeManagers @BusinessEntityID = 6;  
```  
  
### <a name="e-using-execute-with-a-stored-procedure-variable"></a>E. EXECUTE をストアド プロシージャ変数と共に使用する  
 次の例では、ストアド プロシージャ名を表す変数を作成します。  
  
```sql  
DECLARE @proc_name varchar(30);  
SET @proc_name = 'sys.sp_who';  
EXEC @proc_name;  
  
```  
  
### <a name="f-using-execute-with-default"></a>F. EXECUTE を DEFAULT と共に使用する  
 次の例では、第 1 および第 3 パラメーターに既定値を指定して、ストアド プロシージャを作成します。 プロシージャを実行するとき、値を指定しなかったり、既定値が指定されていた場合は、これらの既定値が第 1 および第 3 パラメーターに挿入されます。 `DEFAULT` キーワードはさまざまな方法で使用できます。  
  
```  
IF OBJECT_ID(N'dbo.ProcTestDefaults', N'P')IS NOT NULL  
   DROP PROCEDURE dbo.ProcTestDefaults;  
GO  
-- Create the stored procedure.  
CREATE PROCEDURE dbo.ProcTestDefaults (  
@p1 smallint = 42,   
@p2 char(1),   
@p3 varchar(8) = 'CAR')  
AS   
   SET NOCOUNT ON;  
   SELECT @p1, @p2, @p3  
;  
GO  
  
```  
  
 `Proc_Test_Defaults`ストアド プロシージャは、多くの組み合わせで実行することができます。  
  
```  
-- Specifying a value only for one parameter (@p2).  
EXECUTE dbo.ProcTestDefaults @p2 = 'A';  
-- Specifying a value for the first two parameters.  
EXECUTE dbo.ProcTestDefaults 68, 'B';  
-- Specifying a value for all three parameters.  
EXECUTE dbo.ProcTestDefaults 68, 'C', 'House';  
-- Using the DEFAULT keyword for the first parameter.  
EXECUTE dbo.ProcTestDefaults @p1 = DEFAULT, @p2 = 'D';  
-- Specifying the parameters in an order different from the order defined in the procedure.  
EXECUTE dbo.ProcTestDefaults DEFAULT, @p3 = 'Local', @p2 = 'E';  
-- Using the DEFAULT keyword for the first and third parameters.  
EXECUTE dbo.ProcTestDefaults DEFAULT, 'H', DEFAULT;  
EXECUTE dbo.ProcTestDefaults DEFAULT, 'I', @p3 = DEFAULT;  
  
```  
  
### <a name="g-using-execute-with-at-linkedservername"></a>G. EXECUTE を AT linked_server_name と共に使用する  
 次の例では、コマンド文字列をリモート サーバーに渡します。 リンク サーバーを作成、`SeattleSales`の別のインスタンスを指す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]DDL ステートメントを実行し、(`CREATE TABLE`) そのリンク サーバーに対してです。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
EXEC sp_addlinkedserver 'SeattleSales', 'SQL Server'  
GO  
EXECUTE ( 'CREATE TABLE AdventureWorks2012.dbo.SalesTbl   
(SalesID int, SalesName varchar(10)) ; ' ) AT SeattleSales;  
GO  
```  
  
### <a name="h-using-execute-with-recompile"></a>H. EXECUTE WITH RECOMPILE を使用する  
 次の例を実行、`Proc_Test_Defaults`コンパイルする新しいクエリ プランが使用され、モジュールの実行後に破棄されたストアド プロシージャを強制的に実行します。  
  
```  
EXECUTE dbo.Proc_Test_Defaults @p2 = 'A' WITH RECOMPILE;  
GO  
```  
  
### <a name="i-using-execute-with-a-user-defined-function"></a>I. EXECUTE をユーザー定義関数と共に使用する  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースでユーザー定義のスカラー関数 `ufnGetSalesOrderStatusText` を実行します。 変数を使用して`@returnstatus`関数によって返される値を格納します。 この関数には 1 つの入力パラメーター `@Status` が必要です。 これには、定義として、 **tinyint**データ型。  
  
```  
DECLARE @returnstatus nvarchar(15);  
SET @returnstatus = NULL;  
EXEC @returnstatus = dbo.ufnGetSalesOrderStatusText @Status = 2;  
PRINT @returnstatus;  
GO  
```  
  
### <a name="j-using-execute-to-query-an-oracle-database-on-a-linked-server"></a>J. EXECUTE を使用して、リンク サーバー上の Oracle データベースに対してクエリを実行する  
 次の例では、いくつか実行`SELECT`リモートの Oracle サーバーでのステートメント。 この例では、まず Oracle サーバーをリンク サーバーとして追加し、リンク サーバー ログインを作成します。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
-- Setup the linked server.  
EXEC sp_addlinkedserver    
        @server='ORACLE',  
        @srvproduct='Oracle',  
        @provider='OraOLEDB.Oracle',   
        @datasrc='ORACLE10';  
  
EXEC sp_addlinkedsrvlogin   
    @rmtsrvname='ORACLE',  
    @useself='false',   
    @locallogin=null,   
    @rmtuser='scott',   
    @rmtpassword='tiger';  
  
EXEC sp_serveroption 'ORACLE', 'rpc out', true;  
GO  
  
-- Execute several statements on the linked Oracle server.  
EXEC ( 'SELECT * FROM scott.emp') AT ORACLE;  
GO  
EXEC ( 'SELECT * FROM scott.emp WHERE MGR = ?', 7902) AT ORACLE;  
GO  
DECLARE @v INT;   
SET @v = 7902;  
EXEC ( 'SELECT * FROM scott.emp WHERE MGR = ?', @v) AT ORACLE;  
GO   
```  
  
### <a name="k-using-execute-as-user-to-switch-context-to-another-user"></a>K. EXECUTE AS USER を使用して、コンテキストを別のユーザーに切り替える  
 次の例を実行、[!INCLUDE[tsql](../../includes/tsql-md.md)]テーブルを作成しを指定する文字列、`AS USER`句を呼び出し元のステートメントの実行コンテキストを切り替える`User1`です。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の権限はチェック`User1`ステートメントを実行するとします。 `User1`データベース内のユーザーとして存在し、内のテーブルを作成する権限が必要、`Sales`スキーマ、または、ステートメントは失敗します。  
  
```  
EXECUTE ('CREATE TABLE Sales.SalesTable (SalesID int, SalesName varchar(10));')  
AS USER = 'User1';  
GO  
```  
  
### <a name="l-using-a-parameter-with-execute-and-at-linkedservername"></a>L. EXECUTE および AT linked_server_name と共にパラメーターを使用する  
 次の例は、疑問符 () を使用してリモート サーバーにコマンド文字列を渡します (`?`) パラメーターのプレース ホルダーです。 例では、リンク サーバーを作成する`SeattleSales`の別のインスタンスを指す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行し、`SELECT`そのリンク サーバーに対してステートメントです。 `SELECT` ステートメントでは、`ProductID` パラメーター (`952`) のプレースホルダーとして疑問符を使用します。このパラメーターは、ステートメントの後で提供されます。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
-- Setup the linked server.  
EXEC sp_addlinkedserver 'SeattleSales', 'SQL Server'  
GO  
-- Execute the SELECT statement.  
EXECUTE ('SELECT ProductID, Name   
    FROM AdventureWorks2012.Production.Product  
    WHERE ProductID = ? ', 952) AT SeattleSales;  
GO  
```  
  
### <a name="m-using-execute-to-redefine-a-single-result-set"></a>M. EXECUTE を使用して単一の結果セットを再定義する  
 実行前の例のいくつか`EXEC dbo.uspGetEmployeeManagers 6;`7 つの列が返されます。 次の例では、`WITH RESULT SET` 構文を使用して、返される結果セットの名前とデータ型を変更する方法を示します。  
  
**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]
  
```  
EXEC uspGetEmployeeManagers 16  
WITH RESULT SETS  
(   
   ([Reporting Level] int NOT NULL,  
    [ID of Employee] int NOT NULL,  
    [Employee First Name] nvarchar(50) NOT NULL,  
    [Employee Last Name] nvarchar(50) NOT NULL,  
    [Employee ID of Manager] nvarchar(max) NOT NULL,  
    [Manager First Name] nvarchar(50) NOT NULL,  
    [Manager Last Name] nvarchar(50) NOT NULL )  
);  
  
```  
  
### <a name="n-using-execute-to-redefine-a-two-result-sets"></a>N. EXECUTE を使用して 2 つの結果セットを再定義する  
 複数の結果セットを返すステートメントを実行する場合は、予期される各結果セットを定義してください。 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] の次の例では、2 つの結果セットを返すプロシージャを作成します。 使用して、手順を実行し、 **WITH RESULT SETS**句、および 2 つの結果を指定する定義を設定します。  
  
**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]
  
```  
--Create the procedure  
CREATE PROC Production.ProductList @ProdName nvarchar(50)  
AS  
-- First result set  
SELECT ProductID, Name, ListPrice  
    FROM Production.Product  
    WHERE Name LIKE @ProdName;  
-- Second result set   
SELECT Name, COUNT(S.ProductID) AS NumberOfOrders  
    FROM Production.Product AS P  
    JOIN Sales.SalesOrderDetail AS S  
        ON P.ProductID  = S.ProductID   
    WHERE Name LIKE @ProdName  
    GROUP BY Name;  
GO  
  
-- Execute the procedure   
EXEC Production.ProductList '%tire%'  
WITH RESULT SETS   
(  
    (ProductID int,   -- first result set definition starts here  
    Name Name,  
    ListPrice money)  
    ,                 -- comma separates result set definitions  
    (Name Name,       -- second result set definition starts here  
    NumberOfOrders int)  
);  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="example-o-basic-procedure-execution"></a>例 o: 基本的な手順の実行  
 ストアド プロシージャを実行しています。  
  
```  
EXEC proc1;  
```  
  
 実行時に決定する名前を持つストアド プロシージャの呼び出し。  
  
```  
EXEC ('EXEC ' + @var);  
```  
  
 ストアド プロシージャ内からストアド プロシージャの呼び出し。  
  
```  
CREATE sp_first AS EXEC sp_second; EXEC sp_third;  
```  
  
### <a name="example-p-executing-strings"></a>例 p: 文字列を実行します。  
 SQL 文字列を実行するには。  
  
```  
EXEC ('SELECT * FROM sys.types');  
```  
  
 入れ子になった文字列を実行するには。  
  
```  
EXEC ('EXEC (''SELECT * FROM sys.types'')');  
```  
  
 文字列変数を実行しています。  
  
```  
DECLARE @stringVar nvarchar(100);  
SET @stringVar = N'SELECT name FROM' + ' sys.sql_logins';  
EXEC (@stringVar);  
```  
  
### <a name="example-q-procedures-with-parameters"></a>パラメーターを使用して手順を例 q:  
 次の例では、パラメーターを持つプロシージャを作成し、プロシージャを実行する 3 つの方法を示しています。  
  
```  
-- Uses AdventureWorks  
  
CREATE PROC ProcWithParameters  
    @name nvarchar(50),  
@color nvarchar (15)  
AS   
SELECT ProductKey, EnglishProductName, Color FROM [dbo].[DimProduct]  
WHERE EnglishProductName LIKE @name  
AND Color = @color;  
GO  
  
-- Executing using positional parameters  
EXEC ProcWithParameters N'%arm%', N'Black';  
-- Executing using named parameters in order  
EXEC ProcWithParameters @name = N'%arm%', @color = N'Black';  
-- Executing using named parameters out of order  
EXEC ProcWithParameters @color = N'Black', @name = N'%arm%';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [@@NESTLEVEL &#40;Transact-SQL&#41;](../../t-sql/functions/nestlevel-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [EXECUTE AS 句 &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md)   
 [osql ユーティリティ](../../tools/osql-utility.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [元に戻す (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revert-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md)   
 [SUSER_NAME &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/suser-name-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [USER_NAME &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/user-name-transact-sql.md)   
 [OPENDATASOURCE &#40;Transact-SQL&#41;](../../t-sql/functions/opendatasource-transact-sql.md)   
 [インメモリ OLTP でのユーザー定義のスカラー関数](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md)  
  
  
