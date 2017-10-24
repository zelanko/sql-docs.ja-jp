---
title: "CREATE INDEX (TRANSACT-SQL) |Microsoft ドキュメント"
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
- CREATE INDEX
- INDEX
- INDEX_TSQL
- CREATE_INDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE XML INDEX statement
- PRIMARY XML INDEX statement
- indexes [SQL Server], creating
- online index operations
- index keys [SQL Server]
- PROPERTY INDEX statement
- computed columns, index creation
- clustered indexes, creating
- indexed views [SQL Server], index creation
- partitioned indexes [SQL Server], creating
- VALUE INDEX statement
- index creation [SQL Server], CREATE INDEX statement
- DROP_EXISTING clause
- row locks [SQL Server]
- composite indexes
- MAXDOP index option, CREATE INDEX statement
- filtered indexes [SQL Server], creating
- PATH INDEX statement
- locking [SQL Server], indexes
- unique indexes, creating
- primary indexes [SQL Server]
- CREATE PRIMARY XML INDEX statement
- SET statement, index creation
- index options [SQL Server]
- included columns
- ONLINE option
- nonclustered indexes [SQL Server], creating
- CREATE INDEX statement
- IGNORE_DUP_KEY option
- deterministic functions
- keys [SQL Server], index
- SECONDARY XML INDEX statement
- page locks [SQL Server]
- secondary indexes [SQL Server]
- XML indexes [SQL Server], creating
ms.assetid: d2297805-412b-47b5-aeeb-53388349a5b9
caps.latest.revision: 223
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ce92f7f55f82a7245818cbe669da76900f76be89
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-index-transact-sql"></a>CREATE INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  テーブルまたはビューをリレーショナル インデックスを作成します。 行ストア インデックスは、いずれかのクラスター化または非クラスター化 btree インデックスであるためにも呼び出されます。 テーブルにデータが前に、行ストア インデックスを作成することができます。 クエリでは、特定の列から選択するか、特定の順序で並べ替えの基準値を要求する場合は特に、クエリのパフォーマンスを向上させるために、行ストア インデックスを使用します。  
  
  
> [!NOTE]  
>  Azure SQL Data Warehouse と Parallel Data Warehouse 現在では、一意の制約はサポートされません。 Unique 制約を参照している例は、SQL Server と Azure SQL データベースに適用可能なのみ    
  
 **簡単な例:**  
  
```  
-- Create a nonclustered index on a table or view  
CREATE INDEX i1 ON t1 (col1);  
```  
  
```  
--Create a clustered index on a table and use a 3-part name for the table  
CREATE CLUSTERED INDEX i1 ON d1.s1.t1 (col1);  
```  
  
```  
-- Syntax for SQL Server and Azure SQL Database
-- Create a nonclustered index with a unique constraint 
-- on 3 columns and specify the sort order for each column  
CREATE UNIQUE INDEX i1 ON t1 (col1 DESC, col2 ASC, col3 DESC);  
```  
  
 **主要なシナリオ:**  
  
-   SQL Server 2016 と Azure SQL データベースでデータ ウェアハウスのクエリのパフォーマンスを向上させるために列ストア インデックスに非クラスター化インデックスを使用します。 参照してください[列ストア インデックスのデータ ウェアハウス](../../relational-databases/indexes/columnstore-indexes-data-warehouse.md)  
  
 **別の種類のインデックスを作成する必要がありますか。**  
  
-   [XML インデックス &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-xml-index-transact-sql.md)  
  
-   [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-spatial-index-transact-sql.md)  
  
-   [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database
  
CREATE [ UNIQUE ] [ CLUSTERED | NONCLUSTERED ] INDEX index_name   
    ON <object> ( column [ ASC | DESC ] [ ,...n ] )   
    [ INCLUDE ( column_name [ ,...n ] ) ]  
    [ WHERE <filter_predicate> ]  
    [ WITH ( <relational_index_option> [ ,...n ] ) ]  
    [ ON { partition_scheme_name ( column_name )   
         | filegroup_name   
         | default   
         }  
    ]  
    [ FILESTREAM_ON { filestream_filegroup_name | partition_scheme_name | "NULL" } ]  
  
[ ; ]  
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]   
    table_or_view_name  
}  
  
<relational_index_option> ::=  
{  
    PAD_INDEX = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY = { ON | OFF }  
  | STATISTICS_NORECOMPUTE = { ON | OFF }  
  | STATISTICS_INCREMENTAL = { ON | OFF }  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE = { ON | OFF }  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
  | DATA_COMPRESSION = { NONE | ROW | PAGE}   
     [ ON PARTITIONS ( { <partition_number_expression> | <range> }   
     [ , ...n ] ) ]  
}  
  
<filter_predicate> ::=   
    <conjunct> [ AND <conjunct> ]  
  
<conjunct> ::=  
    <disjunct> | <comparison>  
  
<disjunct> ::=  
        column_name IN (constant ,...n)  
  
<comparison> ::=  
        column_name <comparison_op> constant  
  
<comparison_op> ::=  
    { IS | IS NOT | = | <> | != | > | >= | !> | < | <= | !< }  
  
<range> ::=   
<partition_number_expression> TO <partition_number_expression>  
  
Backward Compatible Relational Index  
Important   The backward compatible relational index syntax structure 
will be removed in a future version of SQL Server. Avoid using this 
syntax structure in new development work, and plan to modify 
applications that currently use the feature. Use the syntax structure 
specified in <relational_index_option> instead.  
  
CREATE [ UNIQUE ] [ CLUSTERED | NONCLUSTERED ] INDEX index_name   
    ON <object> ( column_name [ ASC | DESC ] [ ,...n ] )   
    [ WITH <backward_compatible_index_option> [ ,...n ] ]  
    [ ON { filegroup_name | "default" } ]  
  
<object> ::=  
{  
    [ database_name. [ owner_name ] . | owner_name. ]   
    table_or_view_name  
}  
  
<backward_compatible_index_option> ::=  
{   
    PAD_INDEX  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB  
  | IGNORE_DUP_KEY  
  | STATISTICS_NORECOMPUTE   
  | DROP_EXISTING   
}  
```  

  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CREATE [ CLUSTERED | NONCLUSTERED ] INDEX index_name   
    ON [ database_name . [ schema ] . | schema . ] table_name   
        ( { column [ ASC | DESC ] } [ ,...n ] )  
    WITH ( DROP_EXISTING = { ON | OFF } )  
[;]  
  
```  
  
## <a name="arguments"></a>引数  
 UNIQUE  
 テーブルまたはビューに一意のインデックスを作成します。 一意のインデックスとは、どの 2 つの行にも同じインデックス キー値が設定されていないインデックスです。 ビューのクラスター化インデックスは一意である必要があります。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]では、IGNORE_DUP_KEY が ON に設定されているかどうかに関係なく、重複する値が既に含まれている列に対して一意のインデックスを作成できません。 作成しようとすると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]ではエラー メッセージが表示されます。 1 行または複数行に対して一意のインデックスを作成するには、先に重複する値を削除しておく必要があります。 一意のインデックスに使用する列は NOT NULL に設定してください。一意のインデックスを作成するとき、複数の NULL 値は重複した値と見なされます。  
  
 CLUSTERED  
 キー値の論理的順序がテーブル内にある対応する行の物理的な順序を決めるインデックスを作成します。 クラスター化インデックスの最下位レベル (リーフ レベル) には、テーブルの実際のデータ行が含まれます。 1 つのテーブルまたはビューに、同時に複数のクラスター化インデックスを定義することはできません。  
  
 一意のクラスター化インデックスが定義されているビューは、インデックス付きビューと呼ばれます。 ビューに一意のクラスター化インデックスを作成すると、ビューを物理的に具体化することになります。 ビューにその他のインデックスを定義するには、まずそのビューに一意のクラスター化インデックスを作成する必要があります。 詳細については、「 [インデックス付きビューの作成](../../relational-databases/views/create-indexed-views.md)」を参照してください。  
  
 非クラスター化インデックスを作成する前に、クラスター化インデックスを作成します。 これは、クラスター化インデックスを作成すると、テーブルの既存の非クラスター化インデックスが再構築されるためです。  
  
 CLUSTERED を指定しない場合、非クラスター化インデックスが作成されます。  
  
