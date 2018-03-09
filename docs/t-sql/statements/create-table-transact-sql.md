---
title: "テーブル (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILESTREAM_TSQL
- TABLE
- CREATE_TABLE_TSQL
- CREATE TABLE
- FILESTREAM
- TABLE_TSQL
- FILESTREAM_ON
- FILESTREAM_ON_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CHECK constraints
- global temporary tables [SQL Server]
- local temporary tables [SQL Server]
- size [SQL Server], tables
- UNIQUE constraints [SQL Server], creating
- constraints [SQL Server], columns
- maximum number of indexes per table
- number of tables per database
- number of indexes per table
- table creation [SQL Server], CREATE TABLE
- temporary tables [SQL Server], creating
- table size [SQL Server]
- nullability [SQL Server]
- partitioned tables [SQL Server], creating
- DEFAULT definition
- null values [SQL Server], columns
- number of rows per table
- maximum number of columns per table
- FOREIGN KEY constraints, creating
- PRIMARY KEY constraints
- number of bytes per row
- CREATE TABLE statement
- number of columns per table
- maximum number of bytes per row
ms.assetid: 1e068443-b9ea-486a-804f-ce7b6e048e8b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: ad0dd6ed4d8006a596ac05c35730a8132368d5df
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="create-table-transact-sql"></a>CREATE TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  新しいテーブルを作成[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
> [!NOTE]   
>  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]構文を参照してください[CREATE TABLE (Azure SQL Data Warehouse)](../../t-sql/statements/create-table-azure-sql-data-warehouse.md)です。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
--Simple CREATE TABLE Syntax (common if not using options)  
CREATE TABLE   
    [ database_name . [ schema_name ] . | schema_name . ] table_name   
    ( { <column_definition> } [ ,...n ] )   
[ ; ]  
```  
  
## <a name="syntax"></a>構文  
  
```  
--Disk-Based CREATE TABLE Syntax  
CREATE TABLE   
    [ database_name . [ schema_name ] . | schema_name . ] table_name   
    [ AS FileTable ]  
    ( {   <column_definition>   
        | <computed_column_definition>    
        | <column_set_definition>   
        | [ <table_constraint> ]   
        | [ <table_index> ] }  
          [ ,...n ]    
          [ PERIOD FOR SYSTEM_TIME ( system_start_time_column_name   
             , system_end_time_column_name ) ]  
      )  
    [ ON { partition_scheme_name ( partition_column_name )   
           | filegroup   
           | "default" } ]   
    [ TEXTIMAGE_ON { filegroup | "default" } ]   
    [ FILESTREAM_ON { partition_scheme_name   
           | filegroup   
           | "default" } ]  
    [ WITH ( <table_option> [ ,...n ] ) ]  
[ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ FILESTREAM ]  
    [ COLLATE collation_name ]   
    [ SPARSE ]  
    [ MASKED WITH ( FUNCTION = ' mask_function ') ]  
    [ CONSTRAINT constraint_name [ DEFAULT constant_expression ] ]   
    [ IDENTITY [ ( seed,increment ) ]  
    [ NOT FOR REPLICATION ]   
    [ GENERATED ALWAYS AS ROW { START | END } [ HIDDEN ] ]   
    [ NULL | NOT NULL ]  
    [ ROWGUIDCOL ]  
    [ ENCRYPTED WITH   
        ( COLUMN_ENCRYPTION_KEY = key_name ,  
          ENCRYPTION_TYPE = { DETERMINISTIC | RANDOMIZED } ,   
          ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'  
        ) ]  
    [ <column_constraint> [ ...n ] ]   
    [ <column_index> ]  
  
<data type> ::=   
[ type_schema_name . ] type_name   
    [ ( precision [ , scale ] | max |   
        [ { CONTENT | DOCUMENT } ] xml_schema_collection ) ]   
  
<column_constraint> ::=   
[ CONSTRAINT constraint_name ]   
{     { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [   
            WITH FILLFACTOR = fillfactor    
          | WITH ( < index_option > [ , ...n ] )   
        ]   
        [ ON { partition_scheme_name ( partition_column_name )   
            | filegroup | "default" } ]  
  
  | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
  
  | CHECK [ NOT FOR REPLICATION ] ( logical_expression )   
}   
  
<column_index> ::=   
 INDEX index_name [ CLUSTERED | NONCLUSTERED ]  
    [ WITH ( <index_option> [ ,... n ] ) ]  
    [ ON { partition_scheme_name (column_name )   
         | filegroup_name  
         | default   
         }  
    ]   
    [ FILESTREAM_ON { filestream_filegroup_name | partition_scheme_name | "NULL" } ]  
  
<computed_column_definition> ::=  
column_name AS computed_column_expression   
[ PERSISTED [ NOT NULL ] ]  
[   
    [ CONSTRAINT constraint_name ]  
    { PRIMARY KEY | UNIQUE }  
        [ CLUSTERED | NONCLUSTERED ]  
        [   
            WITH FILLFACTOR = fillfactor   
          | WITH ( <index_option> [ , ...n ] )  
        ]  
        [ ON { partition_scheme_name ( partition_column_name )   
        | filegroup | "default" } ]  
  
    | [ FOREIGN KEY ]   
        REFERENCES referenced_table_name [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE } ]   
        [ ON UPDATE { NO ACTION } ]   
        [ NOT FOR REPLICATION ]   
  
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )   
]   
  
<column_set_definition> ::=  
column_set_name XML COLUMN_SET FOR ALL_SPARSE_COLUMNS  
  
