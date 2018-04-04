---
title: ALTER TABLE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- WAIT_AT_LOW_PRIORITY
- ABORT_AFTER_WAIT
- ABORT_AFTER_WAIT_TSQL
- ALTER_TABLE_TSQL
- ALTER TABLE
- WAIT_AT_LOW_PRIORITY_TSQL
- ALTER_COLUMN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- columns [SQL Server], resizing
- changing column size
- MAXDOP index option, ALTER TABLE statement
- table modifications [SQL Server], ALTER TABLE
- ALTER TABLE statement
- modifying tables
- partitioned tables [SQL Server], lock escalation
- resizing columns
- removing columns
- switching partitions
- reassigning partitions
- removing constraints
- triggers [SQL Server], disabling
- columns [SQL Server], adding
- LOCK_ESCALATION option of ALTER TABLE
- constraints [SQL Server], deleting
- constraints [SQL Server], disabling
- triggers [SQL Server], enabling
- re-enabling constraints
- index modifications [SQL Server]
- disabling constraints
- columns [SQL Server], removing
- max degree of parallelism option
- locking [SQL Server], tables
- ONLINE option
- disabling triggers
- constraints [SQL Server], adding
- deleting constraints
- adding constraints
- adding columns
- SWITCH partitions
- partitioned tables [SQL Server], switching
- lock escalation [SQL Server], option of ALTER TABLE
- constraints [SQL Server], enabling
- dropping constraints
- dropping columns
- table changes [SQL Server]
ms.assetid: f1745145-182d-4301-a334-18f799d361d1
caps.latest.revision: ''
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: b4a725960612c90a4619cf16587df0f67a68a3ba
ms.sourcegitcommit: 6e16d1616985d65484c72f5e0f34fb2973f828f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/16/2018
---
# <a name="alter-table-transact-sql"></a>ALTER TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  列と制約の変更、追加、削除、パーティションの再割り当てと再構築、制約とトリガーの無効化や有効化などの方法で、テーブル定義を変更します。  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ALTER TABLE [ database_name . [ schema_name ] . | schema_name . ] table_name   
{   
    ALTER COLUMN column_name   
    {   
        [ type_schema_name. ] type_name   
            [ (   
                {   
                   precision [ , scale ]   
                 | max   
                 | xml_schema_collection   
                }   
            ) ]   
        [ COLLATE collation_name ]   
        [ NULL | NOT NULL ] [ SPARSE ]  
      | { ADD | DROP }   
          { ROWGUIDCOL | PERSISTED | NOT FOR REPLICATION | SPARSE | HIDDEN }  
      | { ADD | DROP } MASKED [ WITH ( FUNCTION = ' mask_function ') ]  
    }   
    [ WITH ( ONLINE = ON | OFF ) ]  
    | [ WITH { CHECK | NOCHECK } ]  
  
    | ADD   
    {   
        <column_definition>  
      | <computed_column_definition>  
      | <table_constraint>   
      | <column_set_definition>   
    } [ ,...n ]  
      | [ system_start_time_column_name datetime2 GENERATED ALWAYS AS ROW START   
                   [ HIDDEN ] [ NOT NULL ] [ CONSTRAINT constraint_name ] 
           DEFAULT constant_expression [WITH VALUES] ,  
            system_end_time_column_name datetime2 GENERATED ALWAYS AS ROW END   
                   [ HIDDEN ] [ NOT NULL ]  [ CONSTRAINT constraint_name ] 
           DEFAULT constant_expression [WITH VALUES] ,  
         ]  
       PERIOD FOR SYSTEM_TIME ( system_start_time_column_name, system_end_time_column_name )  
    | DROP   
     [ {  
         [ CONSTRAINT ]  [ IF EXISTS ]  
         {   
              constraint_name   
              [ WITH   
               ( <drop_clustered_constraint_option> [ ,...n ] )   
              ]   
          } [ ,...n ]  
          | COLUMN  [ IF EXISTS ]  
          {  
              column_name   
          } [ ,...n ]  
          | PERIOD FOR SYSTEM_TIME  
     } [ ,...n ]  
    | [ WITH { CHECK | NOCHECK } ] { CHECK | NOCHECK } CONSTRAINT   
        { ALL | constraint_name [ ,...n ] }   
  
    | { ENABLE | DISABLE } TRIGGER   
        { ALL | trigger_name [ ,...n ] }  
  
    | { ENABLE | DISABLE } CHANGE_TRACKING   
        [ WITH ( TRACK_COLUMNS_UPDATED = { ON | OFF } ) ]  
  
    | SWITCH [ PARTITION source_partition_number_expression ]  
        TO target_table   
        [ PARTITION target_partition_number_expression ]  
        [ WITH ( <low_priority_lock_wait> ) ]  
    | SET   
        (  
            [ FILESTREAM_ON =   
                { partition_scheme_name | filegroup | "default" | "NULL" } ]  
            | SYSTEM_VERSIONING =   
                  {   
                      OFF   
                  | ON   
                      [ ( HISTORY_TABLE = schema_name . history_table_name   
                          [, DATA_CONSISTENCY_CHECK = { ON | OFF } ] 
                          [, HISTORY_RETENTION_PERIOD = 
                          { 
                               INFINITE | number {DAY | DAYS | WEEK | WEEKS 
                 | MONTH | MONTHS | YEAR | YEARS } 
                          } 
                          ]  
                        )  
                      ]  
                  }  
          )  
    | REBUILD   
      [ [PARTITION = ALL]  
        [ WITH ( <rebuild_option> [ ,...n ] ) ]   
      | [ PARTITION = partition_number   
           [ WITH ( <single_partition_rebuild_option> [ ,...n ] ) ]  
        ]  
      ]  
  
    | <table_option>  
  
    | <filetable_option>  
  
    | <stretch_configuration>  
  
}  
[ ; ]  
  
-- ALTER TABLE options  
  
<column_set_definition> ::=   
    column_set_name XML COLUMN_SET FOR ALL_SPARSE_COLUMNS  
  
<drop_clustered_constraint_option> ::=    
    {   
        MAXDOP = max_degree_of_parallelism  
      | ONLINE = { ON | OFF }  
      | MOVE TO   
         { partition_scheme_name ( column_name ) | filegroup | "default" }  
    }  
<table_option> ::=  
    {  
        SET ( LOCK_ESCALATION = { AUTO | TABLE | DISABLE } )  
    }  
  
<filetable_option> ::=  
    {  
       [ { ENABLE | DISABLE } FILETABLE_NAMESPACE ]  
       [ SET ( FILETABLE_DIRECTORY = directory_name ) ]  
    }  
  
<stretch_configuration> ::=  
    {  
      SET (  
        REMOTE_DATA_ARCHIVE   
        {  
            = ON (  <table_stretch_options>  )  
          | = OFF_WITHOUT_DATA_RECOVERY ( MIGRATION_STATE = PAUSED )  
          | ( <table_stretch_options> [, ...n] )  
        }  
            )  
    }  
  
<table_stretch_options> ::=  
    {  
     [ FILTER_PREDICATE = { null | table_predicate_function } , ]  
       MIGRATION_STATE = { OUTBOUND | INBOUND | PAUSED }  
    }  
  
<single_partition_rebuild__option> ::=  
{  
      SORT_IN_TEMPDB = { ON | OFF }  
    | MAXDOP = max_degree_of_parallelism  
    | DATA_COMPRESSION = { NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE} }  
    | ONLINE = { ON [( <low_priority_lock_wait> ) ] | OFF }  
}  
  