> [!NOTE]  
>  クラスター化インデックスおよびデータ ページのリーフ レベルは、定義では同一であるため、クラスター化インデックスを作成して、ON を使用して*partition_scheme_name*または ON *filegroup_name*句効果的にテーブルが作成されたファイル グループからテーブルを新しいパーティション構成またはファイル グループに移動します。 特定のファイル グループ上にテーブルまたはインデックスを作成する前に、使用可能なファイル グループとインデックス用の十分な空領域を確認しておいてください。  
  
 場合によっては、クラスター化インデックスを作成すると、以前に無効化されたインデックスが有効になることがあります。 詳細については、次を参照してください。 [Enable Indexes and Constraints](../../relational-databases/indexes/enable-indexes-and-constraints.md)と[無効にするインデックスと制約](../../relational-databases/indexes/disable-indexes-and-constraints.md)です。  
  
 **非クラスター化**  
 テーブルの論理順序を示すインデックスを作成します。 非クラスター化インデックスの場合、データ行の物理的な順序は、そのインデックスが作成された順序とは関係ありません。  
  
 インデックスの作成方法に関係なく、PRIMARY KEY および UNIQUE 制約で暗黙的に作成する場合も、CREATE INDEX で明示的に作成する場合も、各テーブルには 999 個までの非クラスター化インデックスを作成できます。  
  
 インデックス付きビューの場合は、既に一意のクラスター化インデックスが作成されているビューにのみ、非クラスター化インデックスを作成できます。  
  
 既定値は NONCLUSTERED です。  
  
 *index_name*  
 インデックスの名前。 インデックス名は、テーブルまたはビュー内では一意である必要がありますが、データベース内で一意である必要はありません。 インデックス名の規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 *列*  
 インデックスの基準となる 1 列または複数列を指定します。 指定した列を組み合わせた値で複合インデックスを作成するには、2 つ以上の列名を指定します。 後のかっこ内の優先度の並べ替え順序での複合インデックスに含まれる列を一覧する*table_or_view_name*です。  
  
 1 つの複合インデックス キーには、最大 32 の列を結合できます。 複合インデックス キーに含まれる列はすべて、同じテーブルまたはビュー内に存在する必要があります。 複合インデックスの値の最大許容サイズは、クラスター化インデックスの場合は、900 バイトまたは非クラスター化インデックスの 1,700 です。 16 列とより前に、のバージョンの 900 バイトに制限は[!INCLUDE[ssSDS](../../includes/sssds-md.md)]V12 および[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。  
  
 ラージ オブジェクト (LOB) データ型である列**ntext**、**テキスト**、 **varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、 **xml**、または**イメージ**インデックスのキー列として指定することはできません。 また、ビュー定義に含めることはできません**ntext**、**テキスト**、または**イメージ**列、CREATE INDEX ステートメントで参照されていない場合でもです。  
  
 バイナリ順序がサポートされる CLR ユーザー定義型列に対してインデックスを作成できます。 ユーザー定義型列からメソッドを呼び出すように定義されている計算列にも、そのメソッドが決定的とマークされていて、データ アクセス操作が実行されない限り、インデックスを作成できます。 CLR ユーザー定義型列のインデックス作成の詳細については、次を参照してください。 [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)です。  
  
 [ **ASC** |DESC]  
 特定のインデックス列に対して、昇順または降順の並べ替えの方向を指定します。 既定値は ASC です。  
  
 含める**(***列*[ **、**.*n* ] **)**  
 非クラスター化インデックスのリーフ レベルに、非キー列を追加します。 非クラスター化インデックスは、一意であっても一意でなくてもかまいません。  
  
 列名は INCLUDE リスト内で繰り返すことはできず、キー列と非キー列両方で同時に使用することはできません。 テーブルにクラスター化インデックスが定義されている場合、非クラスター化インデックスには常にクラスター化インデックスの列が含まれます。 詳細については、「 [付加列インデックスの作成](../../relational-databases/indexes/create-indexes-with-included-columns.md)」を参照してください。  
  
 **text**、 **ntext**、および **image**を除く、すべてのデータ型を使用できます。 インデックスを作成またはオフラインで再構築する必要があります (ONLINE = OFF) かどうか、指定された非キー列のいずれかが**varchar (max)**、 **nvarchar (max)**、または**varbinary (max)**データ型。  
  
 決定的な計算列、および正確または不正確な計算列を、付加列にできます。 派生した計算列**イメージ**、 **ntext**、**テキスト**、 **varchar (max)**、 **nvarchar (max)**、**varbinary (max)**、および**xml**計算列のデータ型が含まれる列として使用できる限り、非キー列のデータ型を含めることができます。 詳細については、「 [計算列のインデックス](../../relational-databases/indexes/indexes-on-computed-columns.md)」を参照してください。  
  
 XML インデックスを作成する方法については、次を参照してください。 [CREATE XML INDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-xml-index-transact-sql.md).  
  
 ここで\<filter_predicate > インデックスに含める行を指定してフィルター選択されたインデックスを作成します。 フィルター選択されたインデックスは、テーブル上の非クラスター化インデックスである必要があります。 フィルター選択されたインデックスのデータ行のフィルター選択された統計情報を作成します。  
  
 フィルター述語には単純な比較ロジックを使用するので、計算列、UDT 列、空間データ型列、または hierarchyID データ型列を参照することはできません。 比較演算子では、NULL リテラルを使用する比較を実行できません。 代わりに、IS NULL 演算子と IS NOT NULL 演算子を使用します。  
  
 次に、`Production.BillOfMaterials` テーブルのフィルター述語の例をいくつか示します。  
  
 * `WHERE StartDate > '20000101' AND EndDate <= '20000630'`  
  
 * `WHERE ComponentID IN (533, 324, 753)`  
  
 * `WHERE StartDate IN ('20000404', '20000905') AND EndDate IS NOT NULL`  
  
 フィルター選択されたインデックスは、XML インデックスおよびフルテキスト インデックスには適用されません。 UNIQUE インデックスの場合、一意のインデックス値を持つ必要があるのは選択した行のみです。 フィルター選択されたインデックスでは IGNORE_DUP_KEY オプションを使用できません。  
  
 ON *partition_scheme_name***(***column_name***)**  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 ファイル グループが定義されているパーティション構成を指定します。このファイル グループは、パーティション インデックスのパーティションのマップ先となります。 パーティション構成はいずれかの操作を実行することによって、データベース内に存在する必要があります[CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md)または[ALTER PARTITION SCHEME](../../t-sql/statements/alter-partition-scheme-transact-sql.md)です。 *column_name*パーティション インデックスのパーティション分割される対象の列を指定します。 この列はデータ型、長さ、一致する必要があります関数および有効桁数の引数のパーティションを*partition_scheme_name*を使用しています。 *column_name*インデックス定義内の列に限定されません。 ときに、一意のインデックスをパーティション分割を除く、ベース テーブルの任意の列を指定することができます*column_name*一意のキーとして使用されるものの中から選択する必要があります。 この制限により、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では、単一のパーティション内だけでキー値の一意性を確認できます。  
  
> [!NOTE]  
>  一意でないクラスター化インデックスをパーティション分割するとき、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では既定により、まだ指定されていない場合、パーティション分割列がクラスター化インデックス キーのリストに追加されます。 非一意の非クラスター化インデックスをパーティション分割するとき、[!INCLUDE[ssDE](../../includes/ssde-md.md)]が指定されていない場合は、インデックスの非キー (付加) 列として、パーティション分割列を追加します。  
  
 場合*partition_scheme_name*または*filegroup*が指定されていないと、テーブルがパーティション分割、インデックスは基になるテーブルとして同じのパーティション分割列を使用して、同じパーティション構成に配置されます。  
  
> [!NOTE]  
>  XML インデックスにはパーティション構成を指定できません。 ベース テーブルがパーティション分割される場合、XML インデックスではテーブルと同じパーティション構造が使用されます。  
  
 詳細については、インデックスのパーティション分割の[Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md)です。  
  
 ON *filegroup_name*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 指定したファイル グループに、指定したインデックスを作成します。 位置の指定がなく、テーブルまたはビューがパーティション分割されていない場合、インデックスには、基になるテーブルまたはビューと同じファイル グループが使用されます。 ファイル グループは既に存在している必要があります。  
  
 ON **"**既定**"**  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssCurrent](../../includes/sssdsfull-md.md)]です。  
  
 既定のファイル グループに、指定したインデックスを作成します。  
  
 この文脈での default という語はキーワードではありません。 既定のファイル グループの識別子を指定しのように区切る必要があります**"**既定**"**または ON **[**既定**]**です。 "default" を指定する場合は、現在のセッションに対して QUOTED_IDENTIFIER オプションが ON である必要があります。 これが既定の設定です。 詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
 [FILESTREAM_ON { *filestream_filegroup_name* | *partition_scheme_name* |"NULL"}]  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 クラスター化インデックスの作成時に、テーブルの FILESTREAM データの配置を指定します。 FILESTREAM_ON 句を使用すると、異なる FILESTREAM ファイル グループやパーティション構成に FILESTREAM データを移動できます。  
  
 *filestream_filegroup_name* FILESTREAM ファイル グループの名前を指定します。 ファイル グループの 1 つのファイルを使用して、ファイル グループに対して定義されている必要があります、 [CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md)または[ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md)ステートメントです。 それ以外の場合、エラーが発生します。  
  
 テーブルがパーティション分割されている場合、FILESTREAM_ON 句を使用して、テーブルのパーティション構成と同じパーティション関数とパーティション列を使用するように、FILESTREAM ファイル グループのパーティション構成を指定する必要があります。 それ以外の場合は、エラーが発生します。  
  
 テーブルがパーティション分割されていない場合、FILESTREAM 列も分割できません。 テーブルの FILESTREAM データは、FILESTREAM_ON 句で指定した単一のファイル グループに格納する必要があります。  
  
 クラスター化インデックスの作成で、テーブルに FILESTREAM 列が含まれていないときは、CREATE INDEX ステートメントに FILESTREAM_ON NULL を指定できます。  
  
 詳細については、「[FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)」をご覧ください。  
  
 **\<オブジェクト >:: =**  
  
 インデックスを作成するオブジェクトを、完全修飾または完全修飾ではない形式で指定します。  
  
 *database_name*  
 データベースの名前です。  
  
 *schema_name*  
 テーブルまたはビューが属するスキーマの名前を指定します。  
  
 *table_or_view_name*  
 インデックスを作成するテーブルまたはビューの名前を指定します。  
  
 ビューにインデックスを作成するには、SCHEMABINDING を指定してそのビューを定義する必要があります。 ビューに非クラスター化インデックスを作成する前に、そのビューに一意のクラスター化インデックスを作成する必要があります。 インデックス付きビューの詳細については、「解説」を参照してください。  
  
 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]オブジェクトは、クラスター化列ストア インデックスに格納されたテーブルを指定できます。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]3 部構成の名前の形式をサポートしている*database_name***.**[*schema_name*]**.***object_name*ときに、 *database_name*は、現在のデータベースまたは*database_name* tempdb は、および*object_name*が # で始まる。  
  
 **\<relational_index_option >:: =**  
  
 インデックスを作成するときに使用するオプションを指定します。  
  
 PAD_INDEX = {ON |**OFF** }  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 インデックスの埋め込みを指定します。 既定値は OFF です。  
  
 ON  
 によって指定される空き領域の割合*fillfactor*インデックスの中間レベル ページに適用されます。  
  
 OFF または*fillfactor*が指定されていません  
 中間レベルのページはほぼ全容量が使用されます。ただし、中間ページにあるキーのセットを考慮して、インデックスに割り当てることのできる、少なくとも 1 行の最大サイズが収まる分の領域は残されます。  
  
 PAD_INDEX では FILLFACTOR で指定されるパーセンテージが使用されるので、PAD_INDEX オプションは、FILLFACTOR が指定されている場合にのみ有効です。 FILLFACTOR で指定されるパーセンテージが 1 つの行を許可するのに十分な大きさがない場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]内部的に最小値を許可する比率をオーバーライドします。 中間インデックス ページ上の行の番号 2 にはなりません未満の値をどのように低に関係なく*fillfactor*です。  
  
 旧バージョンと互換性のある構文では、WITH PAD_INDEX は WITH PAD_INDEX = ON と同じです。  
  
 FILLFACTOR  **=**  *fillfactor*  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 インデックスの作成時または再構築時に、[!INCLUDE[ssDE](../../includes/ssde-md.md)] が各インデックス ページのリーフ レベルをどの程度まで埋めるかを、パーセント値で指定します。 *fillfactor* 1 から 100 までの整数値にする必要があります。 場合*fillfactor* 100、[!INCLUDE[ssDE](../../includes/ssde-md.md)]全容量リーフ ページを含むインデックスを作成します。  
  
 FILLFACTOR 設定は、インデックスが作成または再構築されるときのみ適用されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]ページ内の空き領域の指定された割合動的に保持しません。 表示するには、fill factor 設定を使用して、 [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)カタログ ビューです。  
  