< table_constraint > ::=  
[ CONSTRAINT constraint_name ]   
{   
    { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        (column [ ASC | DESC ] [ ,...n ] )   
        [   
            WITH FILLFACTOR = fillfactor   
           |WITH ( <index_option> [ , ...n ] )   
        ]  
        [ ON { partition_scheme_name (partition_column_name)  
            | filegroup | "default" } ]   
    | FOREIGN KEY   
        ( column [ ,...n ] )   
        REFERENCES referenced_table_name [ ( ref_column [ ,...n ] ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )  
 

  
< table_index > ::=   
{  
    {  
      INDEX index_name [ CLUSTERED | NONCLUSTERED ]   
         (column_name [ ASC | DESC ] [ ,... n ] )   
    | INDEX index_name CLUSTERED COLUMNSTORE  
    | INDEX index_name [ NONCLUSTERED ] COLUMNSTORE (column_name [ ,... n ] )  
    }  
    [ WITH ( <index_option> [ ,... n ] ) ]   
    [ ON { partition_scheme_name (column_name )   
         | filegroup_name  
         | default   
         }  
    ]   
    [ FILESTREAM_ON { filestream_filegroup_name | partition_scheme_name | "NULL" } ]  
  
}   


<table_option> ::=  
{  
    [DATA_COMPRESSION = { NONE | ROW | PAGE }  
      [ ON PARTITIONS ( { <partition_number_expression> | <range> }   
      [ , ...n ] ) ]]  
    [ FILETABLE_DIRECTORY = <directory_name> ]   
    [ FILETABLE_COLLATE_FILENAME = { <collation_name> | database_default } ]  
    [ FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME = <constraint_name> ]  
    [ FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME = <constraint_name> ]  
    [ FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME = <constraint_name> ]  
    [ SYSTEM_VERSIONING = ON [ ( HISTORY_TABLE = schema_name . history_table_name  
        [, DATA_CONSISTENCY_CHECK = { ON | OFF } ] ) ] ]  
    [ REMOTE_DATA_ARCHIVE =   
      {   
          ON [ ( <table_stretch_options> [,...n] ) ]  
        | OFF ( MIGRATION_STATE = PAUSED )   
      }   
    ]  
}  
  
<table_stretch_options> ::=  
{  
     [ FILTER_PREDICATE = { null | table_predicate_function } , ]  
       MIGRATION_STATE = { OUTBOUND | INBOUND | PAUSED }  
 }  
  
<index_option> ::=  
{   
    PAD_INDEX = { ON | OFF }   
  | FILLFACTOR = fillfactor   
  | IGNORE_DUP_KEY = { ON | OFF }   
  | STATISTICS_NORECOMPUTE = { ON | OFF }   
  | ALLOW_ROW_LOCKS = { ON | OFF}   
  | ALLOW_PAGE_LOCKS ={ ON | OFF}   
  | COMPRESSION_DELAY= {0 | delay [Minutes]}  
  | DATA_COMPRESSION = { NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
       [ ON PARTITIONS ( { <partition_number_expression> | <range> }   
       [ , ...n ] ) ]  
}  
<range> ::=   
<partition_number_expression> TO <partition_number_expression>  
```  
  
```  
  
      --Memory optimized CREATE TABLE Syntax  
CREATE TABLE  
    [database_name . [schema_name ] . | schema_name . ] table_name  
    ( { <column_definition>  
    | [ <table_constraint> ] [ ,... n ]  
    | [ <table_index> ]  
      [ ,... n ] }   
      [ PERIOD FOR SYSTEM_TIME ( system_start_time_column_name   
        , system_end_time_column_name ) ]  
)  
    [ WITH ( <table_option> [ ,... n ] ) ]  
 [ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ COLLATE collation_name ]  
    [ GENERATED ALWAYS AS ROW { START | END } [ HIDDEN ] ]   
    [ NULL | NOT NULL ]  
[  
    [ CONSTRAINT constraint_name ] DEFAULT memory_optimized_constant_expression ]  
    | [ IDENTITY [ ( 1, 1 ) ]  
]  
    [ <column_constraint> ]  
    [ <column_index> ]  
  
<data type> ::=  
 [type_schema_name . ] type_name [ (precision [ , scale ]) ]  
  
<column_constraint> ::=  
 [ CONSTRAINT constraint_name ]  
{   
  { PRIMARY KEY | UNIQUE }    
      {   NONCLUSTERED   
        | NONCLUSTERED HASH WITH (BUCKET_COUNT = bucket_count)   
      }   
  | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name [ ( ref_column ) ]   
  | CHECK ( logical_expression )   
}  
  
< table_constraint > ::=  
 [ CONSTRAINT constraint_name ]  
{    
   { PRIMARY KEY | UNIQUE }  
     {   
       NONCLUSTERED (column [ ASC | DESC ] [ ,... n ])  
       | NONCLUSTERED HASH (column [ ,... n ] ) WITH ( BUCKET_COUNT = bucket_count )   
                    }   
    | FOREIGN KEY   
        ( column [ ,...n ] )   
        REFERENCES referenced_table_name [ ( ref_column [ ,...n ] ) ]   
    | CHECK ( logical_expression )   
}  
  
<column_index> ::=  
  INDEX index_name  
{ [ NONCLUSTERED ] | [ NONCLUSTERED ] HASH WITH (BUCKET_COUNT = bucket_count)  }  
  
<table_index> ::=  
  INDEX index_name  
{   [ NONCLUSTERED ] HASH (column [ ,... n ] ) WITH (BUCKET_COUNT = bucket_count)   
  | [ NONCLUSTERED ] (column [ ASC | DESC ] [ ,... n ] )   
      [ ON filegroup_name | default ]  
  | CLUSTERED COLUMNSTORE [WITH ( COMPRESSION_DELAY = {0 | delay [Minutes]})]  
      [ ON filegroup_name | default ]  
  
}  
  
<table_option> ::=  
{  
    MEMORY_OPTIMIZED = ON   
  | DURABILITY = {SCHEMA_ONLY | SCHEMA_AND_DATA}  
  | SYSTEM_VERSIONING = ON [ ( HISTORY_TABLE = schema_name . history_table_name  
        [, DATA_CONSISTENCY_CHECK = { ON | OFF } ] ) ]   
  
}  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 テーブルが作成されたデータベースの名前を指定します。 *database_name*既存のデータベースの名前を指定する必要があります。 指定しない場合、 *database_name*既定値は、現在のデータベースです。 現在の接続のログインがで指定されたデータベース内の既存のユーザー ID を関連付ける必要がある*database_name*、そのユーザー ID には、CREATE TABLE アクセス許可が必要とします。  
  
 *schema_name*  
 新しいテーブルが所属するスキーマの名前です。  
  
 *table_name*  
 新しいテーブルの名前です。 テーブル名の規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 *table_name*できるローカル一時テーブル名を除いて、128 文字の最大値 (名前は、1 つの番号記号で始まります (#)) 116 文字を超えることはできません。  
  
 AS FileTable 
 
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 
 
 新しいテーブルを FileTable として作成します。 FileTable には固定スキーマがあるため、列は指定しません。 Filetable の詳細については、次を参照してください。 [Filetable &#40;です。SQL Server &#41;](../../relational-databases/blob/filetables-sql-server.md).  
  
 *column_name*  
 *computed_column_expression*  
 計算列の値を定義する式です。 計算列は、PERSISTED とマークされていない限り、テーブルに物理的に保存されない仮想列です。 列は、同じテーブル内の他の列を使用する式から計算されます。 たとえば、計算列は、定義を持つことができます:**コスト**AS**価格** \* **qty**です。式には、非計算列の名前、定数、関数、および変数のほか、これらを 1 つ以上の演算子によって結合した組み合わせを使用できます。 サブクエリを式にすることはできません。また、別名データ型を含むこともできません。  
  
 計算列は、選択リスト、WHERE 句、ORDER BY 句、その他標準式が使用できる任意の位置で使用できます。ただし、次の場合は除きます。  
  
-   FOREIGN KEY 制約または CHECK 制約で使用される計算列は、PERSISTED に設定する必要があります。  
  
-   計算列できますまたは任意の PRIMARY KEY または UNIQUE 制約の一部として、インデックスのキー列として、計算列の値が決定的な式によって定義されているし、結果のデータ型がインデックス列で許可されている場合。  
  
     たとえば、テーブルに整数の列**、**と**b**、計算列**+ b**が、計算列、インデックスが**+ DATEPART (dd, GETDATE())**後続の呼び出しで値を変更することがありますのでインデックスを作成できません。  
  
-   計算列を INSERT ステートメントまたは UPDATE ステートメントの対象にすることはできません。  
  
> [!NOTE]  
>  テーブル内の個々の行によって、計算列に関係する列の値が異なることがあるため、計算列の値はすべての行について同じにならないことがあります。  
  
 計算列で NULL 値を許容するかどうかは、使用されている式に基づいて[!INCLUDE[ssDE](../../includes/ssde-md.md)]によって自動的に決定されます。 NULL 値を許容しない列のみの場合でも、ほとんどの式の結果は NULL 値を許容すると見なされます。これは、アンダーフローやオーバーフローによって結果が NULL 値になる場合があるためです。 COLUMNPROPERTY 関数で使用して、 **AllowsNull**テーブル内のすべての計算列の null 値許容属性を調査するプロパティです。 値が許容される式は、ISNULL に指定することで許容しない 1 つに変換できる、 *check_expression*定数、null 以外の値を定数がここでは、NULL の結果の代わりに使用します。 計算列では、共通言語ランタイム (CLR) のユーザー定義型の式に基づいて、その型に対する REFERENCES 権限が必要です。  
  
 PERSISTED  
 指定する、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]は物理的に、テーブルに計算値を格納し、計算列が依存するその他の列が更新されたときに、値を更新します。 計算列に PERSISTED とマークすることで、計算列に対し、決定的ではあるが正確ではないインデックスを作成することができます。 詳細については、「 [計算列のインデックス](../../relational-databases/indexes/indexes-on-computed-columns.md)」を参照してください。 パーティション テーブルのパーティション分割列として使用される計算列は、明示的に PERSISTED に設定する必要があります。 *computed_column_expression* PERSISTED が指定されている場合は決定的である必要があります。  
  
 ON { *partition_scheme* | *filegroup* | **"**既定**"** }  

 テーブルが格納されるパーティション構成またはファイル グループを指定します。 場合*partition_scheme*指定すると、パーティションが 1 つのセットに格納されているパーティション分割されたテーブルを指定するのには、テーブルまたはで多くのファイル グループが指定された*partition_scheme*です。 場合*filegroup*を指定すると、名前付きのファイル グループにテーブルを格納します。 ファイル グループはデータベース内に存在している必要があります。 場合**"**既定**"**が指定されているか、ON をまったく指定しない場合、テーブルは既定のファイル グループに格納します。 CREATE TABLE で指定したテーブルの格納方法を後から変更することはできません。  
  
 ON {*partition_scheme* | *filegroup* | **"**既定**"**} の主キーも指定します。制約または UNIQUE 制約。 これらの制約はインデックスを作成します。 場合*filegroup*を指定すると、名前付きのファイル グループにインデックスを格納します。 場合**"**既定**"**が指定されているか、インデックスがテーブルと同じファイル グループに格納されている ON をまったく指定しない場合。 PRIMARY KEY 制約または UNIQUE 制約がクラスター化インデックスを作成する場合、テーブルのデータ ページはインデックスと同じファイル グループに格納されます。 CLUSTERED が指定されているか、それ以外の場合の制約がクラスター化インデックスを作成し、 *partition_scheme*が指定されていることとは異なります、 *partition_scheme*または*ファイルグループ* 、テーブルの定義、またはその逆の制約の定義のみが優先され、もう一方は無視されます。  
  
> [!NOTE]  
>  ここでは、default はキーワードではありません。 既定のファイル グループの識別子を指定しのように区切る必要があります**"**既定**"**または ON **[**既定**]**です。 場合**"**既定**"**を指定すると、現在のセッションの QUOTED_IDENTIFIER オプションが ON をする必要があります。 これが既定の設定です。 詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
> [!NOTE]  
>  パーティション テーブルを作成した後、テーブルの LOCK_ESCALATION オプションを AUTO に設定することを検討してください。 テーブルではなくパーティション (HoBT) レベルにロックをエスカレートできるようにすることで、同時実行性が向上します。 詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)」を参照してください。  
  
 TEXTIMAGE_ON { *filegroup*| **"**既定**"** }  
 示します、**テキスト**、 **ntext**、**イメージ**、 **xml**、 **varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、および CLR ユーザー定義型の列 (geometry と geography を含む) が指定したファイル グループに格納します。  
  
 テーブル内に値の大きな列がない場合は、TEXTIMAGE_ON は指定できません。 場合は、TEXTIMAGE_ON を指定することはできません*partition_scheme*を指定します。 場合**"**既定**"**が指定されている値の大きな列が既定のファイル グループに格納されている TEXTIMAGE_ON をまったく指定しない場合またはします。 CREATE TABLE で指定した値の大きな列のデータの格納方法を、後から変更することはできません。  

> [!NOTE]  
> Varchar (max)、nvarchar (max)、varbinary (max)、xml および大きな UDT 値は、データ行に直接格納、8,000 バイトのと、値と同じ長さの上限に達するまでは、レコードを満たすことはできません。 ポインターが並べ替えられた値が、レコード内に収まらない場合行と残りの部分は、行外の LOB ストレージ領域に保存します。 既定値は 0 です。
TEXTIMAGE_ON のみ「LOB ストレージ領域」の場所を変更、データが行内に格納時に影響しません。 Large value types out sp_tableoption の行のオプションを使用すると、行外 LOB 値全体を格納できます。 


> [!NOTE]  
>  ここでは、default はキーワードではありません。 既定のファイル グループの識別子を指定し、TEXTIMAGE_ON ように区切る必要があります**"**既定**"**または TEXTIMAGE_ON **[**既定**]**. 場合**"**既定**"**を指定すると、現在のセッションの QUOTED_IDENTIFIER オプションが ON をする必要があります。 これが既定の設定です。 詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
 FILESTREAM_ON { *partition_scheme_name* | ファイル グループ |**"**既定**"** }**対象**:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 
 
 FILESTREAM データのファイル グループを指定します。  
  
 テーブルが FILESTREAM データを含んでおり、パーティション分割されている場合、FILESTREAM_ON 句を使用して、FILESTREAM ファイル グループのパーティション構成を指定する必要があります。 このパーティション構成では、テーブルのパーティション構成と同じパーティション関数とパーティション列を使用する必要があります。それ以外の場合は、エラーが発生します。  
  
 テーブルがパーティション分割されていない場合、FILESTREAM 列も分割できません。 テーブルの FILESTREAM データは、単一のファイル グループに格納する必要があります。 このファイル グループは、FILESTREAM_ON 句で指定します。  
  
 テーブルがパーティション分割されておらず、FILESTREAM_ON 句も指定されていない場合、DEFAULT プロパティが設定されている FILESTREAM ファイル グループが使用されます。 FILESTREAM ファイル グループがない場合は、エラーが発生します。  
  
-   ON や TEXTIMAGE_ON と同様に、FILESTREAM_ON の CREATE TABLE を使用して設定された値は、次の場合を除いて変更できません。  
  
-   A [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)ステートメント ヒープをクラスター化インデックスに変換します。 この場合は、異なる FILESTREAM ファイル グループ、パーティション構成、または NULL を指定できます。  
  
-   A [DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md)ステートメントがあるヒープにクラスター化インデックスを変換します。 この場合は、異なる FILESTREAM ファイル グループ、パーティション構成または**"**既定**"**を指定できます。  
  
 内のファイル グループ、`FILESTREAM_ON <filegroup>`句、またはパーティション構成で指定されている各 FILESTREAM ファイル グループには、ファイル グループに対して定義されている 1 つのファイルが必要です。 このファイルを使用して定義する必要があります、 [CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md)または[ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md)ステートメントです。 それ以外の場合、エラーが発生します。  
  
 関連する FILESTREAM のトピックを参照してください。[バイナリ ラージ オブジェクト &#40;です。Blob &#41;データ &#40;です。SQL Server &#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 [ *type_schema_name***です。** *type_name*  
 列のデータ型と、そのデータ型が所属するスキーマを指定します。 ディスク ベース テーブルの場合、データ型は次のいずれかです。  
  
-   システム データ型。  
  
-   基づく別名型、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム データ型。 別名データ型は、CREATE TYPE ステートメントで作成した後、テーブル定義で使用できます。 別名データ型用の NULL/NOT NULL 割り当ては、CREATE TABLE ステートメントの中で上書きできます。 ただし、長さ指定は変更できません。CREATE TABLE ステートメント中の別名データ型の長さは指定できません。  
  
-   CLR ユーザー定義型。 CLR ユーザー定義型をテーブル定義の中で使用するには、まず、CREATE TYPE ステートメントで CLR ユーザー定義型を作成する必要があります。 CLR ユーザー定義型の列を作成するには、その型に対する REFERENCES 権限が必要です。  
  
 場合*type_schema_name*が指定されていない、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]参照*type_name*次の順序で。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データ型  
  
-   現在のデータベースにおける現在のユーザーの既定のスキーマ  
  
-   現在のデータベースの **dbo** スキーマ。  
  
 メモリ最適化テーブルを参照してください。 [、インメモリ OLTP に対してサポートされるデータ型](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md)サポートされているシステムの種類の一覧についてはします。  
  
 *有効桁数 (precision)*  
 指定されるデータ型の有効桁数です。 有効桁数値の詳細については、次を参照してください。[有効桁数、小数点以下桁数、および長さ](../../t-sql/data-types/precision-scale-and-length-transact-sql.md)です。  
  
 *scale*  
 指定されるデータ型の小数点以下桁数です。 有効な小数点以下桁数値の詳細については、次を参照してください。[有効桁数、小数点以下桁数、および長さ](../../t-sql/data-types/precision-scale-and-length-transact-sql.md)です。  
  
 **max**  
 のみ適用され、 **varchar**、 **nvarchar**、および**varbinary** 2 を格納するためのデータ型 ^31 バイトの文字とバイナリ データ、および 2 ^30 バイトの Unicode データ。  
  
 CONTENT  
 指定の各インスタンス、 **xml**のデータ型の*column_name*複数のトップレベル要素を含めることができます。 コンテンツにのみ適用、 **xml**データ型し、する場合にのみ指定できます*xml_schema_collection*も指定されています。 指定しない場合は、CONTENT が既定の動作となります。  
  
 DOCUMENT  
 指定の各インスタンス、 **xml**のデータ型の*column_name* 1 つだけの最上位要素を含めることができます。 ドキュメントにのみ適用、 **xml**データ型し、する場合にのみ指定できます*xml_schema_collection*も指定されています。  
  
 *xml_schema_collection*  
 のみ適用され、 **xml**型と XML スキーマ コレクションの関連付けのデータ型。 入力する前に、 **xml**列をスキーマ、スキーマ必要があります最初に作成するデータベースを使用して[CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)です。  
  
 DEFAULT  
 挿入の際に明示的な値を指定しない場合に、列に入力される値を指定します。 として定義されているものを除くすべての列に DEFAULT 定義を適用できる**タイムスタンプ**、または IDENTITY プロパティを持つ。 暗黙的な変換をサポートする場合は、ユーザー定義型列の既定値を指定すると、 *constant_expression*ユーザー定義型です。 テーブルが削除されると、DEFAULT 定義も削除されます。 既定値として使用できるのは、文字列などの定数値、システム、ユーザー定義、CLR のいずれかのスカラー関数、または NULL だけです。 旧バージョンとの互換性を維持する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]制約の名前は、既定値に割り当てることができます。  
  
 *constant_expression*  
 列の既定値として使用される定数、NULL またはシステム関数です。  
  
 *memory_optimized_constant_expression*  
 列の既定値として使用できる定数、NULL、システム関数です。 ネイティブ コンパイル ストアド プロシージャでサポートされている必要があります。 ネイティブ コンパイル ストアド プロシージャでの組み込み関数の詳細については、次を参照してください。[ネイティブ コンパイル T-SQL モジュールでサポートされる機能](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md)します。  
  
 IDENTITY  
 新しい列が ID 列であることを指定します。 テーブルに新しい行が追加されたときに、[!INCLUDE[ssDE](../../includes/ssde-md.md)]列の一意な増分値を提供します。 Id 列は、テーブルの一意な行識別子として機能する PRIMARY KEY 制約で通常使用されます。 IDENTITY プロパティを割り当てることが**tinyint**、 **smallint**、 **int**、 **bigint**、 **decimal(p,0)**、または**numeric(p,0)**列です。 ID 列は 1 つのテーブルにつき 1 つだけ作成できます。 バインドされた既定値および DEFAULT 制約を ID 列と組み合わせて使用することはできません。 seed と increment の両方を指定するか、またはどちらも指定しません。 どちらも指定しないときの既定値は (1,1) です。  
  
 メモリ最適化テーブルで使用できる唯一の値の両方*シード*と*インクリメント*は 1 です。(1, 1) の既定値は、*シード*と*インクリメント*です。  
  
 *シード*  
 テーブルに読み込まれる最初の行に使用される値です。  
  
 *増分値*  
 前の行の id 値に加算される増分の値が読み込まれます。  
  
 NOT FOR REPLICATION  
 CREATE TABLE ステートメントでは、IDENTITY プロパティ、FOREIGN KEY 制約、CHECK 制約で NOT FOR REPLICATION 句を指定できます。 IDENTITY プロパティでこの句を指定すると、レプリケーション エージェントが挿入を行うときに ID 列の値が増加されません。 制約でこの句を指定すると、レプリケーション エージェントが挿入、更新、削除操作を行う際に制約が適用されません。  
  
 AS 行を常に生成された {開始 |終了 [非表示]} [NOT NULL]  
 **適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 指定した datetime2 列が、システムによって、レコードの有効期限の開始時刻またはレコードの有効期限の終了時刻のいずれかを記録する使用されることを指定します。 列を定義する必要があります、NOT NULL とします。 NULL として指定できるようにしようとすると、システムには、エラーがスローされます。 期間の列に対して NOT NULL を明示的に指定しない場合、システムは、列を既定で NOT NULL として定義します。 この引数を使用して、期間 FOR SYSTEM_TIME とで SYSTEM_VERSIONING と組み合わせて = テーブルにシステムのバージョン管理を有効にする引数にします。 詳細については、「 [Temporal Tables](../../relational-databases/tables/temporal-tables.md)」を参照してください。  
  
 1 つまたは両方の期間列でをマークすることができます**HIDDEN**フラグを暗黙的にこれらの列を非表示にするよう**選択\*FROM**  *`<table>`* しませんこれらの列の値を返します。 既定では、期間の列は非表示にします。 を使用するために非表示の列を時間的なテーブルを直接参照するすべてのクエリに明示的に含まする必要があります。 変更する、 **HIDDEN**既存の期間列の属性**期間**削除し、別の非表示フラグを再作成する必要があります。  
  
 `INDEX *index_name* [ CLUSTERED | NONCLUSTERED ] (*column_name* [ ASC | DESC ] [ ,... *n* ] )`  
     
**適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。

これを指定すると、テーブルにインデックスを作成します。 これには、クラスター化インデックスまたは非クラスター化インデックスを指定できます。 インデックスでは、この一覧を表示すると、列が含まれてし、昇順または降順で並べ替えます。  
  
 インデックス*index_name*クラスター化列ストア  
   
  
**適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。
  
 これを指定すると、テーブル全体をクラスター化列ストア インデックスを持つ列の形式で格納します。 これで、テーブル内のすべての列が常に含まれます。 アルファベットまたは数字の順序では、データが並べ替えられていないため、行の列ストア圧縮の利点は整理されています。  
  
 インデックス*index_name* [非クラスター化] 列ストア (*column_name* [,...*n* ] )  
   
  
**適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。
  
 これを指定すると、テーブルに非クラスター化列ストア インデックスを作成します。 行ストア ヒープまたはクラスター化インデックスは、基になるテーブルを指定でくか、またはクラスター化列ストア インデックスがあることができます。 すべての場合、テーブルに非クラスター化列ストア インデックスを作成すると、インデックス内の列のデータの 2 番目のコピーが格納されます。  
  
 非クラスター化列ストア インデックスが格納され、クラスター化列ストア インデックスとして管理します。 非クラスター化列ストア インデックスは、列が制限されることがあり、テーブルのセカンダリ インデックスとして存在しているために呼び出されます。  
  
 ON *partition_scheme_name***(***column_name***)**  
 ファイル グループが定義されているパーティション構成を指定します。このファイル グループは、パーティション インデックスのパーティションのマップ先となります。 パーティション構成はいずれかの操作を実行することによって、データベース内に存在する必要があります[CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md)または[ALTER PARTITION SCHEME](../../t-sql/statements/alter-partition-scheme-transact-sql.md)です。 *column_name*パーティション インデックスのパーティション分割される対象の列を指定します。 この列はデータ型、長さ、一致する必要があります関数および有効桁数の引数のパーティションを*partition_scheme_name*を使用しています。 *column_name*インデックス定義内の列に限定されません。 ときに、一意のインデックスをパーティション分割を除く、ベース テーブルの任意の列を指定することができます*column_name*一意のキーとして使用されるものの中から選択する必要があります。 この制限により、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では、単一のパーティション内だけでキー値の一意性を確認できます。  
  
> [!NOTE]  
>  一意でないクラスター化インデックスをパーティション分割するとき、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では既定により、まだ指定されていない場合、パーティション分割列がクラスター化インデックス キーのリストに追加されます。 非一意の非クラスター化インデックスをパーティション分割するとき、[!INCLUDE[ssDE](../../includes/ssde-md.md)]が指定されていない場合は、インデックスの非キー (付加) 列として、パーティション分割列を追加します。  
  
 場合*partition_scheme_name*または*filegroup*が指定されていないと、テーブルがパーティション分割、インデックスは基になるテーブルとして同じのパーティション分割列を使用して、同じパーティション構成に配置されます。  
  
> [!NOTE]  
>  XML インデックスにはパーティション構成を指定できません。 ベース テーブルがパーティション分割される場合、XML インデックスではテーブルと同じパーティション構造が使用されます。  
  
 詳細については、インデックスのパーティション分割の[Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md)です。  
  
 ON *filegroup_name*  
 指定したファイル グループに、指定したインデックスを作成します。 位置の指定がなく、テーブルまたはビューがパーティション分割されていない場合、インデックスには、基になるテーブルまたはビューと同じファイル グループが使用されます。 ファイル グループは既に存在している必要があります。  
  
 ON **"**既定**"**  
 既定のファイル グループに、指定したインデックスを作成します。  
  
 この文脈での default という語はキーワードではありません。 既定のファイル グループの識別子を指定しのように区切る必要があります**"**既定**"**または ON **[**既定**]**です。 "default" を指定する場合は、現在のセッションに対して QUOTED_IDENTIFIER オプションが ON である必要があります。 これが既定の設定です。 詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
 [FILESTREAM_ON { *filestream_filegroup_name* | *partition_scheme_name* |"NULL"}]  
   
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion.md)]

 クラスター化インデックスの作成時に、テーブルの FILESTREAM データの配置を指定します。 FILESTREAM_ON 句を使用すると、異なる FILESTREAM ファイル グループやパーティション構成に FILESTREAM データを移動できます。  
  
 *filestream_filegroup_name* FILESTREAM ファイル グループの名前を指定します。 ファイル グループの 1 つのファイルを使用して、ファイル グループに対して定義されている必要があります、 [CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md)または[ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md)ステートメントです。 それ以外の場合、エラーが発生します。  
  
 テーブルがパーティション分割されている場合、FILESTREAM_ON 句を使用して、テーブルのパーティション構成と同じパーティション関数とパーティション列を使用するように、FILESTREAM ファイル グループのパーティション構成を指定する必要があります。 それ以外の場合は、エラーが発生します。  
  
 テーブルがパーティション分割されていない場合、FILESTREAM 列も分割できません。 テーブルの FILESTREAM データは、FILESTREAM_ON 句で指定した単一のファイル グループに格納する必要があります。  
  
 クラスター化インデックスの作成で、テーブルに FILESTREAM 列が含まれていないときは、CREATE INDEX ステートメントに FILESTREAM_ON NULL を指定できます。  
  
 詳細については、「[FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)」をご覧ください。  
  
 ROWGUIDCOL  
 新しい列が行の GUID 列であることを示します。 1 つだけ**uniqueidentifier** ROWGUIDCOL 列として 1 つのテーブルの列を指定することができます。 ROWGUIDCOL プロパティを適用すると、$ROWGUID を使用して列を参照できるようになります。 ROWGUIDCOL プロパティにのみ割り当てることができます、 **uniqueidentifier**列です。 ユーザー定義データ型の列には、ROWGUIDCOL を割り当てることはできません。  
  
 ROWGUIDCOL プロパティは、列に格納されている値の一意性を設定しません。 また、ROWGUIDCOL プロパティは、テーブルに挿入される新しい行の値を自動的に生成しません。 各列の一意の値を生成するに使用するか、 [NEWID](../../t-sql/functions/newid-transact-sql.md)または[NEWSEQUENTIALID](../../t-sql/functions/newsequentialid-transact-sql.md)で機能[挿入](../../t-sql/statements/insert-transact-sql.md)ステートメントかの既定値としてこれらの関数を使用して、列です。  
  
 使用して暗号化  
 使用して暗号化列を指定します、 [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)機能します。  
  
 COLUMN_ENCRYPTION_KEY = *key_name*  
 列の暗号化キーを指定します。 詳細については、次を参照してください。 [CREATE COLUMN ENCRYPTION KEY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-column-encryption-key-transact-sql.md).  
  
 ENCRYPTION_TYPE = {決定的 |ランダム化}  
 **確定的な暗号化** は常に任意のプレーン テキストを指定した値の場合は、同じ暗号化された値を生成するメソッドを使用します。 確定的な暗号化を使用すると、グループ化、および暗号化された値に基づいて、等しいかどうかの結合を使用して、テーブルへの参加の等値比較を使用して検索をできますも確認するには、暗号化された列のパターンについては、暗号化された値を推測する承認されていないユーザーを許可することができます。 確定的に暗号化された列に 2 つのテーブルを結合すると、両方の列が同じ列の暗号化キーを使用して暗号化されている場合にのみ可能なです。 明確な暗号化では、バイナリ 2 文字型の列の並べ替え順序を持つ列の照合順序を使用する必要があります。  
  
 **暗号化をランダム化** は低い予測可能な方法でデータを暗号化するためのメソッドを使用します。 ランダムな暗号化より安全になりますが、により、等しいかどうかの検索、グループ化、および暗号化された列を結合します。 ランダムな暗号化を使用して列のインデックスを付けることはできません。  
  
 検索パラメーターまたは政府の ID 番号など、グループ化のパラメーターとなる列には、確定的な暗号化を使用します。 ランダムな暗号化を使用して、クレジット カード番号などのデータ、これが、他のレコードとグループ化されたかテーブル、およびこれは検索されませんの (トランザクションの数) などの他の列を使用して、関心のある暗号化された列を含む行を検索するために参加するために使用します。  
  
 列は、該当するデータ型である必要があります。  
  
 アルゴリズム  
 必要があります**'AEAD_AES_256_CBC_HMAC_SHA_256'**です。  
  
 機能の制約を含むの詳細については、次を参照してください。 [Always Encrypted &#40;データベース エンジン&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)です。  
  
 **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 SPARSE  
 列がスパース列であることを示します。 スパース列のストレージは NULL 値用に最適化されます。 スパース列を NOT NULL として指定することはできません。 追加の制限とスパース列の詳細については、次を参照してください。[スパース列を使用する](../../relational-databases/tables/use-sparse-columns.md)です。  
  
 マスクの使用 (関数 = ' *mask_function* ')  
 **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 動的なデータのマスクを指定します。 *mask_function*適切なパラメーターを使用してマスク関数の名前を指定します。 3 つの関数を使用できます。  
  
-   default()  
  
-   email()  
  
-   partial()  
  
-   random()  
  
 関数パラメーターの場合は、次を参照してください。[動的データ マスク](../../relational-databases/security/dynamic-data-masking.md)です。  
  
 FILESTREAM  
   
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion.md)]

 に対してのみ有効**varbinary (max)**列です。 FILESTREAM ストレージを指定、 **varbinary (max)** BLOB データです。  
  
 テーブルの列を持つもする必要があります、 **uniqueidentifier** ROWGUIDCOL 属性を持つデータ型です。 この列では、null 値は許可されず、UNIQUE または PRIMARY KEY 単一列制約を持つ必要があります。 列の GUID 値は、データの挿入時にアプリケーションによって、または NEWID () 関数を使用する DEFAULT 制約によって、提供する必要があります。  
  
 テーブルに FILESTREAM 列が定義されているときは、ROWGUIDCOL 列を削除したり関連する制約を変更したりすることはできません。 ROWGUIDCOL 列は、最後の FILESTREAM 列が削除された後でのみ削除できます。  
  
 列に対して FILESTREAM ストレージ属性を指定した場合、この列のすべての値がファイル システム上の FILESTREAM データ コンテナーに格納されます。  
  
 COLLATE *collation_name*  
 列の照合順序を指定します。 照合順序名には、Windows 照合順序名または SQL 照合順序名のいずれかを指定できます。 *collation_name*の列に対してのみ適用できる、 **char**、 **varchar**、**テキスト**、 **nchar**、 **nvarchar**、および**ntext**データ型。 collation_name を指定しないと、列には、ユーザー定義データ型である場合はユーザー定義データ型の照合順序が割り当てられ、ユーザー定義データ型でなければデータベースの既定の照合順序が割り当てられます。  
  
 Windows と SQL 照合順序名の詳細については、次を参照してください。 [Windows 照合順序名](../../t-sql/statements/windows-collation-name-transact-sql.md)と[SQL 照合順序名](../../t-sql/statements/sql-server-collation-name-transact-sql.md)です。  
  
 COLLATE 句の詳細については、次を参照してください。 [COLLATE &#40;です。TRANSACT-SQL と #41 です。](~/t-sql/statements/collations.md).  
  
 CONSTRAINT  
 PRIMARY KEY 制約、NOT NULL 制約、UNIQUE 制約、FOREIGN KEY 制約、または CHECK 制約の開始を示す省略可能なキーワードです。  
  
 *constraint_name*  
 制約の名前です。 制約名は、テーブルが所属するスキーマ内で一意である必要があります。  
  
 NULL | NOT NULL  
 列で null 値を許容するかどうかを決定します。 NULL は厳密には制約ではありませんが、NOT NULL と同じように指定することができます。 計算列で NOT NULL を指定できるのは、同時に PERSISTED も指定した場合だけです。  
  
 PRIMARY KEY  
 一意なインデックスによって、指定した 1 つ以上の列にエンティティの整合性を設定する制約です。 PRIMARY KEY 制約は、1 つのテーブルにつき 1 つだけ作成できます。  
  
 UNIQUE  
 指定された列または一意なインデックスによって列のエンティティの整合性を提供する制約です。 1 つのテーブルには複数の UNIQUE 制約を指定できます。  
  
 CLUSTERED | NONCLUSTERED  
 PRIMARY KEY 制約または UNIQUE 制約に対して、クラスター化インデックスまたは非クラスター化インデックスを作成することを示します。 PRIMARY KEY 制約の既定値は CLUSTERED で、UNIQUE 制約の既定値は NONCLUSTERED です。  
  
 CREATE TABLE ステートメントの中で 1 つの制約だけに CLUSTERED を指定することができます。 UNIQUE 制約で CLUSTERED が指定され、PRIMARY KEY 制約も指定した場合には、PRIMARY KEY の既定値は NONCLUSTERED になります。  
  
 ディスク ベース テーブルで NONCLUSTERED を使用する方法を次に示します。  
  
```  
CREATE TABLE t1 ( c1 int, INDEX ix_1 NONCLUSTERED (c1))   
CREATE TABLE t2( c1 int INDEX ix_1 NONCLUSTERED (c1))   
CREATE TABLE t3( c1 int, c2 int INDEX ix_1 NONCLUSTERED)   
CREATE TABLE t4( c1 int, c2 int, INDEX ix_1 NONCLUSTERED (c1,c2))  
```  
  
 FOREIGN KEY REFERENCES  
 1 つ以上の列内のデータに参照整合性を持たせる制約です。 FOREIGN KEY 制約では、列内の各値が、参照されるテーブル内のその値に対応する参照される列に存在している必要があります。 FOREIGN KEY 制約は、参照されるテーブル内の PRIMARY KEY 制約または UNIQUE 制約である列、または参照されるテーブルの UNIQUE INDEX で参照される列のみを参照できます。 計算列の外部キーには、PERSISTED も設定する必要があります。  
  
 [ *schema_name***.**]*referenced_table_name*]  
 FOREIGN KEY 制約で参照されるテーブル名と、そのテーブルが所属するスキーマ名です。  
  
 **(** *ref_column* [ **、**.*n* ] **)**  
 FOREIGN KEY 制約によって参照されるテーブルの 1 つの列または列の一覧です。  
  
 削除するときに {**何も**|CASCADE |NULL を設定 |既定値に設定}  
 作成されたテーブルの行が参照関係を持ち、参照される行が親テーブルから削除された場合に、その行に対して実行される操作を指定します。 既定値は NO ACTION です。  
  
 NO ACTION  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]エラーと、親テーブル内の行に対して削除操作はロールバックが発生します。  
  
 CASCADE  
 親テーブルから行が削除された場合に、参照元テーブルからもその行が削除されます。  
  
 SET NULL  
 親テーブル内の対応する行が削除されると、外部キーを構成するすべての値に NULL が設定されます。 この制約を実行するには、外部キー列が NULL 値を使用できる必要があります。  
  
 SET DEFAULT  
 親テーブル内の対応する行が削除されると、外部キーを構成するすべての値に既定値が設定されます。 この制約を実行するには、すべての外部キー列に既定値が定義されている必要があります。 列が NULL 値を許容し、明示的な既定値が設定されていない場合は、列の既定値として NULL が暗黙的に使用されます。  
  
 論理レコードを使用するマージ パブリケーションにテーブルを含める場合、CASCADE は使用しないでください。 論理レコードの詳細については、「[論理レコードによる関連行への変更をグループ化](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)」を参照してください。  
  
 該当するテーブルに ON DELETE の INSTEAD OF トリガーが既に存在する場合は、ON DELETE CASCADE を定義できません。  
  
 たとえば、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース、 **ProductVendor**テーブルとの参照関係には、**仕入先**テーブル。 **ProductVendor.BusinessEntityID**の外部キー参照、 **Vendor.BusinessEntityID**主キー。  
  
 内の行で DELETE ステートメントが実行したかどうか、**仕入先**テーブル、および、ON DELETE CASCADE アクションが指定されて**ProductVendor.BusinessEntityID**、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 1 つまたは複数の依存をチェックします行では、 **ProductVendor**テーブル。 内の従属行がある場合、 **ProductVendor**テーブルが削除されで参照される行、**仕入先**テーブル。  
  
 これに対し、NO ACTION が指定した場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]エラーが発生し、に対する削除操作はロールバック、**仕入先**行には、少なくとも 1 つの行がある場合、 **ProductVendor**それを参照するテーブル。  
  
 更新時に {**何も**|CASCADE |NULL を設定 |既定値に設定}  
 変更対象のテーブル内の行が参照関係を持ち、親テーブルで参照先の行が更新された場合、変更対象のテーブル内の行に対して発生する操作を指定します。 既定値は NO ACTION です。  
  
 NO ACTION  
 NO ACTION を指定すると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]でエラーが発生し、親テーブルの行の更新操作はロールバックされます。  
  
 CASCADE  
 親テーブルで行が更新された場合に、参照元のテーブルでも対応する行が更新されます。  
  
 SET NULL  
 親テーブルの対応する行が更新された場合、外部キーを形成するすべての値が NULL に設定されます。 この制約を実行するには、外部キー列が NULL 値を使用できる必要があります。  
  
 SET DEFAULT  
 親テーブルの対応する行が更新された場合、外部キーを形成するすべての値が既定値に設定されます。 この制約を実行するには、すべての外部キー列に既定値が定義されている必要があります。 列が NULL 値を許容し、明示的な既定値が設定されていない場合は、列の既定値として NULL が暗黙的に使用されます。  
  
 論理レコードを使用するマージ パブリケーションにテーブルを含める場合、CASCADE は使用しないでください。 論理レコードの詳細については、「[論理レコードによる関連行への変更をグループ化](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)」を参照してください。  
  
 変更対象のテーブルに ON UPDATE での INSTEAD OF トリガーが既に存在する場合は、ON UPDATE CASCADE、SET NULL、または SET DEFAULT を定義できません。  
  
 たとえば、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース、 **ProductVendor**テーブルとの参照関係には、**仕入先**テーブル: **ProductVendor.BusinessEntity**外部キー参照、 **Vendor.BusinessEntityID**主キー。  
  
 内の行で、UPDATE ステートメントが実行したかどうか、**仕入先**テーブル、および ON UPDATE CASCADE アクションが指定されて**ProductVendor.BusinessEntityID**、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 1 つまたは複数の依存をチェックします行では、 **ProductVendor**テーブル。 内の従属行がある場合、 **ProductVendor**テーブルが更新されで参照される行、**仕入先**テーブル。  
  
 これに対し、NO ACTION が指定した場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]エラーが発生し、更新 操作をロールバック、**仕入先**行には、少なくとも 1 つの行がある場合、 **ProductVendor**それを参照するテーブル。  
  
 CHECK  
 1 つ以上の列に入力できる値を制限することによってドメインの整合性を設定する制約です。 計算列の CHECK 制約には、PERSISTED も設定する必要があります。  
  
 *logical_expression*  
 TRUE または FALSE を返す論理式です。 別名データ型を式に入れることはできません。  
  
 *column*  
 テーブル制約で使われる、かっこで囲まれた 1 つの列または列リストです。制約定義で使われている列を示します。  
  
 [ **ASC** |DESC]  
 テーブル制約に参加している 1 つ以上の列が並べ替えられる順序を指定します。 既定値は ASC です。  
  
 *partition_scheme_name*  
 パーティション テーブルの各パーティションがマップされるファイル グループを定義するパーティション構成の名前を指定します。 パーティション構成はデータベース内に存在している必要があります。  
  
 [ *partition_column_name***です。** ]  
 パーティション テーブルに対して、パーティション分割する列を指定します。 パーティションで指定されている列が一致する必要があります関数*partition_scheme_name*データ型、長さ、および有効桁数の観点からを使用します。 パーティション関数に関与する計算列は、明示的に PERSISTED とマークされている必要があります。  
  