<low_priority_lock_wait>::=  
{  
    WAIT_AT_LOW_PRIORITY ( MAX_DURATION = <time> [ MINUTES ], 
        ABORT_AFTER_WAIT = { NONE | SELF | BLOCKERS } )   
}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER TABLE [ database_name . [schema_name ] . | schema_name. ] source_table_name   
{  
    ALTER COLUMN column_name  
        {   
            type_name [ ( precision [ , scale ] ) ]   
            [ COLLATE Windows_collation_name ]   
            [ NULL | NOT NULL ]   
        }  
    | ADD { <column_definition> | <column_constraint> FOR column_name} [ ,...n ]  
    | DROP { COLUMN column_name | [CONSTRAINT] constraint_name } [ ,...n ]  
    | REBUILD {  
            [ PARTITION = ALL [ WITH ( <rebuild_option> ) ] ] 
          | [ PARTITION = partition_number [ WITH ( <single_partition_rebuild_option> ] ]
      } 
    | { SPLIT | MERGE } RANGE (boundary_value)  
    | SWITCH [ PARTITION source_partition_number  
        TO target_table_name [ PARTITION target_partition_number ]  
}  
[;]  
  
<column_definition>::=  
{  
    column_name  
    type_name [ ( precision [ , scale ] ) ]   
    [ <column_constraint> ]  
    [ COLLATE Windows_collation_name ]  
    [ NULL | NOT NULL ]  
}  
  
<column_constraint>::=  
    [ CONSTRAINT constraint_name ] DEFAULT constant_expression  

<rebuild_option > ::=   
{  
    DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }
        [ ON PARTITIONS ( {<partition_number> [ TO <partition_number>] } [ , ...n ] ) ]   
}

<single_partition_rebuild_option > ::=   
{  
    DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
}  
```    

   
## <a name="arguments"></a>引数  
 *database_name*  
 テーブルが作成されたデータベースの名前を指定します。  
  
 *schema_name*  
 テーブルが所属するスキーマの名前を指定します。  
  
 *table_name*  
 変更するテーブルの名前を指定します。 テーブルが現在のデータベースにないか、現在のユーザーが所有するスキーマに含まれていない場合は、データベースとスキーマを明示的に指定する必要があります。  
  
 ALTER COLUMN  
 指定した列に変更を加えます。  
  
 変更する列に、次の列は指定できません。  
  
-   **timestamp** データ型の列。  
  
-   テーブルの ROWGUIDCOL。  
  
-   計算列、または計算列の中で使用される列。  
  
-   CREATE STATISTICS ステートメントによって生成された統計内の列。ただし、その列のデータ型が **varchar** 型、**nvarchar** 型、または **varbinary** 型であり、データ型の変更がなく、新しいサイズが前のサイズ以上になる場合と、列が NOT NULL から NULL に変更される場合は除きます。 最初に、DROP STATISTICS ステートメントで統計を削除します。 クエリ オプティマイザーによって自動的に生成された統計は、ALTER COLUMN によって自動的に削除されます。  
  
-   PRIMARY KEY 制約、または [FOREIGN KEY] REFERENCES 制約で使用されている列。  
  
-   CHECK 制約、または UNIQUE 制約で使用されている列。 ただし、CHECK 制約または UNIQUE 制約の中で使用されている可変長列の長さを変更することはできます。  
  
-   既定の定義に関連付けられている列。 ただし、データ型を変更しなければ、列の長さ、有効桁数、または小数点以下桁数は変更できます。  
  
**text** 型、**ntext** 型、および **image** 型の列は、次の方法でのみ変更できます。  
  
-   **text** を **varchar(max)**、**nvarchar(max)**、または **xml** へ  
  
-   **ntext** を **varchar(max)**、**nvarchar(max)**、または **xml** へ  
  
-   **image** を **varbinary(max)** へ  
  
データ型を変更すると、データが変更される可能性があります。 たとえば、**nchar** 型または **nvarchar** 型の列を **char** 型または **varchar** 型に変更すると、拡張文字が変換される場合があります。 詳細については、「[CAST and CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)」を参照してください。 列の有効桁数または小数点以下桁数を減らすと、データが切り捨てられる可能性があります。  
  
> [!NOTE]
> パーティション テーブルの列のデータ型は変更できません。  
>  
> 列のデータ型が **varchar**、**nvarchar**、または **varbinary** 以外で、新しいサイズが前のサイズよりも小さい場合、インデックスに含まれている列のデータ型は変更できません。  
>  
> 主キー制約に含まれている列は、**NOT NULL** から **NULL** に変更できません。  
  
変更する列が `ENCRYPTED WITH` を使用して暗号化されている場合は、データ型を互換性のあるデータ型に変更することはできますが (INT から BIGINT への変更など)、暗号化設定を変更することはできません。  
  
 *column_name*  
 変更、追加、または削除する列の名前を指定します。 *column_name* には、最大 128 文字まで指定できます。 **timestamp** データ型で作成された新しい列の場合、*column_name* は省略できます。 **timestamp** データ型列に *column_name* が指定されていない場合は、**timestamp** という名前が使用されます。  
  
 [ *type_schema_name***.** ] *type_name*  
 更新する列の新しいデータ型、または追加する列のデータ型を指定します。 *type_name* は、パーティション テーブルの既存の列には指定できません。 *type_name* には次のいずれかを指定できます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム データ型。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム データ型に基づく別名データ型。 別名データ型は、CREATE TYPE ステートメントで作成した後、テーブル定義で使用できます。  
  
-   [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ユーザー定義型とそれが属するスキーマ。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ユーザー定義型は、CREATE TYPE ステートメントで作成した後、テーブル定義で使用できます。  
  
変更する列に対して *type_name* を指定する場合の条件を次に示します。  
  
-   以前のデータ型は、新しいデータ型に自動的に変換される必要があります。  
-   *type_name* を **timestamp** にすることはできません。  
-   ANSI_NULL の既定値は ALTER COLUMN に対して常にオンです。指定しなかった場合、列では NULL 値が許容されます。  
-   ANSI_PADDING の埋め込みは ALTER COLUMN に対して常にオンです。  
-   変更する列が ID 列の場合、*new_data_type* は、ID プロパティをサポートするデータ型であることが必要です。  
-   SET ARITHABORT の現在の設定値は無視されます。 ALTER TABLE は、ARITHABORT がオンに設定されている場合と同様に動作します。  
  
> [!NOTE]  
> COLLATE 句を指定しないで列のデータ型を変更すると、照合順序が、データベースの既定値とは異なってしまう場合があります。  
  
 *有効桁数 (precision)*  
 指定されるデータ型の有効桁数です。 有効桁数の詳細については、「[有効桁数、小数点以下桁数、および長さ &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md)」を参照してください。  
  
 *scale*  
 指定されるデータ型の小数点以下桁数です。 有効な小数点以下桁数の詳細については、「[有効桁数、小数点以下桁数、および長さ &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md)」を参照してください。  
  
 **max**  
 データ型 **varchar**、**nvarchar**、**varbinary** だけに適用され、2^31-1 バイトの文字データ、バイナリ データ、および Unicode データが格納されます。  
  
 *xml_schema_collection*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 **xml** 型にのみ適用されます。XML スキーマを関連付ける場合に使用します。 **xml** 列をスキーマ コレクションに入力するには、先に [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md) を使ってスキーマ コレクションをデータベース内に作成する必要があります。  
  
COLLATE \< *collation_name* > 変更する列の新しい照合順序を指定します。 照合順序を指定しない場合、データベースの既定の照合順序が列に割り当てられます。 照合順序名には、Windows 照合順序名または SQL 照合順序名を指定できます。 一覧と詳細については、「[Windows 照合順序名 &#40;Transact-SQL&#41;](../../t-sql/statements/windows-collation-name-transact-sql.md)」と「[SQL Server 照合順序名 &#40;Transact-SQL&#41;](../../t-sql/statements/sql-server-collation-name-transact-sql.md)」を参照してください。  
  
 COLLATE 句を使用して照合順序を変更できるのは、**char**データ型、**varchar** データ型、**nchar** データ型、**nvarchar** データ型の列だけです。 ユーザー定義の別名データ型列の照合順序を変更するには、別の ALTER TABLE ステートメントを実行して列を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム データ型に変更し、その照合順序を変更した後、その列を別名データ型に戻します。  
  
 次の条件の 1 つ以上に該当する場合、ALTER COLUMN で照合順序を変更することはできません。  
  
-   CHECK 制約、FOREIGN KEY 制約、またはその列を参照する計算列が変更された場合。  
-   列にインデックス、統計、またはフルテキスト インデックスが作成された場合。 変更する列に対して自動的に作成された統計は、列の照合順序を変更すると削除されます。  
-   スキーマ バインド ビューまたは関数で列が参照されている場合。  
  
詳細については、「[COLLATE &#40;Transact-SQL&#41;](~/t-sql/statements/collations.md)」を参照してください。  
  
NULL | NOT NULL  
 列で NULL 値が許容されるかどうかを指定します。 NULL 値が許容されない列は、既定値が列に指定されているか、テーブルが空の場合にのみ、ALTER TABLE で追加できます。 計算列で NOT NULL を指定できるのは、同時に PERSISTED も指定した場合だけです。 新しい列で NULL 値が許容され、既定値を指定しない場合、テーブル内の各行の新しい列には NULL 値が格納されます。 新しい列で NULL 値が許容され、新しい列と共に既定の定義を追加した場合は、WITH VALUES を使用して、テーブル内にある各行の新しい列に既定値を格納できます。  
  
 新しい列で NULL 値が許容されず、テーブルが空でない場合は、新しい列と共に DEFAULT 定義を追加する必要があります。これによって、既存の各行の新しい列には既定値が自動的に読み込まれます。  
  
 ALTER COLUMN に NULL を指定することによって、NOT NULL 列で NULL 値が許容されるように設定できます。ただし、PRIMARY KEY 制約の列は除きます。 ALTER COLUMN に NOT NULL を指定できるのは、列に NULL 値が格納されていないときだけです。 ALTER COLUMN NOT NULL を指定する前に、NULL 値を別の値に更新しておく必要があります。たとえば次のように行います。  
  
```sql  
UPDATE MyTable SET NullCol = N'some_value' WHERE NullCol IS NULL;  
ALTER TABLE MyTable ALTER COLUMN NullCOl NVARCHAR(20) NOT NULL;  
```  
  
 CREATE TABLE ステートメントまたは ALTER TABLE ステートメントでテーブルを作成または変更すると、データベースとセッションの設定によって、列定義で使われているデータ型の NULL 許容属性が影響を受けたり、場合によっては無効になることがあります。 計算列でない場合は、常に列を明示的に NULL または NOT NULL として定義することをお勧めします。  
  
 ユーザー定義データ型の列を追加する場合は、NULL 値を許容するかどうかの設定がユーザー定義データ型と同じになるように列を定義し、列の既定値を指定することをお勧めします。 詳細については、「[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)」を参照してください。  
  
> [!NOTE]  
> ALTER COLUMN に NULL または NOT NULL を指定した場合は、*new_data_type* [(*precision* [, *scale* ])] も指定する必要があります。 データ型、有効桁数、小数点以下桁数を変更しない場合は、その列の現在の値を指定します。  
  
 [ {ADD | DROP} ROWGUIDCOL ]  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 指定した列に対して ROWGUIDCOL プロパティが追加または削除されます。 ROWGUIDCOL は、列が行の GUID 列であることを示します。 各テーブルでは 1 つの **uniqueidentifier** 列のみを ROWGUIDCOL 列として指定できます。ROWGUIDCOL プロパティは、**uniqueidentifier** 列にのみ割り当てることができます。 ROWGUIDCOL は、ユーザー定義データ型の列に割り当てることはできません。  
  
 ROWGUIDCOL では列に一意な値が格納されるわけではなく、またテーブルに挿入される新しい行に対して値は自動的に生成されません。 各列に一意な値を生成するには、INSERT ステートメントで NEWID 関数を使用するか、列の既定値として NEWID 関数を指定します。  
  
 [ {ADD | DROP} PERSISTED ]  
 指定した列に対して PERSISTED プロパティが追加または削除されます。 列は、決定的な式で定義される計算列であることが必要です。 PERSISTED として指定した列では、[!INCLUDE[ssDE](../../includes/ssde-md.md)] によって物理的にテーブルに計算値が格納され、計算列が依存している他の列が更新されるとその計算値も更新されます。 計算列を PERSISTED とマークすることにより、決定的であるが不正確な式によって定義されている計算列にインデックスを作成できます。 詳細については、「 [計算列のインデックス](../../relational-databases/indexes/indexes-on-computed-columns.md)」を参照してください。  
  
 パーティション テーブルのパーティション分割列として使用する計算列には、明示的に PERSISTED とマークする必要があります。  
  
 DROP NOT FOR REPLICATION  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 レプリケーション エージェントで挿入操作が実行されるときに、ID 列の値を増分することを指定します。 この句は *column_name* が ID 列の場合にのみ指定できます。  
  
 SPARSE  
 列がスパース列であることを示します。 スパース列のストレージは NULL 値用に最適化されます。 スパース列を NOT NULL として指定することはできません。 スパース列を非スパース列に変換したり、非スパース列をスパース列に変換すると、コマンドの実行中にテーブルがロックされます。 REBUILD 句を使用して領域の節約を要求することが必要な場合があります。 スパース列のその他の制限事項と詳細については、「[スパース列の使用](../../relational-databases/tables/use-sparse-columns.md)」を参照してください。  
  
 ADD MASKED WITH ( FUNCTION = ' *mask_function* ')  
 **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 動的なデータのマスクを指定します。 *mask_function* マスキング関数は、適切なパラメーターの名前を指定します。 3 つの関数を使用できます。  
  
-   default()  
-   email()  
-   partial()  
-   random()  
  
 マスクを削除するには、`DROP MASKED` を使用します。 関数のパラメーターについては、「[動的なデータ マスキング](../../relational-databases/security/dynamic-data-masking.md)」を参照してください。  
  
WITH ( ONLINE = ON | OFF) (\<列の変更の適用対象として>)  
 **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 テーブルを使用可能な状態に維持したまま実行する列の変更操作の多くを許可します。 既定値は OFF です。 列の変更は、データ型、列の長さまたは有効桁数、Null 値の許容、スパースかどうか、および照合順序に関連する列の変更をオンラインで実行できます。  
  
 オンラインでの列の変更では、ユーザー作成の統計と自動統計で ALTER COLUMN 操作の実行中に変更された列を参照することができます。 これにより、クエリを通常どおりに実行できます。 操作の最後に、列を参照する自動統計は削除され、ユーザー作成の統計は無効になります。 ユーザーは、操作が完了したら、ユーザー生成の統計を手動で更新する必要があります。 統計やインデックスに使用するフィルター式の中でその列が使われている場合は、列の変更操作は実行できません。  
  
-   オンラインでの列の変更操作の実行中、列への依存関係のあるすべての操作 (インデックス、ビューなど) はブロックされるか、該当するエラーにより失敗します。 これにより、操作の実行中に依存関係が導入されたためにオンラインでの列の変更が失敗しないようになります。  
  
-   変更された列が非クラスター化インデックスによる参照の場合、NOT NULL から NULL への列の変更は、オンライン操作としてサポートしていません。  
  
-   列がチェック制約によって参照されている場合、オンラインでの変更はサポートしていません。変更操作は列の精度を制限しています (数値または日付時刻)。  
  
-   `WAIT_AT_LOW_PRIORITY` オプションは、オンラインでの列の変更に使用できません。  
  
-   オンラインでの列の変更では、`ALTER COLUMN … ADD/DROP PERSISTED` はサポートされていません。  
  
-   `ALTER COLUMN … ADD/DROP ROWGUIDCOL/NOT FOR REPLICATION` は、オンラインでの列の変更の影響を受けません。  
  
-   変更履歴が有効になっているか、テーブルがマージ レプリケーションのパブリッシャーである場合、オンラインでの列の変更ではテーブルの変更をサポートしていません。  
  
-   オンラインでの列の変更は、CLR データ型との変更をサポートしていません。  
  
-   オンラインでの列の変更では、現在のスキーマ コレクションとは異なるスキーマ コレクションの XML データ型の変更はサポートしていません。  
  
-   オンラインでの列の変更では、列を変更できる場合に制限事項を縮小しません。 インデックスまたは統計などでの参照には、変更が失敗する可能性があります。  
  
-   オンラインでの列の変更では、複数の列を同時に変更することをサポートしていません。  
  
-   システムでバージョン管理されたテンポラル テーブルの場合、オンラインでの列の変更による影響はありません。 ONLINE オプションに指定された値に関係なく、ALTER 列はオンラインとしては実行されません。  
  
オンラインでの列の変更には、オンライン インデックスの再構築と同様の要件、制限、および機能があります。 この機能には、次が含まれます。  
  
-   オンラインでのインデックスの再構築は、従来の LOB または filestream 列がテーブルに含まれている場合、またはテーブルに列ストア インデックスがある場合はサポートされません。 同じ制限がオンラインでの列の変更にも適用されます。  
  
-   変更される既存の列には、元の列と、新しく作成される非表示の列に使用するため 2 倍の領域の割り当てが必要です。  
  
-   オンラインでの列の変更の操作中のロック方法は、オンライン インデックスの構築に使用するのと同じロック パターンに従っています。  
  
WITH CHECK | WITH NOCHECK  
 新しく追加または再有効化された FOREIGN KEY 制約や CHECK 制約に対して、テーブル内のデータを検証するかどうかを指定します。 指定しない場合、新しい制約には WITH CHECK が使用され、再有効化された制約には WITH NOCHECK が使用されます。  
  
 既存のデータに対して新しい CHECK 制約または FOREIGN KEY 制約を検証しない場合は、WITH NOCHECK を使用します。 ごくわずかな例外を除き、このオプションは推奨されません。 新しい制約は、それ以降にデータが更新されるたびに評価されます。 制約の追加時、制約違反があっても WITH NOCHECK が指定されていたために検出されなかった場合、その後の更新で制約に従わないデータが使用されると行の更新が失敗する可能性があります。  
  
 クエリ オプティマイザーでは、WITH NOCHECK が定義されている制約は考慮されません。 このような制約は、`ALTER TABLE table WITH CHECK CHECK CONSTRAINT ALL` を使用して再び有効にするまで無視されます。  
  
 ADD  
 1 つまたは複数の列の定義、計算列の定義、またはテーブルの制約が追加されたことを指定またはシステムのバージョン管理のために、システムが使用する列。  
  
 PERIOD FOR SYSTEM_TIME ( system_start_time_column_name, system_end_time_column_name )  
 **適用対象**: [!INCLUDE[ssCurrentLong](../../includes/sscurrentlong-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 レコードの有効期間を記録する、システムを使用する列の名前を指定します。 既存の列を指定したり、追加期間 FOR SYSTEM_TIME 引数の一部として、新しい列を作成することができます。 列は、datetime2 データ型があります。 と NOT として定義する必要が NULL です。 期間の列が NULL として定義される場合は、エラーがスローされます。 system_start_time 列と system_end_time 列の [column_constraint &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-column-constraint-transact-sql.md) を定義し、[列の既定値の指定する](../../relational-databases/tables/specify-default-values-for-columns.md)ことができます。 system_end_time 列の既定値の使用方法については、後述する「[システムのバージョン管理](#system_versioning)」の例 A を参照してください。  
  
 SYSTEM_VERSIONING の設定の引数と組み合わせてこの引数を使用して、既存のテーブルにシステムのバージョン管理を有効にします。 詳細については、「[テンポラル テーブル](../../relational-databases/tables/temporal-tables.md)」と「[Azure SQL Database のテンポラル テーブルの概要](https://azure.microsoft.com/documentation/articles/sql-database-temporal-tables/)」を参照してください。  
  
 [!INCLUDE[ssCurrentLong](../../includes/sscurrentlong-md.md)] 以降、1 つまたは両方の期間列を **HIDDEN** フラグでマークしてこれらの列を暗黙的に非表示にし、**SELECT \* FROM***\<table>* がこのような列の値を返さないようにすることができるようになります。 既定では、期間の列は非表示にします。 を使用するために非表示の列を時間的なテーブルを直接参照するすべてのクエリに明示的に含まする必要があります。  
  
 DROP  
 指定のある 1 つまたは複数の列の定義、計算列の定義、またはテーブルの制約を削除すると、システムは、システムのバージョン管理を使用する列の仕様を削除したりします。  
  
 CONSTRAINT *constraint_name*  
 テーブルから *constraint_name* が削除されることを指定します。 複数の制約の一覧を表示できます。  
  
 ユーザー定義またはシステム提供の制約名は、**sys.check_constraint**、**sys.default_constraints**、**sys.key_constraints**、および **sys.foreign_keys** カタログ ビューに対してクエリを実行することにより確認できます。  
  
 XML インデックスがテーブルに存在する場合、PRIMARY KEY 制約は削除できません。  
  
 COLUMN *column_name*  
 テーブルから *constraint_name* または *column_name* が削除されることを指定します。 複数の列を指定できます。  
  
 次の条件に該当する列は削除できません。  
  
-   インデックスで使用されている列  
  
-   CHECK、FOREIGN KEY、UNIQUE、または PRIMARY KEY 制約で使用されている列  
  
-   DEFAULT キーワードで定義された既定値に関連付けられている列、または既定値のオブジェクトにバインドしている列  
  
-   ルールにバインドしている列  
  
> [!NOTE]  
>  列を削除しても、列のディスク領域は再確保されません。 テーブルの行サイズが制限に近いか制限を超えている場合は、必要に応じて、削除した列のディスク領域を再確保してください。 領域を再確保するには、テーブルにクラスター化インデックスを作成するか、[ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) を使用して既存のクラスター化インデックスを再構築します。 LOB データ型の削除による影響の詳細については、この [CSS ブログ エントリ](http://blogs.msdn.com/b/psssql/archive/2012/12/03/how-it-works-gotcha-varchar-max-caused-my-queries-to-be-slower.aspx)を参照してください。  
  
 FOR SYSTEM_TIME の期間  
 **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 システムのバージョン管理のために、システムが使用する列の仕様を削除します。  
  
 WITH \<drop_clustered_constraint_option>  
 1 つ以上の削除クラスター化制約オプションを設定します。  
  
 MAXDOP = *max_degree_of_parallelism*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 操作中は、**max degree of parallelism** 構成オプションを無効にします。 詳細については、「 [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)」を参照してください。  
  
 並列プランの実行で使用されるプロセッサ数を制限するには、MAXDOP オプションを使用します。 最大数は 64 プロセッサです。  
  
 *max_degree_of_parallelism* には次のいずれかの値を指定できます。  
  
 @shouldalert  
 並列プラン生成を抑制します。  
  
 \>1  
 並列インデックス操作で使用される最大プロセッサ数を、指定した数に制限します。  
  
 0 (既定値)  
 現在のシステム ワークロードに基づいて、実際の数以下のプロセッサを使用します。  
  
 詳細については、「 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)」を参照してください。  
  
> [!NOTE]  
>  並列インデックス操作は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一部のエディションで使用できません。 詳細については、「[SQL Server 2016 の各エディションでサポートされる機能](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
 ONLINE **=** { ON | **OFF** } \<drop_clustered_constraint_option に適用する場合>  
 インデックス操作時に、基になるテーブルや関連するインデックスをクエリやデータ変更で使用できるかどうかを指定します。 既定値は OFF です。 REBUILD は ONLINE 操作として実行できます。  
  
 ON  
 長期のテーブル ロックは、インデックス操作の間は保持されません。 インデックス操作の主なフェーズでは、基になるテーブル、インテント共有 (IS) ロックのみが保持されます。 このことにより、基になるテーブルとインデックスに対するクエリや更新は続行できます。 操作の開始時、非常に短い時間ですが、ソース オブジェクトでは共有 (S) ロックが保持されます。 また操作の終了時は、短い時間ですが、非クラクタ化インデックスが作成される場合は、ソース オブジェクト上で共有 (S) ロックの取得が行われます。また、クラスター化インデックスがオンラインで作成または削除され、クラスター化または非クラスター化インデックスが再構築される場合は、SCH-M (スキーマ修正) ロックが取得されます。 インデックスがローカルの一時テーブルに作成される場合、ONLINE は ON にできません。 シングル スレッドのヒープの再構築操作だけが許可されます。  
  
 **SWITCH** またはオンライン インデックス再構築の DDL を実行するには、特定のテーブルで実行されているすべてのアクティブなブロック トランザクションが完了する必要があります。 実行時には、新しいトランザクションの開始が **SWITCH** または再構築操作によって阻止され、ワークロードのスループットに大きな影響が出たり、基になるテーブルへのアクセスが一時的に遅くなったりする場合があります。  
  
 OFF  
 テーブル ロックは、インデックス操作の間適用されます。 クラスター化インデックスを作成、再構築、または削除するオフライン インデックス操作や、非クラスター化インデックスを再構築または削除するオフライン インデックス操作では、テーブルのスキーマ修正 (Sch-M) ロックが取得されます。 このため、操作中は、すべてのユーザーは基になるテーブルにアクセスできません。 非クラスター化インデックスを作成するオフライン インデックス操作では、テーブルの共有 (S) ロックが取得されます。 この場合は、基になるテーブルに対して更新は許可されませんが、SELECT ステートメントなどの読み取り操作は許可されます。 マルチスレッドのヒープの再構築操作が許可されます。  
  
 詳細については、「[オンライン インデックス操作の動作原理](../../relational-databases/indexes/how-online-index-operations-work.md)」を参照してください。  
  
> [!NOTE]  
>  オンラインでのインデックス操作は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 詳細については、「[SQL Server 2016 の各エディションでサポートされる機能](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
 MOVE TO { *partition_scheme_name***(***column_name* [ 1**,** ... *n*] **)** | *filegroup* | **"**default**"** }  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 現在クラスター化インデックスのリーフ レベルに格納されているデータ行を移動する場所を指定します。 テーブルは新しい位置に移動します。 このオプションは、クラスター化インデックスを作成する制約にのみ適用されます。  
  
> [!NOTE]  
>  ここでは、default はキーワードではありません。 これは、既定のファイル グループの識別子で、MOVE TO **"**default**"** または MOVE TO **[**default**]** のように区切り記号で区切る必要があります。 **"**default**"** を指定する場合は、現在のセッションに対して QUOTED_IDENTIFIER オプションが ON になっている必要があります。 これが既定の設定です。 詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
 { CHECK | NOCHECK } CONSTRAINT  
 *constraint_name* を有効または無効にします。 このオプションは、FOREIGN KEY 制約と CHECK 制約でのみ使用できます。 NOCHECK を指定すると、制約は無効になり、今後列に行われる挿入または更新は、制約条件に対して検証されません。 DEFAULT、PRIMARY KEY、および UNIQUE 制約は無効にできません。  
  
 ALL  
 すべての制約を、NOCHECK オプションで無効にするか CHECK オプションで有効にします。  
  
 { ENABLE | DISABLE } TRIGGER  
 *trigger_name* を有効または無効にします。 トリガーを無効にしてもテーブルのトリガー定義は引き続き有効ですが、テーブルに対して INSERT、UPDATE、または DELETE ステートメントを実行しても、トリガーを再び有効にするまではトリガー内の動作が実行されることはありません。  
  
 ALL  
 テーブル内のすべてのトリガーを有効または無効にします。  
  
 *trigger_name*  
 無効または有効にするトリガーの名前を指定します。  
  
 { ENABLE | DISABLE } CHANGE_TRACKING  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 テーブルに対して変更の追跡を有効にするかどうかを指定します。 既定では、変更の追跡が無効になっています。  
  
 このオプションは、データベースに対して変更の追跡が有効になっている場合にのみ使用できます。 詳細については、「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)」を参照してください。  
  
 変更の追跡を有効にするには、テーブルに主キーが必要です。  
  
 WITH **(** TRACK_COLUMNS_UPDATED **=** { ON | **OFF** } **)**  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 更新された変更の追跡対象の列を [!INCLUDE[ssDE](../../includes/ssde-md.md)] が追跡するかどうかを指定します。 既定値は OFF です。  
  
 SWITCH [ PARTITION *source_partition_number_expression* ] TO [ *schema_name***.** ] *target_table* [ PARTITION *target_partition_number_expression* ]  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 次のいずれかの方法でデータのブロックを切り替えます。  
  
-   テーブルのすべてのデータを、既に存在するパーティション テーブルにパーティションとして再度割り当てます。  
  
-   1 つのパーティション テーブルから別のパーティション テーブルに、パーティションを切り替えます。  
  
-   パーティション テーブルの 1 つのパーティションにあるすべてのデータを、既存の非パーティション テーブルに再度割り当てます。  
  
*table* がパーティション テーブルの場合、*source_partition_number_expression* を指定する必要があります。 *target_table* がパーティション分割されている場合、*target_partition_number_expression* を指定する必要があります。 テーブルのデータを既に存在するパーティション テーブルにパーティションとして再度割り当てる場合、または 1 つのパーティション テーブルから別のパーティション テーブルにパーティションを切り替える場合は、対象のパーティションが存在し、空になっている必要があります。  
  
 1 つのパーティションのデータを再度割り当てて単一のテーブルを作成する場合は、対象テーブルが既に作成されており、空になっている必要があります。 ソース テーブルまたはパーティションと、対象テーブルまたはパーティションは、両方とも同じファイル グループに存在する必要があります。 また、対応するインデックスまたはインデックス パーティションも、同じファイル グループに存在する必要があります。 切り替えるパーティションには、多くの追加の制限が適用されます。 *table* と *target_table* を同じにすることはできません。 *target_table* にはマルチパート識別子を指定できます。  
  
 *source_partition_number_expression* と *target_partition_number_expression* は、変数と関数を参照できる定数式です。 これらの定数式には、ユーザー定義型変数とユーザー定義関数が含まれます。 これらの定数式で [!INCLUDE[tsql](../../includes/tsql-md.md)] 式を参照することはできません。  
  
 Columstore のクラスター化されたインデックスを持つパーティション分割されたテーブルがパーティション分割されたヒープのように動作します。  
  
-   主キーには、パーティション キーを含める必要があります。  
  
-   一意のインデックスには、パーティション キーを含める必要があります。  既存の一意のインデックスをパーティション分割キーを含むで一意性を変更できることに注意してください。  
  
-   パーティションを切り替えるには、するためには、すべての非クラスター化インデックスがパーティション キーを含める必要があります。  
  
レプリケーションを使用する場合の **SWITCH** の制限については、「[パーティション テーブルとパーティション インデックスのレプリケート](../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 CTP1 用およびバージョン V12 より前の SQL Database 用に構築された非クラスター化列ストア インデックスは読み取り専用形式でした。 すべてのパーティションの操作を実行する前に、(これは更新可能な) 現在の形式に非クラスター化列ストア インデックスを再構築する必要があります。  
  
 SET **(** FILESTREAM_ON = { *partition_scheme_name* | *filestream_filegroup_name* |         **"**default**"** | **"**NULL**"** }**)**  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 FILESTREAM データの格納場所を指定します。  
  
 SET FILESTREAM_ON 句を指定した ALTER TABLE は、テーブルに FILESTREAM 列がない場合にのみ成功します。 FILESTREAM 列は、2 番目の ALTER TABLE ステートメントで追加できます。  
  
 *partition_scheme_name* を指定した場合、[CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) のルールが適用されます。 テーブルは、行データ用にパーティション分割されている必要があります。また、テーブルのパーティション構成では、FILESTREAM パーティション構成と同じパーティション関数とパーティション列を使用する必要があります。  
  
 *filestream_filegroup_name* には、FILESTREAM ファイル グループの名前を指定します。 ファイル グループには、[CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md) ステートメントまたは [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) ステートメントを使用してファイルが 1 つ定義されている必要があります。それ以外の場合は、エラーが発生します。  
  
 **"**default**"** には、DEFAULT プロパティ セットを含む FILESTREAM ファイル グループを指定します。 FILESTREAM ファイル グループがない場合は、エラーが発生します。  
  
 **"**NULL**"** を指定すると、テーブルの FILESTREAM ファイル グループへの参照がすべて削除されます。 最初にすべての FILESTREAM 列を削除する必要があります。 テーブルに関連付けられている FILESTREAM データをすべて削除するには、SET FILESTREAM_ON**="**NULL**"** を使用する必要があります。  
  
 SET **(** SYSTEM_VERSIONING **=** { OFF | ON [ ( HISTORY_TABLE = schema_name . history_table_name [ , DATA_CONSISTENCY_CHECK = { **ON** | OFF } ]  ) ] } **)**  
 **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 テーブルのシステムのバージョン管理を無効にするか、テーブルのシステムのバージョン管理を使用します。 テーブルのシステムのバージョン管理を有効にするのには、システムは、データ型、null 値許容制約、およびシステムのバージョン管理の主キー制約の要件を満たしていることを確認します。 HISTORY_TABLE 引数を使用しない場合、システムは 2 つのテーブル間のリンクを作成するには、現在のテーブルのスキーマに一致する新しい履歴テーブルを生成し、により、システムは、履歴テーブルには、現在のテーブル内の各レコードの履歴を記録するします。 この履歴テーブルの名前は `MSSQL_TemporalHistoryFor<primary_table_object_id>` になります。 HISTORY_TABLE 引数を介してへのリンクを作成し、既存の履歴テーブルを使用する場合に、現在のテーブルと、指定したテーブルの間のリンクが作成されます。 既存の履歴テーブルへのリンクを作成する場合は、データの整合性チェックを実行することもできます。 このデータの整合性チェックでは、既存のレコードが重複しないことを確認します。 データを実行する一貫性チェックが、既定値です。 詳細については、「 [Temporal Tables](../../relational-databases/tables/temporal-tables.md)」を参照してください。  
  
HISTORY_RETENTION_PERIOD = { **INFINITE** | number {DAY | DAYS | WEEK |  WEEKS | MONTH | MONTHS | YEAR | YEARS} } **Applies to**:  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  

テンポラル テーブルに履歴データを保持する有限または無限のリテンション期間を指定します。 省略すると、無限のリテンション期間が使用されます。
  
 SET **(** LOCK_ESCALATION = { AUTO | TABLE | DISABLE } **)**  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 許可されるテーブル ロックのエスカレーション方法を指定します。  
  
 AUTO  
 このオプションを指定すると、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] で、テーブル スキーマに適したロック エスカレーションの粒度が選択されます。  
  
-   テーブルがパーティション分割されている場合は、ロック エスカレーションをパーティション分割できます。 パーティション レベルにエスカレートされたロックが、後で TABLE 粒度にエスカレートされることはありません。  
  
-   テーブルがパーティション分割されていない場合は、ロック エスカレーションは TABLE 粒度に設定されます。  
  
TABLE  
 テーブルがパーティション分割されているかどうかに関係なく、ロック エスカレーションはテーブルレベルの粒度で行われます。 TABLE は既定値です。  
  
 DISABLE  
 ほとんどの場合でロック エスカレーションを禁止します。 テーブルレベルのロックは完全には禁止されません。 たとえば、SERIALIZABLE 分離レベルでクラスター化インデックスがないテーブルをスキャンしている場合は、[!INCLUDE[ssDE](../../includes/ssde-md.md)] でテーブル ロックを実行して、データの整合性を保護します。  
  
 REBUILD  
 パーティション テーブル内のすべてのパーティションを含めたテーブル全体を再構築するには、REBUILD WITH 構文を使用します。 テーブルにクラスター化インデックスが含まれている場合、REBUILD オプションを指定すると、クラスター化インデックスが再構築されます。 REBUILD は ONLINE 操作として実行できます。  
  
 パーティション テーブル内の 1 つのパーティションを再構築するには、REBUILD PARTITION 構文を使用します。  
  
 PARTITION = ALL  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 パーティションの圧縮設定の変更時に、すべてのパーティションを再構築します。  
  
 REBUILD WITH ( \<rebuild_option> )  
 クラスター化インデックスを含むテーブルには、すべてのオプションが適用されます。 テーブルにクラスター化インデックスが含まれていない場合、ヒープ構造に影響を与えるのは一部のオプションだけです。  
  
 REBUILD 操作で特定の圧縮設定を指定しないと、パーティションの現在の圧縮設定が使用されます。 現在の設定を取得するには、**sys.partitions** カタログ ビューで **data_compression** 列に対するクエリを実行します。  
  
 再構築オプションの詳細については、「[index_option &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-index-option-transact-sql.md)」を参照してください。  
  
 DATA_COMPRESSION  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 指定したテーブル、パーティション番号、またはパーティション範囲に、データ圧縮オプションを指定します。 次のオプションがあります。  
  
 なし  
 テーブルまたは指定したパーティションが圧縮されません。 これは、列ストア テーブルには適用されません。  
  
 ROW  
 行の圧縮を使用して、テーブルまたは指定したパーティションが圧縮されます。 これは、列ストア テーブルには適用されません。  
  
 PAGE  
 ページの圧縮を使用して、テーブルまたは指定したパーティションが圧縮されます。 これは、列ストア テーブルには適用されません。  
  
 COLUMNSTORE  
 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 列ストア テーブルにのみ適用されます。 COLUMNSTORE は、COLUMNSTORE_ARCHIVE オプションで圧縮されたパーティションを解凍するように指定します。 復元されるデータは、すべての列ストア テーブルに使用された列ストア圧縮を使用して引き続き圧縮されます。  
  
 COLUMNSTORE_ARCHIVE  
 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 クラスター化列ストア インデックスを使用して格納されているテーブルである、列ストア テーブルにのみ適用されます。 COLUMNSTORE_ARCHIVE は、指定したパーティションをより小さなサイズにさらに圧縮します。 これは、保存用や、ストレージの使用量を減らす必要があり、しかも保存と取得に時間をかける余裕があるその他の状況で使用できます。  
  
 複数のパーティションを同時に再構築するには、「[index_option &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-index-option-transact-sql.md)」を参照してください。 テーブルにクラスター化インデックスが含まれていない場合、データ圧縮を変更するとヒープと非クラスター化インデックスが再構築されます。 圧縮の詳細については、「[データ圧縮](../../relational-databases/data-compression/data-compression.md)」を参照してください。  
  
 ONLINE **=** { ON  | **OFF** } \<single_partition_rebuild_option に適用する場合>  
 インデックス操作中に、基となるテーブルの 1 つのパーティションとそれに関連する各インデックスに対してクエリやデータ変更を行うことができるかどうかを指定します。 既定値は OFF です。 REBUILD は ONLINE 操作として実行できます。  
  
 ON  
 長期のテーブル ロックは、インデックス操作の間は保持されません。 インデックスの再構築を開始するときにテーブルに対する S ロックが必要であり、オンライン インデックス再構築を終了するときにテーブルに対する Sch-M ロックが必要です。 どちらのロックも短いメタデータ ロックですが、特に Sch-M ロックは、すべてのブロックしているトランザクションの完了を待機する必要があります。 待機中、Sch-M ロックは、同じテーブルにアクセスするためにこのロックの後に待機している他のすべてのトランザクションをブロックします。  
  
> [!NOTE]  
>  オンライン インデックス再構築では、このセクションの後の方で説明されている *low_priority_lock_wait* オプションを設定できます。  
  
 OFF  
 テーブル ロックは、インデックス操作の間適用されます。 このため、操作中は、すべてのユーザーは基になるテーブルにアクセスできません。  
  
 *column_set_name* XML COLUMN_SET FOR ALL_SPARSE_COLUMNS  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 列セットの名前を指定します。 列セットは、型指定されていない XML 表記であり、テーブルのすべてのスパース列を 1 つにまとめて構造化した出力です。 スパース列を含むテーブルには列セットを追加できません。 列セットの詳細については、「 [列セットの使用](../../relational-databases/tables/use-column-sets.md)」を参照してください。  
  
 { ENABLE | DISABLE } FILETABLE_NAMESPACE  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 FileTable に対するシステム定義の制約を有効または無効にします。 FileTable でのみ使用できます。  
  
 SET ( FILETABLE_DIRECTORY = *directory_name* )  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 Windows と互換性のある FileTable ディレクトリ名を指定します。 この名前は、データベース内のすべての FileTable ディレクトリ名の中で一意である必要があります。 一意性の比較では、SQL 照合順序の設定とは関係なく、大文字と小文字は区別されません。 FileTable でのみ使用できます。  
```    
 SET (  
        REMOTE_DATA_ARCHIVE   
        {  
            = ON (  <table_stretch_options> )  
          | = OFF_WITHOUT_DATA_RECOVERY  
          ( MIGRATION_STATE = PAUSED ) | ( <table_stretch_options> [, ...n] )  
        } )  
```    
**適用対象**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 テーブルに対して Stretch Database を有効または無効にします。 詳細については、「 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)」を参照してください。  
  
 **テーブルに対して Stretch Database を有効にする**  
  
 `ON` を指定してテーブルに対して Stretch を有効にする場合は、`MIGRATION_STATE = OUTBOUND` を指定してデータの移行を即時に開始するか、`MIGRATION_STATE = PAUSED` を指定してデータの移行を延期するかを指定する必要があります。 既定値は `MIGRATION_STATE = OUTBOUND` です。 テーブルに対して Stretch を有効にする方法については、「[データベースに対して Stretch Database を有効にする](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)」を参照してください。  
  
 **前提条件**。 テーブルに対して Stretch を有効にする前に、サーバーおよびデータベースで Stretch を有効にする必要があります。 詳細については、「 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)」を参照してください。  
  
 **権限**: データベースまたはテーブルの拡張を有効にするには、db_owner アクセス許可が必要です。 テーブルの拡張を有効にすると、テーブルに対する ALTER 権限も必要です。  
  
 **テーブルに対して Stretch Database を無効にする**  
  
 テーブルの Stretch を無効にすると、既に Azure に移行されているリモート データには 2 つの選択肢があります。 詳細については、「 [Stretch Database を無効にして、リモート データを戻す](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md)」を参照してください。  
  
-   テーブルに対する Stretch を無効にして、テーブルのリモート データを Azure から SQL Server にコピーして戻すには、次のコマンドを実行します。 このコマンドは取り消すことができません。  
  
    ```sql  
ALTER TABLE \<table name>
       SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = INBOUND ) ) ;  
    ```  
  
     この操作によりデータ転送コストが発生し、取り消すことはできません。 詳細については、「 [Data Transfers (データ転送) の料金詳細](https://azure.microsoft.com/en-us/pricing/details/data-transfers/)」を参照してください。  
  
     すべてのリモート データが Azure から SQL Server にコピーして戻されると、テーブルに対する Stretch は無効になります。  
  
-   テーブルに対する Stretch を無効にして、リモート データを破棄するには、次のコマンドを実行します。  
  
    ```sql  