> [!IMPORTANT]  
>  100 未満、fillfactor の値をクラスター化インデックスを作成するため、データが占める記憶域スペースの量、影響、[!INCLUDE[ssDE](../../includes/ssde-md.md)]クラスター化インデックスを作成するときに、データを再分配します。  
  
 詳細については、「 [インデックスの FILL FACTOR の指定](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)」を参照してください。  
  
 SORT_IN_TEMPDB = {ON |**OFF** }  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 一時的な並べ替え結果を格納するかどうかを示す**tempdb**です。 既定値は OFF です。  
  
 ON  
 インデックスの構築に使用される並べ替えの中間結果が格納されている**tempdb**です。 場合、インデックスの作成に必要な時間が削減**tempdb**が別のユーザー データベースのディスク セットにします。 インデックスの構築中に使用されるディスク領域のサイズは増加します。  
  
 OFF  
 中間の並べ替え結果はインデックスと同じデータベースに格納されます。  
  
 ユーザー データベースで、インデックスを作成するために必要な容量に加えて**tempdb**について、一定の並べ替えの中間結果を格納する追加の領域がある必要があります。 詳細については、次を参照してください。[インデックスの SORT_IN_TEMPDB オプション](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)です。  
  
 旧バージョンと互換性のある構文では、WITH SORT_IN_TEMPDB は WITH SORT_IN_TEMPDB = ON と同じです。  
  
 IGNORE_DUP_KEY = {ON |**OFF** }  
 挿入操作で、一意のインデックスに重複するキー値を挿入しようとした場合のエラー応答を指定します。 IGNORE_DUP_KEY オプションは、インデックスが作成または再構築された後の挿入操作のみに適用されます。 オプションも何も起こりませんの実行時に[CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)、 [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)、または[更新](../../t-sql/queries/update-transact-sql.md)です。 既定値は OFF です。  
  
 ON  
 重複したキー値が一意のインデックスに挿入されると、警告メッセージが表示されます。 一意性制約に違反する行のみが失敗します。  
  
 OFF  
 重複したキー値が一意のインデックスに挿入されると、エラー メッセージが表示されます。 INSERT 操作全体がロールバックされます。  
  
 ビューに作成されたインデックス、一意でないインデックス、XML インデックス、空間インデックス、およびフィルター選択されたインデックスの IGNORE_DUP_KEY を ON に設定できません。  
  
 IGNORE_DUP_KEY を表示する[sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)です。  
  
 旧バージョンと互換性のある構文では、WITH IGNORE_DUP_KEY は WITH IGNORE_DUP_KEY = ON と同じです。  
  
 STATISTICS_NORECOMPUTE = {ON |**OFF**}  
 分布統計を再計算するかどうかを指定します。 既定値は OFF です。  
  
 ON  
 古い統計情報は、自動的には再計算されません。  
  
 OFF  
 自動統計更新が有効です。  
  
 自動統計更新を復元するには、STATISTICS_NORECOMPUTE を OFF に設定するか、NORECOMPUTE 句を指定せずに UPDATE STATISTICS を実行します。  
  
> [!IMPORTANT]  
>  分布統計の自動再計算を無効にすると、クエリ オプティマイザーで、テーブルが関与するクエリの最適実行プランが選択されなくなる場合があります。  
  
 旧バージョンと互換性のある構文では、WITH STATISTICS_NORECOMPUTE は WITH STATISTICS_NORECOMPUTE = ON と同じです。  
  
 STATISTICS_INCREMENTAL = {ON |**OFF** }  
 ときに**ON**、作成される統計は、パーティションごとの統計はします。 ときに**OFF**、統計ツリーが削除されると[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]統計が再計算します。 既定値は**OFF**です。  
  
 パーティションごとの統計がサポートされていない場合、このオプションは無視され、警告が生成されます。 次の種類の統計では、増分統計がサポートされていません。  
  
-   ベース テーブルにパーティションで固定されていないインデックスを使用して作成された統計。  
  
-   Always On の読み取り可能なセカンダリ データベースに対して作成された統計。  
  
-   読み取り専用のデータベースに対して作成された統計。  
  
-   フィルター選択されたインデックスに対して作成された統計。  
  
-   ビューに対して作成された統計。  
  
-   内部テーブルに対して作成された統計。  
  
-   空間インデックスまたは XML インデックスを使用して作成された統計。  
  
 DROP_EXISTING = {ON |**OFF** }  
 削除、変更した列の仕様を既存のクラスター化または非クラスター化インデックスを再構築し、インデックスの同じ名前を保持するオプションです。 既定値は OFF です。  
  
 ON  
 削除し、パラメーターと同じ名前を持つ必要がある既存のインデックスを再構築することを指定*index_name*です。  
  
 OFF  
 削除し、既存のインデックスを再構築をしないように指定します。 SQL Server では、指定したインデックス名が既に存在する場合、エラーが表示されます。  
  
 With DROP_EXISTING を変更することができます。  
  