> [!IMPORTANT]  
>  パーティション テーブルのパーティション分割列に加え、ALTER TABLE...SWITCH 操作のソースまたはターゲットとなっているパーティション分割されていないテーブルの列にも、NOT NULL を指定することをお勧めします。 こうすることで、パーティション分割列の CHECK 制約で NULL 値のチェックを行う必要がなくなります。  
  
 Fillfactor の値を **=**  *fillfactor*  
 どの程度を指定します、[!INCLUDE[ssDE](../../includes/ssde-md.md)]インデックス データの格納に使用される各インデックス ページを作成する必要があります。 ユーザーが指定した*fillfactor* 1 ~ 100 の値を指定できます。 値を指定しない場合の既定値は 0 です。 Fill factor 値 0 と 100 は、すべての点で同じです。  
  
> [!IMPORTANT]  
>  マニュアルは、WITH FILLFACTOR = *fillfactor* PRIMARY KEY または UNIQUE 制約に適用される唯一のインデックス オプションは、旧バージョンとの互換性のために維持されますが、この方法で、将来的には記載いないようを解放します。  
  
 *column_set_name* XML COLUMN_SET の ALL_SPARSE_COLUMNS  
 列セットの名前を指定します。 列セットは、型指定されていない XML 表記であり、テーブルのすべてのスパース列を 1 つにまとめて構造化した出力です。 列セットの詳細については、「 [列セットの使用](../../relational-databases/tables/use-column-sets.md)」を参照してください。  
  
 期間 FOR SYSTEM_TIME (*system_start_time_column_name* 、 *system_end_time_column_name* )  
   
