---
title: "関数 (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FUNCTION
- CREATE FUNCTION
- CREATE_FUNCTION_TSQL
- FUNCTION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- invoking functions
- extended stored procedures [SQL Server], functions
- table-valued parameters
- user-defined functions [SQL Server], creating
- CLR functions [SQL Server]
- CREATE FUNCTION statement
- nondeterministic functions
- user-defined data types
- functions [SQL Server], creating
- inline table-valued functions [SQL Server]
- multi-statement table-valued functions [SQL Server]
- table-valued functions [SQL Server], CREATE FUNCTION
- parameters [SQL Server], functions
- nesting user-defined functions
- deterministic functions
- scalar-valued functions
- functions [SQL Server], invoking
ms.assetid: 864b393f-225f-4895-8c8d-4db59ea60032
caps.latest.revision: "162"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 76b25e852e94ff6a511d8b18adb31f9da883a7fe
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="create-function-transact-sql"></a>CREATE FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] でユーザー定義関数を作成します。 ユーザー定義関数は、パラメーターを受け取り、複雑な計算などのアクションを実行し、そのアクションの結果を値として返す [!INCLUDE[tsql](../../includes/tsql-md.md)] または共通言語ランタイム (CLR) のルーチンです。 戻り値は、スカラー (単一) 値またはテーブルにすることができます。 このステートメントを使用して、次の方法で使用できる再利用可能なルーチンを作成します。  
  
-   SELECT などの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント内で使用する  
  
-   関数を呼び出すアプリケーション内で使用する  
  
-   別のユーザー定義関数の定義内で使用する  
  
-   ビューをパラメーター化したり、インデックス付きビューの機能を向上させる  
  
-   テーブルの列を定義する  
  
-   列の CHECK 制約を定義する  
  
-   ストアド プロシージャを置換する  
  
-   セキュリティ ポリシーのフィルター述語としてのインライン関数を使用します。  
  
> [!NOTE]  
>  SQL Server への .NET Framework CLR の統合はこのトピックで説明します。 CLR 統合は、Azure SQL Database には適用されません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Transact-SQL Scalar Function Syntax  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ][ type_schema_name. ] parameter_data_type   
    [ = default ] [ READONLY ] }   
    [ ,...n ]  
  ]  
)  
RETURNS return_data_type  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    BEGIN   
        function_body   
        RETURN scalar_expression  
    END  
[ ; ]  
```  
  
```  
-- Transact-SQL Inline Table-Valued Function Syntax   
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] [ type_schema_name. ] parameter_data_type   
    [ = default ] [ READONLY ] }   
    [ ,...n ]  
  ]  
)  
RETURNS TABLE  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    RETURN [ ( ] select_stmt [ ) ]  
[ ; ]  
  
```  
  
```  
-- Transact-SQL Multi-Statement Table-Valued Function Syntax  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] [ type_schema_name. ] parameter_data_type   
    [ = default ] [READONLY] }   
    [ ,...n ]  
  ]  
)  
RETURNS @return_variable TABLE <table_type_definition>  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    BEGIN   
        function_body   
        RETURN  
    END  
[ ; ]  
  
```  

```  
-- Transact-SQL Function Clauses   
<function_option>::=   
{  
    [ ENCRYPTION ]  
  | [ SCHEMABINDING ]  
  | [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]  
  | [ EXECUTE_AS_Clause ]  
}  
  
<table_type_definition>:: =   
( { <column_definition> <column_constraint>   
  | <computed_column_definition> }   
    [ <table_constraint> ] [ ,...n ]  
)   
<column_definition>::=  
{  
    { column_name data_type }  
    [ [ DEFAULT constant_expression ]   
      [ COLLATE collation_name ] | [ ROWGUIDCOL ]  
    ]  
    | [ IDENTITY [ (seed , increment ) ] ]  
    [ <column_constraint> [ ...n ] ]   
}  
  