-   クラスター化行ストア インデックスに非クラスター化行ストア インデックスです。  
  
 With DROP_EXISTING を変更することはできません。  
  
-   非クラスター化行ストア インデックスをクラスター化行ストア インデックスです。  
  
-   任意の種類の行ストア インデックスをクラスター化列ストア インデックスです。  
  
 旧バージョンと互換性のある構文では、WITH DROP_EXISTING は WITH DROP_EXISTING = ON と同じです。  
  
 ONLINE = {ON |**OFF** }  
 インデックス操作時に、基になるテーブルや関連するインデックスをクエリやデータ変更で使用できるかどうかを指定します。 既定値は OFF です。  
  
> [!NOTE]  
>  オンラインでのインデックス操作は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各エディションでサポートされる機能の一覧については、「[Editions and Supported Features for SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)」 (SQL Server 2016 のエディションとサポートされる機能) を参照してください。  
  
 ON  
 長期のテーブル ロックは、インデックス操作の間は保持されません。 インデックス操作の主なフェーズでは、基になるテーブル、インテント共有 (IS) ロックのみが保持されます。 これにより、基になるテーブルやインデックスに対するクエリや更新を続行できます。 操作の開始時、非常に短い時間ですが、ソース オブジェクトの共有 (S) ロックが保持されます。 操作の終了時、短い時間ですが、非クラクタ化インデックスが作成される場合は、ソース オブジェクト上で共有 (S) ロックの取得が行われます。また、クラスター化インデックスがオンラインで作成または削除され、クラスター化または非クラスター化インデックスが再構築される場合は、SCH-M (スキーマ修正) ロックが取得されます。 インデックスがローカルの一時テーブルに作成される場合、ONLINE は ON にできません。  
  
 OFF  
 テーブル ロックは、インデックス操作の間適用されます。 クラスター化インデックスを作成、再構築、または削除するオフライン インデックス操作や、非クラスター化インデックスを再構築または削除するオフライン インデックス操作では、テーブルのスキーマ修正 (Sch-M) ロックが取得されます。 このため、操作中は、すべてのユーザーは基になるテーブルにアクセスできません。 非クラスター化インデックスを作成するオフライン インデックス操作では、テーブルの共有 (S) ロックが取得されます。 この場合は、基になるテーブルに対して更新は許可されませんが、SELECT ステートメントなどの読み取り操作は許可されます。  
  
 詳細については、次を参照してください。[オンライン インデックス操作しくみ](../../relational-databases/indexes/how-online-index-operations-work.md)です。  
  
 インデックスは、グローバル一時テーブル上のインデックスを含めてオンラインで作成できます。ただし次のインデックスは例外です。  
  
-   XML インデックス  
  
-   ローカル一時テーブル上のインデックス。  
  
-   ビュー上の最初の一意のクラスター化インデックス。  
  
-   無効なクラスター化インデックス。  
  
-   基になるテーブルに LOB データ型が含まれている場合、クラスター化インデックス:**イメージ**、 **ntext**、**テキスト**、および空間型です。  
  
-   **varchar (max)**と**varbinary (max)**列がインデックスの一部にすることはできません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) し、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]テーブルが含まれている場合、 **varchar (max)**または**varbinary (max)**列、他の列を含むクラスター化インデックスを指定できます構築または再構築を使用して、**オンライン**オプション。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]許可しない、**オンライン**オプション、ベース テーブルが含まれている**varchar (max)**または**varbinary (max)**列です。  
  
 詳しくは、「 [Perform Index Operations Online](../../relational-databases/indexes/perform-index-operations-online.md)」をご覧ください。  
  
 ALLOW_ROW_LOCKS = { **ON** |オフ}  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 行ロックを許可するかどうかを指定します。 既定値は ON です。  
  
 ON  
 インデックスにアクセスするとき、行ロックが許可されます。 いつ行ロックを使用するかは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]によって決定されます。  
  
 OFF  
 行ロックは使用されません。  
  
 ALLOW_PAGE_LOCKS = { **ON** |オフ}  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 ページ ロックを許可するかどうかを指定します。 既定値は ON です。  
  
 ON  
 ページにアクセスするとき、行ロックが許可されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]ページ ロックを使用する場合を決定します。  
  
 OFF  
 ページ ロックは使用されません。  
  
 MAXDOP = *max_degree_of_parallelism*  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 上書き、 [max degree of parallelism サーバー構成オプションを構成する](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)インデックス操作の実行中の構成オプション。 並列プランの実行で使用されるプロセッサ数を制限するには、MAXDOP を使用します。 最大数は 64 プロセッサです。  
  
 *max_degree_of_parallelism*を指定できます。  
  
 1  
 並列プラン生成を抑制します。  
  
 \>1  
 現在のシステム ワークロードに基づいて、並列インデックス操作で使用される最大プロセッサ数を指定の数以下に制限します。  
  
 0 (既定値)  
 現在のシステム ワークロードに基づいて、実際の数以下のプロセッサを使用します。  
  
 詳細については、「 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)」を参照してください。  
  
> [!NOTE]  
>  並列インデックス操作はすべてのエディションで使用できない[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各エディションでサポートされる機能の一覧については、「[Editions and Supported Features for SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)」 (SQL Server 2016 のエディションとサポートされる機能) を参照してください。  
  
 DATA_COMPRESSION  
 指定したインデックス、パーティション番号、またはパーティション範囲に、データ圧縮オプションを指定します。 次のオプションがあります。  
  
 なし  
 インデックスまたは指定したパーティションが圧縮されません。  
  
 ROW  
 行の圧縮を使用して、インデックスまたは指定したパーティションが圧縮されます。  
  
 PAGE  
 ページの圧縮を使用して、インデックスまたは指定したパーティションが圧縮されます。  
  
 圧縮の詳細については、次を参照してください。[データ圧縮](../../relational-databases/data-compression/data-compression.md)です。  
  
 パーティションで**(** { \<partition_number_expression > |\<範囲 >}[ **,**... *n*  ] **)** **対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 DATA_COMPRESSION 設定を適用するパーティションを指定します。 インデックスがパーティション分割されていない場合に ON PARTITIONS 引数を使用すると、エラーが発生します。 ON PARTITIONS 句を指定しないと、パーティション インデックスのすべてのパーティションに対して DATA_COMPRESSION オプションが適用されます。  
  
 \<partition_number_expression > 次のように指定することができます。  
  
-   ON PARTITIONS (2) などのように、1 つのパーティションの番号を指定します。  
  
-   ON PARTITIONS (1, 5) などのように、複数のパーティションのパーティション番号をコンマで区切って指定します。  
  
-   ON PARTITIONS (2, 4, 6 TO 8) などのように、範囲と個別のパーティションの両方を指定します。  
  
 \<範囲 > パーティション番号など、to で区切って指定できます: ON PARTITIONS (6 TO 8)。  
  
 さまざまなパーティションにさまざまな種類のデータ圧縮を設定するには、次のように DATA_COMPRESSION オプションを複数回指定します。  
  
```  
REBUILD WITH   
(  
DATA_COMPRESSION = NONE ON PARTITIONS (1),   
DATA_COMPRESSION = ROW ON PARTITIONS (2, 4, 6 TO 8),   
DATA_COMPRESSION = PAGE ON PARTITIONS (3, 5)  
);  
```  
  
## <a name="remarks"></a>解説  
 CREATE INDEX ステートメントは、他のクエリと同じように最適化されます。 クエリ プロセッサでは I/O 操作を減らすため、テーブル スキャンの代わりに別のインデックスがスキャンされる場合があります。 状況によっては、並べ替え操作が行われない場合もあります。 マルチプロセッサ コンピューターの場合、CREATE INDEX では他のクエリと同様に、インデックス作成に関連するスキャンおよび並べ替え操作を実行するために、より多くのプロセッサを使用することができます。 詳細については、「 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)」を参照してください。  
  
 データベース復旧モデルが一括ログ復旧モデルまたは単純復旧モデルのいずれかに設定されている場合、インデックス作成操作のログへの記録を最小限にできます。  
  
 一時テーブルにインデックスを作成することもできます。 テーブルが削除されるか、セッションが終了すると、インデックスは削除されます。  
  
 インデックスでは拡張プロパティがサポートされます。  
  