**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。
  
 レコードの有効期間を記録する、システムを使用する列の名前を指定します。 この引数を使用して、生成された常に、行と組み合わせて {開始 |終了} SYSTEM_VERSIONING = テーブルにシステムのバージョン管理を有効にする引数にするとします。 詳細については、「 [Temporal Tables](../../relational-databases/tables/temporal-tables.md)」を参照してください。  
  
 COMPRESSION_DELAY  
   
**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。
  
 メモリ最適化での遅延は、変更せずに、列ストア インデックスへの圧縮の対象となる前に、テーブルに行がある必要があります (分) の最小数を指定します。 SQL Server では、その最終更新時刻に従ってを圧縮する特定の行を選択します。 たとえば、行を 2 時間の時間帯に頻繁に変更する場合は、COMPRESSION_DELAY を設定できます = 120 分以内に SQL Server は、行を圧縮する前に更新が完了したことを確認します。  
  
 ディスク ベース テーブルでは、SQL Server を使用すると、圧縮された行グループに圧縮できる前に、遅延はデルタ行グループで閉じられた状態で、デルタ行グループがある必要があります (分) の最小数を指定します。 ディスク ベース テーブルの挿入を追跡および更新されないため時間個々 の行に SQL Server を適用の遅延が閉じられた状態で、デルタ行グループ。  
  
 既定値は、0 分です。  
  
 COMPRESSION_DELAY を使用する場合の推奨事項を参照してください[リアルタイム運用分析の列ストアの概要](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)  
  
 \<table_option >:: = 1 つまたは複数のテーブル オプションを指定します。  
  
 DATA_COMPRESSION  
 指定したテーブル、パーティション番号、またはパーティション範囲に、データ圧縮オプションを指定します。 次のオプションがあります。  
  
 なし  
 テーブルまたは指定したパーティションが圧縮されません。  
  
 ROW  
 行の圧縮を使用して、テーブルまたは指定したパーティションが圧縮されます。  
  
 PAGE  
 ページの圧縮を使用して、テーブルまたは指定したパーティションが圧縮されます。  
  
 COLUMNSTORE  
   
  
**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。
  
 非クラスター化列ストア インデックスとクラスター化列ストア インデックスの両方を含む列ストア インデックスにのみ適用されます。 列ストアは、ほとんどのパフォーマンスの高い列ストア圧縮で圧縮を指定します。 これは、一般的な選択肢です。  
  
 COLUMNSTORE_ARCHIVE  
   
  
