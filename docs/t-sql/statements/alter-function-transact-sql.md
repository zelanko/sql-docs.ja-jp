---
title: "ALTER 関数 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_FUNCTION_TSQL
- ALTER FUNCTION
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER FUNCTION statement
- modifying functions
- functions [SQL Server], modifying
ms.assetid: 89f066ee-05ac-4439-ab04-d8c3d5911179
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4b1008715d9cfd3e48945d0651f454253bc4e4bc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="alter-function-transact-sql"></a>ALTER FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  既存の変更[!INCLUDE[tsql](../../includes/tsql-md.md)]または CLR 関数をアクセス許可を変更することがなく、CREATE FUNCTION ステートメントを実行して作成されたと影響を与えず、従属する関数、ストアド プロシージャ、またはトリガー。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Transact-SQL Scalar Function Syntax    
ALTER FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ][ type_schema_name. ] parameter_data_type   
    [ = default ] }   
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
ALTER FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
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
-- Transact-SQL Multistatement Table-valued Function Syntax
ALTER FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
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
-- CLR Scalar and Table-Valued Function Syntax
ALTER FUNCTION [ schema_name. ] function_name   
( { @parameter_name [AS] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
)  
RETURNS { return_data_type | TABLE <clr_table_type_definition> }  
    [ WITH <clr_function_option> [ ,...n ] ]  
    [ AS ] EXTERNAL NAME <method_specifier>  
[ ; ]  
```
  
```
-- CLR Function Clauses
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
-- Syntax for In-Memory OLTP: Natively compiled, scalar user-defined function  
ALTER FUNCTION [ schema_name. ] function_name    
 ( [ { @parameter_name [ AS ][ type_schema_name. ] parameter_data_type   
    [ NULL | NOT NULL ] [ = default ] }   
    [ ,...n ]   
  ]   
)   
RETURNS return_data_type  
    [ WITH <function_option> [ ,...n ] ]   
    [ AS ]   
    BEGIN ATOMIC WITH (set_option [ ,... n ])  
        function_body   
        RETURN scalar_expression  
    END  
    
<function_option>::=   
{ |  NATIVE_COMPILATION   
  |  SCHEMABINDING   
  | [ EXECUTE_AS_Clause ]   
  | [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]   
}  
```   
  
## <a name="arguments"></a>引数  
 *schema_name*  
 ユーザー定義関数が属するスキーマの名前を指定します。  
  
 *function_name*  
 変更するユーザー定義関数です。  
  
> [!NOTE]  
>  パラメーターを指定しない場合でも、関数名の後にはかっこが必要です。  
  
 **@***parameter_name*  
 ユーザー定義関数内のパラメーターです。 1 つ以上のパラメーターを宣言できます。  
  
 1 つの関数では、最高 2,100 個のパラメーターを使用できます。 宜言した各パラメーターの値は、関数の実行時に、ユーザーが指定する必要があります (そのパラメーターの既定値が定義されていない場合)。  
  
 使用して、パラメーター名を指定するアット マーク (**@**) 最初の文字として。 パラメーター名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 パラメーターは関数に対してローカルです。同じパラメーター名を他の関数で使用できます。 パラメーターは定数の代わりとしてのみ使用できます。パラメーターは、テーブル名、列名、またはその他のデータベース オブジェクト名の代わりに使用することはできません。  
  
> [!NOTE]  
>  ストアド プロシージャでパラメーターを引き渡す場合や、バッチ ステートメントで変数を宣言または設定する場合、またはユーザー定義関数においては、ANSI_WARNINGS は無視されます。 たとえば、として変数が定義されている**char (3)**とし、次の 3 つの文字を超える値に設定、データは切り捨てに定義されているサイズと、INSERT または UPDATE ステートメントは成功します。  
  
 [ *type_schema_name です。* *parameter_data_type*  
 パラメーターのデータ型です。このデータ型が属するスキーマを指定することもできます。 [!INCLUDE[tsql](../../includes/tsql-md.md)]関数、CLR ユーザー定義型を含めた、すべてのデータ型は除く許可、**タイムスタンプ**データ型。 CLR 関数では、CLR ユーザー定義型を含めた、すべてのデータ型は除く許可**テキスト**、 **ntext**、**イメージ**、および**タイムスタンプ**データ型。 スカラー型**カーソル**と**テーブル**でパラメーターのデータ型として指定することはできません[!INCLUDE[tsql](../../includes/tsql-md.md)]関数と CLR 関数。  
  
 場合*type_schema_name*が指定されていない、[!INCLUDE[ssDEversion2005](../../includes/ssdeversion2005-md.md)]は検索、 *parameter_data_type*次の順序で。  
  
-   SQL Server システム データ型の名前を含むスキーマ  
  
-   現在のデータベースにおける現在のユーザーの既定のスキーマ  
  
-   現在のデータベースの **dbo** スキーマ。  
  
 [  **=** *既定*]  
 パラメーターの既定値です。 場合、*既定*値は、そのパラメーターの値を指定せず、関数を実行することができます。  
  
> [!NOTE]  
>  除く、CLR 関数のパラメーターの既定値を指定することができます**varchar (max)**と**varbinary (max)**データ型。  
  
 関数のパラメーターが既定値を持つ、既定値を取得する関数を呼び出すときに DEFAULT キーワードを指定する必要があります。 この動作は、ストアド プロシージャで既定値を持つパラメーターを使用する場合とは異なります。ストアド プロシージャの場合は、パラメーターを省略すると既定値が暗黙的に使用されます。  
  
 *return_data_type*  
 スカラー ユーザー定義関数の戻り値です。 [!INCLUDE[tsql](../../includes/tsql-md.md)]関数、CLR ユーザー定義型を含めた、すべてのデータ型は除く許可、**タイムスタンプ**データ型。 CLR 関数では、CLR ユーザー定義型を含めた、すべてのデータ型は除く許可**テキスト**、 **ntext**、**イメージ**、および**タイムスタンプ**データ型。 スカラー型**カーソル**と**テーブル**両方で戻り値のデータ型として指定することはできません[!INCLUDE[tsql](../../includes/tsql-md.md)]関数と CLR 関数。  
  
 *function_body*  
 総合して副作用 (テーブルの変更など) がない一連の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが、関数の値を定義することを指定します。 *function_body*はスカラー関数および複数ステートメント テーブル値関数でのみ使用します。  
  
 スカラー関数は、 *function_body*一連の[!INCLUDE[tsql](../../includes/tsql-md.md)]スカラー値にまとめて評価されるステートメントです。  
  
 複数ステートメント テーブル値関数の*function_body*一連の[!INCLUDE[tsql](../../includes/tsql-md.md)]テーブルを作成するステートメントが変数を返します。  
  
 *scalar_expression*  
 スカラー関数がスカラー値を返すように指定します。  
  
 TABLE  
 テーブル値関数の戻り値がテーブルになるように指定します。 定数のみと **@**  *local_variables*テーブル値関数に渡すことができます。  
  
 インライン テーブル値関数の TABLE 戻り値は、単一の SELECT ステートメントを使用して定義します。 インライン関数には、関連付けられている戻り変数はありません。  
  
 複数ステートメント テーブル値関数の **@**  *return_variable*は、テーブル変数を格納および関数の値として返される行を蓄積するために使用します。 **@***return_variable*に対してのみ指定できます[!INCLUDE[tsql](../../includes/tsql-md.md)]関数し、CLR ではなく機能します。  
  
 *選択 stmt*  
 インライン テーブル値関数の戻り値を定義する単一の SELECT ステートメントです。  
  
 外部名\<method_specifier >*assembly_name.class_name*.*メソッド名が*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 関数にバインドするアセンブリのメソッドを指定します。 *アセンブリ名*で既存のアセンブリに一致する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の可視性を持つ現在のデータベースにします。 *class_name*は有効な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子、アセンブリ内のクラスとして存在する必要があります。 クラスにピリオドを使用する名前空間で修飾された名前 (**.**) 名前空間の部分を分割する、クラス名を角かっこで区切る必要があります (**:operator[]**) または引用符 (**""**). *メソッド名が*は有効な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子、指定したクラスの静的メソッドとして存在する必要があります。  
  
> [!NOTE]  
>  既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は CLR コードを実行できません。 作成、変更、および共通言語ランタイム モジュール; を参照するデータベース オブジェクトを削除することができます。ただし、これらの参照を実行することはできません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]有効にするまで、 [clr enabled オプション](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)です。 オプションを有効にするには、 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)です。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
 *\<*table_type_definition*>***(** { \<column_definition > \<column_constraint > |\<computed_column_definition >}[ \<table_constraint >] [ **、**.*n* ]**)**  
 テーブルのデータ型を定義、[!INCLUDE[tsql](../../includes/tsql-md.md)]関数。 テーブルの定義には、列の定義、および列またはテーブルの制約が含まれます。  
  
\<clr_table_type_definition > **(** { *column_name**data_type* } [ **、**. *n*  ] **)** **対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([いくつかのプレビュー地域](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag))。  
  
 CLR 関数のテーブル データ型を定義します。 テーブルの定義には、列名およびデータ型のみが含まれます。  
  
 NULL|NULL でないです。  
 ネイティブ コンパイル、スカラー ユーザー定義関数でのみサポートされます。 詳細については、次を参照してください。 [scalar user-defined 関数は、インメモリ OLTP](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md)です。  
  
 NATIVE_COMPILATION  
 ユーザー定義の関数をネイティブでコンパイルするかどうかを示します。 この引数は、ネイティブ コンパイル、スカラー ユーザー定義関数に必要です。  
  
 NATIVE_COMPILATION 引数が必要、関数を変更してのみ使用できます、NATIVE_COMPILATION 引数を持つ関数が作成された場合です。  
  
 アトミックの開始します。  
 ユーザー定義スカラー関数、および、必要なはネイティブでコンパイルすると、のみサポートされます。 詳細については、「 [Atomic Blocks](../../relational-databases/in-memory-oltp/atomic-blocks-in-native-procedures.md)」を参照してください。  
  
 SCHEMABINDING  
 SCHEMABINDING の引数は、ネイティブ コンパイル、スカラー ユーザー定義関数に必要です。  
  
 **\<function_option >:: = と\<clr_function_option >:: =**  
  
 関数に以下のオプションを 1 つ以上指定します。  
  
 ENCRYPTION  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ALTER FUNCTION ステートメントのテキストを含むカタログ ビューの列を、[!INCLUDE[ssDE](../../includes/ssde-md.md)]が暗号化することを示します。 暗号化を使用すると、関数がの一部としてパブリッシュできなく[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レプリケーション。 CLR 関数には ENCRYPTION を指定できません。  
  
 SCHEMABINDING  
 参照するデータベース オブジェクトに対して、その関数がバインドされるように指定します。 このバインドによって、他のスキーマ バインド オブジェクトがその関数を参照している場合に関数が変更されるのを防ぐことができます。  
  
 関数からその参照先のオブジェクトへのバインドは、次のいずれかの操作が行われた場合にのみ削除されます。  
  
-   関数を削除した場合。  
  
-   関数を、SCHEMABINDING オプションを指定せずに ALTER ステートメントを使用して変更した場合。  
  
関数がスキーマ バインドをする前に満たす必要がある条件の一覧は、次を参照してください。 [CREATE FUNCTION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-function-transact-sql.md).  
  
 RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT  
 指定します、 **OnNULLCall**スカラー値関数の属性です。 指定しない場合は、既定で CALLED ON NULL INPUT が暗黙的に使用されます。 つまり、NULL が引数として渡された場合でも、関数本体が実行されます。  
  
 CLR 関数で RETURNS NULL ON NULL INPUT が指定されている場合ことを示して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が受け取った引数のいずれかの NULL の場合、関数の本体を呼び出すことがなく、NULL を返すことができます。 メソッドで指定される場合\<method_specifier > 既に CALLED ON NULL INPUT を示す RETURNS NULL ON NULL INPUT、ただし、ALTER FUNCTION ステートメント、ALTER FUNCTION ステートメントの優先を示すカスタム属性があります。 **OnNULLCall** CLR テーブル値関数の属性を指定することはできません。  
  
 EXECUTE AS 句  
 ユーザー定義関数が実行されるセキュリティ コンテキストを指定します。 これにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が、関数で参照されているデータベース オブジェクトに対する権限を検証する際に使用するユーザー アカウントを制御できます。  
  
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
 列の照合順序を指定します。 照合順序を指定しない場合、データベースの既定の照合順序が列に割り当てられます。 照合順序名には、Windows 照合順序名または SQL 照合順序名を指定できます。 一覧と詳細については、「 [Windows 照合順序名 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/windows-collation-name-transact-sql.md)と[SQL Server 照合順序名 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 のみの列の照合順序を変更するのには、COLLATE 句を使用できます、 **char**、 **varchar**、 **nchar**、および**nvarchar**データ型。  
  
 CLR テーブル値関数には COLLATE を指定できません。  
  
 ROWGUIDCOL  
 新しい列が行グローバル一意識別子列であることを指定します。 1 つだけ**uniqueidentifier** ROWGUIDCOL 列として 1 つのテーブルの列を指定することができます。 ROWGUIDCOL プロパティにのみ割り当てることができます、 **uniqueidentifier**列です。  
  
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
  
 PRIMARY KEY インデックスまたは UNIQUE インデックスのインデックス オプションを指定します。 インデックス オプションの詳細については、次を参照してください。 [CREATE INDEX &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-index-transact-sql.md).  
  
 PAD_INDEX = { ON | OFF }  
 インデックスの埋め込みを指定します。 既定値は OFF です。  
  
 FILLFACTOR = *fillfactor*  
 どの程度を示すパーセンテージを指定します、[!INCLUDE[ssDE](../../includes/ssde-md.md)]インデックス作成時に各インデックス ページのリーフ レベルを作成または変更する必要があります。 *fillfactor* 1 から 100 までの整数値にする必要があります。 既定値は 0 です。  
  
 IGNORE_DUP_KEY = { ON | OFF }  
 挿入操作で、一意のインデックスに重複するキー値を挿入しようとした場合のエラー応答を指定します。 IGNORE_DUP_KEY オプションは、インデックスが作成または再構築された後の挿入操作のみに適用されます。 既定値は OFF です。  
  
 STATISTICS_NORECOMPUTE = { ON | OFF }  
 分布統計を再計算するかどうかを指定します。 既定値は OFF です。  
  
 ALLOW_ROW_LOCKS = { ON | OFF }  
 行ロックを許可するかどうかを指定します。 既定値は ON です。  
  
 ALLOW_PAGE_LOCKS = { ON | OFF }  
 ページ ロックを許可するかどうかを指定します。 既定値は ON です。  
  
## <a name="remarks"></a>解説  
 ALTER FUNCTION を使用してスカラー値関数をテーブル値関数に変更したり、その逆の変更を行ったりすることはできません。 また、ALTER FUNCTION を使用してインライン関数を複数ステートメント関数に変更したり、その逆の変更を行ったりすることもできません。 変更する ALTER FUNCTION を使用することはできません、[!INCLUDE[tsql](../../includes/tsql-md.md)]関数、CLR 関数またはその逆にします。  
  
 定義では、次の Service Broker ステートメントを含めることができません、[!INCLUDE[tsql](../../includes/tsql-md.md)]ユーザー定義関数。  
  
-   BEGIN DIALOG CONVERSATION  
-   END CONVERSATION  
-   GET CONVERSATION GROUP  
-   MOVE CONVERSATION  
-   RECEIVE  
-   SEND  
  
## <a name="permissions"></a>Permissions  
 関数またはスキーマに対する ALTER 権限が必要です。 関数でユーザー定義型が指定されている場合は、その型に対する EXECUTE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)   
 [DROP FUNCTION &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-function-transact-sql.md)   
 [パブリケーション データベースでのスキーマの変更](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