## <a name="clustered-indexes"></a>クラスター化インデックス  
 テーブル (ヒープ) にクラスター化インデックスを作成したり、既存のクラスター化インデックスを削除して再作成する場合は、データの並べ替えや、基のテーブルまたは既存のクラスター化インデックス データの一時的コピーを実行するために、データベース内で追加の作業領域が使用可能になっている必要があります。 クラスター化インデックスの詳細については、次を参照してください。[クラスター化インデックスを作成する](../../relational-databases/indexes/create-clustered-indexes.md)です。  
  
## <a name="nonclustered-indexes"></a>非クラスター化インデックス  
 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]し、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、クラスター化列ストア インデックスとして格納されるテーブルに非クラスター化インデックスを作成することができます。 最初に保存されているテーブルに非クラスター化インデックスを作成するかどうかは後で、テーブルをクラスター化列ストア インデックスに変換する場合は、ヒープまたはクラスター化インデックスに適用する場合は、インデックスが永続化されます。 クラスター化列ストア インデックスを再構築するときに、非クラスター化インデックスを削除する必要がではありません。  
  
 制限事項と制約事項:  
  
-   クラスター化列ストア インデックスとして格納されたテーブルに非クラスター化インデックスを作成する場合、FILESTREAM_ON オプションが無効です。  
  
## <a name="unique-indexes"></a>一意のインデックス  
 一意のインデックスが存在する場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]は、挿入操作によってデータが追加されるたびに、重複した値がないかをチェックします。 重複キー値を生成する挿入操作はロールバックされ、[!INCLUDE[ssDE](../../includes/ssde-md.md)]はエラー メッセージを表示します。 挿入操作で多くの行が変更された場合でも、重複が 1 つでもあれば、ロールバックが行われます。 IGNORE_DUP_KEY 句が ON に設定されている一意のインデックスにデータを入力しようとすると一意のインデックスに違反する行だけが失敗します。  
  
## <a name="partitioned-indexes"></a>パーティション インデックス  
 パーティション インデックスは、パーティション分割されたテーブルと同様の方法で作成および維持されますが、通常のインデックスのように、個別のデータベース オブジェクトとして扱われます。 パーティション分割されていないテーブルにパーティション インデックスを作成したり、パーティション分割されているテーブルに非パーティション インデックスを作成することもできます。  
  
 パーティション分割されているテーブルにインデックスを作成し、インデックスを配置するファイル グループを指定しない場合、インデックスは基になるテーブルと同じ方法でパーティション分割されます。 これは、既定では、インデックスは基になるテーブルと同じファイル グループに配置され、パーティション分割されたテーブルの場合、同じパーティション分割列を使用する同じパーティション構成に配置されるためです。 インデックスの値は、インデックスを使用する場合、同じパーティション構成とパーティション分割列のテーブルと*揃え*テーブルにします。  
  
> [!WARNING]  
>  固定されていないインデックスをパーティションが 1, 000 個以上あるテーブルに作成または再構築することは可能ですが、サポートされていません。 このような操作を行うと、操作中にパフォーマンスが低下したりメモリが過度に消費される可能性があります。 パーティションの数が 1, 000 個を超えた場合は、固定されたインデックスのみを使用することをお勧めします。  
  
 一意でないクラスター化インデックスをパーティション分割するとき、[!INCLUDE[ssDE](../../includes/ssde-md.md)] は既定では、まだ指定されていないパーティション分割列をクラスター化インデックス キーのリストに追加します。  
  
 インデックス付きビューは、テーブルのインデックスと同じ方法でパーティション分割されたテーブルに作成できます。 パーティション インデックスの詳細については、「 [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md)」を参照してください。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、パーティション分割されたインデックスを作成または再構築時に、テーブル内のすべての行をスキャンして統計は作成されません。 代わりに、クエリ オプティマイザーが既定のサンプリング アルゴリズムを使用して統計を生成します。 テーブル内のすべての行をスキャンしてパーティション インデックスの統計を作成するには、FULLSCAN 句で CREATE STATISTICS または UPDATE STATISTICS を使用します。  
  
## <a name="filtered-indexes"></a>フィルター選択されたインデックス  
 フィルター選択されたインデックスは、最適化された非クラスター化インデックスであり、テーブルから選択する行の少ないクエリに適しています。 フィルター選択されたインデックスは、フィルター述語を使用してテーブル内の一部のデータにインデックスを作成します。 フィルター選択されたインデックスを適切に設計すると、クエリのパフォーマンスを向上させ、ストレージ コストとメンテナンス コストを削減することができます。  
  
### <a name="required-set-options-for-filtered-indexes"></a>フィルター選択されたインデックスに必要な SET オプション  
 次の条件のいずれかに該当する場合、"必要な値" 列の SET オプションが必要となります。  
  
-   フィルター選択されたインデックスを作成するとき。  
  
-   INSERT、UPDATE、DELETE、MERGE のいずれかの操作で、フィルター選択されたインデックスのデータを変更するとき。  
  
-   フィルター選択されたインデックスは、クエリ プランを生成するために、クエリ オプティマイザーによって使用されます。  
  
    |SET オプション|必要な値|既定のサーバー値|既定値<br /><br /> OLE DB および ODBC 値|既定値<br /><br /> DB-Library 値|  
    |-----------------|--------------------|--------------------------|---------------------------------------|-----------------------------------|  
    |ANSI_NULLS|ON|ON|ON|OFF|  
    |ANSI_PADDING|ON|ON|ON|OFF|  
    |ANSI_WARNINGS*|ON|ON|ON|OFF|  
    |ARITHABORT|ON|ON|OFF|OFF|  
    |CONCAT_NULL_YIELDS_NULL|ON|ON|ON|OFF|  
    |NUMERIC_ROUNDABORT|OFF|OFF|OFF|OFF|  
    |QUOTED_IDENTIFIER|ON|ON|ON|OFF|   
  
     *ANSI_WARNINGS を ON に設定すると、データベース互換性レベルが 90 以上に設定されている場合、暗黙的に ARITHABORT が ON に設定されます。 データベース互換性レベルが 80 以下に設定されている場合は、ARITHABORT オプションを明示的に ON に設定する必要があります。  
  
 SET オプションが正しくないと、次の状態が発生する場合があります。  
  
-   フィルター選択されたインデックスが作成されません。  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]エラーが発生し、インデックス内のデータを変更する INSERT、UPDATE、DELETE、または MERGE ステートメントをロールバックします。  
  
-   Transact-SQL ステートメントの実行プランで、クエリ オプティマイザーがインデックスを無視します。  
  
 フィルター選択されたインデックスの詳細については、次を参照してください。 [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)です。  
  
## <a name="spatial-indexes"></a>空間インデックス  
 空間インデックスについては、次を参照してください。 [CREATE SPATIAL INDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-spatial-index-transact-sql.md)と[空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)です。  
  
## <a name="xml-indexes"></a>XML インデックス  
 XML インデックスについては、「の[CREATE XML INDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-xml-index-transact-sql.md)と[XML インデックス & #40 です。SQL Server &#41;](../../relational-databases/xml/xml-indexes-sql-server.md).  
  
## <a name="index-key-size"></a>インデックス キーのサイズ  
 インデックス キーの最大サイズは 900 バイトをクラスター化インデックスと非クラスター化インデックスの 1,700 バイトです。 (前に[!INCLUDE[ssSDS](../../includes/sssds-md.md)]V12 および[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]制限が 900 バイトでは常にします)。インデックス**varchar**列の既存のデータは、インデックスが作成時の制限を超えない場合をバイトの制限を超える列を作成することができますただし、後続の挿入や更新操作となる列、合計サイズの制限を超えることは失敗します。 クラスター化インデックスのインデックス キーには、ROW_OVERFLOW_DATA アロケーション ユニットに既存のデータを持つ **varchar** 列を含めることはできません。 クラスター化インデックスが **varchar** 列に作成され、既存のデータが IN_ROW_DATA アロケーション ユニットにある場合に、データを行外に押し出すような挿入処理や更新処理をその列に対して行うと失敗します。  
  
 非クラスター化インデックスのリーフ レベルに非キー列を含めることができます。 これらの列が考慮されない、[!INCLUDE[ssDE](../../includes/ssde-md.md)]インデックス キーのサイズを計算するときにします。 詳細については、「 [付加列インデックスの作成](../../relational-databases/indexes/create-indexes-with-included-columns.md)」を参照してください。  
  
> [!NOTE]  
>  テーブルがパーティション分割、パーティション分割キー列が一意でないクラスター化インデックスに存在しない場合、ユーザーは追加のインデックスを[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。 インデックス付きの列の合計サイズ (付加列は含みません) と追加されるパーティション分割列のサイズの合計は、一意でないクラスター化インデックスでは 1800 バイトを超えることはできません。  
  
## <a name="computed-columns"></a>計算列  
 インデックスを計算列に作成できます。 また、計算列にプロパティ PERSISTED を設定することができます。 その場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] によってテーブルに計算値が格納され、計算列が依存している他の列が更新されるとその計算値も更新されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] は、列にインデックスを作成するとき、およびインデックスがクエリで参照されるときに、これらの保存値を使用します。  
  
 計算列のインデックスを作成するには、計算列が決定的で正確である必要があります。 ただし、PERSISTED プロパティを使用した場合、インデックス作成が可能となる計算列の種類は、次のようになります。  
  