**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 非クラスター化列ストア インデックスとクラスター化列ストア インデックスの両方を含む列ストア インデックスにのみ適用されます。 COLUMNSTORE_ARCHIVE は、テーブルまたはパーティション サイズを小さく絞り込みますにさらに圧縮されます。 これは、保存用や、ストレージのサイズを減らす必要があり、しかも保存と取得に時間をかける余裕があるその他の状況で使用できます。  
  
 圧縮の詳細については、次を参照してください。[データ圧縮](../../relational-databases/data-compression/data-compression.md)です。  
  
 パーティションで**(** { `<partition_number_expression>` |[ **,**...*n* ] **)**  
 DATA_COMPRESSION 設定を適用するパーティションを指定します。 テーブルがパーティション分割されていない場合に ON PARTITIONS 引数を使用すると、エラーが発生します。 ON PARTITIONS 句を指定しないと、パーティション テーブルのすべてのパーティションに対して DATA_COMPRESSION オプションが適用されます。  
  
 *partition_number_expression*次のように指定することができます。  
  
-   ON PARTITIONS (2) などのように、1 つのパーティションのパーティション番号を指定します。  
  
-   ON PARTITIONS (1, 5) などのように、複数のパーティションのパーティション番号をコンマで区切って指定します。  
  
-   たとえば、範囲と個別のパーティションの両方を提供: ON PARTITIONS (2、4, 6 TO 8)  
  
 `<range>`パーティション番号など、to で区切って指定できます: ON PARTITIONS (6 TO 8)。  
  
 さまざまなパーティションにさまざまな種類のデータ圧縮を設定するには、次のように DATA_COMPRESSION オプションを複数回指定します。  
  
```  
WITH   
(  
DATA_COMPRESSION = NONE ON PARTITIONS (1),   
DATA_COMPRESSION = ROW ON PARTITIONS (2, 4, 6 TO 8),   
DATA_COMPRESSION = PAGE ON PARTITIONS (3, 5)  
)  
```  
  
 \<index_option >:: =  
 1 つ以上のインデックス オプションを指定します。 これらのオプションの詳細については、次を参照してください。 [CREATE INDEX &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-index-transact-sql.md).  
  
 PAD_INDEX = {ON |**OFF** }  
 ON の場合、FILLFACTOR で指定された空き領域の割合が、インデックスの中間レベル ページに適用されます。 OFF の場合や、FILLFACTOR 値が指定されていない場合は、中間レベル ページは、中間ページの一連のキーを考慮しつつ、インデックスが持つことのできる最大サイズの行が少なくとも 1 つ格納できる領域を残して、ほぼ容量いっぱいに使用されます。 既定値は OFF です。  
  
 FILLFACTOR  **=**  *fillfactor*  
 どの程度を示すパーセンテージを指定します、[!INCLUDE[ssDE](../../includes/ssde-md.md)]インデックスの作成または変更時に各インデックス ページのリーフ レベルを作成する必要があります。 *fillfactor* 1 から 100 までの整数値にする必要があります。 既定値は 0 です。 Fill factor 値 0 と 100 は、すべての点で同じです。  
  
 IGNORE_DUP_KEY = {ON |**OFF** }  
 挿入操作で、一意のインデックスに重複するキー値を挿入しようとした場合のエラー応答を指定します。 IGNORE_DUP_KEY オプションは、インデックスが作成または再構築された後の挿入操作のみに適用されます。 オプションも何も起こりませんの実行時に[CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)、 [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)、または[更新](../../t-sql/queries/update-transact-sql.md)です。 既定値は OFF です。  
  
 ON  
 重複したキー値が一意のインデックスに挿入されると、警告メッセージが表示されます。 一意性制約に違反する行のみが失敗します。  
  
 OFF  
 重複したキー値が一意のインデックスに挿入されると、エラー メッセージが表示されます。 INSERT 操作全体がロールバックされます。  
  
 ビューに作成されたインデックス、一意でないインデックス、XML インデックス、空間インデックス、およびフィルター選択されたインデックスの IGNORE_DUP_KEY を ON に設定できません。  
  
 IGNORE_DUP_KEY を表示する[sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)です。  
  
 旧バージョンと互換性のある構文では、WITH IGNORE_DUP_KEY は WITH IGNORE_DUP_KEY = ON と同じです。  
  
 STATISTICS_NORECOMPUTE  **=**  {ON |**OFF** }  
 ON の場合、古いインデックス統計値は自動的には再計算されません。 OFF の場合、統計値の自動的な更新が有効になります。 既定値は OFF です。  
  
 ALLOW_ROW_LOCKS  **=**  { **ON** |オフ}  
 ON の場合、インデックスにアクセスするときに行ロックが許可されます。 いつ行ロックを使用するかは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]によって決定されます。 OFF の場合、行のロックは使用されません。 既定値は ON です。  
  
 ALLOW_PAGE_LOCKS  **=**  { **ON** |オフ}  
 ON の場合、インデックスにアクセスするときにページ ロックが許可されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]ページ ロックを使用する場合を決定します。 OFF の場合、ページ ロックは使用されません。 既定値は ON です。  
  
 FILETABLE_DIRECTORY = *directory_name*  
   
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 
  
 Windows と互換性のある FileTable ディレクトリ名を指定します。 この名前は、データベース内のすべての FileTable ディレクトリ名の中で一意である必要があります。 一意性の比較では、照合順序の設定とは関係なく、大文字と小文字は区別されません。 この値を指定しない場合、FileTable の名前が使用されます。  
  
 FILETABLE_COLLATE_FILENAME = { *collation_name* | database_default}  
   
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 
  
 FileTable の **Name** 列に適用される照合順序の名前を指定します。 照合順序は、Windows のファイル名のセマンティクスに準拠するために、大文字と小文字を区別しない設定にする必要があります。 この値が指定されていない場合、データベースの既定の照合順序が使用されます。 データベースの既定の照合順序で大文字と小文字が区別される場合は、エラーが発生し、CREATE TABLE 操作は失敗します。  
  
 *collation_name*  
 大文字と小文字を区別しない照合順序の名前です。  
  
 database_default  
 データベースの既定の照合順序を使用するように指定します。 この照合順序は、大文字と小文字を区別しないものである必要があります。  
  
 FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME = *constraint_name*  
   
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 
  
 FileTable に対して自動的に作成される主キー制約で使用する名前を指定します。 この値を指定しない場合、システムによって制約の名前が生成されます。  
  
 FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME = *constraint_name*  
   
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 
  
 自動的に作成される一意制約で使用する名前を指定、 **stream_id** FileTable 内の列です。 この値を指定しない場合、システムによって制約の名前が生成されます。  
  
 FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME = *constraint_name*  
   
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 
  
 自動的に作成される一意制約で使用する名前を指定、 **parent_path_locator**と**名前**FileTable 内の列です。 この値を指定しない場合、システムによって制約の名前が生成されます。  
  
 SYSTEM_VERSIONING  **=**  ON [(HISTORY_TABLE  **=**  *schema_name*です。  *history_table_name* [、DATA_CONSISTENCY_CHECK  **=**  { **ON** |オフ}])]  
   
  
**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。   
  
 データ型、null 値許容制約、および主キー制約の要件が満たされている場合は、テーブルのシステムのバージョン管理を有効にします。 場合、 **HISTORY_TABLE**引数を使用しない場合、システムは 2 つのテーブル間のリンクを作成する、現在のテーブルと同じファイル グループに現在のテーブルのスキーマに一致する新しい履歴テーブルを生成により、システム履歴テーブルに、現在のテーブル内の各レコードの履歴を記録します。 この履歴テーブルの名前になります`MSSQL_TemporalHistoryFor<primary_table_object_id>`です。 履歴テーブルには既定では、 **PAGE** 圧縮します。 HISTORY_TABLE 引数を介してへのリンクを作成し、既存の履歴テーブルを使用する場合に、現在のテーブルと、指定したテーブルの間のリンクが作成されます。 現在のテーブルがパーティション分割する場合、履歴テーブルは、パーティション分割構成がレプリケートされていないために自動的に現在のテーブルから履歴テーブルに既定のファイル グループに作成されます。 履歴テーブルの作成時に履歴テーブルの名前を指定すると場合、は、スキーマとテーブルの名前を指定する必要があります。 既存の履歴テーブルへのリンクを作成する場合は、データの整合性チェックを実行することもできます。 このデータの整合性チェックでは、既存のレコードが重複しないことを確認します。 データを実行する一貫性チェックが、既定値です。 この引数を使用して、期間 FOR SYSTEM_TIME と生成された常に行と組み合わせて {開始 |終了} 引数を使用して、テーブルでのシステムのバージョン管理を有効にします。 詳細については、「 [Temporal Tables](../../relational-databases/tables/temporal-tables.md)」を参照してください。  
  
 REMOTE_DATA_ARCHIVE = {ON [( *table_stretch_options* [,... n])] |OFF (MIGRATION_STATE = 一時停止)}  
   
  
**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 Stretch database が有効または無効になっている新しいテーブルを作成します。 詳細については、「 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)」を参照してください。  
  
 **テーブルに対して Stretch Database を有効にします。**  
  
 有効にすると拡大テーブルを指定して`ON`、必要に応じて指定することができます`MIGRATION_STATE = OUTBOUND`を開始するデータの移行をすぐに、または`MIGRATION_STATE = PAUSED`データ移行を延期します。 既定値は `MIGRATION_STATE = OUTBOUND` です。 テーブルの Stretch を有効にする方法の詳細については、次を参照してください。[テーブルに対して Stretch Database を有効にする](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)です。  
  
 **前提条件**。 テーブルの Stretch を有効にする前にする必要があるサーバーおよびデータベースの Stretch を有効にします。 詳細については、「 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)」を参照してください。  
  
 **権限**: データベースまたはテーブルの拡張を有効にするには、db_owner アクセス許可が必要です。 テーブルの拡張を有効にすると、テーブルに対する ALTER 権限も必要です。  
  
 [FILTER_PREDICATE = {null |*述語*}]  
   
  
**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 過去と現在の両方のデータを含むテーブルから移行する行を選択するフィルター述語を指定します。 この述語には、決定的なインライン テーブル値関数を呼び出す必要があります。 詳細については、次を参照してください。[テーブルに対して Stretch Database を有効にする](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)と[フィルター関数を使用して移行する行を選択して](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md)です。 
   
> [!IMPORTANT]  
>  指定したフィルター述語のパフォーマンスが低いと、データ移行のパフォーマンスも低くなります。 Stretch Database では、CROSS APPLY 演算子を使用してテーブルにフィルター述語を適用します。  
  
 フィルター述語を指定しない場合、テーブル全体が移行されます。  
  
 フィルター述語を指定するときにも指定する必要が*MIGRATION_STATE*です。  
  
 MIGRATION_STATE = {送信 | 受信 |一時停止している}  
   
  
**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、および Azure SQL です。 
  
-   指定`OUTBOUND`SQL Server からデータを Azure に移行します。  
  
-   指定`INBOUND`Azure からテーブルのデータをバックアップおよびテーブルの Stretch を無効にする SQL Server にリモートをコピーします。 詳細については、「 [Stretch Database を無効にして、リモート データを戻す](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md)」を参照してください。  
  
     この操作によりデータ転送コストが発生し、取り消すことはできません。  
  
-   指定`PAUSED`を一時停止またはデータの移行を延期します。 詳細については、次を参照してください。[一時停止と再開データの移行 &#40;です。Stretch Database &#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
 MEMORY_OPTIMIZED  
   
  
**適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 値には、テーブルがメモリ最適化であることを示します。 メモリ最適化テーブルは、トランザクション処理のパフォーマンスの最適化に使用される、インメモリ OLTP 機能の一部です。 インメモリ OLTP での概要を参照してください[クイック スタート 1: TRANSACT-SQL のパフォーマンスを向上をインメモリ OLTP テクノロジ](../../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md)です。 メモリ最適化テーブルに関するより詳細な情報を参照してください。[メモリ最適化テーブル](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)です。  
  
 既定値は OFF、テーブルがディスク ベースであることを示します。  
  
 DURABILITY  
   
  
**適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。   
  
 値 SCHEMA_AND_DATA は、テーブルが持続性で、変更がディスクに保存し、再起動またはフェールオーバー後も存続することを示します。  SCHEMA_AND_DATA は、既定値です。  
  
 値 SCHEMA_ONLY は、テーブルに持続性がないことを示します。 テーブルのスキーマが保存されていますが、再起動またはデータベースのフェールオーバー時に、データの更新プログラムは保持されません。 DURABILITY = SCHEMA_ONLY はメモリ最適化でのみ使用 = ON です。  
  
> [!WARNING]  
>  使用してテーブルを作成するときに**持続性 = SCHEMA_ONLY**、および**READ_COMMITTED_SNAPSHOT**を使用して後で変更**ALTER DATABASE**テーブル内のデータは失われます。  
  
 BUCKET_COUNT  
   
  
**適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。 
  
 ハッシュ インデックスに作成されるバケットの数を示します。 ハッシュ インデックスの BUCKET_COUNT の最大値は 1,073,741,824 です。 バケット数の詳細については、次を参照してください。[メモリ最適化テーブルのインデックス](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)です。  
  
 BUCKET_COUNT は必須の引数です。  
  
 INDEX  
   
  
**適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。 
  
列とテーブルのインデックスは、CREATE TABLE ステートメントの一部として指定できます。 追加と削除、メモリ最適化テーブルのインデックスに関する詳細を参照してください:[メモリ最適化テーブル](../../relational-databases/in-memory-oltp/altering-memory-optimized-tables.md)
  
 HASH  
   
  
**適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。 
  
 ハッシュ インデックスを作成することを示します。  
  
 ハッシュ インデックスは、メモリ最適化テーブルでのみサポートされます。  
  
## <a name="remarks"></a>解説  
 許容されるテーブル、列、制約、およびインデックスの数については、次を参照してください。 [Maximum Capacity Specifications for SQL Server](../../sql-server/maximum-capacity-specifications-for-sql-server.md)です。  
  
 一般的にテーブルとインデックスには、一度に 1 エクステントの増分で領域が割り当てられます。 ALTER DATABASE の SET MIXED_PAGE_ALLOCATION オプション設定されている場合 true の場合、または always より前のバージョン[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]テーブルまたはインデックスの作成時に、十分なページが均一エクステントを埋めるのにまでは混合エクステントからページが割り当てられます。 ページが均一エクステントを埋めるのに十分な量になった後は、現在割り当てられているエクステントが埋まるたびに新しいエクステントが割り当てられます。 テーブルで使用して割り当てられた領域の量に関するレポートを次のように実行します。 **sp_spaceused**です。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]どの既定、IDENTITY、ROWGUIDCOL または列の制約が列定義で指定された順序は強制されません。  
  
 テーブルを作成するときに、QUOTED IDENTIFIER オプションが OFF に設定されている場合でも、ON としてテーブルのメタデータ内に格納されます。  
  