<column_constraint>::=   
{  
    [ NULL | NOT NULL ]   
    { PRIMARY KEY | UNIQUE }  
      [ CLUSTERED | NONCLUSTERED ]   
      [ WITH FILLFACTOR = fillfactor   
        | WITH ( < index_option > [ , ...n ] )  
      [ ON { filegroup | "default" } ]  
  | [ CHECK ( logical_expression ) ] [ ,...n ]  
}  
  
<computed_column_definition>::=  
column_name AS computed_column_expression   
  
<table_constraint>::=  
{   
    { PRIMARY KEY | UNIQUE }  
      [ CLUSTERED | NONCLUSTERED ]   
      ( column_name [ ASC | DESC ] [ ,...n ] )  
        [ WITH FILLFACTOR = fillfactor   
        | WITH ( <index_option> [ , ...n ] )  
  | [ CHECK ( logical_expression ) ] [ ,...n ]  
}  
  
<index_option>::=  
{   
    PAD_INDEX = { ON | OFF }   
  | FILLFACTOR = fillfactor   
  | IGNORE_DUP_KEY = { ON | OFF }  
  | STATISTICS_NORECOMPUTE = { ON | OFF }   
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS ={ ON | OFF }   
}  
```  
  
```  
-- CLR Scalar Function Syntax  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( { @parameter_name [AS] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
)  
RETURNS { return_data_type }  
    [ WITH <clr_function_option> [ ,...n ] ]  
    [ AS ] EXTERNAL NAME <method_specifier>  
[ ; ]  
```  
  
```  
-- CLR Table-Valued Function Syntax  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( { @parameter_name [AS] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
)  
RETURNS TABLE <clr_table_type_definition>   
    [ WITH <clr_function_option> [ ,...n ] ]  
    [ ORDER ( <order_clause> ) ]  
    [ AS ] EXTERNAL NAME <method_specifier>  
[ ; ]  
```  

```  
-- CLR Function Clauses  
<order_clause> ::=   
{  
   <column_name_in_clr_table_type_definition>  
   [ ASC | DESC ]   
} [ ,...n]   
  
<method_specifier>::=  
    assembly_name.class_name.method_name  
  
<clr_function_option>::=  
}  
    [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]  
  | [ EXECUTE_AS_Clause ]  
}  
  
<clr_table_type_definition>::=   
( { column_name data_type } [ ,...n ] )  
  
```  
  
```  
-- In-Memory OLTP: Syntax for natively compiled, scalar user-defined function  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
 ( [ { @parameter_name [ AS ][ type_schema_name. ] parameter_data_type   
    [ NULL | NOT NULL ] [ = default ] [ READONLY ] }   
    [ ,...n ]   
  ]   
)   
RETURNS return_data_type  
     WITH <function_option> [ ,...n ]   
    [ AS ]   
    BEGIN ATOMIC WITH (set_option [ ,... n ])   
        function_body   
        RETURN scalar_expression  
    END  
  
<function_option>::=   
{  
  |  NATIVE_COMPILATION   
  |  SCHEMABINDING   
  | [ EXECUTE_AS_Clause ]   
  | [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]   
}  
  
```  
  
## <a name="arguments"></a>引数
*または変更*  
 **適用されます**: Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1)。  
  
 条件付きでは既に存在する場合にのみ、関数を変更します。 
 
> [!NOTE]  
>  CLR の省略可能な [かの変更] 構文は以降で利用可能な[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1 CU1 です。   
 
 *schema_name*  
 ユーザー定義関数が属するスキーマの名前を指定します。  
  
 *function_name*  
 ユーザー定義関数の名前です。 関数名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)およびそのスキーマ、データベース内で一意である必要があります。  
  
> [!NOTE]  
>  パラメーターを指定しない場合でも、関数名の後にはかっこが必要です。  
  
 @*parameter_name*  
 ユーザー定義関数内のパラメーターです。 1 つ以上のパラメーターを宣言できます。  
  
 1 つの関数では、最高 2,100 個のパラメーターを使用できます。 宜言した各パラメーターの値は、関数の実行時に、ユーザーが指定する必要があります (そのパラメーターの既定値が定義されていない場合)。  
  
 最初の文字をアット マーク (@) にしてパラメーター名を指定します。 パラメーター名は識別子のルールに従っている必要があります。 パラメーターは関数に対してローカルです。同じパラメーター名を他の関数で使用できます。 パラメーターは定数の代わりとしてのみ使用できます。パラメーターは、テーブル名、列名、またはその他のデータベース オブジェクト名の代わりに使用することはできません。  
  
> [!NOTE]  
>  ストアド プロシージャまたはユーザー定義関数でパラメーターを渡すとき、あるいはバッチ ステートメントで変数を宣言して設定するときには、ANSI_WARNINGS が無視されます。 たとえば、として変数が定義されている**char (3)**とし、次の 3 つの文字を超える値に設定、データは切り捨てに定義されているサイズと、INSERT または UPDATE ステートメントは成功します。  
  
 [ *type_schema_name*です。 *parameter_data_type*  
 パラメーターのデータ型、および必要に応じてが所属するスキーマです。 [!INCLUDE[tsql](../../includes/tsql-md.md)]関数、CLR ユーザー定義型と、ユーザー定義テーブル型を含む、すべてのデータ型は除く許可、**タイムスタンプ**データ型。 CLR 関数では、CLR ユーザー定義型を含めた、すべてのデータ型は除く許可**テキスト**、 **ntext**、**イメージ**、ユーザー定義テーブル型および**タイムスタンプ**データ型。 スカラー型の**カーソル**と**テーブル**、いずれかのパラメーターのデータ型として指定することはできません[!INCLUDE[tsql](../../includes/tsql-md.md)]関数と CLR 関数。  
  
 場合*type_schema_name*が指定されていない、[!INCLUDE[ssDE](../../includes/ssde-md.md)]は検索、 *scalar_parameter_data_type*次の順序で。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム データ型の名前を含むスキーマ  
  
-   現在のデータベースにおける現在のユーザーの既定のスキーマ  
  
-   現在のデータベースの **dbo** スキーマ。  
  
 [=*既定*]  
 パラメーターの既定値です。 場合、*既定*値は、そのパラメーターの値を指定せず、関数を実行することができます。  
  
> [!NOTE]  
>  除く、CLR 関数のパラメーターの既定値を指定することができます、 **varchar (max)**と**varbinary (max)**データ型。  
  
 関数のパラメーターに既定値がある場合に、既定値を取得する目的でその関数を呼び出すときは、DEFAULT キーワードを指定する必要があります。 この動作は、ストアド プロシージャで既定値を持つパラメーターを使用する場合とは異なります。ストアド プロシージャの場合は、パラメーターを省略すると既定値が暗黙的に使用されます。 ただし、EXECUTE ステートメントを使用してスカラー関数を呼び出す場合は、DEFAULT キーワードは必要ありません。  
  
 READONLY  
 パラメーターを関数の定義内で更新または変更できないことを示します。 パラメーターの型がユーザー定義テーブル型の場合は、READONLY を指定する必要があります。  
  
 *return_data_type*  
 スカラー ユーザー定義関数の戻り値です。 [!INCLUDE[tsql](../../includes/tsql-md.md)]関数、CLR ユーザー定義型を含めた、すべてのデータ型は除く許可、**タイムスタンプ**データ型。 CLR 関数では、CLR ユーザー定義型を含めた、すべてのデータ型は除く許可、**テキスト**、 **ntext**、**イメージ**、および**タイムスタンプ**データ型。 スカラー型の**カーソル**と**テーブル**、いずれかで戻り値のデータ型として指定することはできません[!INCLUDE[tsql](../../includes/tsql-md.md)]関数と CLR 関数。  
  
 *function_body*  
 総合して副作用 (テーブルの変更など) がない一連の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが、関数の値を定義することを指定します。 *function_body*はスカラー関数および複数ステートメント テーブル値関数でのみ使用します。  
  
 スカラー関数は、 *function_body*一連の[!INCLUDE[tsql](../../includes/tsql-md.md)]スカラー値にまとめて評価されるステートメントです。  
  
 複数ステートメント テーブル値関数の*function_body*一連の[!INCLUDE[tsql](../../includes/tsql-md.md)]テーブルを作成するステートメントが変数を返します。  
  
 *scalar_expression*  
 スカラー関数が返すスカラー値を指定します。  
  
 TABLE  
 テーブル値関数の戻り値がテーブルになるように指定します。 定数のみと @*local_variables*テーブル値関数に渡すことができます。  
  
 インライン テーブル値関数の TABLE 戻り値は、単一の SELECT ステートメントを使用して定義します。 インライン関数には、関連付けられている戻り変数はありません。  
  
 複数ステートメント テーブル値関数の @*return_variable*テーブル変数では、格納および関数の値として返される行を蓄積するために使用します。 @*return_variable*に対してのみ指定できます[!INCLUDE[tsql](../../includes/tsql-md.md)]関数し、CLR ではなく機能します。  
  
> [!WARNING]  
>  内の関数に値を持つ複数ステートメントのテーブルへの参加、 **FROM**句は可能ですが、パフォーマンスの低下を与えることができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]複数ステートメント関数になっているため、その結果、最適なクエリ プランに含めることがいくつかのステートメントに対して最適化されたすべての技術を使用できません。 パフォーマンスをできるだけ高くするには、可能な限り、関数間ではなくベース テーブル間の結合を使用してください。  
  
 *select_stmt*  
 インライン テーブル値関数の戻り値を定義する単一の SELECT ステートメントです。  
  
 順序 (\<order_clause >)、テーブル値関数からを結果が返される順序を指定します。 詳細については、このトピックで後述する「並べ替え順序の使用に関するガイダンス」を参照してください。  
  
 外部名\<method_specifier > *assembly_name*.*class_name*.*メソッド名が***対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。  
  
 アセンブリおよび作成した関数名が参照するメソッドを指定します。  
  
-   *アセンブリ名*-の値に一致する必要があります、`name`の列   
    `SELECT * FROM sys.assemblies;`」をご覧ください。  
    これは、`CREATE ASSEMBLY` ステートメントで使用された名前です。  
  
-   *class_name* -の値に一致する必要があります、`assembly_name`の列  
    `SELECT * FROM sys.assembly_modules;`」をご覧ください。  
    多くの場合、値には、埋め込まれたピリオドまたはドット (.) が含まれています。 このような場合、TRANSACT-SQL 構文必要で、二重の角かっこのペアまたは二重引用符のペアに値を制限することを""です。  
  
-   *メソッド名が*-の値に一致する必要があります、`method_name`の列   
    `SELECT * FROM sys.assembly_modules;`」をご覧ください。  
    メソッドを静的にする必要があります。  
  
 一般的な例として、MyFood.DLL において、すべての型が MyFood 名前空間にあるため、`EXTERNAL NAME` 値は次のようになることがあります。   
`MyFood.[MyFood.MyClass].MyStaticMethod`  
  
> [!NOTE]  
>  既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は CLR コードを実行できません。 作成、変更、および共通言語ランタイム モジュール; を参照するデータベース オブジェクトを削除することができます。ただし、これらの参照を実行することはできません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]有効にするまで、 [clr enabled オプション](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)です。 このオプションを有効にするには、 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)です。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
 *\<*table_type_definition *>*  ({ \<column_definition > \<column_constraint > |\<computed_column_definition >}   [ \<table_constraint >] [,... *n*  ]) のテーブル データ型を定義、[!INCLUDE[tsql](../../includes/tsql-md.md)]関数。 テーブルの定義には、列の定義、および列またはテーブルの制約が含まれます。 テーブルは、常にプライマリ ファイル グループに保存されます。  
  
 \<clr_table_type_definition > ({ *column_name**data_type* } [,... *n*  ])**対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([一部の地域でプレビュー](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)). |  
  
 CLR 関数のテーブル データ型を定義します。 テーブルの定義には、列名およびデータ型のみが含まれます。 テーブルは、常にプライマリ ファイル グループに保存されます。  
  
 NULL|NULL でないです。  
 ネイティブ コンパイル、スカラー ユーザー定義関数でのみサポートされます。 詳細については、次を参照してください。 [scalar user-defined 関数は、インメモリ OLTP](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md)です。  
  
 NATIVE_COMPILATION  
 ユーザー定義の関数をネイティブでコンパイルするかどうかを示します。 この引数は、ネイティブ コンパイル、スカラー ユーザー定義関数に必要です。  
  
 アトミックの開始します。  
 ユーザー定義スカラー関数、および、必要なはネイティブでコンパイルすると、のみサポートされます。 詳細については、「 [Atomic Blocks](../../relational-databases/in-memory-oltp/atomic-blocks-in-native-procedures.md)」を参照してください。  
  
 SCHEMABINDING  
 SCHEMABINDING の引数は、ネイティブ コンパイル、スカラー ユーザー定義関数に必要です。  
  
 EXECUTE AS  
 EXECUTE AS は、ネイティブ コンパイル、スカラー ユーザー定義関数に必要です。  
  
 **\<function_option >:: = と\<clr_function_option >:: =** 
  
 関数が、次のオプションの 1 つ以上を持つことを指定します。  
  
 ENCRYPTION  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 示します、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] CREATE FUNCTION ステートメントの元のテキストを暗号化した形式に変換されます。 暗号化した形式の出力は、どのカタログ ビューでも直接見ることはできません。 システム テーブルまたはデータベース ファイルへのアクセスがないユーザーは、難読化テキストを取得できません。 ただし、テキストができるように特権を持つ経由でシステム テーブルにアクセスできるか、 [DAC ポート](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)または直接データベース ファイルにアクセスします。 また、サーバー プロセスにデバッガーをアタッチできるユーザーは、実行時にメモリから元のプロシージャを取得できます。 システム メタデータへのアクセスの詳細については、次を参照してください。 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)です。  
  
 このオプションを使用すると、関数がの一部としてパブリッシュできなく[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レプリケーション。 CLR 関数にはこのオプションを指定できません。  
  
 SCHEMABINDING  
 参照するデータベース オブジェクトに対して、その関数がバインドされるように指定します。 SCHEMABINDING を指定した場合、ベース オブジェクトに対して関数定義に影響を与えるような変更は行えません。 まず関数定義を変更または削除して、変更するオブジェクトとの依存関係を解消する必要があります。  
  
 関数からその参照先のオブジェクトへのバインドは、次のいずれかの操作が行われた場合にのみ削除されます。 
  
-   関数を削除した場合。  
  
-   関数を、SCHEMABINDING オプションを指定せずに ALTER ステートメントを使用して変更した場合。  
  
 関数をスキーマにバインドできるのは、次の条件が満たされている場合に限られます。  
  
-   関数が [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数である。  
  
-   関数が参照するユーザー定義関数とビューも同様にスキーマにバインドされている。  
  
-   関数が参照するオブジェクトが、2 つの要素から成る名前を使用して参照されている。  
  
-   関数およびその関数が参照するオブジェクトが、同じデータベースに属している。  
  
-   CREATE FUNCTION ステートメントを実行したユーザーが、その関数が参照するデータベース オブジェクトに対する REFERENCES 権限を持っている。  
  
 NULL 入力時に NULL を返します |**NULL 入力時に呼び出されます**  
 指定します、 **OnNULLCall**スカラー値関数の属性です。 指定しない場合は、既定で CALLED ON NULL INPUT が暗黙的に使用されます。 つまり、NULL が引数として渡された場合でも、関数本体が実行されます。  
  
 CLR 関数で RETURNS NULL ON NULL INPUT が指定されている場合ことを示して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が受け取った引数のいずれかの NULL の場合、関数の本体を呼び出すことがなく、NULL を返すことができます。 CLR 関数のメソッドで指定される場合\<method_specifier > 既に RETURNS NULL ON NULL INPUT を示すカスタム属性ですが、CREATE FUNCTION ステートメントと呼ばれる ON NULL INPUT を示す、CREATE FUNCTION ステートメントが優先順位。 **OnNULLCall** CLR テーブル値関数の属性を指定することはできません。 
  
 EXECUTE AS 句  
 ユーザー定義関数が実行されるセキュリティ コンテキストを指定します。 そのため、ユーザー アカウントを制御できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]関数によって参照されているすべてのデータベース オブジェクトに対するアクセス許可の検証に使用します。  
  
> [!NOTE]  
>  インライン ユーザー定義関数には EXECUTE AS を指定できません。  
  
 詳細については、「[EXECUTE AS 句 &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md)」を参照してください。  
  
 **\<column_definition >:: =** 
  
 Table データ型を定義します。 テーブルの定義には、列の定義および制約が含まれます。 CLR 関数では、のみ*column_name*と*data_type*を指定できます。  
  
 *column_name*  
 テーブルの列名です。 列名は、識別子のルールに従っていること、およびテーブル内で一意であることが必要です。 *column_name* 1 ~ 128 文字で構成できます。  
  
 *data_type*  
 列のデータ型を指定します。 [!INCLUDE[tsql](../../includes/tsql-md.md)]関数、CLR ユーザー定義型を含めた、すべてのデータ型は除く許可**タイムスタンプ**です。 CLR 関数では、CLR ユーザー定義型を含めた、すべてのデータ型は除く許可**テキスト**、 **ntext**、**イメージ**、 **char**、 **varchar**、 **varchar (max)**、および**タイムスタンプ**です。スカラー型**カーソル**で列のデータ型として指定することはできません[!INCLUDE[tsql](../../includes/tsql-md.md)]関数と CLR 関数。  
  
 既定の*constant_expression*  
 挿入の際に明示的な値を指定しない場合に、列に入力される値を指定します。 *constant_expression*は、定数、NULL の場合、またはシステム関数値です。 DEFAULT 定義は、IDENTITY プロパティを持つ列を除くすべての列に適用できます。 CLR テーブル値関数には DEFAULT を指定できません。  
  
 COLLATE *collation_name*  
 列の照合順序を指定します。 照合順序を指定しない場合、データベースの既定の照合順序が列に割り当てられます。 照合順序名には、Windows 照合順序名または SQL 照合順序名を指定できます。 一覧と照合順序の詳細については、次を参照してください。 [Windows 照合順序名 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/windows-collation-name-transact-sql.md)と[SQL Server 照合順序名 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 のみの列の照合順序を変更するのには、COLLATE 句を使用できます、 **char**、 **varchar**、 **nchar**、および**nvarchar**データ型。  
  
 CLR テーブル値関数には COLLATE を指定できません。  
  
 ROWGUIDCOL  
 新しい列が行グローバル一意識別子列であることを示します。 1 つだけ**uniqueidentifier** ROWGUIDCOL 列として 1 つのテーブルの列を指定することができます。 ROWGUIDCOL プロパティにのみ割り当てることができます、 **uniqueidentifier**列です。  
  
 ROWGUIDCOL プロパティは、列に格納されている値の一意性を設定しません。 これも自動的に生成しません、テーブルに挿入される新しい行の値。 各列に対して一意な値を生成するには、INSERT ステートメントで NEWID 関数を使用します。 既定値も指定できますが、NEWID を既定値として指定することはできません。  
  
 IDENTITY  
 新しい列が ID 列であることを指定します。 テーブルに行が新しく追加されると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は列に一意な増加値を設定します。 ID 列は通常、PRIMARY KEY 制約と共に使用され、テーブルの一意な行識別子 (ROWID) の役割を果たします。 IDENTITY プロパティを割り当てることが**tinyint**、 **smallint**、 **int**、 **bigint**、 **decimal(p,0)**、または**numeric(p,0)**列です。 ID 列は 1 つのテーブルにつき 1 つだけ作成できます。 バインドされた既定値および DEFAULT 制約を ID 列と組み合わせて使用することはできません。 両方を指定する必要があります、*シード*と*インクリメント*またはどちらもします。 どちらも指定しないときの既定値は (1,1) です。  
  
 CLR テーブル値関数には IDENTITY を指定できません。  
  
 *シード*  
 テーブル内の先頭行に割り当てる整数値を指定します。  
  
 *増分値*  
 整数値に追加するには、*シード*テーブル内の後続の行の値。  
  
 **\<column_constraint >:: = と\<table_constraint >:: =** 
  
 指定された列またはテーブルの制約を定義します。 CLR 関数の場合、制約の種類として指定できるのは NULL だけです。 名前付き制約は使用できません。  
  
 NULL | NOT NULL  
 列で NULL 値を許すかどうかを示します。 NULL は厳密には制約ではありませんが、NOT NULL と同じように指定することができます。 CLR テーブル値関数には NOT NULL を指定できません。  
  
 PRIMARY KEY  
 一意なインデックスによって、指定した列にエンティティの整合性を設定する制約です。 テーブル値ユーザー定義関数では、1 つのテーブルにつき 1 つの列にのみ PRIMARY KEY 制約を作成できます。 CLR テーブル値関数には PRIMARY KEY を指定できません。  
  
 UNIQUE  
 指定された列または一意なインデックスによって列のエンティティの整合性を提供する制約です。 1 つのテーブルには複数の UNIQUE 制約を指定できます。 CLR テーブル値関数には UNIQUE を指定できません。  
  
 CLUSTERED | NONCLUSTERED  
 PRIMARY KEY 制約または UNIQUE 制約に対して、クラスター化インデックスまたは非クラスター化インデックスを作成することを示します。 PRIMARY KEY 制約では CLUSTERED が、UNIQUE 制約では NONCLUSTERED が、それぞれ使用されます。  
  
 CLUSTERED は 1 つの制約にのみ指定できます。 UNIQUE 制約で CLUSTERED が指定され、PRIMARY KEY 制約も指定した場合には、PRIMARY KEY は NONCLUSTERED を使用します。  
  
 CLR テーブル値関数には、CLUSTERED および NONCLUSTERED を指定できません。  
  
 CHECK  
 1 つ以上の列に入力できる値を制限することによってドメインの整合性を設定する制約です。 CLR テーブル値関数には CHECK 制約を指定できません。  
  
 *logical_expression*  
 TRUE または FALSE を返す論理式です。  
  
 **\<computed_column_definition >:: =**  
  
 計算列を指定します。 計算列の詳細については、次を参照してください。 [CREATE TABLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-table-transact-sql.md).  
  
 *column_name*  
 計算列の名前です。  
  
 *computed_column_expression*  
 計算列の値を定義する式です。  
  
 **\<index_option >:: =**  
  
 PRIMARY KEY インデックスまたは UNIQUE インデックスのインデックス オプションを指定します。 インデックス オプションの詳細については、次を参照してください。 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md).  
  
 PAD_INDEX = {ON |**OFF** }  
 インデックスの埋め込みを指定します。 既定値は OFF です。  
  
 FILLFACTOR = *fillfactor*  
 どの程度を示すパーセンテージを指定します、[!INCLUDE[ssDE](../../includes/ssde-md.md)]インデックス作成時に各インデックス ページのリーフ レベルを作成または変更する必要があります。 *fillfactor* 1 から 100 までの整数値にする必要があります。 既定値は 0 です。  
  
 IGNORE_DUP_KEY = {ON |**OFF** }  
 挿入操作で、一意のインデックスに重複するキー値を挿入しようとした場合のエラー応答を指定します。 IGNORE_DUP_KEY オプションは、インデックスが作成または再構築された後の挿入操作のみに適用されます。 既定値は OFF です。  
  
 STATISTICS_NORECOMPUTE = {ON |**OFF** }  
 分布統計を再計算するかどうかを指定します。 既定値は OFF です。  
  
 ALLOW_ROW_LOCKS = { **ON** |オフ}  
 行ロックを許可するかどうかを指定します。 既定値は ON です。  
  
 ALLOW_PAGE_LOCKS = { **ON** |オフ}  
 ページ ロックを許可するかどうかを指定します。 既定値は ON です。  
  
## <a name="best-practices"></a>ベスト プラクティス  
 ユーザー定義関数の作成時に SCHEMABINDING 句を使用しないと、基になるオブジェクトに加えられた変更が関数の定義に影響して、関数が呼び出されたときに予期しない結果が生じる可能性があります。 基になるオブジェクトに対する変更によって関数が古くならないように、次のいずれかの操作を行うことをお勧めします。  
  
-   関数を作成するときに WITH SCHEMABINDING 句を指定します。 これにより、関数定義で参照されているオブジェクトは、一緒に関数も変更しない限り変更できなくなります。  
  
-   実行、 [sp_refreshsqlmodule](../../relational-databases/system-stored-procedures/sp-refreshsqlmodule-transact-sql.md)関数の定義で指定されている任意のオブジェクトを変更した後のストアド プロシージャです。  
  
## <a name="data-types"></a>データ型  
 CLR 関数では、パラメーターが指定されている場合があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型用に定義されていた*scalar_parameter_data_type*です。 比較する方法について[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]CLR 統合データ型へのシステム データ型または[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]共通言語ランタイム データの型を参照してください[CLR パラメーター データのマッピング](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メソッドをクラスではオーバー ロードは、適切な方法を参照するに示されている\<method_specifier > 次の特性が必要です。 
  
-   指定されたパラメーターの同じ番号が表示される [,...*n* ].  
  
-   すべてのパラメーターを、参照ではなく値で受け取る。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 関数で指定されたパラメーター型と互換性のあるパラメーター型を使用する。  
  
 CLR 関数の戻り値のデータ型が、テーブル型 (RETURNS TABLE) でメソッドの戻り値のデータ型を指定するかどうかは\<method_specifier > 型でなければなりません**IEnumerator**または**IEnumerable**、インターフェイスが、関数の作成者によって実装されることが前提とします。 異なり[!INCLUDE[tsql](../../includes/tsql-md.md)]関数、CLR 関数はで PRIMARY KEY、UNIQUE、または CHECK 制約を含めることはできません\<table_type_definition >。 指定された列のデータ型\<table_type_definition > 内のメソッドによって返される結果セットの対応する列の型に一致する必要があります\<method_specifier > の実行時にします。 この型チェックは、関数の作成時には実行されません。 
  
 CLR 関数のプログラミング方法の詳細については、次を参照してください。 [clr ユーザー定義関数](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)です。  
  
## <a name="general-remarks"></a>全般的な解説  
 スカラー値関数は、スカラー式が使用されている場所で呼び出すことができます。 これには、計算列および CHECK 制約定義が含まれます。 使用してスカラー値関数を実行することも、 [EXECUTE](../../t-sql/language-elements/execute-transact-sql.md)ステートメントです。 スカラー値関数は、2 つ以上の要素から構成される名前を使用して呼び出す必要があります。 マルチパート名の詳細については、次を参照してください。 [TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md). SELECT、INSERT、UPDATE、DELETE の各ステートメントの FROM 句でテーブル式を使用できる場合は、テーブル値関数を呼び出すことができます。 詳細については、次を参照してください。[実行のユーザー定義関数](../../relational-databases/user-defined-functions/execute-user-defined-functions.md)です。  
  
## <a name="interoperability"></a>相互運用性  
 関数で有効なステートメントは以下のとおりです。  
  
-   代入ステートメント。  
  
-   TRY...CATCH ステートメント以外の流れ制御ステートメント。  
  
-   ローカル データ変数およびローカル カーソルを定義する DECLARE ステートメント。  
  
-   ローカル変数に値を代入する式を持つ選択リストが含まれている SELECT ステートメント。  
  
-   関数内で宣言、オープン、クローズ、割り当ての解除を実行するローカル カーソルを参照するカーソル操作。 INTO 句を使用してローカル変数に値を代入する FETCH ステートメントのみが許可され、クライアントにデータを返す FETCH ステートメントは許可されません。  
  
-   ローカルなテーブル変数を変更する、INSERT、UPDATE、および DELETE ステートメント。  
  
-   拡張ストアド プロシージャを呼び出す EXECUTE ステートメント。  
  
-   詳細については、次を参照してください。[作成するユーザー定義関数 &#40; データベース エンジン&#41;](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md)です。  
  
### <a name="computed-column-interoperability"></a>計算列の相互運用性  
 関数には次のプロパティがあります。 これらのプロパティの値によって、保存される計算列またはインデックス付き計算列で関数を使用できるかどうかが決まります。  
  
|プロパティ|Description|注|  
|--------------|-----------------|-----------|  
|**IsDeterministic**|関数が決定的か非決定的かを示します。|決定的関数では、ローカル データ アクセスが可能です。 たとえば、特定の一連の入力値を使用して同じ状態のデータベースで呼び出されるたびに、必ず同じ結果を返す関数は、決定的と呼ばれます。|  
|**IsPrecise**|関数が正確か不正確かを示します。|不正確な関数には、浮動小数点演算などの演算を含みます。|  
|**IsSystemVerified**|関数の有効桁数と決定性プロパティを検証できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。||  
|**SystemDataAccess**|関数のローカル インスタンス内のシステム データ (システム カタログまたは仮想システム テーブル) にアクセスする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。||  
|**UserDataAccess**|関数が、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスのユーザー データにアクセスします。|ユーザー定義テーブルと、一時テーブルですがないテーブル変数が含まれます。|  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数の有効桁数のプロパティと決定性のプロパティは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって自動的に決定されます。 CLR 関数のデータ アクセス プロパティと決定性のプロパティは、ユーザーが指定できます。 詳細については、次を参照してください。[概要の CLR 統合のカスタム属性](http://msdn.microsoft.com/library/ecf5c097-0972-48e2-a9c0-b695b7dd2820)です。  
  
 これらのプロパティの現在の値を表示する使用[OBJECTPROPERTYEX](../../t-sql/functions/objectpropertyex-transact-sql.md)です。  
  
 関数は、決定的になるようにスキーマ バインドを使用して作成する必要があります。  
  
 ユーザー定義関数に以下のプロパティ値がある場合、その関数を呼び出す計算列をインデックスで使用できます。  
  
-   **IsDeterministic** = true  
  
-   **IsSystemVerified** = true (計算列が保持されます)  
  
-   **UserDataAccess** = false  
  
-   **SystemDataAccess** = false  
  
 詳細については、「 [計算列のインデックス](../../relational-databases/indexes/indexes-on-computed-columns.md)」を参照してください。  
  
### <a name="calling-extended-stored-procedures-from-functions"></a>関数からの拡張ストアド プロシージャ呼び出し  
 拡張ストアド プロシージャは、関数の内部から呼び出された場合、結果セットをクライアントに返しません。 結果セットをクライアントに返す ODS API はすべて FAIL を返します。 拡張ストアド プロシージャは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続し直すことはできますが、その拡張ストアド プロシージャを起動した関数と同じトランザクションに参加することはできません。  
  
 同様に呼び出しから、バッチまたはストアド プロシージャ、拡張ストアド プロシージャが実行する Windows セキュリティ アカウントのコンテキストで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。 ストアド プロシージャの所有者は、その EXECUTE 権限をユーザーに与えるときに、この点を考慮する必要があります。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 ユーザー定義関数は、データベースの状態を変更するアクションの実行に使用することはできません。  
  
 出力先がテーブルである OUTPUT INTO 句をユーザー定義関数に含めることはできません。  
  
 以下の [!INCLUDE[ssSB](../../includes/sssb-md.md)] ステートメントは、[!INCLUDE[tsql](../../includes/tsql-md.md)] ユーザー定義関数の定義に含めることができません。  
  
-   BEGIN DIALOG CONVERSATION  
  
-   END CONVERSATION  
  
-   GET CONVERSATION GROUP  
  
-   MOVE CONVERSATION  
  
-   RECEIVE  
  
-   SEND  
  
 ユーザー定義関数は入れ子にすることができます。つまり、1 つのユーザー定義関数で、別のユーザー定義関数を呼び出すことができます。 呼び出された関数が実行を開始すると入れ子レベルが 1 つ上がり、呼び出された関数が実行を終了するとレベルが 1 つ下がります。 ユーザー定義関数は、32 レベルまで入れ子にすることができます。 入れ子レベルが最大値を超えると、関数チェーン全体の呼び出しが失敗します。 [!INCLUDE[tsql](../../includes/tsql-md.md)] ユーザー定義関数からマネージ コードへの参照は、32 レベルの入れ子制限のうちの 1 レベルとカウントします。 マネージ コード内から呼び出されたメソッドは、この制限としてはカウントされません。  
  
### <a name="using-sort-order-in-clr-table-valued-functions"></a>並べ替え順序の使用に関するガイダンス  
 CLR テーブル値関数で ORDER 句を使用する場合は、以下のガイドラインに従ってください。  
  
-   結果が常に指定した順序で並べられるようにする必要があります。 指定した順序で、結果は場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クエリを実行すると、エラー メッセージが生成されます。  
  
-   ORDER 句を指定した場合は、テーブル値関数の出力を列の照合順序に従って明示的または暗黙的に並べ替える必要があります。 たとえば、列の照合順序が中国語である場合 (テーブル値関数の DDL で指定するか、またはデータベースの照合順序から取得) は、返される値が中国語の並べ替え規則に従って並べられていなければなりません。  
  
-   ORDER 句を指定した場合は、結果が返される際に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって、クエリ プロセッサが ORDER 句を使用してさらに最適化を実行するかどうかが確認されます。 ORDER 句は、クエリ プロセッサに役立つことがわかっている場合にのみ使用してください。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のクエリ プロセッサは、次のケースで ORDER 句を自動的に利用します。  
  
    -   インデックスと ORDER 句が互換である挿入クエリ  
  
    -   ORDER 句と互換である ORDER BY 句  
  
    -   GROUP BY 句と ORDER 句が互換である集計  
  
    -   非重複列と ORDER 句が互換である DISTINCT 集計  
  
 SELECT クエリを実行するときは、そのクエリで ORDER BY を一緒に指定しないと、ORDER 句で順序どおりの結果が得られるかどうかは保証されません。 参照してください[sys.function_order_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-function-order-columns-transact-sql.md)テーブル値関数の並べ替え順序で含まれている列を照会する方法についてはします。  
  
## <a name="metadata"></a>メタデータ  
 次の表に、ユーザー定義関数に関するメタデータを返すために使用できるシステム カタログ ビューを示します。  
  
|システム ビュー|Description|  
|-----------------|-----------------|  
|[sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)|後述の「例」の例 E を参照してください。|  
|[sys.assembly_modules](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)|CLR ユーザー定義関数の情報を表示します。|  
|[sys.parameters](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)|ユーザー定義関数で定義されているパラメーターの情報を表示します。|  
|[sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)|関数が参照する基になるオブジェクトを表示します。|  
  
## <a name="permissions"></a>アクセス許可  
 データベースの CREATE FUNCTION 権限と、関数を作成するスキーマの ALTER 権限が必要です。 関数でユーザー定義型が指定されている場合は、その型に対する EXECUTE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-a-scalar-valued-user-defined-function-that-calculates-the-iso-week"></a>A. ISO 週番号を計算するスカラー値ユーザー定義関数を使用する  
 次の例では、ユーザー定義関数 `ISOweek` を作成します。 この関数は、日付引数を受け取って、ISO 週番号を計算します。 この関数は、正確な計算を`SET DATEFIRST 1`関数が呼び出される前に呼び出す必要があります。  
  
 使用しても示します、 [EXECUTE AS](../../t-sql/statements/execute-as-clause-transact-sql.md)句をストアド プロシージャを実行できるセキュリティ コンテキストを指定します。 例では、オプションで`CALLER`プロシージャを呼び出したユーザーのコンテキストで実行されることを指定します。 指定できるその他のオプションは、SELF、OWNER、および*user_name*です。  
  
 以下に関数呼び出しを示します。 注意して`DATEFIRST`に設定されている`1`です。  
  
```sql
CREATE FUNCTION dbo.ISOweek (@DATE datetime)  
RETURNS int  
WITH EXECUTE AS CALLER  
AS  
BEGIN  
     DECLARE @ISOweek int;  
     SET @ISOweek= DATEPART(wk,@DATE)+1  
          -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104');  
--Special cases: Jan 1-3 may belong to the previous year  
     IF (@ISOweek=0)   
          SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1   
               AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1;  
--Special case: Dec 29-31 may belong to the next year  
     IF ((DATEPART(mm,@DATE)=12) AND   
          ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28))  
          SET @ISOweek=1;  
     RETURN(@ISOweek);  
END;  
GO  
SET DATEFIRST 1;  
SELECT dbo.ISOweek(CONVERT(DATETIME,'12/26/2004',101)) AS 'ISO Week';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
``` 
ISO Week  
----------------  
52  
```  
  
### <a name="b-creating-an-inline-table-valued-function"></a>B. インライン テーブル値関数を作成する  
 次の例は、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベース内のインライン テーブル値関数を返します。 次の 3 つの列を返します`ProductID`、`Name`店舗別合計を年度累計の集計`YTD Total`ストアに販売された製品ごとです。  
  
```sql  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
GO  
```

 関数を呼び出すには、次のクエリを実行します。    

```sql  
SELECT * FROM Sales.ufn_SalesByStore (602);  
```  
  
### <a name="c-creating-a-multi-statement-table-valued-function"></a>C. 複数ステートメントのテーブル値関数を作成する  
 次の例は、テーブル値関数を作成`fn_FindReports(InEmpID)`では、AdventureWorks2012 データベース。 有効な従業員 ID をこの関数に指定すると、その従業員に対して直接または間接の報告関係にあるすべての従業員に対応した表が返されます。 この関数は、再帰共通テーブル式 (CTE) を使用して、従業員の階層リストを生成します。 再帰 Cte の詳細については、次を参照してください。[で common_table_expression と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
```sql  
CREATE FUNCTION dbo.ufn_FindReports (@InEmpID INTEGER)  
RETURNS @retFindReports TABLE   
(  
    EmployeeID int primary key NOT NULL,  
    FirstName nvarchar(255) NOT NULL,  
    LastName nvarchar(255) NOT NULL,  
    JobTitle nvarchar(50) NOT NULL,  
    RecursionLevel int NOT NULL  
)  
--Returns a result set that lists all the employees who report to the   
--specific employee directly or indirectly.*/  
AS  
BEGIN  
WITH EMP_cte(EmployeeID, OrganizationNode, FirstName, LastName, JobTitle, RecursionLevel) -- CTE name and columns  
    AS (  
        -- Get the initial list of Employees for Manager n
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, 0   
        FROM HumanResources.Employee e   
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        WHERE e.BusinessEntityID = @InEmpID  
        UNION ALL  
        -- Join recursive member to anchor
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, RecursionLevel + 1   
        FROM HumanResources.Employee e   
            INNER JOIN EMP_cte  
            ON e.OrganizationNode.GetAncestor(1) = EMP_cte.OrganizationNode  
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        )  
-- copy the required columns to the result of the function   
   INSERT @retFindReports  
   SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
   FROM EMP_cte   
   RETURN  
END;  
GO  
-- Example invocation  
SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
FROM dbo.ufn_FindReports(1);   
  
GO  
```  
  
### <a name="d-creating-a-clr-function"></a>D. CLR 関数を作成する  
 例では、CLR 関数を作成する`len_s`です。 関数が作成される前に、アセンブリ`SurrogateStringFunction.dll`がローカル データベースに登録します。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```sql  
DECLARE @SamplesPath nvarchar(1024);  
-- You may have to modify the value of this variable if you have  
-- installed the sample in a location other than the default location.  
SELECT @SamplesPath = REPLACE(physical_name, 'Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\master.mdf', 
                                              'Microsoft SQL Server\130\Samples\Engine\Programmability\CLR\')   
    FROM master.sys.database_files   
    WHERE name = 'master';  
  
CREATE ASSEMBLY [SurrogateStringFunction]  
FROM @SamplesPath + 'StringManipulate\CS\StringManipulate\bin\debug\SurrogateStringFunction.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
GO  
  
CREATE FUNCTION [dbo].[len_s] (@str nvarchar(4000))  
RETURNS bigint  
AS EXTERNAL NAME [SurrogateStringFunction].[Microsoft.Samples.SqlServer.SurrogateStringFunction].[LenS];  
GO  
```  
  
 CLR テーブル値関数を作成する方法の例は、次を参照してください。 [clr table-valued 関数](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-table-valued-functions.md)です。  
  
### <a name="e-displaying-the-definition-of-includetsqlincludestsql-mdmd-user-defined-functions"></a>E. 定義を表示する[!INCLUDE[tsql](../../includes/tsql-md.md)]ユーザー定義関数  
  
```sql  
SELECT definition, type   
FROM sys.sql_modules AS m  
JOIN sys.objects AS o ON m.object_id = o.object_id   
    AND type IN ('FN', 'IF', 'TF');  
GO  
```  
  
 ENCRYPTION オプションを使用して作成した関数の定義は、sys.sql_modules で表示することができません。ただし、暗号化された関数に関するその他の情報は表示されます。  
  
## <a name="see-also"></a>参照  
 [ALTER FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-function-transact-sql.md)   
 [DROP FUNCTION &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-function-transact-sql.md)   
 [OBJECTPROPERTYEX &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/objectpropertyex-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [CLR ユーザー定義関数](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [セキュリティ ポリシー &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-security-policy-transact-sql.md)  
  
 