ALTER TABLE \<table_name>
       SET ( REMOTE_DATA_ARCHIVE = OFF_WITHOUT_DATA_RECOVERY ( MIGRATION_STATE = PAUSED ) ) ;  
    ```  
  
 テーブルに対する Stretch Database を無効にすると、データの移行が停止し、クエリの結果にリモート テーブルからの結果が含まれなくなります。  
  
 Stretch を無効にしても、リモート テーブルは削除されません。 リモート テーブルを削除する場合は、Azure 管理ポータルを使用して削除する必要があります。  
  
[ FILTER_PREDICATE = { null | *predicate* } ]  
 **適用対象**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 必要に応じて、履歴データと現在のデータの両方を含むテーブルから移行する行を選択するフィルター述語を指定します。 この述語で決定論的インライン テーブル値関数を呼び出す必要があります。 詳細については、「[テーブルに対して Stretch Database を有効にする](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)」と「[フィルター関数を使用して移行する行を選択する &#40;Stretch Database&#41;](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md)」を参照してください。   
  
> [!IMPORTANT]  
>  指定したフィルター述語のパフォーマンスが低いと、データ移行のパフォーマンスも低くなります。 Stretch Database では、CROSS APPLY 演算子を使用してテーブルにフィルター述語を適用します。  
  
 フィルター述語を指定しない場合、テーブル全体が移行されます。  
  
 フィルター述語を指定する場合は、*MIGRATION_STATE* も指定する必要があります。  
  
 MIGRATION_STATE = { OUTBOUND |  INBOUND | PAUSED }  
 **適用対象**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
-   SQL Server から Azure にデータを移行するには `OUTBOUND` を指定します。  
  
-   Azure から SQL Server にテーブルのリモート データをコピーして戻し、テーブルに対する Stretch を無効にするには、`INBOUND` を指定します。 詳細については、「 [Stretch Database を無効にして、リモート データを戻す](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md)」を参照してください。  
  
     この操作によりデータ転送コストが発生し、取り消すことはできません。  
  
-   データの移行を一時停止または延期するには `PAUSED` を指定します。 詳細については、「[データ移行の一時停止と再開 &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)」を参照してください。  
  
WAIT_AT_LOW_PRIORITY  
 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 オンライン インデックス再構築では、このテーブルに対する操作がブロックされるまで待機する必要があります。 **WAIT_AT_LOW_PRIORITY** は、オンライン インデックス再構築操作が優先度の低いロックを待機して、オンライン インデックス構築操作が待機している間、他の操作を続行可能にすることを示します。 **WAIT AT LOW PRIORITY** オプションを省略すると、`WAIT_AT_LOW_PRIORITY ( MAX_DURATION = 0 minutes, ABORT_AFTER_WAIT = NONE)` と同等になります。  
  
 MAX_DURATION = *time* **[MINUTES]**  
 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 **SWITCH** またはオンライン インデックス再構築のロックが、DDL コマンドの実行時に低い優先度で待機する時間 (分単位で指定した整数値) です。 操作が **MAX_DURATION** の期間ブロックされると、**ABORT_AFTER_WAIT** アクションのいずれかが実行されます。 **MAX_DURATION** の期間は常に分単位なので、**MINUTES** という単語は省略できます。  
  
 ABORT_AFTER_WAIT = [**NONE** | **SELF** | **BLOCKERS** } ]  
 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 なし  
 通常の (標準) 優先度のロックを待機し続けます。  
  
 SELF  
 いずれのアクションも行わずに、現在実行中の **SWITCH** またはオンライン インデックス再構築の DDL 操作を終了します。  
  
 BLOCKERS  
 現在 **SWITCH** またはオンライン インデックス再構築の DDL 操作をブロックしているすべてのユーザー トランザクションを強制終了して、操作を続行できるようにします。  
  
 **ALTER ANY CONNECTION** 権限が必要です。  
  
IF EXISTS  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで) および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
 既に存在する場合にのみ、列または制約を条件付きで削除します。  
  
## <a name="remarks"></a>Remarks  
 新しいデータ行を追加するには、[INSERT](../../t-sql/statements/insert-transact-sql.md) を使用します。 データの行を削除するには、[DELETE](../../t-sql/statements/delete-transact-sql.md) または [TRUNCATE TABLE](../../t-sql/statements/truncate-table-transact-sql.md) を使用します。 既存の行の値を変更するには、[UPDATE](../../t-sql/queries/update-transact-sql.md) を使用します。  
  
 プロシージャ キャッシュにテーブルを参照する実行プランがある場合、ALTER TABLE ではこれらの実行プランに対して、次の実行時に再コンパイルするというマークが付けられます。  
  
## <a name="changing-the-size-of-a-column"></a>列のサイズの変更  
 ALTER COLUMN 句で列のデータ型の新しいサイズを指定すると、列の長さ、有効桁数、または小数点以下桁数を変更できます。 列内にデータが存在する場合は、新しいサイズをデータの最大サイズより小さくすることはできません。 また、インデックス内で列を定義することはできません。ただし、その列のデータ型が **varchar**、**nvarchar**、または **varbinary** であり、インデックスが PRIMARY KEY 制約の結果として生じたものでない場合は除きます。 例 P を参照してください。  
  
## <a name="locks-and-alter-table"></a>ロックと ALTER TABLE  
 ALTER TABLE で指定した変更は、直ちに実装されます。 変更でテーブル内の行の修正が必要になる場合、ALTER TABLE では行が更新されます。 ALTER TABLE では、変更中にテーブルのメタデータが他の接続で参照されないように、テーブルに対してスキーマ修正 (SCH-M) ロックが取得されます。ただし、オンライン インデックス操作の終了時に、非常に短い時間 SCH-M ロックを必要とする場合は、このロックの取得は行われません。 `ALTER TABLE…SWITCH` 操作では、ロックはソース テーブルと対象テーブルの両方に対して取得されます。 テーブルに加えられた変更はログに記録され、完全に復旧できます。 列の削除や、一部のエディションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] における既定値を伴う NOT NULL 列の追加など、きわめて大きなテーブル内のすべての行に影響する変更は、その実行終了までに長い時間がかかり、多くのログ レコードが生成されます。 このような ALTER TABLE ステートメントは、多くの行に影響する INSERT、UPDATE、DELETE の各ステートメントと同じように、十分な注意を払って実行する必要があります。  
  
### <a name="adding-not-null-columns-as-an-online-operation"></a>オンライン操作としての NOT NULL 列の追加  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Enterprise Edition 以降では、既定値を持つ NOT NULL 列の追加は、既定値が*ランタイム定数*である場合、オンライン操作です。 これは、テーブル内の行数に関係なく、操作がほぼ瞬時に完了することを意味します。 テーブル内の既存の行は、操作中に更新されないためです。その代わりに、既定値はテーブルのメタデータだけに格納され、これらの列にアクセスするクエリで必要になった場合に値が参照されます。 この動作は自動的に行われます。ADD COLUMN 構文以外に、オンライン操作を実装するための追加の構文は必要ありません。 ランタイム定数は、決定性に関係なく、テーブルの各行に対して実行時に同じ値を生成する式です。 たとえば、定数式 "My temporary data" やシステム関数 GETUTCDATETIME() は、ランタイム定数です。 一方、関数の `NEWID()` や `NEWSEQUENTIALID()` は、テーブルの各行で一意の値が生成されるので、ランタイム定数ではありません。 ランタイム定数ではない既定値を持つ NOT NULL 列の追加は、常にオフラインで実行され、操作中は排他 (SCH-M) ロックが取得されます。  
  
 既存の行はメタデータに格納された値を参照しますが、新しい行が挿入され、列に別の値が指定されない場合、既定値はその行に格納されます。 メタデータに格納された既定値は、行が更新されるか (UPDATE ステートメントで実際の列が指定されなくても)、テーブルまたはクラスター化インデックスが再構築された場合、既存の列に移動されます。  
  
 型 **varchar(max)**、**nvarchar(max)**、**varbinary(max)**、**xml**、**text**、**ntext**、**image**、**hierarchyid**、**geometry**、**geography**、または CLR UDTS の列をオンライン操作で追加することはできません。 行の最大サイズが 8,060 バイトの制限を超える場合は、列をオンラインで追加することはできません。 その場合、列はオフライン操作として追加されます。  
  
## <a name="parallel-plan-execution"></a>並列プランの実行  
 [!INCLUDE[ssEnterpriseEd11](../../includes/ssenterpriseed11-md.md)] 以降では、単一の ALTER TABLE ADD (インデックス ベース) CONSTRAINT または DROP (クラスター化インデックス) CONSTRAINT ステートメントの実行に使用されるプロセッサ数は、**max degree of parallelism** 構成オプションと現在のワークロードによって決定されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] でシステムがビジー状態であることが検出されると、ステートメントの実行前に自動的に操作の並列処理の次数が減らされます。 MAXDOP オプションを指定すると、ステートメントの実行に使用されるプロセッサ数を手動で構成できます。 詳細については、「 [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)」を参照してください。  
  
## <a name="partitioned-tables"></a>パーティション テーブル  
 ALTER TABLE は、パーティション テーブルを対象にした SWITCH 操作の実行に使用できるほか、非パーティション テーブルと同様に、パーティション テーブルの列、制約、トリガーの状態を変更する場合にも使用できます。 ただし、このステートメントを使用して、テーブル自体のパーティション分割方法を変更することはできません。 パーティション テーブルを再びパーティション分割するには、[ALTER PARTITION SCHEME](../../t-sql/statements/alter-partition-scheme-transact-sql.md) および [ALTER PARTITION FUNCTION](../../t-sql/statements/alter-partition-function-transact-sql.md) を使用します。 また、パーティション テーブルの列のデータ型を変更することもできません。  
  
## <a name="restrictions-on-tables-with-schema-bound-views"></a>スキーマ バインド ビューによるテーブルへの制限  
 スキーマ バインド ビューのあるテーブルに ALTER TABLE ステートメントを実行するときに適用される制約は、単純なインデックスのあるテーブルを変更する場合に現在適用されている制約と同じです。 列の追加は許可されますが、 任意のスキーマ バインド ビューに含まれる列を削除または変更することはできません。 ALTER TABLE ステートメントによって、スキーマ バインド ビューで使用されている列の変更が要求された場合、ALTER TABLE は失敗し、[!INCLUDE[ssDE](../../includes/ssde-md.md)] ではエラー メッセージが表示されます。 スキーマ バインド ビューとインデックス付きビューの詳細については、「[CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)」を参照してください。  
  
 ベース テーブルを参照するスキーマ バインド ビューを作成しても、そのテーブルに対するトリガーの追加や削除には影響はありません。  
  
## <a name="indexes-and-alter-table"></a>インデックスと ALTER TABLE  
 制約が削除されると、制約の要素として作成されたインデックスも削除されます。 CREATE INDEX で作成されたインデックスは、DROP INDEX で削除する必要があります。 ALTER INDEX ステートメントを使用すると、制約定義の要素であるインデックスを再構築できます。ALTER TABLE で制約を削除して再び追加する必要はありません。  
  
 列に基づくすべてのインデックスと制約を削除してからでないと、列は削除できません。  
  
 クラスター化インデックスを作成した制約が削除されると、クラスター化インデックスのリーフ レベルに格納されていたデータ行は、非クラスター化テーブルに格納されるようになります。 MOVE TO オプションを指定すると、1 つのトランザクションで、クラスター化インデックスを削除し、その結果生成されたテーブルを別のファイル グループまたはパーティション構成に移動できます。 MOVE TO オプションには次の制限があります。  
  
-   MOVE TO は、インデックス付きビューまたは非クラスター化インデックスに対しては有効ではありません。  
-   パーティション構成またはファイル グループは、既に存在している必要があります。  
-   MOVE TO を指定しない場合、テーブルは、クラスター化インデックスに定義されたものと同じパーティション構成またはファイル グループに配置されます。  
  
クラスター化インデックスを削除すると、ONLINE **=** ON オプションを指定できます。このため、DROP INDEX トランザクションによって、基になるデータや関連する非クラスター化インデックスに対するクエリおよび変更がブロックされることはありません。  
  
ONLINE **=** ON には次の制限があります。  
 
-   ONLINE **=** ON は、無効化されたクラスター化インデックスに対しては有効ではありません。 無効化されたインデックスは、ONLINE **=** OFF を使って削除する必要があります。  
-   一度に 1 つのインデックスのみを削除できます。  
-   ONLINE **=** ON は、インデックス付きビュー、非クラスター化インデックス、またはローカル一時テーブル上のインデックスに対しては有効ではありません。  
-   ONLINE **=** ON は、列ストア インデックスに対しては無効です。  
  
既存のクラスター化インデックスを削除するには、クラスター化インデックスの大きさと同じ一時ディスク領域が必要です。 この追加領域は、操作が完了するとすぐに解放されます。  
  
> [!NOTE]  
>  *\<drop_clustered_constraint_option>* に示されているオプションは、テーブル上のクラスター化インデックスに適用され、ビュー上のクラスター化インデックスまたは非クラスター化インデックスには適用できません。  
  
## <a name="replicating-schema-changes"></a>スキーマ変更のレプリケート  
 既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーでパブリッシュされたテーブルに ALTER TABLE を実行すると、すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーに変更が反映されます。 この機能にはいくつか制限事項があります。また、この機能は無効にできます。 詳細については、「[パブリケーション データベースでのスキーマの変更](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)」を参照してください。  
  
## <a name="data-compression"></a>Data Compression  
 システム テーブルで圧縮を有効にすることはできません。 テーブルがヒープの場合、ONLINE モードでは、再構築操作がシングル スレッドになります。 マルチスレッドのヒープの再構築操作では、OFFLINE モードを使用してください。 データ圧縮の詳細については、「[データ圧縮](../../relational-databases/data-compression/data-compression.md)」を参照してください。  
  
 圧縮状態の変更による、テーブル、インデックス、またはパーティションへの影響を評価するには、 [sp_estimate_data_compression_savings](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md) ストアド プロシージャを使用します。  
  
 パーティション テーブルには次の制限が適用されます。  
  
-   固定されていないインデックスがテーブルにある場合、そのパーティションの圧縮設定を変更できません。  
-   ALTER TABLE \<table> REBUILD PARTITION ... 構文は、指定されたパーティションを再構築します。  
-   ALTER TABLE \<table> REBUILD WITH ... 構文は、すべてのパーティションを再構築します。  
  
## <a name="dropping-ntext-columns"></a>NTEXT 列の削除  
 NTEXT 列を削除すると、削除されたデータのクリーンアップが、シリアル化された操作としてすべての行で実行されます。 このクリーンアップは、長時間かかる場合があります。 多数の行を含むテーブルの NTEXT 列を削除する場合は、最初に NTEXT 列を NULL 値に更新し、次に列を削除します。 これを並列操作で実行すると、より速く処理することができます。  
  
## <a name="online-index-rebuild"></a>オンラインでのインデックス再構築  
 オンライン インデックス再構築の DDL ステートメントを実行するには、特定のテーブルで実行されているすべてのアクティブなブロック トランザクションが完了する必要があります。 オンライン インデックス再構築を実行すると、このテーブルに対する実行の開始が準備できているすべての新しいトランザクションがブロックされます。 オンライン インデックス再構築のロックの期間は非常に短いですが、特定のテーブルに対して開かれているすべてのトランザクションの完了を待機し、新しいトランザクションの開始をブロックすることで、スループットに大きな影響を与える場合があり、ワークロードの速度低下またはタイムアウトを引き起こしたり、基になるテーブルへのアクセスが大幅に制限されたりします。 **WAIT_AT_LOW_PRIORITY** オプションは、オンライン インデックス再構築に必要な S ロックおよび Sch-M ロックを DBA が管理できるようにし、3 つのオプションのいずれかを選択できるようにします。 3 つのいずれのケースでも、待機時間 (`(MAX_DURATION =n [minutes])`) 中にブロックするアクティビティがない場合は、オンライン インデックス再構築が待機なしで直ちに実行され、DDL ステートメントが完了します。  
  
## <a name="compatibility-support"></a>互換性サポート  
 ALTER TABLE ステートメントでは、2 部構成 (schema.object) のテーブル名だけを使用できます。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、次の形式を使用してテーブル名を指定すると、コンパイル時にエラー 117 で失敗します。  
  
-   server.database.schema.table  
-   .database.schema.table  
-   ..schema.table  
  
以前のバージョンでは、server.database.schema.table という形式を指定すると、エラー 4902 が返されました。 .database.schema.table または ..schema.table という形式を指定すると、成功しました。  
  
問題を解決するには、4 部構成のプレフィックスの使用を削除してください。  
  
## <a name="permissions"></a>アクセス許可  
 テーブルに対する ALTER 権限が必要です。  
  
 ALTER TABLE 権限は、ALTER TABLE SWITCH ステートメントに含まれる両方のテーブルに適用されます。 切り替えられるデータには、対象テーブルのセキュリティが継承されます。  
  
 ALTER TABLE ステートメント内の列が、共通言語ランタイム (CLR) ユーザー定義型または別名データ型として定義されている場合は、そのデータ型に対する REFERENCES 権限が必要です。  
  
 テーブルの行を更新する列を追加するには、テーブルの **UPDATE** 権限が必要です。 たとえば、既定値の **NOT NULL** 列を追加する場合や、テーブルが空でないときに ID 列を追加する場合です。  
  
##  <a name="Example_Top"></a> 使用例  
  
|カテゴリ|主な構文要素|  
|--------------|------------------------------|  
|[列と制約を追加する](#add)|ADD • PRIMARY KEY とインデックス オプション • スパース列と列セット •|  
|[列と制約を削除する](#Drop)|DROP|  
|[列定義を変更する](#alter_column)|データ型の変更 • 列のサイズの変更 • 照合順序|  
|[テーブル定義を変更する](#alter_table)|DATA_COMPRESSION • SWITCH PARTITION • LOCK ESCALATION • 変更の追跡|  
|[制約およびトリガーを無効および有効にする](#disable_enable)|CHECK • NO CHECK • ENABLE TRIGGER • DISABLE TRIGGER|  
  
###  <a name="add"></a>列と制約を追加する  
 このセクションの例では、テーブルに列と制約を追加する方法を示します。  
  
#### <a name="a-adding-a-new-column"></a>A. 新しい列を追加する  
 次の例では、NULL 値を許容し、DEFAULT 定義で値が提供されない列を追加します。 新しい列では、各行に `NULL` が設定されます。  
  
```sql  
CREATE TABLE dbo.doc_exa (column_a INT) ;  
GO  
ALTER TABLE dbo.doc_exa ADD column_b VARCHAR(20) NULL ;  
GO  
```  
  
#### <a name="b-adding-a-column-with-a-constraint"></a>B. 制約を含む列を追加する  
 次の例では、`UNIQUE` 制約を含む新しい列を追加します。  
  
```sql  
CREATE TABLE dbo.doc_exc (column_a INT) ;  
GO  
ALTER TABLE dbo.doc_exc ADD column_b VARCHAR(20) NULL   
    CONSTRAINT exb_unique UNIQUE ;  