-   計算列に基づく[!INCLUDE[tsql](../../includes/tsql-md.md)]CLR 関数およびユーザーによって決定的とマークされた CLR ユーザー定義型のメソッドです。  
  
-   計算列の定義に従って決定論的である式に基づく、[!INCLUDE[ssDE](../../includes/ssde-md.md)]が不正確です。  
  
 保存される計算列に対しては、前の「インデックス付きビューに必要な SET オプション」で示すように、次の SET オプションを設定する必要があります。  
  
 インデックス作成の条件をすべて満たしている限り、UNIQUE または PRIMARY KEY 制約があっても計算列を含めることができます。 この計算列は、決定的かつ正確であるか、決定的かつ持続可能である必要があります。 決定性の詳細については、次を参照してください。[決定的関数と非決定的関数](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)です。  
  
 派生した計算列**イメージ**、 **ntext**、**テキスト**、 **varchar (max)**、 **nvarchar (max)**、**varbinary (max)**、および**xml**の型があるデータとしてインデックスを設定、キー列または付加非キー列、計算列のデータ型がインデックス キー列または非キー列として使用できる限り、します。 たとえば、計算で、プライマリ XML インデックスを作成することはできません**xml**列です。 インデックス サイズが 900 バイトを超える場合、警告メッセージが表示されます。  
  
 計算列にインデックスを作成すると、以前は機能していた挿入または更新の操作が失敗することがあります。 このような失敗は、計算列の結果が算術エラーになる場合に発生する可能性があります。 たとえば、次のテーブルでは、計算列 `c` は計算エラーになりますが、`INSERT` ステートメントは正常に実行されます。  
  
```  
CREATE TABLE t1 (a int, b int, c AS a/b);  
INSERT INTO t1 VALUES (1, 0);  
```  
  
 これに対し、テーブルの作成後に計算列 `c` にインデックスを作成すると、同じ `INSERT` ステートメントは失敗します。  
  
```  
CREATE TABLE t1 (a int, b int, c AS a/b);  
CREATE UNIQUE CLUSTERED INDEX Idx1 ON t1(c);  
INSERT INTO t1 VALUES (1, 0);  
```  
  
 詳細については、「 [計算列のインデックス](../../relational-databases/indexes/indexes-on-computed-columns.md)」を参照してください。  
  
## <a name="included-columns-in-indexes"></a>インデックスの付加列  
 付加列と呼ばれる非キー列は、非クラスター化インデックスのリーフ レベルに追加でき、クエリに対応することによりクエリ パフォーマンスを向上できます。 この場合、クエリで参照されるすべての列は、キー列または非キー列としてインデックスに含まれます。 これにより、クエリ オプティマイザーではテーブルまたはクラスター化インデックス データにアクセスすることなく、インデックス スキャンによって必要な情報をすべて特定できます。 詳細については、「 [付加列インデックスの作成](../../relational-databases/indexes/create-indexes-with-included-columns.md)」を参照してください。  
  
## <a name="specifying-index-options"></a>インデックス オプションの指定  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]導入された新しいインデックス オプションしもオプションが指定されている方法を変更します。 旧バージョンとの互換性のある構文では WITH *option_name*は WITH に相当**(** \<option_name >  **=**  ON **)**. インデックス オプションを設定する場合は、次の規則が適用されます。 
  
-   WITH を使用して新しいインデックス オプションを指定することができますのみ**(***option_name*  **=**  ON |OFF**)**です。  
  
-   同じステートメントで、旧バージョンとの互換性がある構文と新しい構文の両方を使ってオプションを指定することはできない。 たとえば、WITH を指定する**(**DROP_EXISTING**、**オンライン **=**  ON**)**により、ステートメントが失敗します。  
  
-   WITH を使用して、オプションを指定する必要があります XML インデックスを作成するときに**(***option_name*  **=**  ON |OFF**)**です。  
  
## <a name="dropexisting-clause"></a>DROP_EXISTING 句  
 DROP_EXISTING 句を使用して、インデックスの再構築、列の追加または削除、オプションの変更、列の並べ替え順の変更、パーティション構成またはファイル グループの変更を行うことができます。  
  
 インデックスに PRIMARY KEY または UNIQUE 制約が設定されていて、インデックス定義が変更されることがない場合は、既存の制約を保持したままインデックスが削除され再作成されます。 ただし、インデックス定義が変更されると、ステートメントは失敗します。 PRIMARY KEY または UNIQUE 制約の定義を変更するには、制約を削除し、新しい定義で制約を追加します。  
  
 DROP_EXISTING を使用すると、非クラスター化インデックスが定義されているテーブル上で、同じまたは異なるキー セットのクラスター化インデックスを再作成するときのパフォーマンスを向上できます。 DROP_EXISTING では、古いクラスター化インデックスに DROP INDEX ステートメントを実行した後、新しいクラスター化インデックスに CREATE INDEX ステートメントを実行するという操作を一度に実行できます。 非クラスター化インデックスは一度だけ再構築され、その後はインデックス定義が変更された場合のみ再構築されます。 インデックス定義に元のインデックスと同じインデックス名、キーおよびパーティション列、一意性属性、および並べ替え順がある場合、DROP_EXISTING 句で非クラスター化インデックスを再構築できません。  
  
 非クラスター化インデックスが再構築されるかどうかに関係なく、非クラスター化インデックスは元のファイル グループまたはパーティション構成に常に属したままになり、元のパーティション関数を使用します。 クラスター化インデックスが他のファイル グループまたはパーティション構成に再構築される場合、非クラスター化インデックスはクラスター化インデックスの新しい位置に移動されません。 したがって、以前に非クラスター化インデックスがクラスター化インデックスに対応した位置にあっても、再構築後は別の位置になる可能性があります。 パーティション インデックスの位置合わせの詳細については、「」を参照してください。  
  
 インデックス ステートメントで非クラスター化インデックスが指定され、かつ ONLINE オプションが OFF に設定されている場合を除き、同じインデックス キー列が同じ順序 (昇順または降順も同じ) で使用される場合、DROP_EXISTING 句では再度データの並べ替えは行われません。 クラスター化インデックスが無効になっている場合、CREATE INDEX WITH DROP_EXISTING 操作は ONLINE が OFF に設定された状態で実行する必要があります。 非クラスター化インデックスが無効で、無効なクラスター化インデックスと関連がない場合、CREATE INDEX WITH DROP_EXISTING 操作は、ONLINE が OFF または ON に設定された状態で実行できます。  
  
 128 以上のエクステントがあるインデックスを削除または再構築するとき、[!INCLUDE[ssDE](../../includes/ssde-md.md)]は、トランザクションがコミットされるまで実際のページの割り当て解除とそれに関連するロックを延期します。  
  
## <a name="online-option"></a>ONLINE オプション  
 インデックス操作をオンラインで実行する場合は、次のガイドラインが適用されます。  
  
-   オンライン インデックス操作の実行中、基になるテーブルは変更、切り捨て、削除できない。  
  
-   インデックス操作中は、追加の一時ディスク領域が必要。  
  
-   オンライン操作は、パーティション インデックスや、保存される計算列を含むインデックス、または付加列で実行できる。  
  
 詳しくは、「 [Perform Index Operations Online](../../relational-databases/indexes/perform-index-operations-online.md)」をご覧ください。  
  
## <a name="row-and-page-locks-options"></a>行およびページ ロック オプション  
 ALLOW_ROW_LOCKS = ON かつ ALLOW_PAGE_LOCK = ON の場合は、インデックスにアクセスするときに、行、ページ、およびテーブル レベルのロックが許可されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]適切なロックを選択し、行またはページ ロックからテーブル ロックのロックをエスカレートすることができます。  
  
 ALLOW_ROW_LOCKS = OFF かつ ALLOW_PAGE_LOCK = OFF の場合は、インデックスにアクセスするときに、テーブル レベルのロックのみが許可されます。  
  
## <a name="viewing-index-information"></a>インデックス情報の表示  
 インデックスに関する情報を返すには、カタログ ビュー、システム関数、およびシステム ストアド プロシージャを使用できます。  
  