## <a name="temporary-tables"></a>一時テーブル  
 ローカルおよびグローバル一時テーブルを作成できます。 ローカル一時テーブルは現在のセッション内でしか使えませんが、グローバル一時テーブルはすべてのセッションで使用できます。 一時テーブルをパーティション分割することはできません。  
  
 1 つの番号記号でローカル一時テーブル名のプレフィックス (#*table_name*)、二重シャープ記号とグローバル一時テーブル名のプレフィックス (##*table_name*)。  
  
 SQL ステートメントに指定された値を使用して、一時テーブルを参照する*table_name*例 ### の CREATE TABLE ステートメントで。  
  
```  
CREATE TABLE #MyTempTable (cola INT PRIMARY KEY);  
  
INSERT INTO #MyTempTable VALUES (1);  
```  
  
 1 つのストアド プロシージャまたはバッチ内で複数の一時テーブルを作成する場合は、それぞれ違う名前で作成する必要があります。  
  
 ストアド プロシージャまたは複数のユーザーによって同時に実行できるアプリケーションでローカル一時テーブルを作成する場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]別のユーザーによって作成されたテーブルを区別できる必要があります。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]は、各ローカル一時テーブル名の末尾に数値サフィックスを内部的に追加することによって、テーブルを区別します。 格納されている一時テーブルの完全な名前、 **sysobjects**テーブルに**tempdb** CREATE TABLE ステートメントと、システムによって生成された数値のサフィックスで指定したテーブル名で構成します。 サフィックスを許可する*table_name*指定されたローカル一時テーブル名は、116 文字を超えることはできません。  
  
 一時テーブルは、DROP TABLE を使用して明示的に削除される場合を除き、有効範囲外になったときに自動的に削除されます。  
  
-   ストアド プロシージャで作成されたローカル一時テーブルは、ストアド プロシージャが終了すると自動的に削除されます。 テーブルは、そのテーブルを作成したストアド プロシージャによって実行される任意の入れ子になったストアド プロシージャから参照できます。 テーブルは、そのテーブルを作成したストアド プロシージャを呼び出したプロセスから参照することはできません。  
  
-   その他すべてのローカル一時テーブルは、現在のセッションの終了時に自動的に削除されます。  
  
-   グローバル一時テーブルは、テーブルを作成したセッションが終了し、その他すべてのタスクがテーブルの参照をやめたときに自動的に削除されます。 タスクとテーブルの間の関連付けは、1 つの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが存続する間のみ維持されます。 つまり、最後の完了時に、グローバル一時テーブルがドロップされる[!INCLUDE[tsql](../../includes/tsql-md.md)]がアクティブにテーブルを参照して、作成したセッションが終了したときにステートメントです。  
  
 ストアド プロシージャまたはトリガーの内部で作成されたローカル一時テーブルは、ストアド プロシージャまたはトリガーが呼び出される前に作成された一時テーブルと同じ名前にすることができます。 ただし、クエリが一時テーブルを参照し、かつ同じ名前の一時テーブルが同時に 2 つ存在する場合、クエリがどちらのテーブルに対して解決されるかは定義されません。 入れ子になったストアド プロシージャも、そのプロシージャを呼び出したストアド プロシージャによって作成された一時テーブルと同じ名前を持つ一時テーブルを作成することができます。 ただし、入れ子になったプロシージャで作成したテーブルへの解決を変更するためには、呼び出し元プロシージャで作成されたテーブルと同じ構造、同じ列名である必要があります。 次の例を参照してください。  
  
```  
CREATE PROCEDURE dbo.Test2  
AS  
n    CREATE TABLE #t(x INT PRIMARY KEY);  
    INSERT INTO #t VALUES (2);  
    SELECT Test2Col = x FROM #t;  
GO  
  
CREATE PROCEDURE dbo.Test1  
AS  
    CREATE TABLE #t(x INT PRIMARY KEY);  
    INSERT INTO #t VALUES (1);  
    SELECT Test1Col = x FROM #t;  
 EXEC Test2;  
GO  
  
CREATE TABLE #t(x INT PRIMARY KEY);  
INSERT INTO #t VALUES (99);  
GO  
  
EXEC Test1;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 (1 row(s) affected) 
 Test1Col 
 ----------- 
 1 

 (1 row(s) affected) 
 Test2Col 
 ----------- 
 2 
 ```
  
 ローカル一時テーブルまたはグローバル一時テーブルを作成する場合、CREATE TABLE の構文では、FOREIGN KEY 制約を除く制約定義をサポートします。 一時テーブルで FOREIGN KEY 制約が指定されていると、ステートメントは、制約が省略されたことを示す警告メッセージを返します。 テーブルは FOREIGN KEY 制約なしで作成されます。 FOREIGN KEY 制約の中で一時テーブルを参照することはできません。  
  
 名前付き制約のある一時テーブルがユーザー定義トランザクションのスコープ内で作成される場合、一時テーブルを作成するステートメントを実行できるのは、一度に 1 ユーザーだけです。 たとえば、ストアド プロシージャで名前付き主キー制約のある一時テーブルが作成される場合、そのストアド プロシージャを複数のユーザーが同時に実行することはできません。  


## <a name="database-scoped-global-temporary-tables-azure-sql-database"></a>データベース スコープのグローバル一時テーブル (Azure SQL データベース)

SQL Server のグローバルの一時テーブル (を使用して開始 ## テーブル名) は tempdb に格納され、SQL Server インスタンス全体のすべてのユーザーのセッションの間で共有します。 SQL テーブル型については、テーブルの作成で、前のセクションを参照してください。  

Azure SQL データベースでは、グローバルの一時テーブルも tempdb に格納され、データベース レベルのスコープをサポートしています。  つまり、同じ Azure SQL データベース内のすべてのユーザーのセッションのグローバル一時テーブルを共有します。 他の Azure SQL データベースからのユーザー セッションは、グローバル一時テーブルにアクセスできません。

Azure SQL DB のグローバルの一時テーブルは、同じの構文とセマンティクスを一時テーブルは、SQL Server に従います。  同様に、グローバル一時ストアド プロシージャも、Azure SQL DB 内のデータベース レベルにスコープされます。 ローカル一時テーブルの (# テーブル名を使用して開始) では、Azure SQL データベースでもサポートされ、同じの構文とセマンティクスを SQL Server を使用してに従います。  前のセクションを参照してください[一時テーブル](#temporary-tables)です。  

> [!IMPORTANT]
> この機能は、Azure SQL データベースで使用できるのみです。
>

### <a name="troubleshooting-global-temporary-tables-for-azure-sql-db"></a>Azure SQL DB のグローバル一時テーブルのトラブルシューティング 

トラブルシューティングについては、tempdb を参照してください。[のトラブルシューティングのディスク領域不足 tempdb](https://technet.microsoft.com/library/ms176029%28v=sql.105%29.aspx?f=255&MSPPError=-2147217396)です。 Azure SQL Database のトラブルシューティングの Dmv にアクセスするには、サーバー管理者をする必要があります。
  
### <a name="permissions"></a>アクセス許可  

 すべてのユーザーには、グローバルの一時オブジェクトを作成できます。 ユーザーは追加の権限を付与されない限り、自分で作成したオブジェクトにしかアクセスできません。 のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。  
  
### <a name="examples"></a>使用例 

- セッション A は、Azure SQL Database testdb1 に ##test グローバル一時テーブルを作成し、1 行を追加

```sql
CREATE TABLE ##test ( a int, b int);
INSERT INTO ##test values (1,1);

--Obtain object ID for temp table ##test 
SELECT OBJECT_ID('tempdb.dbo.##test') AS 'Object ID'; 

---Result
1253579504

---Obtain global temp table name for a given object ID 1253579504 in tempdb (2)
SELECT name FROM tempdb.sys.objects WHERE object_id = 1253579504

---Result
##test
```
- セッション B は、Azure SQL Database testdb1 に接続し、##test セッション A で作成されたテーブルにアクセスできます。

```sql
SELECT * FROM ##test
---Results
1,1
```

- C のセッションでは、Azure SQL Database testdb2 で別のデータベースに接続する、##test testdb1 で作成したにアクセスしようとします。 この選択は、グローバルな一時テーブルのデータベース スコープのため失敗します。 

```sql
SELECT * FROM ##test
---Results
Msg 208, Level 16, State 0, Line 1
Invalid object name '##test'
```

- 現在のユーザー データベース testdb1 から Azure SQL データベース tempdb 内のシステム オブジェクトのアドレス指定

```sql
SELECT * FROM tempdb.sys.objects
SELECT * FROM tempdb.sys.columns
SELECT * FROM tempdb.sys.database_files
```



## <a name="partitioned-tables"></a>パーティション テーブル  
 CREATE TABLE を使用してパーティション テーブルを作成するには、まず、テーブルをパーティション分割する方法を指定するパーティション関数を作成する必要があります。 使用して、パーティション関数が作成された[CREATE PARTITION FUNCTION](../../t-sql/statements/create-partition-function-transact-sql.md)です。 次に、パーティション構成を作成する必要があります。パーティション構成では、パーティション関数が示すパーティションを保持するファイル グループを指定します。 使用して、パーティション構成が作成された[CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md)です。 パーティション テーブルでは、PRIMARY KEY 制約または UNIQUE 制約を別のファイル グループに配置するよう指定できません。 詳細については、「 [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md)」を参照してください。  
  
## <a name="primary-key-constraints"></a>PRIMARY KEY 制約  
  
-   テーブルに含めることができる PRIMARY KEY 制約は 1 つだけです。  
  
-   PRIMARY KEY 制約によって生成されたインデックスが含まれていても、テーブル上のインデックスの数を、非クラスター化インデックス 999 個、クラスター化インデックス 1 個より多くすることはできません。  
  
-   PRIMARY KEY 制約に対して CLUSTERED または NONCLUSTERED が指定されていない場合は、UNIQUE 制約にクラスター化インデックスが指定されていなければ、CLUSTERED が使用されます。  
  
-   PRIMARY KEY 制約中で定義する列はすべて、NOT NULL として定義する必要があります。 NULL 値を許容するかどうかを指定しない場合、PRIMARY KEY 制約の影響を受けるすべての列は NOT NULL に設定されます。  
  
    > [!NOTE]  
    >  メモリ最適化テーブルでは、null 許容のキー列が許可されます。  
  
-   CLR ユーザー定義型の列に対して主キーを定義する場合は、型の実装でバイナリ順がサポートされている必要があります。 詳細については、「 [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)」を参照してください。  
  
## <a name="unique-constraints"></a>UNIQUE 制約  
  
-   UNIQUE 制約に対して CLUSTERED または NONCLUSTERED が指定されていない場合は、特に指定がない限り、NONCLUSTERED が使用されます。  
  
-   個々の UNIQUE 制約はインデックスを生成します。 UNIQUE 制約の数が増えても、テーブル上のインデックスの数を、非クラスター化インデックス 999 個、クラスター化インデックス 1 個より多くすることはできません。  
  
-   CLR ユーザー定義型の列に対して一意の UNIQUE 制約を定義する場合は、型の実装でバイナリ順または演算子順がサポートされている必要があります。 詳細については、「 [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)」を参照してください。  
  
## <a name="foreign-key-constraints"></a>外部キー制約  
  
-   FOREIGN KEY 制約の列に NULL 以外の値を入力するときは、その値が参照される列に存在している必要があります。存在していないと外部キー違反のエラー メッセージが返されます。  
  
-   FOREIGN KEY 制約は、変換元列が指定されている場合を除き、前の列に適用されます。  
  
-   FOREIGN KEY 制約は、同じサーバー上の同じデータベース内のテーブルのみを参照できます。 複数のデータベースにまたがる参照整合性は、トリガーを使って実装する必要があります。 詳細については、「[CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)」を参照してください。  
  
-   FOREIGN KEY 制約は、同じテーブル内の他の列を参照できます。 これは、自己参照と呼ばれます。  
  
-   列レベルの FOREIGN KEY 制約の REFERENCES 句は、参照列を 1 つだけ表示できます。 この参照列は、制約が定義されている列と同じデータ型である必要があります。  
  
-   テーブルレベルの FOREIGN KEY 制約の REFERENCES 句は、制約列リスト内の列の数と同じ数の参照列を持っている必要があります。 また、各参照列のデータ型は、列リスト内の、参照列に対応する列と同じでなければなりません。  
  
-   CASCADE、SET NULL、または既定値の設定を指定することはできません型の列の場合**タイムスタンプ**外部キーまたは参照先キーの一部です。  
  
-   CASCADE、SET NULL、SET DEFAULT および NO ACTION は、互いに参照関係にあるテーブルに対して組み合わせて使用することができます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] が NO ACTION を検出すると、関連する CASCADE、SET NULL および SET DEFAULT 操作が停止されロールバックされます。 DELETE ステートメントの実行によって、CASCADE、SET NULL、SET DEFAULT および NO ACTION 操作の組み合わせが適用される場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] が NO ACTION があるかどうかを調べる前にすべての CASCADE、SET NULL および SET DEFAULT 操作が適用されます。  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)] には、他のテーブルを参照するテーブルに含めることができる FOREIGN KEY 制約の数についても、特定のテーブルを参照する他のテーブルが持つ FOREIGN KEY 制約の数についても、事前定義済みの制限はありません。  
  
     ただし、使用できる FOREIGN KEY 制約の実際の数は、ハードウェア構成やデータベースおよびアプリケーションのデザインにより制限されます。 1 つのテーブルに含める FOREIGN KEY 制約は 253 個までとし、253 個以内の FOREIGN KEY 制約から参照することをお勧めします。 効率的な制限は、アプリケーションとハードウェアにある程度依存します。 データベースやアプリケーションをデザインする際には、FOREIGN KEY 制約を適用することのコストを考慮してください。  
  