GO  
EXEC sp_help doc_exc ;  
GO  
DROP TABLE dbo.doc_exc ;  
GO  
```  
  
#### <a name="c-adding-an-unverified-check-constraint-to-an-existing-column"></a>C. 既存の列に検証なしの CHECK 制約を追加する  
 次の例では、テーブル内の既存の列に制約を追加します。 列には制約に違反する値があります。 このため、制約が既存の行に対して検証されないよう、また制約を追加できるよう、`WITH NOCHECK` を使用します。  
  
```sql  
CREATE TABLE dbo.doc_exd ( column_a INT) ;  
GO  
INSERT INTO dbo.doc_exd VALUES (-1) ;  
GO  
ALTER TABLE dbo.doc_exd WITH NOCHECK   
ADD CONSTRAINT exd_check CHECK (column_a > 1) ;  
GO  
EXEC sp_help doc_exd ;  
GO  
DROP TABLE dbo.doc_exd ;  
GO  
```  
  
#### <a name="d-adding-a-default-constraint-to-an-existing-column"></a>D. 既存の行に DEFAULT 制約を追加する  
 次の例では、2 つの列を含んだテーブルを作成し、最初の列には値を挿入し、もう 1 つの列は NULL のままにします。 2 番目の列には `DEFAULT` 制約を追加します。 既定値が適用されていることを確認するには、最初の列にさらに値を挿入し、テーブルに対してクエリを実行します。  
  
```sql  
CREATE TABLE dbo.doc_exz ( column_a INT, column_b INT) ;  
GO  
INSERT INTO dbo.doc_exz (column_a)VALUES ( 7 ) ;  
GO  
ALTER TABLE dbo.doc_exz  
ADD CONSTRAINT col_b_def  
DEFAULT 50 FOR column_b ;  
GO  
INSERT INTO dbo.doc_exz (column_a) VALUES ( 10 ) ;  
GO  
SELECT * FROM dbo.doc_exz ;  
GO  
DROP TABLE dbo.doc_exz ;  
GO  
```  
  
#### <a name="e-adding-several-columns-with-constraints"></a>E. 制約を含む列を複数追加する  
 次の例では、制約を含む列を複数追加します。制約は新しい列ごとに定義されます。 先頭の新しい列には `IDENTITY` プロパティが設定され、 テーブル内の各行では、ID 列に新しい増分値が挿入されます。  
  
```sql  
CREATE TABLE dbo.doc_exe ( column_a INT CONSTRAINT column_a_un UNIQUE) ;  
GO  
ALTER TABLE dbo.doc_exe ADD   
  
