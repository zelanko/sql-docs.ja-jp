---
title: "型 (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sql13.swb.sysdatatype.properties.f1
- CREATE TYPE
- TYPE_TSQL
- TYPE
- CREATE_TYPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- UDTs [SQL Server], creating
- CLR user-defined types [SQL Server]
- user-defined table types [SQL Server]
- user-defined types [SQL Server], creating
- CREATE TYPE statement
- alias data types [SQL Server], creating
- data types [SQL Server], creating
ms.assetid: 2202236b-e09f-40a1-bbc7-b8cff7488905
caps.latest.revision: 92
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4e7f411871d98fc6854b97478402567017d28222
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-type-transact-sql"></a>CREATE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベースで別名データ型またはユーザー定義型を作成[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。 別名データ型の実装は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のネイティブ システム型に基づきます。 内のアセンブリのクラスを使用して、ユーザー定義型が実装されている、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]共通言語ランタイム (CLR)。 ユーザー定義型をその実装をバインドする型の実装を含む CLR アセンブリ必要があります最初に登録する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して[CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md)です。  
  
 CLR コードを実行する機能が既定でオフ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 これらの参照が実行されませんが、作成、変更およびマネージ コード モジュールを参照するデータベース オブジェクトを削除することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しない限り、 [clr enabled オプション](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)を使用して有効になっているは[sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
 
> [!NOTE]  
>  SQL Server への .NET Framework CLR の統合はこのトピックで説明します。 CLR 統合は、Azure には適用されません[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Disk-Based Type Syntax  
CREATE TYPE [ schema_name. ] type_name  
{   
    FROM base_type   
    [ ( precision [ , scale ] ) ]  
    [ NULL | NOT NULL ]   
  | EXTERNAL NAME assembly_name [ .class_name ]   
  | AS TABLE ( { <column_definition> | <computed_column_definition> }  
        [ <table_constraint> ] [ ,...n ] )    
} [ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ COLLATE collation_name ]   
    [ NULL | NOT NULL ]  
    [   
        DEFAULT constant_expression ]   
      | [ IDENTITY [ ( seed ,increment ) ]   
    ]  
    [ ROWGUIDCOL ] [ <column_constraint> [ ...n ] ]   
  
<data type> ::=   
[ type_schema_name . ] type_name   
    [ ( precision [ , scale ] | max |   
                [ { CONTENT | DOCUMENT } ] xml_schema_collection ) ]   
  
<column_constraint> ::=   
{     { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [   
            WITH ( <index_option> [ ,...n ] )   
        ]  
  | CHECK ( logical_expression )   
}   
  
<computed_column_definition> ::=  
  
column_name AS computed_column_expression   
[ PERSISTED [ NOT NULL ] ]  
[   
    { PRIMARY KEY | UNIQUE }  
        [ CLUSTERED | NONCLUSTERED ]  
        [   
            WITH ( <index_option> [ ,...n ] )  
        ]  
    | CHECK ( logical_expression )   
]   
  
<table_constraint> ::=  
{   
    { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
    ( column [ ASC | DESC ] [ ,...n ] )   
        [   
    WITH ( <index_option> [ ,...n ] )   
        ]  
    | CHECK ( logical_expression )   
}   
  
<index_option> ::=  
{  
    IGNORE_DUP_KEY = { ON | OFF }  
}  
```  
  
```  
-- Memory-Optimized Table Type Syntax  
CREATE TYPE [schema_name. ] type_name  
AS TABLE ( { <column_definition> }  
    |  [ <table_constraint> ] [ ,... n ]    
    | [ <table_index> ] [ ,... n ]    } )
    [ WITH ( <table_option> [ ,... n ] ) ]  
 [ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ COLLATE collation_name ]   [ NULL | NOT NULL ]    [  
      [ IDENTITY [ (1 , 1) ]  
    ]  
    [ <column_constraint> [ ... n ] ]    [ <column_index> ]  
  
<data type> ::=  
 [type_schema_name . ] type_name [ (precision [ , scale ]) ]  
  
<column_constraint> ::=  
{ PRIMARY KEY {   NONCLUSTERED HASH WITH (BUCKET_COUNT = bucket_count) 
                | NONCLUSTERED } }  
  
< table_constraint > ::=  
{ PRIMARY KEY { NONCLUSTERED HASH (column [ ,... n ] ) 
                   WITH (BUCKET_COUNT = bucket_count) 
               | NONCLUSTERED  (column [ ASC | DESC ] [ ,... n ] )  } }  
  
<column_index> ::=  
  INDEX index_name  
{ { [ NONCLUSTERED ] HASH WITH (BUCKET_COUNT = bucket_count) 
     | NONCLUSTERED } }  
  
< table_index > ::=  
  INDEX constraint_name  
{ { [ NONCLUSTERED ] HASH (column [ ,... n ] ) WITH (BUCKET_COUNT = bucket_count) 
 |  [NONCLUSTERED]  (column [ ASC | DESC ] [ ,... n ] )} }  
  
<table_option> ::=  
{  
    [MEMORY_OPTIMIZED = {ON | OFF}]  
}  
```  
  
## <a name="arguments"></a>引数  
 *schema_name*  
 別名データ型またはユーザー定義型が所属しているスキーマの名前です。  
  
 *type_name*  
 別名データ型またはユーザー定義型の名前です。 型名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 *base_type*  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]別名データ型の基になるデータ型を指定します。 *base_type*は**sysname**, で、既定値はありませんは、次の値のいずれかを指定します。  
  
|||||  
|-|-|-|-|  
|**bigint**|**バイナリ (**  *n*  **)**|**bit**|**char (**  *n*  **)**|  
|**date**|**datetime**|**datetime2**|**datetimeoffset**|  
|**decimal**|**float**|**image**|**int**|  
|**money**|**nchar (**  *n*  **)**|**ntext**|**numeric**|  
|**nvarchar (**  *n*  & #124 です。**最大)**|**real**|**smalldatetime**|**smallint**|  
|**smallmoney**|**sql_variant**|**text**|**time**|  
|**tinyint**|**uniqueidentifier**|**varbinary (**  *n*  & #124 です。**最大)**|**varchar (**  *n*  & #124 です。**最大)**|  
  
 *base_type*これらのシステム データ型のいずれかにマップされる任意のデータ型のシノニムをすることもできます。  
  
 *有効桁数 (precision)*  
 **Decimal**または**数値**は、小数点の右側および左側に格納できる 10 進数字の最大合計数を示す正の整数。 詳細については、次を参照してください[decimal および numeric 型 &#40;。TRANSACT-SQL と #41 です。](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 *scale*  
 **Decimal**または**数値**正の整数を小数点の右側に格納できる 10 進数字の最大数を示す、有効桁数未満にする必要があります. 詳細については、次を参照してください[decimal および numeric 型 &#40;。TRANSACT-SQL と #41 です。](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 **NULL** |NOT NULL します。  
 型が NULL 値を保持できるかどうかを指定します。 指定しない場合は、NULL が既定値です。  
  
 *アセンブリ名*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]共通言語ランタイムでのユーザー定義型の実装を参照するアセンブリ。 *アセンブリ名*で既存のアセンブリに一致する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]現在のデータベースでします。  
  
> [!NOTE]  
>  EXTERNAL_NAME は、包含データベースでは使用できません。  
  
 **[.** *class_name***]**   
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ユーザー定義型を実装するアセンブリ内のクラスを指定します。 *class_name*有効な識別子である必要があり、アセンブリの可視性を持つアセンブリ内のクラスとして存在する必要があります。 *class_name*は、データベースの照合順序に関係なく大文字小文字が区別し、対応するアセンブリ内のクラス名と一致する必要があります。 クラス名が角かっこで囲まれた名前空間の修飾名を指定できます (****) 場合は、クラスを記述するために使用するプログラミング言語は c# などの名前空間の概念を使用します。 場合*class_name*が指定されていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と同じであると仮定*type_name*です。  
  
 \<column_definition >  
 ユーザー定義テーブル型の列を定義します。  
  
 \<データ型 >  
 ユーザー定義テーブル型の列でデータ型を定義します。 データ型の詳細については、次を参照してください。[データ型 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/data-types-transact-sql.md). テーブルの詳細については、次を参照してください。 [CREATE TABLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-table-transact-sql.md).  
  
 \<column_constraint >  
 ユーザー定義テーブル型の列制約を定義します。 PRIMARY KEY、UNIQUE、CHECK などの制約がサポートされています。 テーブルの詳細については、次を参照してください。 [CREATE TABLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-table-transact-sql.md).  
  
 \<computed_column_definition >  
 計算列の式をユーザー定義テーブル型の列として定義します。 テーブルの詳細については、次を参照してください。 [CREATE TABLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-table-transact-sql.md).  
  
 \<table_constraint >  
 ユーザー定義テーブル型のテーブル制約を定義します。 PRIMARY KEY、UNIQUE、CHECK などの制約がサポートされています。  
  
 \<index_option >  
 一意のクラスター化インデックスまたは一意の非クラスター化インデックスにおいて、複数行の挿入操作で重複したキー値が見つかった場合の、エラー応答を指定します。 インデックス オプションの詳細については、次を参照してください。 [CREATE INDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-index-transact-sql.md).  
  
 INDEX  
 CREATE TABLE ステートメントの一部として列インデックスとテーブル インデックスを指定する必要があります。 メモリ最適化テーブルでは、CREATE INDEX および DROP INDEX はサポートされません。  
  
 MEMORY_OPTIMIZED  
 **適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 テーブル型がメモリ最適化かどうかを示します。 既定では、このオプションはオフになっています。テーブル (型) は、メモリ最適化テーブル (型) ではありません。 メモリ最適化テーブル型は、他のユーザー テーブルと同様にスキーマがディスク上に保存されるメモリ最適化ユーザー テーブルです。  
  
 BUCKET_COUNT  
 **適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 ハッシュ インデックスに作成されるバケットの数を示します。 ハッシュ インデックスの BUCKET_COUNT の最大値は 1,073,741,824 です。 バケット数の詳細については、次を参照してください。[メモリ最適化テーブルのインデックス](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)です。 *bucket_count*必要な引数です。  
  
 HASH  
 **適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 ハッシュ インデックスを作成することを示します。 ハッシュ インデックスは、メモリ最適化テーブルでのみサポートされます。  
  
## <a name="remarks"></a>解説  
 参照されるアセンブリのクラスは*assembly_name*とそのメソッドでユーザー定義型を実装するためのすべての要件を満たす必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 これらの要件の詳細については、次を参照してください。 [clr ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)です。  
  
 その他、次のような注意事項があります。  
  
-   メソッド、クラスをオーバー ロードできますがこれらのメソッドでのみ呼び出すことが、マネージ コード内からではなく[!INCLUDE[tsql](../../includes/tsql-md.md)]です。  
  
-   として、静的メンバーを宣言する必要があります**const**または**readonly**場合*assembly_name*が SAFE または EXTERNAL_ACCESS します。  
  
 データベース内では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で CLR からアップロードされた任意の指定された型に対して、1 つのユーザー定義型のみを登録できます。 データベース内にユーザー定義型が既に存在する CLR 型に対してユーザー定義型を作成した場合、CREATE TYPE は失敗し、エラーが発生します。 この制約が必要なのは、CLR 型を複数のユーザー定義型にマップすることが可能な場合の、SQL 型の解決時のあいまいな状態を避けるためです。  
  
 かどうか、型のミューテーター メソッドは返しません*void*、CREATE TYPE ステートメントは実行されません。  
  
 ユーザー定義型を変更するには、DROP TYPE ステートメントを使用して型を削除してから、再作成する必要があります。  
  
 使用して作成したユーザー定義の型とは異なり**sp_addtype**、**パブリック**データベース ロールでは、CREATE TYPE を使用して作成した型の REFERENCES 権限が自動的に付与されません。 この権限は個別に付与する必要があります。  
  
 ユーザー定義テーブル型、構造化ユーザー定義型で使用されている*column_name* \<データ型 > テーブルの型が定義されているデータベースのスキーマ スコープの一部であります。 データベース内の別のスコープに含まれている構造化ユーザー定義型にアクセスするには、2 つの部分から構成される名前を使用します。  
  
 ユーザー定義テーブル型では、計算列の主キーを PERSISTED および NOT NULL にする必要があります。  
  
## <a name="memory-optimized-table-types"></a>メモリ最適化テーブル型  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 以降では、ディスク上ではなく、プライマリ メモリ内でテーブル型のデータを処理できます。 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。 メモリ最適化テーブル型を作成する方法を示すコード サンプルでは、次を参照してください。[メモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャの作成](../../relational-databases/in-memory-oltp/creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md)です。  
  
## <a name="permissions"></a>Permissions  
 現在のデータベース内の CREATE TYPE 権限、および *schema_name*に対する ALTER 権限が必要です。 *schema_name* を指定しなかった場合は、現在のユーザーのスキーマを判断するための既定の名前解決ルールが適用されます。 場合*assembly_name*が指定されて、ユーザーのアセンブリを所有してかに REFERENCES 権限を使用する必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-an-alias-type-based-on-the-varchar-data-type"></a>A. varchar データ型に基づいた別名型を作成する  
 次の例では、システムから提供されている `varchar` データ型に基づいて、別名型を作成します。  
  
```  
CREATE TYPE SSN  
FROM varchar(11) NOT NULL ;  
```  
  
### <a name="b-creating-a-user-defined-type"></a>B. ユーザー定義型を作成する  
 次の例では、型`Utf8String`クラスを参照する`utf8string`アセンブリ`utf8string`です。 型、アセンブリを作成する前に`utf8string`がローカル データベースに登録します。 CREATE ASSEMBLY ステートメントのバイナリ部分を有効な記述と置き換えます。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
CREATE ASSEMBLY utf8string  
AUTHORIZATION [dbi]   
FROM 0x4D... ;  
GO  
CREATE TYPE Utf8String   
EXTERNAL NAME utf8string.[Microsoft.Samples.SqlServer.utf8string] ;  
GO  
```  
  
### <a name="c-creating-a-user-defined-table-type"></a>C. ユーザー定義テーブル型を作成する  
 次の例では、2 つの列を持つユーザー定義テーブル型が作成されます。 作成して、テーブル値パラメーターを使用する方法の詳細については、次を参照してください。[テーブル値パラメーター (&) #40";"データベース エンジン"&"#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)です。  
  
```  
CREATE TYPE LocationTableType AS TABLE   
    ( LocationName VARCHAR(50)  
    , CostRate INT );  
GO  
```  
  
## <a name="see-also"></a>参照  
 [アセンブリ &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-assembly-transact-sql.md)   
 [ドロップ タイプ & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