-   FOREIGN KEY 制約は一時テーブルには設定されません。  
  
-   FOREIGN KEY 制約は、参照されているテーブルの PRIMARY KEY 制約または UNIQUE 制約の中の列だけを参照できます。  
  
-   CLR ユーザー定義型の列に対して外部キーを定義する場合は、型の実装でバイナリ順がサポートされている必要があります。 詳細については、「 [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)」を参照してください。  
  
-   外部キー リレーションシップに参加する列は、長さおよび小数点以下桁数を同じにして定義してください。  
  
## <a name="default-definitions"></a>DEFAULT 定義  
  
-   1 つの列は DEFAULT 定義を 1 つだけ持つことができます。  
  
-   DEFAULT 定義には、定数値、関数、SQL 標準ニラディック関数、または NULL を含めることができます。 次の表は、ニラディック関数と、ニラディック関数が INSERT ステートメントの実行中に既定値として返す値を示しています。  
  
    |SQL-92 ニラディック関数|返される値|  
    |------------------------------|--------------------|  
    |CURRENT_TIMESTAMP|現在の日付と時刻です。|  
    |CURRENT_USER|挿入を実行しているユーザーの名前です。|  
    |SESSION_USER|挿入を実行しているユーザーの名前です。|  
    |SYSTEM_USER|挿入を実行しているユーザーの名前です。|  
    |User|挿入を実行しているユーザーの名前です。|  
  
-   *constant_expression*定義は、既定値で、テーブル内の別の列に、またはその他のテーブル、ビュー、またはストアド プロシージャを参照できません。  
  
-   持つ列の DEFAULT 定義を作成することはできません、**タイムスタンプ**データ型または IDENTITY プロパティを持つ列。  
  
-   別名データ型が既定のオブジェクトにバインドされている場合、別名データ型を持つ列に DEFAULT 定義を作成することはできません。  
  
## <a name="check-constraints"></a>CHECK 制約  
  
-   列は CHECK 制約をいくつでも持つことが可能で、条件には、AND および OR で結合された複数の論理式を含めることができます。 列に対する複数の CHECK 制約は、作成された順に検証されます。  
  
-   検索条件はブール式によって評価する必要があり、他のテーブルを参照することはできません。  
  
-   列レベルの CHECK 制約は、制約された列のみを参照でき、テーブルレベルの CHECK 制約は、同じテーブル内の列のみを参照できます。  
  
     CHECK CONSTRAINTS とルールは、INSERT ステートメントと UPDATE ステートメントの実行中のデータの検証という同じ役割を果たします。  
  
-   列に対して 1 つのルールおよび複数の CHECK 制約がある場合、すべての制限が評価されます。  
  
-   CHECK 制約を定義することはできません**テキスト**、 **ntext**、または**イメージ**列です。  
  
## <a name="additional-constraint-information"></a>制約に関する追加情報  
  
-   制約に対して作成されたインデックスは、DROP INDEX で削除することはできません。ALTER TABLE を使用して制約を削除する必要があります。 制約に対して作成され、制約によって使用されるインデックスは、ALTER INDEX...REBUILD を使用して再構築できます。 詳細については、「 [インデックスの再編成と再構築](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)」を参照してください。  
  
-   制約名の規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md),、名前に番号記号を開始できません点が異なります (#)。 場合*constraint_name*が指定されていない、システムによって生成された名前を割り当て、制約にします。 制約の違反に関するすべてのエラー メッセージには、制約名が表示されます。  
  
-   INSERT ステートメント、UPDATE ステートメントまたは DELETE ステートメントで制約の違反があった場合は、ステートメントが終了します。 ただし、SET XACT_ABORT に OFF が設定されている場合は、トランザクション (ステートメントが明示的なトランザクションの一部である場合) の処理は続行されます。 SET XACT_ABORT に ON が設定されている場合は、トランザクション全体がロールバックされます。 チェックして、トランザクション定義付きの ROLLBACK TRANSACTION ステートメントを使用することもできます、@@ERRORシステム関数です。  
  
-   ALLOW_ROW_LOCKS が ON かつ ALLOW_PAGE_LOCK が ON の場合、インデックスにアクセスするときに行レベル、ページ レベル、テーブル レベルのロックが許可されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]適切なロックを選択し、行またはページ ロックからテーブル ロックのロックをエスカレートすることができます。 ALLOW_ROW_LOCKS = OFF かつ ALLOW_PAGE_LOCK = OFF の場合は、インデックスにアクセスするときにテーブル レベルのロックだけが許可されます。  
  
-   テーブルが FOREIGN KEY 制約または CHECK 制約とトリガーを持っている場合、制約条件は、トリガーが実行される前に評価されます。  
  
 テーブルとその列でレポートを**sp_help**または**sp_helpconstraint**です。 テーブルの名前を変更するには使用**sp_rename**です。 テーブルに依存するストアド プロシージャ、ビューでレポートを[sys.dm_sql_referenced_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)と[sys.dm_sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)です。  
  
## <a name="nullability-rules-within-a-table-definition"></a>テーブル定義内での NULL 値許容の規則  
 列に NULL 値を許容するかどうかは、その列にデータとして NULL 値を入力できるかどうかを決めるものです。 NULL は 0 でも空白でもありません。NULL は、何も入力されなかった、または明示的な NULL が供給されたことを意味し、通常、値が未知である、または使用できないことを示します。  
  
 CREATE TABLE または ALTER TABLE でテーブルを作成または変更すると、データベースとセッションの設定は、列定義で使われているデータ型に NULL 値を許容するかどうかの設定に影響を及ぼし、場合によっては、NULL 値の許容を無効にします。 計算列でない場合は、常に列を明示的に NULL または NOT NULL として定義することをお勧めします。ユーザー定義データ型を使用する場合は、データ型に NULL 値を許容するかどうかの既定の設定を列が使用できるようにすることをお勧めします。 スパース列では常に NULL を許容する必要があります。  
  
 明示的に指定しない場合、列に対して NULL 値を許容するかどうかは以下の表に示す規則に従います。  
  
|[列データ型]|Rule|  
|----------------------|----------|  
|別名データ型|[!INCLUDE[ssDE](../../includes/ssde-md.md)]は、データ型が作成されたときに指定された NULL 値を許容するかどうかの設定を使用します。 データ型の既定の null 値を調べるには使用**sp_help**です。|  
|CLR ユーザー定義型 (CLR user-defined type)|NULL 値を許容するかどうかは列の定義によって決まります。|  
|システムから提供されているデータ型|システムから提供されているデータ型にオプションが 1 つしかない場合は、それが優先されます。 **タイムスタンプ**データ型である必要がありますが NOT NULL します。 SET を使用してセッションの設定が ON に設定されている場合<br />**ANSI_NULL_DFLT_ON** = ON の場合、NULL が割り当てられます。  <br />**ANSI_NULL_DFLT_OFF** = ON の場合、NULL が割り当てられます。<br /><br /> ALTER DATABASE を使用してデータベース設定が構成されている場合<br />**ANSI_NULL_DEFAULT_ON** = ON の場合、NULL が割り当てられます。  <br />**ANSI_NULL_DEFAULT_OFF** = ON の場合、NULL が割り当てられます。<br /><br /> ANSI_NULL_DEFAULT のデータベース設定を表示する、 **sys.databases**カタログ ビュー|  
  
 どちらの ANSI_NULL_DFLT オプションもセッションに設定されていない状態で、データベースが既定値 (ANSI_NULL_DEFAULT が OFF) に設定されていると、既定値である NOT NULL が割り当てられます。  
  
 によって、null 値許容属性が決まります常に自動的に列が計算列の場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。 この種類の列の null 値を調べるには、COLUMNPROPERTY 関数で使用して、 **AllowsNull**プロパティです。  
  
> [!NOTE]  
>  SQL Server ODBC ドライバーでも Microsoft OLE DB Provider for SQL Server でも、特に指定のない限り ANSI_NULL_DFLT_ON が ON に設定されます。 ODBC ユーザーと OLE DB ユーザーは、ODBC データ ソースで、またはアプリケーションで設定される接続の属性またはプロパティを使って、これを構成することができます。  
  
## <a name="data-compression"></a>Data Compression  
 システム テーブルで圧縮を有効にすることはできません。 特に指定しない限り、データ圧縮はテーブルの作成時に NONE に設定されます。 範囲外の一連のパーティションまたは単独のパーティションを指定すると、エラーが生成されます。 データ圧縮の詳細については、「 [データの圧縮](../../relational-databases/data-compression/data-compression.md)」を参照してください。  
  
 圧縮状態の変更による、テーブル、インデックス、またはパーティションへの影響を評価するには、 [sp_estimate_data_compression_savings](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md) ストアド プロシージャを使用します。  
  
## <a name="permissions"></a>アクセス許可  
 データベースの CREATE TABLE 権限と、テーブルを作成するスキーマの ALTER 権限が必要です。  
  
 CLR ユーザー定義型にするのには、CREATE TABLE ステートメント内の列が定義されている場合、型の所有権か、それに対する REFERENCES 権限が必要です。  
  
 CREATE TABLE ステートメント内の列に XML スキーマ コレクションが関連付けられている場合は、その XML スキーマ コレクションの所有権か、そのスキーマ コレクションに対する REFERENCES 権限が必要です。  
  
 すべてのユーザーは、tempdb の一時テーブルを作成することができます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-create-a-primary-key-constraint-on-a-column"></a>A. 列に PRIMARY KEY 制約を作成する  
 次の例で、クラスター化インデックス、PRIMARY KEY 制約の列定義を示しています、`EmployeeID`の列、`Employee`テーブル。 制約名を指定していないため、制約名はシステムによって提供されます。  
  
```  
CREATE TABLE dbo.Employee (EmployeeID int  
PRIMARY KEY CLUSTERED);  
```  
  
### <a name="b-using-foreign-key-constraints"></a>B. FOREIGN KEY 制約を使用する  
 FOREIGN KEY 制約は、他のテーブルを参照するために使用します。 外部キーは単一列キーの場合も複数列キーの場合もあります。 次の例では、単一列 FOREIGN KEY 制約を示して上、`SalesOrderHeader`を参照するテーブル、`SalesPerson`テーブル。 単一列 FOREIGN KEY 制約では、REFERENCES 句のみが必要とされます。  
  
```  
SalesPersonID int NULL  
REFERENCES SalesPerson(SalesPersonID)  
```  
  
 FOREIGN KEY 句を明示的に使用して、列属性を書き換えることもできます。 列名が両方のテーブルで同じである必要はないことに注意してください。  
  
```  
FOREIGN KEY (SalesPersonID) REFERENCES SalesPerson(SalesPersonID)  
```  
  
 複数列キー制約はテーブル制約として作成されます。 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース内の `SpecialOfferProduct` テーブルには、複数列 PRIMARY KEY が含まれています。 次の例は、このキーを他のテーブルから参照する方法を示しています。明示的な制約名は省略可能です。  
  
```  
CONSTRAINT FK_SpecialOfferProduct_SalesOrderDetail FOREIGN KEY  
 (ProductID, SpecialOfferID)  
REFERENCES SpecialOfferProduct (ProductID, SpecialOfferID)  
```  
  
### <a name="c-using-unique-constraints"></a>C. UNIQUE 制約を使用する  
 UNIQUE 制約は、非主キー列に一意性を設定するために使用します。 次の例では、`Name` テーブルの `Product` 列が一意でなくてはならないという制限を課しています。  
  
```  
Name nvarchar(100) NOT NULL  
UNIQUE NONCLUSTERED  
```  
  
### <a name="d-using-default-definitions"></a>D. DEFAULT 定義を使用する  
 既定値は (INSERT ステートメントおよび UPDATE ステートメントと組み合わせて使用され)、値が何も提供されていないときに、値を提供します。 たとえば、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースは、会社内で従業員が行うさまざまな職務を列挙する参照テーブルを含むことができます。 各職務の説明を示す列に、実際の説明が明示的に入力されなかったときの説明となる既定の文字列を指定できます。  
  
```  
DEFAULT 'New Position - title not formalized yet'  
```  
  
 DEFAULT 定義には、定数の他に関数を含めることができます。 次の例を使用すると、エントリの現在の日付が取得できます。  
  
```  
DEFAULT (getdate())  
```  
  
 ニラディック関数スキャンの使用により、データ整合性を向上させることもできます。 行を挿入したユーザーを追跡するには、USER 用ニラディック関数を使用します。 ニラディック関数をかっこで囲まないでください。  
  
```  
DEFAULT USER  
```  
  
### <a name="e-using-check-constraints"></a>E. CHECK 制約を使用する  
 次の例に入力された値に対する制限を示しています、`CreditRating`の列、`Vendor`テーブル。 制約には名前がありません。  
  