-- Add a PRIMARY KEY identity column.  
column_b INT IDENTITY  
CONSTRAINT column_b_pk PRIMARY KEY,   
  
-- Add a column that references another column in the same table.  
column_c INT NULL    
CONSTRAINT column_c_fk   
REFERENCES doc_exe(column_a),  
  
-- Add a column with a constraint to enforce that   
-- nonnull data is in a valid telephone number format.  
column_d VARCHAR(16) NULL   
CONSTRAINT column_d_chk  
CHECK   
(column_d LIKE '[0-9][0-9][0-9]-[0-9][0-9][0-9][0-9]' OR  
column_d LIKE  
'([0-9][0-9][0-9]) [0-9][0-9][0-9]-[0-9][0-9][0-9][0-9]'),  
  
-- Add a nonnull column with a default.  
column_e DECIMAL(3,3)  
CONSTRAINT column_e_default  
DEFAULT .081 ;  
GO  
EXEC sp_help doc_exe ;  
GO  
DROP TABLE dbo.doc_exe ;  
GO  
```  
  
#### <a name="f-adding-a-nullable-column-with-default-values"></a>F. NULL 値を許容する列を既定値と共に追加する  
 次の例では、NULL 値を許容する列を `DEFAULT` 定義と共に追加し、`WITH VALUES` を使用して、テーブル内の既存の各行に値を格納します。 WITH VALUES を使用しない場合、新しい列には NULL 値が格納されます。  
  
```sql  
CREATE TABLE dbo.doc_exf ( column_a INT) ;  
GO  
INSERT INTO dbo.doc_exf VALUES (1) ;  
GO  
ALTER TABLE dbo.doc_exf   
ADD AddDate smalldatetime NULL  
CONSTRAINT AddDateDflt  
DEFAULT GETDATE() WITH VALUES ;  
GO  
DROP TABLE dbo.doc_exf ;  
GO  
```  
  
#### <a name="g-creating-a-primary-key-constraint-with-index-options"></a>G. PRIMARY KEY 制約をインデックス オプションと共に作成する  
 次の例では、PRIMARY KEY 制約 `PK_TransactionHistoryArchive_TransactionID` を作成し、オプション `FILLFACTOR`、`ONLINE`、および `PAD_INDEX` を設定します。 結果のクラスター化インデックスは制約と同じ名前になります。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
```sql  
USE AdventureWorks2012;  
GO  
ALTER TABLE Production.TransactionHistoryArchive WITH NOCHECK   
ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)  
WITH (FILLFACTOR = 75, ONLINE = ON, PAD_INDEX = ON);  
GO  
```  
  
#### <a name="h-adding-a-sparse-column"></a>H. スパース列を追加する  
 次の例では、テーブル T1 にスパース列を追加する方法と、T1 のスパース列を変更する方法を示します。 テーブル `T1` を作成するコードは次のとおりです。  
  
```sql  
CREATE TABLE T1  
(C1 int PRIMARY KEY,  
C2 varchar(50) SPARSE NULL,  
C3 int SPARSE NULL,  
C4 int ) ;  
GO  
```  
  
 スパース列 `C5` を追加するには、次のステートメントを実行します。  
  
```sql  
ALTER TABLE T1  
ADD C5 char(100) SPARSE NULL ;  
GO  
```  
  
 非スパース列 `C4` をスパース列に変換するには、次のステートメントを実行します。  
  
```sql  
ALTER TABLE T1  
ALTER COLUMN C4 ADD SPARSE ;  
GO  
```  
  
 スパース列 `C4`を非スパース列に変換するには、次のステートメントを実行します。  
  
```sql  
ALTER TABLE T1  
ALTER COLUMN C4 DROP SPARSE;  
GO  
```  
  
#### <a name="i-adding-a-column-set"></a>I. 列セットを追加する  
 次の例では、テーブル `T2` に列を追加する方法を示します。 既にスパース列が含まれるテーブルには列セットを追加できません。 テーブル `T2` を作成するコードは次のとおりです。  
  
```sql  
CREATE TABLE T2  
(C1 int PRIMARY KEY,  
C2 varchar(50) NULL,  
C3 int NULL,  
C4 int ) ;  
GO  
```  
  
 次の 3 つのステートメントでは、`CS` という列セットが追加され、列 `C2` および `C3` が `SPARSE` に変更されます。  
  
```sql  
ALTER TABLE T2  
ADD CS XML COLUMN_SET FOR ALL_SPARSE_COLUMNS ;  
GO  
  