## <a name="data-compression"></a>Data Compression  
 データ圧縮は、トピックに記載されて[データ圧縮](../../relational-databases/data-compression/data-compression.md)です。 特に次の点に注意してください。  
  
-   圧縮を使用すると、ページに格納できる行数が増えますが、最大行サイズは変更されません。  
  
-   インデックスの非リーフ ページでは、ページの圧縮は行われませんが、行の圧縮は可能です。  
  
-   非クラスター化インデックスにはそれぞれ個別の圧縮設定があり、基になるテーブルの圧縮設定は継承されません。  
  
-   ヒープにクラスター化インデックスを作成する場合、圧縮状態を特に指定しない限り、ヒープの圧縮状態がクラスター化インデックスに継承されます。  
  
 パーティション インデックスには次の制限が適用されます。  
  
-   固定されていないインデックスがテーブルにある場合、そのパーティションの圧縮設定を変更できません。  
  
-   ALTER INDEX \<index >.REBUILD PARTITION ... 構文は、そのインデックスの指定のパーティションを再構築します。  
  
-   ALTER INDEX \<index >.REBUILD WITH ... 構文は、そのインデックスのすべてのパーティションを再構築します。  
  
 圧縮状態の変更による、テーブル、インデックス、またはパーティションへの影響を評価するには、 [sp_estimate_data_compression_savings](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md) ストアド プロシージャを使用します。  
  