```  
CHECK (CreditRating >= 1 and CreditRating <= 5)  
```  
  
 この例は、テーブルの列に入力される文字データのパターンを制限する名前付き制約を示しています。  
  
```  
CONSTRAINT CK_emp_id CHECK (emp_id LIKE   
'[A-Z][A-Z][A-Z][1-9][0-9][0-9][0-9][0-9][FM]'   
OR emp_id LIKE '[A-Z]-[A-Z][1-9][0-9][0-9][0-9][0-9][FM]')  
```  
  
 この例では、値が特定のリストの範囲内にあるか、特定のパターンに従う必要があるという条件を指定しています。  
  
```  
CHECK (emp_id IN ('1389', '0736', '0877', '1622', '1756')  
OR emp_id LIKE '99[0-9][0-9]')  
```  
  
### <a name="f-showing-the-complete-table-definition"></a>F. 完全なテーブル定義を表示する  
 次の例は、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース内に作成された `PurchaseOrderDetail` テーブルの完全なテーブル定義とすべての制約定義を示します。 サンプルを実行するテーブルのスキーマが変更されたことに注意してください`dbo`です。  
  
```  
CREATE TABLE dbo.PurchaseOrderDetail  
(  
    PurchaseOrderID int NOT NULL  
        REFERENCES Purchasing.PurchaseOrderHeader(PurchaseOrderID),  
    LineNumber smallint NOT NULL,  
    ProductID int NULL   
        REFERENCES Production.Product(ProductID),  
    UnitPrice money NULL,  
    OrderQty smallint NULL,  
    ReceivedQty float NULL,  
    RejectedQty float NULL,  
    DueDate datetime NULL,  
    rowguid uniqueidentifier ROWGUIDCOL  NOT NULL  
        CONSTRAINT DF_PurchaseOrderDetail_rowguid DEFAULT (newid()),  
    ModifiedDate datetime NOT NULL   
        CONSTRAINT DF_PurchaseOrderDetail_ModifiedDate DEFAULT (getdate()),  
    LineTotal  AS ((UnitPrice*OrderQty)),  
    StockedQty  AS ((ReceivedQty-RejectedQty)),  
    CONSTRAINT PK_PurchaseOrderDetail_PurchaseOrderID_LineNumber  
               PRIMARY KEY CLUSTERED (PurchaseOrderID, LineNumber)  
               WITH (IGNORE_DUP_KEY = OFF)  
)   
ON PRIMARY;  
```  
  
### <a name="g-creating-a-table-with-an-xml-column-typed-to-an-xml-schema-collection"></a>G. XML スキーマ コレクションに型指定された xml 列を含むテーブルを作成する  
 次の例では、XML スキーマ コレクション `xml` 型の `HRResumeSchemaCollection` 列を持つテーブルを作成します。 `DOCUMENT`キーワードを指定するの各インスタンス、`xml`のデータ型の*column_name* 1 つだけの最上位要素を含めることができます。  
  
```  
CREATE TABLE HumanResources.EmployeeResumes   
   (LName nvarchar(25), FName nvarchar(25),   
    Resume xml( DOCUMENT HumanResources.HRResumeSchemaCollection) );  
```  
  
### <a name="h-creating-a-partitioned-table"></a>H. パーティション分割されたテーブルを作成する  
 次の例では、テーブルまたはインデックスを 4 つのパーティションに分割するパーティション関数を作成します。 次に、4 つのパーティションをそれぞれ保持するファイル グループを指定するパーティション構成を作成します。 最後に、そのパーティション構成を使用するテーブルを作成します。 この例では、ファイル グループが既にデータベースに存在していると仮定しています。  
  
```  
CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES (1, 100, 1000) ;  
GO  
  
CREATE PARTITION SCHEME myRangePS1  
    AS PARTITION myRangePF1  
    TO (test1fg, test2fg, test3fg, test4fg) ;  
GO  
  
CREATE TABLE PartitionTable (col1 int, col2 char(10))  
    ON myRangePS1 (col1) ;  
GO  
```  
  
 列の値に基づいて`col1`の`PartitionTable`パーティションは、次のように割り当てられます。  
  
|[ファイル グループ]|test1fg|test2fg|test3fg|test4fg|  
|---------------|-------------|-------------|-------------|-------------|  
|**パーティション**|@shouldalert|2|3|4|  
|**値**|col 1 \<= 1|col1 > 1 の AND col1 \<= 100|col1 > 100 AND col1 \<1,000 を =|col1 > 1000|  
  
### <a name="i-using-the-uniqueidentifier-data-type-in-a-column"></a>I. 列で uniqueidentifier データ型を使用する  
 次の例を含むテーブルを作成する、`uniqueidentifier`列です。 この例では、PRIMARY KEY 制約を使用して、重複する値を挿入するユーザーを対象とするテーブルの保護を使用して、`NEWSEQUENTIALID()`で機能、`DEFAULT`新しい行の値を指定する制約です。 また、$ROWGUID キーワードを使用して参照できるように、この `uniqueidentifier` 列に ROWGUIDCOL プロパティを適用します。  
  
```  
CREATE TABLE dbo.Globally_Unique_Data  
    (guid uniqueidentifier   
        CONSTRAINT Guid_Default DEFAULT   
        NEWSEQUENTIALID() ROWGUIDCOL,  
    Employee_Name varchar(60)  
    CONSTRAINT Guid_PK PRIMARY KEY (guid) );  
```  
  
### <a name="j-using-an-expression-for-a-computed-column"></a>J. 計算列に式を使用する  
 次の例は、式 (`(low + high)/2`) を使用して `myavg` 計算列を計算する方法を示しています。  
  
```  
CREATE TABLE dbo.mytable   
    ( low int, high int, myavg AS (low + high)/2 ) ;  
```  
  
### <a name="k-creating-a-computed-column-based-on-a-user-defined-type-column"></a>K. ユーザー定義型の列に基づいて計算列を作成する  
 次の例は、ユーザー定義型として定義されている 1 つの列を持つテーブルを作成`utf8string`型のアセンブリと、型自身が既に作成されて、現在のデータベースのものと仮定します。 2 番目の列はに基づいて定義`utf8string`、メソッドを使用して`ToString()`の**type (class)** `utf8string`列の値を計算します。  
  
```  
CREATE TABLE UDTypeTable   
    ( u utf8string, ustr AS u.ToString() PERSISTED ) ;  
```  
  
### <a name="l-using-the-username-function-for-a-computed-column"></a>L. 計算列に USER_NAME 関数を使用する  
 次の例では、`USER_NAME()`で機能、`myuser_name`列です。  
  
```  
CREATE TABLE dbo.mylogintable  
    ( date_in datetime, user_id int, myuser_name AS USER_NAME() ) ;  
```  
  
### <a name="m-creating-a-table-that-has-a-filestream-column"></a>M. FILESTREAM 列を含むテーブルを作成する  
 次の例を含むテーブルを作成する、`FILESTREAM`列`Photo`です。 1 つまたは複数が存在する場合`FILESTREAM`列、テーブルには、いずれかが必要`ROWGUIDCOL`列です。  
  
```  
CREATE TABLE dbo.EmployeePhoto  
    (  
    EmployeeId int NOT NULL PRIMARY KEY,  
    ,Photo varbinary(max) FILESTREAM NULL  
    ,MyRowGuidColumn uniqueidentifier NOT NULL ROWGUIDCOL  
        UNIQUE DEFAULT NEWID()  
    );  
```  
  
### <a name="n-creating-a-table-that-uses-row-compression"></a>N. 行の圧縮を使用するテーブルを作成する  
 次の例では、行の圧縮を使用するテーブルを作成します。  
  
```  
CREATE TABLE dbo.T1   
(c1 int, c2 nvarchar(200) )  
WITH (DATA_COMPRESSION = ROW);  
```  
  
 追加のデータ圧縮例については、次を参照してください。[データ圧縮](../../relational-databases/data-compression/data-compression.md)です。  
  
### <a name="o-creating-a-table-that-has-sparse-columns-and-a-column-set"></a>O.  スパース列と列セットを含むテーブルを作成する  
 次の各例では、1 つのスパース列を含むテーブル、および 2 つのスパース列と 1 つの列セットを含むテーブルを作成する方法を示します。 これらの例では基本構文を使用します。 複雑な例については、次を参照してください。[スパース列を使用する](../../relational-databases/tables/use-sparse-columns.md)と[列セットの使用](../../relational-databases/tables/use-column-sets.md)です。  
  
 次の例では、スパース列を含むテーブルを作成します。  
  
```  
CREATE TABLE dbo.T1  
    (c1 int PRIMARY KEY,  
    c2 varchar(50) SPARSE NULL ) ;  
```  
  
 次の例では、2 つのスパース列と `CSet` という 1 つの列セットを含むテーブルを作成します。  
  
```  
CREATE TABLE T1  
    (c1 int PRIMARY KEY,  
    c2 varchar(50) SPARSE NULL,  
    c3 int SPARSE NULL,  
    CSet XML COLUMN_SET FOR ALL_SPARSE_COLUMNS ) ;  
```  
  
### <a name="p-creating-a-system-versioned-disk-based-temporal-table"></a>P. システムのバージョン管理されたディスク ベースの一時的なテーブルを作成します。  
   
  
**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。
  
 次の例では、新しい履歴テーブルにリンクされている一時的なテーブルを作成する方法と、既存の履歴テーブルにリンクされている一時的なテーブルを作成する方法を示しています。 一時的なテーブルでは、主キーがシステムのバージョン管理を有効にするテーブルを有効にするのに定義される場合がありますに注意してください。 例を追加または既存のテーブルでシステム バージョン管理を削除する方法を示す参照システムでバージョン管理[例](../../t-sql/statements/alter-table-transact-sql.md#Example_Top)です。 使用する場合、次を参照してください。[テンポラル テーブル](../../relational-databases/tables/temporal-tables.md)です。  
  
 この例では、新しい履歴テーブルにリンクされている、新しい一時的なテーブルを作成します。  
  
```  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)     
)  
WITH (SYSTEM_VERSIONING = ON);  
```  
  
 この例では、既存の履歴テーブルにリンクされている、新しい一時的なテーブルを作成します。  
  
```  
  
--Existing table   
CREATE TABLE Department_History   
(  
    DepartmentNumber char(10) NOT NULL,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 NOT NULL,   
    SysEndTime datetime2 NOT NULL   
);  
--Temporal table  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID INT  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)    
)  
WITH   
    (SYSTEM_VERSIONING = ON   
        (HISTORY_TABLE = dbo.Department_History, DATA_CONSISTENCY_CHECK = ON )  
    );  
```  
  
### <a name="q-creating-a-system-versioned-memory-optimized-temporal-table"></a>Q.  システムのバージョン管理されたメモリ最適化の一時的なテーブルを作成します。  
   
  
**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。
  
 次の例では、テーブルを作成するシステムのバージョン管理されたメモリ最適化時間的な新しい履歴のディスク ベース テーブルにリンクする方法を示します。  
  
 この例では、新しい履歴テーブルにリンクされている、新しい一時的なテーブルを作成します。  
  
```  
CREATE SCHEMA History  
GO  
CREATE TABLE dbo.Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)     
)  
WITH   
    (  
        MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA,  
            SYSTEM_VERSIONING = ON ( HISTORY_TABLE = History.DepartmentHistory )   
    );  
```  
  
 この例では、既存の履歴テーブルにリンクされている、新しい一時的なテーブルを作成します。  
  
```  
  
--Existing table   
CREATE TABLE Department_History   
(  
    DepartmentNumber char(10) NOT NULL,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 NOT NULL,   
    SysEndTime datetime2 NOT NULL   
);  
--Temporal table  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID INT  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)    
)  
WITH   
    (SYSTEM_VERSIONING = ON   
        (HISTORY_TABLE = dbo.Department_History, DATA_CONSISTENCY_CHECK = ON )  
    );  
```  
  
### <a name="r-creating-a-table-with-encrypted-columns"></a>R.  暗号化された列を含むテーブルを作成します。  
 次の例では、次の 2 つの暗号化された列を含むテーブルを作成します。 詳細については、「[Always Encrypted &#40;データベース エンジン&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)」を参照してください。  
  
```  
CREATE TABLE Customers (  
    CustName nvarchar(60)   
        ENCRYPTED WITH   
            (  
             COLUMN_ENCRYPTION_KEY = MyCEK,  
             ENCRYPTION_TYPE = RANDOMIZED,  
             ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'  
            ),   
    SSN varchar(11) COLLATE  Latin1_General_BIN2  
        ENCRYPTED WITH   
            (  
             COLUMN_ENCRYPTION_KEY = MyCEK,  
             ENCRYPTION_TYPE = DETERMINISTIC ,  
             ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'  
            ),   
    Age int NULL  
);  
```

### <a name="s-create-an-inline-filtered-index"></a>S.  インラインのフィルター選択されたインデックスを作成します。 
インラインのフィルター選択されたインデックスをテーブルを作成します。
  
  ```
  CREATE TABLE t1 
 (
      c1 int,
      index IX1  (c1) WHERE c1 > 0   
 )
GO
 ```
 
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [COLUMNPROPERTY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/columnproperty-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [DROP INDEX &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-index-transact-sql.md)   
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)   
 [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)   
 [DROP TABLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helpconstraint &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpconstraint-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_spaceused &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)  
  
  