ALTER TABLE T2  
ALTER COLUMN C2 ADD SPARSE ;   
GO  
  
ALTER TABLE T2  
ALTER COLUMN C3 ADD SPARSE ;  
GO  
```  
  
#### <a name="j-adding-an-encrypted-column"></a>J. 暗号化された列を追加します。  
 次の文は、`PromotionCode` という名前の暗号化された列を追加します。  
  
```sql  
ALTER TABLE Customers ADD  
    PromotionCode nvarchar(100)   
    ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = MyCEK,  
    ENCRYPTION_TYPE = RANDOMIZED,  
    ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') ;  
```  
  
###  <a name="Drop"></a>列と制約を削除する  
 このセクションの例では、列と制約を削除する方法を示します。  
  
#### <a name="a-dropping-a-column-or-columns"></a>A. 1 つまたは複数の列を削除する  
 最初の例では、テーブルを変更して列を削除します。 2 番目の例では、複数の列を削除します。  
  
```sql  
CREATE TABLE dbo.doc_exb   
    (column_a INT  
     ,column_b VARCHAR(20) NULL  
     ,column_c datetime  
     ,column_d int) ;  
GO  
-- Remove a single column.  
ALTER TABLE dbo.doc_exb DROP COLUMN column_b ;  
GO  
-- Remove multiple columns.  
ALTER TABLE dbo.doc_exb DROP COLUMN column_c, column_d;  
```  
  
#### <a name="b-dropping-constraints-and-columns"></a>B. 制約と列を削除する  
 最初の例では、テーブルから `UNIQUE` 制約を削除します。 2 番目の例では、2 つの制約と 1 つの列を削除します。  
  
```sql  
CREATE TABLE dbo.doc_exc ( column_a int NOT NULL CONSTRAINT my_constraint UNIQUE) ;  
GO  
  
-- Example 1. Remove a single constraint.  
ALTER TABLE dbo.doc_exc DROP my_constraint ;  
GO  
  
DROP TABLE dbo.doc_exc;  
GO  
  
CREATE TABLE dbo.doc_exc ( column_a int    
                          NOT NULL CONSTRAINT my_constraint UNIQUE  
                          ,column_b int   
                          NOT NULL CONSTRAINT my_pk_constraint PRIMARY KEY) ;  
GO  
  
-- Example 2. Remove two constraints and one column  
-- The keyword CONSTRAINT is optional. The keyword COLUMN is required.  
ALTER TABLE dbo.doc_exc   
  
    DROP CONSTRAINT CONSTRAINT my_constraint, my_pk_constraint, COLUMN column_b ;  
GO  
```  
  
#### <a name="c-dropping-a-primary-key-constraint-in-the-online-mode"></a>C. ONLINE モードで PRIMARY KEY 制約を削除する  
 次の例では、`ONLINE` オプションを `ON` に設定して PRIMARY KEY 制約を削除します。  
  
```sql  
ALTER TABLE Production.TransactionHistoryArchive  
DROP CONSTRAINT PK_TransactionHistoryArchive_TransactionID  
WITH (ONLINE = ON);  
GO  
```  
  
#### <a name="d-adding-and-dropping-a-foreign-key-constraint"></a>D. FOREIGN KEY 制約を追加および削除する  
 次の例では、`ContactBackup` テーブルを作成し、`FOREIGN KEY` テーブルを参照する `Person.Person` 制約を追加した後、`FOREIGN KEY` 制約を削除して、テーブルを変更します。  
  
```sql  
CREATE TABLE Person.ContactBackup  
    (ContactID int) ;  
GO  
  
ALTER TABLE Person.ContactBackup  
ADD CONSTRAINT FK_ContactBacup_Contact FOREIGN KEY (ContactID)  
    REFERENCES Person.Person (BusinessEntityID) ;  
GO  
  
ALTER TABLE Person.ContactBackup  
DROP CONSTRAINT FK_ContactBacup_Contact ;  
GO  
  