## <a name="permissions"></a>Permissions  
 テーブルまたはビューに対する ALTER 権限が必要です。 実行するには、 **sysadmin** 固定サーバー ロール、または **db_ddladmin** 固定データベース ロールおよび **db_owner** 固定データベース ロールのメンバーである必要があります。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]および[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、作成することはできません。  
  
-   列ストア インデックスが既に存在する場合は、データ ウェアハウスのテーブルにクラスター化または非クラスター化行ストア インデックスです。 この動作は同じテーブル上に共存する行ストアと列ストアの両方のインデックス使用できる SMP SQL サーバーと異なるです。  
  
-   ビューにインデックスを作成できません。  
  
## <a name="metadata"></a>メタデータ  
 既存のインデックス情報を表示するにはクエリ、 [sys.indexes & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)カタログ ビューです。  
  
## <a name="version-notes"></a>バージョンのメモ  
 SQL データベースは、ファイル グループと filestream オプションをサポートしていません。  
  
## <a name="examples-all-versions-uses-the-adventureworks-database"></a>例: すべてのバージョン。 AdventureWorks データベースを使用します。  
  
### <a name="a-create-a-simple-nonclustered-rowstore-index"></a>A. 単純な非クラスター化行ストア インデックスを作成します。  
 次の例では、非クラスター化インデックスを作成で、`VendorID`の列、`Purchasing.ProductVendor`テーブル。  
  
```  
CREATE INDEX IX_VendorID ON ProductVendor (VendorID);  
CREATE INDEX IX_VendorID ON dbo.ProductVendor (VendorID DESC, Name ASC, Address DESC);  
CREATE INDEX IX_VendorID ON Purchasing..ProductVendor (VendorID);  
```  
  
### <a name="b-create-a-simple-nonclustered-rowstore-composite-index"></a>B. 単純な非クラスター化行ストア複合インデックスを作成します。  
 次の例では、非クラスター化複合インデックスを作成で、`SalesQuota`と`SalesYTD`の列、`Sales.SalesPerson`テーブル。  
  
```  
CREATE NONCLUSTERED INDEX IX_SalesPerson_SalesQuota_SalesYTD ON Sales.SalesPerson (SalesQuota, SalesYTD);  
```  
  
### <a name="c-create-an-index-on-a-table-in-another-database"></a>C. 別のデータベース内のテーブルにインデックスを作成します。  
 次の例では、非クラスター化インデックスを作成で、`VendorID`の列、`ProductVendor`テーブルに、`Purchasing`データベース。  
  
```  
CREATE CLUSTERED INDEX IX_ProductVendor_VendorID ON Purchasing..ProductVendor (VendorID);   
```  
  
### <a name="d-add-a-column-to-an-index"></a>D. インデックスに列を追加します。  
 次の例では、dbo から 2 つの列をインデックス IX_FF を作成します。FactFinance テーブルです。  次のステートメントでは、1 つ以上の列にインデックスを再構築し、既存の名前を保持します。  
  
```  
CREATE INDEX IX_FF ON dbo.FactFinance ( FinanceKey ASC, DateKey ASC );  
  
--Rebuild and add the OrganizationKey  
CREATE INDEX IX_FF ON dbo.FactFinance ( FinanceKey, DateKey, OrganizationKey DESC)  
WITH ( DROP_EXISTING = ON );  
 ```  
  
## <a name="examples-sql-server-azure-sql-database"></a>例: SQL Server、Azure SQL データベース  
  
### <a name="e-create-a-unique-nonclustered-index"></a>E. 一意非クラスター化インデックスを作成します。  
 次の例では、一意の非クラスター化インデックスを作成で、`Name`の列、`Production.UnitMeasure`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。 このインデックスでは、`Name` 列に挿入されるデータが一意である必要があります。  
  
```  
CREATE UNIQUE INDEX AK_UnitMeasure_Name   
    ON Production.UnitMeasure(Name);  
```  
  
 次のクエリでは、既存の行と同じ値の行を挿入することによって、一意性の制約をテストします。  
  
```  
--Verify the existing value.  
SELECT Name FROM Production.UnitMeasure WHERE Name = N'Ounces';  
GO  
INSERT INTO Production.UnitMeasure (UnitMeasureCode, Name, ModifiedDate)  
    VALUES ('OC', 'Ounces', GetDate());  
```  
  
 結果のエラー メッセージは次のようになります。  
  
```  
Server: Msg 2601, Level 14, State 1, Line 1  
Cannot insert duplicate key row in object 'UnitMeasure' with unique index 'AK_UnitMeasure_Name'. The statement has been terminated.  
```  
  
### <a name="f-use-the-ignoredupkey-option"></a>F. IGNORE_DUP_KEY オプションを使用します。  
 次の例の効果を示して、`IGNORE_DUP_KEY`オプションに設定するオプションを使用して最初に一時テーブルに複数の行を挿入して`ON`およびオプションに設定を使用して`OFF`です。 2 番目の複数行の `#Test` ステートメントを実行するときには、`INSERT` テーブルに、重複する値となる 1 行を意図的に挿入します。 テーブル内の行数としては、挿入された行数が返されます。  
  
```  
CREATE TABLE #Test (C1 nvarchar(10), C2 nvarchar(50), C3 datetime);  
GO  
CREATE UNIQUE INDEX AK_Index ON #Test (C2)  
    WITH (IGNORE_DUP_KEY = ON);  
GO  
INSERT INTO #Test VALUES (N'OC', N'Ounces', GETDATE());  
INSERT INTO #Test SELECT * FROM Production.UnitMeasure;  
GO  
SELECT COUNT(*)AS [Number of rows] FROM #Test;  
GO  
DROP TABLE #Test;  
GO  
```  
  
 ここでは、2 つ目の結果`INSERT`ステートメントです。  
  
```  
Server: Msg 3604, Level 16, State 1, Line 5 Duplicate key was ignored.  
  
Number of rows   
--------------   
38  
```  
  
 行が挿入されることに注意してください、`Production.UnitMeasure`一意性制約に違反していないテーブルが正常に挿入されました。 ここでは警告が発行され、重複する行が無視されましたが、トランザクション全体はロールバックされていません。  
  
 もう一度同じステートメントが実行される`IGNORE_DUP_KEY`'éý'`OFF`です。  
  
```  
CREATE TABLE #Test (C1 nvarchar(10), C2 nvarchar(50), C3 datetime);  
GO  
CREATE UNIQUE INDEX AK_Index ON #Test (C2)  
    WITH (IGNORE_DUP_KEY = OFF);  
GO  
INSERT INTO #Test VALUES (N'OC', N'Ounces', GETDATE());  
INSERT INTO #Test SELECT * FROM Production.UnitMeasure;  
GO  
SELECT COUNT(*)AS [Number of rows] FROM #Test;  
GO  
DROP TABLE #Test;  
GO  
```  
  
 ここでは、2 つ目の結果`INSERT`ステートメントです。  
  
```  
Server: Msg 2601, Level 14, State 1, Line 5  
Cannot insert duplicate key row in object '#Test' with unique index  
'AK_Index'. The statement has been terminated.  
  
Number of rows   
--------------   
1  
```  
  
 注意してくださいのどの行を`Production.UnitMeasure`に違反するテーブルの行の 1 つだけ場合でも、テーブルが、テーブルに挿入された、`UNIQUE`制約のインデックスを作成します。  
  
### <a name="g-using-dropexisting-to-drop-and-re-create-an-index"></a>G. DROP_EXISTING を使ってインデックスを削除し再作成する  
 次の例では、`ProductID` オプションを使って、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースにある`Production.WorkOrder` テーブルの `DROP_EXISTING` 列にある既存のインデックスを削除して再作成します。 ここではオプション `FILLFACTOR` および `PAD_INDEX` も設定されています。  
  
```  
CREATE NONCLUSTERED INDEX IX_WorkOrder_ProductID  
    ON Production.WorkOrder(ProductID)  
    WITH (FILLFACTOR = 80,  
        PAD_INDEX = ON,  
        DROP_EXISTING = ON);  
GO  
  
```  
  
### <a name="h-create-an-index-on-a-view"></a>H. ビューにインデックスを作成します。  
 次の例では、ビューとそのビューのインデックスを作成します。 ここでは、インデックス付きビューを使用する 2 つのクエリを実行します。  
  
```  
--Set the options to support indexed views.  
SET NUMERIC_ROUNDABORT OFF;  
SET ANSI_PADDING, ANSI_WARNINGS, CONCAT_NULL_YIELDS_NULL, ARITHABORT,  
    QUOTED_IDENTIFIER, ANSI_NULLS ON;  
GO  
--Create view with schemabinding.  
IF OBJECT_ID ('Sales.vOrders', 'view') IS NOT NULL  
DROP VIEW Sales.vOrders ;  
GO  
CREATE VIEW Sales.vOrders  
WITH SCHEMABINDING  
AS  
    SELECT SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Revenue,  
        OrderDate, ProductID, COUNT_BIG(*) AS COUNT  
    FROM Sales.SalesOrderDetail AS od, Sales.SalesOrderHeader AS o  
    WHERE od.SalesOrderID = o.SalesOrderID  
    GROUP BY OrderDate, ProductID;  
GO  
--Create an index on the view.  
CREATE UNIQUE CLUSTERED INDEX IDX_V1   
    ON Sales.vOrders (OrderDate, ProductID);  
GO  
--This query can use the indexed view even though the view is   
--not specified in the FROM clause.  
SELECT SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Rev,   
    OrderDate, ProductID  
FROM Sales.SalesOrderDetail AS od  
    JOIN Sales.SalesOrderHeader AS o ON od.SalesOrderID=o.SalesOrderID  
        AND ProductID BETWEEN 700 and 800  
        AND OrderDate >= CONVERT(datetime,'05/01/2002',101)  
GROUP BY OrderDate, ProductID  
ORDER BY Rev DESC;  
GO  
--This query can use the above indexed view.  
SELECT  OrderDate, SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Rev  
FROM Sales.SalesOrderDetail AS od  
    JOIN Sales.SalesOrderHeader AS o ON od.SalesOrderID=o.SalesOrderID  
        AND DATEPART(mm,OrderDate)= 3  
        AND DATEPART(yy,OrderDate) = 2002  
GROUP BY OrderDate  
ORDER BY OrderDate ASC;  
GO  
  
```  
  
### <a name="i-create-an-index-with-included-non-key-columns"></a>I. (非キー) の付加列を含むインデックスを作成します。  
 次の例では、1 つのキー列 (`PostalCode`) と 4 つの非キー列 (`AddressLine1`、`AddressLine2`、`City`、`StateProvinceID`) を使って非クラクタ化インデックスを作成します。 次に、そのインデックスが対応するクエリを実行します。 クエリ オプティマイザーによって選択されたインデックスを表示する、**クエリ**メニューの[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**実際の実行プランを表示**クエリを実行する前にします。  
  
```  
CREATE NONCLUSTERED INDEX IX_Address_PostalCode  
    ON Person.Address (PostalCode)  
    INCLUDE (AddressLine1, AddressLine2, City, StateProvinceID);  
GO  
SELECT AddressLine1, AddressLine2, City, StateProvinceID, PostalCode  
FROM Person.Address  
WHERE PostalCode BETWEEN N'98000' and N'99999';  
GO  
```  
  
### <a name="j-create-a-partitioned-index"></a>J. パーティション インデックスを作成します。  
 次の例では、非クラスター化パーティション インデックスを作成で`TransactionsPS1`、既存のパーティション構成で、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。 この例では、パーティション インデックスのサンプルがインストールされていることを前提としています。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
```  
CREATE NONCLUSTERED INDEX IX_TransactionHistory_ReferenceOrderID  
    ON Production.TransactionHistory (ReferenceOrderID)  
    ON TransactionsPS1 (TransactionDate);  
GO  
```  
  
### <a name="k-creating-a-filtered-index"></a>K. フィルター選択されたインデックスを作成する  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースの Production.BillOfMaterials テーブルにフィルター選択されたインデックスを作成します。 フィルター述語では、フィルター選択されたインデックスに非キー列を含めることができます。 この例の述語では、EndDate が NULL 以外の行だけを選択します。  
  
```  
CREATE NONCLUSTERED INDEX "FIBillOfMaterialsWithEndDate"  
    ON Production.BillOfMaterials (ComponentID, StartDate)  
    WHERE EndDate IS NOT NULL;  
```  
  
### <a name="l-create-a-compressed-index"></a>L. 圧縮されたインデックスを作成します。  
 次の例では、行の圧縮を使用して、非パーティション テーブルのインデックスを作成します。  
  
```  
CREATE NONCLUSTERED INDEX IX_INDEX_1   
    ON T1 (C2)  
WITH ( DATA_COMPRESSION = ROW ) ;   
GO  
```  
  
 次の例では、インデックスのすべてのパーティションに行の圧縮を使用して、パーティション テーブルのインデックスを作成します。  
  
```  
CREATE CLUSTERED INDEX IX_PartTab2Col1  
ON PartitionTable1 (Col1)  
WITH ( DATA_COMPRESSION = ROW ) ;  
GO  
```  
  
 次の例は、パーティションをページの圧縮を使用してパーティション テーブルのインデックスを作成`1`パーティションに対するインデックスと行の圧縮の`2`を通じて`4`のインデックス。  
  
```  
CREATE CLUSTERED INDEX IX_PartTab2Col1  
ON PartitionTable1 (Col1)  
WITH (DATA_COMPRESSION = PAGE ON PARTITIONS(1),  
    DATA_COMPRESSION = ROW ON PARTITIONS (2 TO 4 ) ) ;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="m-basic-syntax"></a>M. 基本構文  
  
```  
CREATE INDEX IX_VendorID   
    ON ProductVendor (VendorID);  
CREATE INDEX IX_VendorID   
    ON dbo.ProductVendor (VendorID DESC, Name ASC, Address DESC);  
CREATE INDEX IX_VendorID   
    ON Purchasing..ProductVendor (VendorID);  
```  
  
### <a name="n-create-a-non-clustered-index-on-a-table-in-the-current-database"></a>N. 現在のデータベース内のテーブルに非クラスター化インデックスを作成します。  
 次の例では、非クラスター化インデックスを作成で、`VendorID`の列、`ProductVendor`テーブル。  
  
```  
CREATE INDEX IX_ProductVendor_VendorID   
    ON ProductVendor (VendorID);   
```  
  
### <a name="o-create-a-clustered-index-on-a-table-in-another-database"></a>O.  別のデータベース内のテーブルにクラスター化インデックスを作成します。  
 次の例では、非クラスター化インデックスを作成で、`VendorID`の列、`ProductVendor`テーブルに、`Purchasing`データベース。  
  
```  
CREATE CLUSTERED INDEX IX_ProductVendor_VendorID   
    ON Purchasing..ProductVendor (VendorID);   
```  
  
### <a name="p-add-a-column-to-an-index"></a>P. インデックスに列を追加します。  
 次の例では、dbo から 2 つの列をインデックス IX_FF を作成します。FactFinance テーブルです。  次のステートメントでは、同じ名前と 1 つ以上の列には、そのインデックスを再構築を示します。  
  
```  
CREATE INDEX IX_FF ON dbo.FactFinance (  
    FinanceKey ASC, DateKey ASC );  
  
--Rebuild and add the OrganizationKey  
CREATE INDEX IX_FF ON dbo.FactFinance (  
    FinanceKey, DateKey, OrganizationKey DESC)  
WITH ( DROP_EXISTING = ON );  
```  
  
## <a name="see-also"></a>参照  
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [空間インデックス &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-spatial-index-transact-sql.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [XML インデックス &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-xml-index-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP INDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-index-transact-sql.md)   
 [XML インデックス &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [sys.xml_indexes & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-xml-indexes-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
 