DROP TABLE Person.ContactBackup ;  
```  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [例](#Example_Top)  
  
###  <a name="alter_column"></a> 列定義を変更する  
  
#### <a name="a-changing-the-data-type-of-a-column"></a>A. 列のデータ型を変更する  
 次の例では、テーブルの列を `INT` 型から `DECIMAL` 型に変更します。  
  
```sql  
CREATE TABLE dbo.doc_exy (column_a INT ) ;  
GO  
INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
GO  
ALTER TABLE dbo.doc_exy ALTER COLUMN column_a DECIMAL (5, 2) ;  
GO  
DROP TABLE dbo.doc_exy ;  
GO  
```  
  
#### <a name="b-changing-the-size-of-a-column"></a>B. 列のサイズを変更する  
 次の例では、**varchar** 列のサイズと、**decimal** 列の有効桁数および小数点以下桁数を拡張します。 列にデータが含まれているため、列のサイズを拡張することしかことができます。 また、`col_a` が一意インデックスで定義されていることにも注意してください。 この場合でも、`col_a` のサイズは拡張できます。データ型が **varchar** 型であり、インデックスが PRIMARY KEY 制約の結果として生じたものでないためです。  
  
```sql  
-- Create a two-column table with a unique index on the varchar column.  
CREATE TABLE dbo.doc_exy ( col_a varchar(5) UNIQUE NOT NULL, col_b decimal (4,2));  
GO  
INSERT INTO dbo.doc_exy VALUES ('Test', 99.99);  
GO  
-- Verify the current column size.  
SELECT name, TYPE_NAME(system_type_id), max_length, precision, scale  
FROM sys.columns WHERE object_id = OBJECT_ID(N'dbo.doc_exy');  
GO  
-- Increase the size of the varchar column.  
ALTER TABLE dbo.doc_exy ALTER COLUMN col_a varchar(25);  
GO  
-- Increase the scale and precision of the decimal column.  
ALTER TABLE dbo.doc_exy ALTER COLUMN col_b decimal (10,4);  
GO  
-- Insert a new row.  
INSERT INTO dbo.doc_exy VALUES ('MyNewColumnSize', 99999.9999) ;  
GO  
-- Verify the current column size.  
SELECT name, TYPE_NAME(system_type_id), max_length, precision, scale  
FROM sys.columns WHERE object_id = OBJECT_ID(N'dbo.doc_exy');  
```  
  
#### <a name="c-changing-column-collation"></a>C. 列の照合順序を変更する  
 次の例では、列の照合順序を変更する方法を示します。 まず、既定のユーザー照合順序でテーブルを作成します。  
  
```sql  
CREATE TABLE T3  
(C1 int PRIMARY KEY,  
C2 varchar(50) NULL,  
C3 int NULL,  
C4 int ) ;  
GO  
```  
  
 次に、列 `C2` の照合順序を Latin1_General_BIN に変更します。 データ型は変更しませんが、必須であることに注意してください。  
  
```sql  
ALTER TABLE T3  
ALTER COLUMN C2 varchar(50) COLLATE Latin1_General_BIN;  
GO  
```  
  
###  <a name="alter_table"></a> テーブル定義を変更する  
 このセクションの例では、テーブルの定義を変更する方法を示します。  
  
#### <a name="a-modifying-a-table-to-change-the-compression"></a>A. テーブルを修正して圧縮を変更する  
 次の例では、非パーティション テーブルの圧縮を変更します。 ヒープまたはクラスター化インデックスが再構築されます。 テーブルがヒープの場合、すべての非クラスター化インデックスが再構築されます。  
  
```sql  
ALTER TABLE T1   
REBUILD WITH (DATA_COMPRESSION = PAGE);  
```  
  
 次の例では、パーティション テーブルの圧縮を変更します。 `REBUILD PARTITION = 1` 構文を使用すると、パーティション番号 `1` のみが再構築されます。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
```sql  
ALTER TABLE PartitionTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  NONE) ;  
GO  
```  
  
次の代替構文を使用して同じ操作を行うと、テーブル内のすべてのパーティションが再構築されます。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
```sql  
ALTER TABLE PartitionTable1   
REBUILD PARTITION = ALL   
WITH (DATA_COMPRESSION = PAGE ON PARTITIONS(1) ) ;  
```  
  
 その他のデータ圧縮の例については、「[データ圧縮](../../relational-databases/data-compression/data-compression.md)」を参照してください。  
  
#### <a name="b-modifying-a-columnstore-table-to-change-archival-compression"></a>B. 列ストアを修正して保存用圧縮を変更する  
 次の例では、追加の圧縮アルゴリズムを適用することによって、列ストア テーブル パーティションをさらに圧縮します。 これによってテーブルのサイズは小さくなりますが、保存と取得に必要な時間が増加します。 これは、アーカイブや、ストレージの容量を減らす必要があり、しかも保存と取得に時間をかける余裕がある状況には便利です。  
  
**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
```sql  
ALTER TABLE PartitionTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE) ;  
GO  
```  
  
次の例では、COLUMNSTORE_ARCHIVE オプションで圧縮された列ストア テーブル パーティションを解凍します。 復元されるデータは、すべての列ストア テーブルに使用された列ストア圧縮を使用して引き続き圧縮されます。  
  
**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
```sql  
ALTER TABLE PartitionTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  COLUMNSTORE) ;  
GO  
```  
  
#### <a name="c-switching-partitions-between-tables"></a>C. テーブル間でパーティションを切り替える  
 次の例では、パーティション テーブルを作成します。ここでは、データベースにパーティション構成 `myRangePS1` が既に作成されていることが前提となります。 次に、パーティション テーブルと同じ構造で、`PARTITION 2` テーブルの `PartitionTable` と同じファイル グループに、非パーティション テーブルを作成し、 `PARTITION 2` テーブルの `PartitionTable` のデータを、`NonPartitionTable` テーブルに切り替えます。  
  
```sql  
CREATE TABLE PartitionTable (col1 int, col2 char(10))  
ON myRangePS1 (col1) ;  
GO  
CREATE TABLE NonPartitionTable (col1 int, col2 char(10))  
ON test2fg ;  
GO  
ALTER TABLE PartitionTable SWITCH PARTITION 2 TO NonPartitionTable ;  
GO  
```  
  
#### <a name="d-allowing-lock-escalation-on-partitioned-tables"></a>D. パーティション テーブルでのロック エスカレーションを許可する  
 次の例では、パーティション テーブルで、パーティション レベルへのロック エスカレーションを有効にします。 テーブルがパーティション分割されていない場合は、ロック エスカレーションは TABLE レベルに設定されます。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
```sql  
ALTER TABLE dbo.T1 SET (LOCK_ESCALATION = AUTO);  
GO  
```  
  
#### <a name="e-configuring-change-tracking-on-a-table"></a>E. テーブルに変更の追跡を構成する  
 次の例では、`Person.Person` テーブルの変更の追跡を有効にします。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
```sql  
USE AdventureWorks2012;  
ALTER TABLE Person.Person  
ENABLE CHANGE_TRACKING;  
```  
  
次の例では、変更の追跡を有効にし、変更時に更新される列の追跡を有効にします。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```sql  
USE AdventureWorks2012;  
GO  
ALTER TABLE Person.Person  
ENABLE CHANGE_TRACKING  
WITH (TRACK_COLUMNS_UPDATED = ON)  
```  
  
次の例では、`Person.Person` テーブルの変更の追跡を無効にします。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
```sql  
USE AdventureWorks2012;  
Go  
ALTER TABLE Person.Person  
DISABLE CHANGE_TRACKING;  
```  

###  <a name="disable_enable"></a>制約およびトリガーを無効および有効にする  
  
#### <a name="a-disabling-and-re-enabling-a-constraint"></a>A. 制約を無効化および再有効化する  
 次の例では、データとして許容される給与を制限する制約を無効にします。 ここでは、`NOCHECK CONSTRAINT` と共に `ALTER TABLE` を使用して制約を無効にし、通常は制約違反となるような挿入を許可します。 次に、`CHECK CONSTRAINT` を使用して制約を再び有効にします。  
  
```sql  
CREATE TABLE dbo.cnst_example   
(id INT NOT NULL,  
 name VARCHAR(10) NOT NULL,  
 salary MONEY NOT NULL  
    CONSTRAINT salary_cap CHECK (salary < 100000)  
);  
  
-- Valid inserts  
INSERT INTO dbo.cnst_example VALUES (1,'Joe Brown',65000);  
INSERT INTO dbo.cnst_example VALUES (2,'Mary Smith',75000);  
  
-- This insert violates the constraint.  
INSERT INTO dbo.cnst_example VALUES (3,'Pat Jones',105000);  
  
-- Disable the constraint and try again.  
ALTER TABLE dbo.cnst_example NOCHECK CONSTRAINT salary_cap;  
INSERT INTO dbo.cnst_example VALUES (3,'Pat Jones',105000);  
  
-- Re-enable the constraint and try another insert; this will fail.  
ALTER TABLE dbo.cnst_example CHECK CONSTRAINT salary_cap;  
INSERT INTO dbo.cnst_example VALUES (4,'Eric James',110000) ;  
```  
  
#### <a name="b-disabling-and-re-enabling-a-trigger"></a>B. トリガーを無効化および再有効化する  
 次の例では、`DISABLE TRIGGER` の `ALTER TABLE` オプションを使用してトリガーを無効にし、通常はトリガー違反となるような挿入を許可します。 次に、`ENABLE TRIGGER` を使用してトリガーを再び有効にします。  
  
```sql  
CREATE TABLE dbo.trig_example   
(id INT,   
name VARCHAR(12),  
salary MONEY) ;  
GO  
-- Create the trigger.  
CREATE TRIGGER dbo.trig1 ON dbo.trig_example FOR INSERT  
AS  
IF (SELECT COUNT(*) FROM INSERTED  
WHERE salary > 100000) > 0  
BEGIN  
    print 'TRIG1 Error: you attempted to insert a salary > $100,000'  
    ROLLBACK TRANSACTION  
END ;  
GO  
-- Try an insert that violates the trigger.  
INSERT INTO dbo.trig_example VALUES (1,'Pat Smith',100001) ;  
GO  
-- Disable the trigger.  
ALTER TABLE dbo.trig_example DISABLE TRIGGER trig1 ;  
GO  
-- Try an insert that would typically violate the trigger.  
INSERT INTO dbo.trig_example VALUES (2,'Chuck Jones',100001) ;  
GO  
-- Re-enable the trigger.  
ALTER TABLE dbo.trig_example ENABLE TRIGGER trig1 ;  
GO  
-- Try an insert that violates the trigger.  
INSERT INTO dbo.trig_example VALUES (3,'Mary Booth',100001) ;  
GO  
```  
 
### <a name="online"></a>オンライン操作  
  
#### <a name="a-online-index-rebuild-using-low-priority-wait-options"></a>A. 優先度の低い待機オプションを使用してオンライン インデックス再構築を行う  
 次の例では、優先度の低い待機オプションを指定する、オンライン インデックス再構築を実行する方法を示します。  
  
**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
```sql  
ALTER TABLE T1   
REBUILD WITH   
(  
    PAD_INDEX = ON,  
    ONLINE = ON ( WAIT_AT_LOW_PRIORITY ( MAX_DURATION = 4 MINUTES, 
                                         ABORT_AFTER_WAIT = BLOCKERS ) )  
)  
;  
```  
  
#### <a name="b-online-alter-column"></a>B. オンラインでの列の変更  
 次の例は、ONLINE オプションを使用して列の変更操作を実行する方法を示しています。  
  
**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
```sql  
CREATE TABLE dbo.doc_exy (column_a INT ) ;  
GO  
INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
GO  
ALTER TABLE dbo.doc_exy   
    ALTER COLUMN column_a DECIMAL (5, 2) WITH (ONLINE = ON);  
GO  
sp_help doc_exy;  
DROP TABLE dbo.doc_exy ;  
GO  
```  
  
###  <a name="system_versioning"></a> システムのバージョン管理  
 システムのバージョン管理を使用する構文に慣れるには、次の 4 つの例を参照してください。 詳細については、「[システム バージョン管理されたテンポラル テーブルの概要](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)」を参照してください。  
  
**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。  
  
#### <a name="a-add-system-versioning-to-existing-tables"></a>A. システムのバージョン管理を既存のテーブルに追加します。  
 次の例では、既存のテーブルをシステムのバージョン管理を追加し、将来の履歴テーブルを作成する方法を示します。 この例では、主キーが定義された `InsurancePolicy` という既存のテーブルがあることを前提としています。 この例では、これらの値を null にすることはできませんので、開始時刻と終了の既定値を使用してシステムのバージョン管理の場合は、新しく作成された期間列を設定します。 この例では、非表示の句を使用して、既存のアプリケーションが、現在のテーブルとの対話に与える影響がないことを確認します。  [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] でのみ利用できる HISTORY_RETENTION_PERIOD も使用します。 
  
```sql  
--Alter non-temporal table to define periods for system versioning  
ALTER TABLE InsurancePolicy  
ADD PERIOD FOR SYSTEM_TIME (SysStartTime, SysEndTime),   
SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL 
    DEFAULT GETUTCDATE(),   
SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL 
    DEFAULT CONVERT(DATETIME2, '9999-12-31 23:59:59.99999999');  
--Enable system versioning with 1 year retention for historical data
ALTER TABLE InsurancePolicy 
SET (SYSTEM_VERSIONING = ON (HISTORY_RETENTION_PERIOD = 1 YEAR));  
```  
  
#### <a name="b-migrate-an-existing-solution-to-use-system-versioning"></a>B. システムのバージョン管理を使用する既存のソリューションを移行します。  
 次の例では、一時的なサポートを模倣するために、トリガーを使用するソリューションからシステムのバージョン管理に移行する方法を示します。 この例では、`ProjectTaskCurrent` テーブルと `ProjectTaskHistory` テーブルを使用する既存のソリューションがあることを前提としています。つまり、変更された日付と改訂された日付の列が期間として使用され、これらの期間列には datetime2 データ型を使用されず、`ProjectTaskCurrent` テーブルに主キーが定義されています。  
  
```sql  
-- Drop existing trigger  
DROP TRIGGER ProjectTaskCurrent_Trigger;  
-- Adjust the schema for current and history table  
-- Change data types for existing period columns  
ALTER TABLE ProjectTaskCurrent ALTER COLUMN [Changed Date] datetime2 NOT NULL;  
ALTER TABLE ProjectTaskCurrent ALTER COLUMN [Revised Date] datetime2 NOT NULL;  
  
ALTER TABLE ProjectTaskHistory ALTER COLUMN [Changed Date] datetime2 NOT NULL;  
ALTER TABLE ProjectTaskHistory ALTER COLUMN [Revised Date] datetime2 NOT NULL;  
  
-- Add SYSTEM_TIME period and set system versioning with linking two existing tables  
-- (a certain set of data checks happen in the background)  
ALTER TABLE ProjectTaskCurrent  
ADD PERIOD FOR SYSTEM_TIME ([Changed Date], [Revised Date])  
  
ALTER TABLE ProjectTaskCurrent  
SET (SYSTEM_VERSIONING = ON (HISTORY_TABLE = dbo.ProjectTaskHistory, DATA_CONSISTENCY_CHECK = ON))  
```  
  
#### <a name="c-disabling-and-re-enabling-system-versioning-to-change-table-schema"></a>C. 無効にして、テーブルのスキーマを変更するシステムのバージョン管理を再度有効にします。  
 この例は、`Department` テーブルでシステムのバージョン管理を無効にし、列を追加し、システムのバージョン管理を再度有効にする方法を示しています。 テーブルのスキーマを変更するのには、システムのバージョン管理を無効化が必要です。 有効にする、DBA は、データの整合性をスキップするは、システムのバージョン管理を再度有効にするときに確認して、パフォーマンスを得るためのメリットを得る、テーブルのスキーマの更新中に、両方のテーブルに更新プログラムを防ぐために、トランザクション内で次の手順を実行します。 統計を作成する、パーティションの切り替え、圧縮を 1 つまたは両方のテーブルに適用するなどのタスクをシステムのバージョン管理を無効にする必要がないことに注意してください。  
  
```sql  
BEGIN TRAN  
/* Takes schema lock on both tables */  
ALTER TABLE Department  
    SET (SYSTEM_VERSIONING = OFF);  
/* expand table schema for temporal table */  
ALTER TABLE Department  
     ADD Col5 int NOT NULL DEFAULT 0;  
/* Expand table schema for history table */  
ALTER TABLE DepartmentHistory  
    ADD Col5 int NOT NULL DEFAULT 0;  
/* Re-establish versioning again  */
ALTER TABLE Department  
    SET (SYSTEM_VERSIONING = ON (HISTORY_TABLE=dbo.DepartmentHistory, 
                                 DATA_CONSISTENCY_CHECK = OFF));  
COMMIT   
```  
  
#### <a name="d-removing-system-versioning"></a>D. システムのバージョン管理を削除します。  
 この例は、Department テーブルからシステムのバージョン管理を完全に削除し、`DepartmentHistory` テーブルを削除する方法を示しています。 必要に応じて、システムのバージョン管理情報を記録する、システムによって使用される期間の列を削除することがもできます。 システムのバージョン管理が有効な場合は、`Department` か `DepartmentHistory` のいずれかのテーブルを削除できないことに注意してください。  
  
```sql  
ALTER TABLE Department  
    SET (SYSTEM_VERSIONING = OFF);  
ALTER TABLE Department  
DROP PEROD FOR SYSTEM_TIME;  
DROP TABLE DepartmentHistory;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例 A から C では、[!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] データベースの `FactResellerSales` テーブルを使用しています。  
  
### <a name="a-determining-if-a-table-is-partitioned"></a>A. テーブルがパーティション分割されているかどうかを調べる  
 次のクエリでは、テーブル `FactResellerSales` がパーティション分割されている場合、1 つ以上の行が返されます。 テーブルがパーティション分割されていない場合は、行が返されません。  
  
```sql  
SELECT * FROM sys.partitions AS p  
JOIN sys.tables AS t  
    ON  p.object_id = t.object_id  
WHERE p.partition_id IS NOT NULL  
    AND t.name = 'FactResellerSales';  
```  
  
### <a name="b-determining-boundary-values-for-a-partitioned-table"></a>B. パーティション テーブルの境界値を調べる  
 次のクエリでは、 `FactResellerSales` テーブルの各パーティションの境界値を返します。  
  
```sql  
SELECT t.name AS TableName, i.name AS IndexName, p.partition_number, 
    p.partition_id, i.data_space_id, f.function_id, f.type_desc, 
    r.boundary_id, r.value AS BoundaryValue   
FROM sys.tables AS t  
JOIN sys.indexes AS i  
    ON t.object_id = i.object_id  
JOIN sys.partitions AS p  
    ON i.object_id = p.object_id AND i.index_id = p.index_id   
JOIN  sys.partition_schemes AS s   
    ON i.data_space_id = s.data_space_id  
JOIN sys.partition_functions AS f   
    ON s.function_id = f.function_id  
LEFT JOIN sys.partition_range_values AS r   
    ON f.function_id = r.function_id and r.boundary_id = p.partition_number  
WHERE t.name = 'FactResellerSales' AND i.type <= 1  
ORDER BY p.partition_number;  
```  
  
### <a name="c-determining-the-partition-column-for-a-partitioned-table"></a>C. パーティション テーブルのパーティション列を調べる  
 次のクエリでは、テーブルのパーティション分割列の名前を返します。 `FactResellerSales`」をご覧ください。  
  
```sql  
SELECT t.object_id AS Object_ID, t.name AS TableName, 
    ic.column_id as PartitioningColumnID, c.name AS PartitioningColumnName   
FROM sys.tables AS t  
JOIN sys.indexes AS i  
    ON t.object_id = i.object_id  
JOIN sys.columns AS c  
    ON t.object_id = c.object_id  
JOIN sys.partition_schemes AS ps  
    ON ps.data_space_id = i.data_space_id  
JOIN sys.index_columns AS ic  
    ON ic.object_id = i.object_id 
    AND ic.index_id = i.index_id AND ic.partition_ordinal > 0  
WHERE t.name = 'FactResellerSales'  
AND i.type <= 1  
AND c.column_id = ic.column_id;  
```  
  
### <a name="d-merging-two-partitions"></a>D. 2 つのパーティションをマージする  
次の例では、テーブル上の 2 つのパーティションをマージします。  
  
`Customer` テーブルの定義は次のとおりです。  
  
```sql  
CREATE TABLE Customer (  
    id int NOT NULL,  
    lastName varchar(20),  
    orderCount int,  
    orderDate date)  
WITH   
    ( DISTRIBUTION = HASH(id),  
    PARTITION ( orderCount RANGE LEFT  
    FOR VALUES (1, 5, 10, 25, 50, 100)));  
```  
  
 次のコマンドは、10 と 25 のパーティション境界を結合します。  
  
```sql  
ALTER TABLE Customer MERGE RANGE (10);  
```  
  
 テーブルの新しい DDL は次のとおりです。  
  
```sql  
CREATE TABLE Customer (  
    id int NOT NULL,  
    lastName varchar(20),  
    orderCount int,  
    orderDate date)  
WITH   
    ( DISTRIBUTION = HASH(id),  
    PARTITION ( orderCount RANGE LEFT  
    FOR VALUES (1, 5, 25, 50, 100)));  
```  
  
### <a name="e-splitting-a-partition"></a>E. パーティションを分割する  
 次の例では、テーブル上のパーティションを分割します。  
  
 `Customer` テーブルには、次の DDL があります。  
  
```sql  
DROP TABLE Customer;  
  
CREATE TABLE Customer (  
    id int NOT NULL,  
    lastName varchar(20),  
    orderCount int,  
    orderDate date)  
WITH   
    ( DISTRIBUTION = HASH(id),  
    PARTITION ( orderCount RANGE LEFT  
    FOR VALUES (1, 5, 10, 25, 50, 100 )));  
```  
  
 次のコマンドは、50 と 100 の間に値 75 にバインドされた新しいパーティションを作成します。  
  
```sql  
ALTER TABLE Customer SPLIT RANGE (75);  
```  
  
 テーブルの新しい DDL は次のとおりです。  
  
```sql  
CREATE TABLE Customer (  
   id int NOT NULL,  
   lastName varchar(20),  
   orderCount int,  
   orderDate date)  
   WITH DISTRIBUTION = HASH(id),  
   PARTITION ( orderCount (RANGE LEFT  
      FOR VALUES (1, 5, 10, 25, 50, 75, 100 )));  
```  
  
### <a name="f-using-switch-to-move-a-partition-to-a-history-table"></a>F. SWITCH を使用してパーティションを履歴テーブルに移動する  
 次の例では、`Orders` テーブルのパーティション内のデータを `OrdersHistory` テーブル内のパーティションに移動します。  
  
 `Orders` テーブルには、次の DDL があります。  
  
```sql  
CREATE TABLE Orders (  
    id INT,  
    city VARCHAR (25),  
    lastUpdateDate DATE,  
    orderDate DATE )  
WITH   
    (DISTRIBUTION = HASH ( id ),  
    PARTITION ( orderDate RANGE RIGHT   
    FOR VALUES ('2004-01-01', '2005-01-01', '2006-01-01', '2007-01-01' )));  
```  
  
 この例では、`Orders` テーブルに次のパーティションがあります。 各パーティションにはデータがあります。  
  
|パーティション|データがある|境界の範囲|  
|---------------|---------------|--------------------|  
|@shouldalert|はい|OrderDate < '2004-01-01'|  
|2|はい|'2004-01-01' <= OrderDate < '2005-01-01'|  
|3|はい|'2005-01-01' <= OrderDate< '2006-01-01'|  
|4|はい|'2006-01-01'<= OrderDate < '2007-01-01'|  
|5|はい|'2007-01-01' <= OrderDate|  
  
-   パーティション 1 (データがある): OrderDate < '2004-01-01'  
-   パーティション 2 (データがある): '2004-01-01' <= OrderDate < '2005-01-01'  
-   パーティション 3 (データがある): '2005-01-01' <= OrderDate< '2006-01-01'  
-   パーティション 4 (データがある): '2006-01-01'<= OrderDate < '2007-01-01'  
-   パーティション 5 (データがある): '2007-01-01' <= OrderDate  
  
`OrdersHistory` テーブルには、`Orders` テーブルと列と列名が同じ次の DDL があります。 どちらも `id` 列に対してハッシュ分散されています。  
  
```sql  
CREATE TABLE OrdersHistory (  
   id INT,  
   city VARCHAR (25),  
   lastUpdateDate DATE,  
   orderDate DATE )  
WITH   
    (DISTRIBUTION = HASH ( id ),  
    PARTITION ( orderDate RANGE RIGHT   
    FOR VALUES ( '2004-01-01' )));  
```  
  
 列と列名は同じである必要がありますが、パーティションの境界が同じである必要はありません。 この例では、`OrdersHistory` テーブルに次の 2 つのパーティションがあり、両方のパーティションが空です。  
  
-   パーティション 1 (データがない): OrderDate < '2004-01-01'  
-   パーティション 2 (空): '2004-01-01' <= OrderDate  
  
これら 2 つのテーブルの場合、次のコマンドで、`OrderDate < '2004-01-01'` があるすべての行は `Orders` テーブルから `OrdersHistory` テーブルに移動されます。  
  
```sql  
ALTER TABLE Orders SWITCH PARTITION 1 TO OrdersHistory PARTITION 1;  
```  
  
 その結果、`Orders` の最初のパーティションは空になり、`OrdersHistory` の最初のパーティションにはデータがある状態になります。 テーブルは次のようになります。  
  
 `Orders` テーブル  
  
-   パーティション 1 (空): OrderDate < '2004-01-01'  
-   パーティション 2 (データがある): '2004-01-01' <= OrderDate < '2005-01-01'  
-   パーティション 3 (データがある): '2005-01-01' <= OrderDate< '2006-01-01'  
-   パーティション 4 (データがある): '2006-01-01'<= OrderDate < '2007-01-01'  
-   パーティション 5 (データがある): '2007-01-01' <= OrderDate  
  
 `OrdersHistory` テーブル  
  
-   パーティション 1 (データがある): OrderDate < '2004-01-01'  
-   パーティション 2 (空): '2004-01-01' <= OrderDate  
  
`Orders` テーブルをクリーン アップするには、次のようにパーティション 1 と 2 をマージして空のパーティションを削除します。  
  
```sql  
ALTER TABLE Orders MERGE RANGE ('2004-01-01');  
```  
  
 マージ後、`Orders` テーブルには次のパーティションがあります。  
  
 `Orders` テーブル  
  
-   パーティション 1 (データがある): OrderDate < '2005-01-01'  
-   パーティション 2 (データがある): '2005-01-01' <= OrderDate< '2006-01-01'  
-   パーティション 3 (データがある): '2006-01-01'<= OrderDate < '2007-01-01'  
-   パーティション 4 (データがある): '2007-01-01' <= OrderDate  
  
もう 1 年が経過し、2005 年をアーカイブする準備が整ったとします。 空のパーティションを次のように分割して、2005 年の空のパーティションを `OrdersHistory` テーブルに割り当てることができます。  
  
```sql  
ALTER TABLE OrdersHistory SPLIT RANGE ('2005-01-01');  
```  
  
 分割後、`OrdersHistory` テーブルには次のパーティションがあります。  
  
 `OrdersHistory` テーブル  
  
-   パーティション 1 (データがある): OrderDate < '2004-01-01'  
-   パーティション 2 (空): '2004-01-01' < '2005-01-01'  
-   パーティション 3 (空): '2005-01-01' <= OrderDate  
  
## <a name="see-also"></a>参照  
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [DROP TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [ALTER PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/alter-partition-scheme-transact-sql.md)   
 [ALTER PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-partition-function-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

