---
title: CREATE COLUMNSTORE INDEX (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE_COLUMNSTORE_INDEX_TSQL
- COLUMNSTORE INDEX
- COLUMNSTORE_INDEX_TSQL
- CREATE CLUSTERED COLUMNSTORE INDEX
- COLUMNSTORE_TSQL
- CREATE NONCLUSTERED COLUMNSTORE INDEX
- CREATE_NONCLUSTERED_COLUMNSTORE_INDEX_TSQL
- CREATE COLUMNSTORE INDEX
- CREATE_CLUSTERED_COLUMNSTORE_INDEX_TSQL
- COLUMNSTORE
dev_langs:
- TSQL
helpviewer_keywords:
- index creation [SQL Server], columnstore indexes
- columnstore index, creating
- CREATE COLUMNSTORE INDEX statement
- CREATE INDEX statement
ms.assetid: 7e1793b3-5383-4e3d-8cef-027c0c8cb5b1
caps.latest.revision: 76
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f00d346a509c7a240b00ce287782001804126311
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34236143"
---
# <a name="create-columnstore-index-transact-sql"></a>CREATE COLUMNSTORE INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

行ストア テーブルをクラスター化された列ストア インデックスに変換するか、クラスター化されていない列ストア インデックスを作成します。 OLTP ワークロードに効率的にリアルタイムの経営分析を実行する、またはデータ ウェアハウスのワークロードのデータの圧縮とクエリのパフォーマンスを向上させるためには、列ストア インデックスを使用します。  
  
> [!NOTE]  
> [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降、テーブルをクラスター化列ストア インデックスとして作成できます。   最初に行ストア テーブルを作成し、それをクラスター化列ストア インデックスに変換する作業は不要になりました。  

> [!TIP]
> インデックスの設計のガイドラインについては、「[SQL Server インデックス デザイン ガイド](../../relational-databases/sql-server-index-design-guide.md)」をご覧ください。

例に進みます。  
-   [行ストア テーブルを列ストアに変換する例](../../t-sql/statements/create-columnstore-index-transact-sql.md#convert)  
-   [非クラスター化列ストア インデックスの例](../../t-sql/statements/create-columnstore-index-transact-sql.md#nonclustered)  
  
シナリオに移動:  
-   [リアルタイム運用分析の列ストア インデックス](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)  
-   [データ ウェアハウスの列ストア インデックス](../../relational-databases/indexes/columnstore-indexes-data-warehouse.md)  
  
詳細情報:  
-   [列ストア インデックス ガイド](../../relational-databases/indexes/columnstore-indexes-overview.md)  
-   [列ストア インデックスの機能の概要](../../relational-databases/indexes/columnstore-indexes-what-s-new.md)  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Create a clustered columnstore index on disk-based table.  
CREATE CLUSTERED COLUMNSTORE INDEX index_name  
    ON [database_name. [schema_name ] . | schema_name . ] table_name  
    [ WITH ( < with_option> [ ,...n ] ) ]  
    [ ON <on_option> ]  
[ ; ]  
  
--Create a non-clustered columnstore index on a disk-based table.  
CREATE [NONCLUSTERED]  COLUMNSTORE INDEX index_name   
    ON [database_name. [schema_name ] . | schema_name . ] table_name   
        ( column  [ ,...n ] )  
    [ WHERE <filter_expression> [ AND <filter_expression> ] ]
    [ WITH ( < with_option> [ ,...n ] ) ]  
    [ ON <on_option> ]   
[ ; ]  
  
<with_option> ::=  
      DROP_EXISTING = { ON | OFF } -- default is OFF  
    | MAXDOP = max_degree_of_parallelism 
    | ONLINE = { ON | OFF } 
    | COMPRESSION_DELAY  = { 0 | delay [ Minutes ] }  
    | DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
      [ ON PARTITIONS ( { partition_number_expression | range } [ ,...n ] ) ]  
  
<on_option>::=  
      partition_scheme_name ( column_name )   
    | filegroup_name   
    | "default"   
  
<filter_expression> ::=  
      column_name IN ( constant [ ,...n ]  
    | column_name { IS | IS NOT | = | <> | != | > | >= | !> | < | <= | !< } constant  
  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CREATE CLUSTERED COLUMNSTORE INDEX index_name   
    ON [ database_name . [ schema_name ] . | schema_name . ] table_name  
    [ WITH ( DROP_EXISTING = { ON | OFF } ) ] --default is OFF  
[;]  
```  
  
## <a name="arguments"></a>引数  
CREATE CLUSTERED COLUMNSTORE INDEX  
すべてのデータが列ごとに圧縮されて格納されるクラスター化列ストア インデックスを作成します。 インデックスにはテーブル内の列がすべて含まれ、テーブル全体が格納されます。 既存のテーブルがヒープまたはクラスター化インデックスである場合、そのテーブルはクラスター化列ストア インデックスに変換されます。 テーブルが既にクラスター化列ストア インデックスとして格納されている場合、既存のインデックスは削除され、再構築されます。  
  
*index_name*  
新しいインデックスの名前を指定します。  
  
テーブルは、クラスター化列ストア インデックスを既に持っている場合、既存のインデックスと同じ名前を指定できます。 または DROP EXISTING オプションを使用するには新しい名前を指定します。  
  
ON [*database_name*. [*schema_name* ] . | *schema_name* . ] *table_name*  
   クラスター化列ストア インデックスとして格納するテーブルの 1 部、2 部、または 3 部構成の名前を指定します。 テーブルがヒープかクラスター化インデックスの場合、テーブルは行ストアから列ストアに変換されます。 テーブルが既に列ストアである場合、このステートメントでクラスター化列ストア インデックスが再構築されます。  
  
のすべてのメンションを  
DROP_EXISTING = [オフ] |ON  
   DROP_EXISTING = ON を使用する既存のクラスター化列ストア インデックスを削除して、新しい列ストア インデックスを作成します。  

   既定では、DROP_EXISTING = OFF インデックス名は、既存の名前と同じが必要です。 指定したインデックス名が既に存在するは、エラーが発生します。  
  
MAXDOP = *max_degree_of_parallelism*  
   インデックス操作の間、既存の "並列処理の最大限度" サーバー構成をオーバーライドします。 並列プランの実行で使用されるプロセッサ数を制限するには、MAXDOP を使用します。 最大数は 64 プロセッサです。  
  
   *max_degree_of_parallelism* 値に指定できる値:  
   - 1 - 並列プラン生成を抑制します。  
   - \>1 - 現在のシステム ワークロードに基づいて、並列インデックス操作で使用される最大プロセッサ数を指定の数以下に制限します。 たとえば、MAXDOP が 4 の場合、使用されるプロセッサの数は 4 以下になります。  
   - 0 (既定) - 現在のシステム ワークロードに基づいて、実際の数以下のプロセッサを使用します。  
  
   詳細については、「[max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) 」と「 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)」を参照してください。  
 
COMPRESSION_DELAY = **0** | *delay* [ Minutes ]  
   適用対象: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。

   ディスク ベースのテーブルの場合は、CLOSED 状態のデルタ行グループがそのデルタ行グループに留まる必要がある最低限の分数が*遅延*によって指定され、その時間が経過すると、SQL Server は行グループを、圧縮された行グループに圧縮できるようになります。 ディスク ベース テーブルでは個々の行において挿入時間と更新時間が追跡されないため、SQL Server は CLOSED 状態のデルタ行グループに遅延を適用します。  
   既定値は、0 分です。  
   COMPRESSION_DELAY を使用する場合の推奨事項については、「[列ストアを使用したリアルタイム運用分析の概要](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)」をご覧ください。  
  
DATA_COMPRESSION = COLUMNSTORE | COLUMNSTORE_ARCHIVE  
   適用対象: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。
指定したテーブル、パーティション番号、またはパーティション範囲に、データ圧縮オプションを指定します。 次のオプションがあります。   
COLUMNSTORE  
   列ストアでは、既定値は、し、ほとんどのパフォーマンスの高い列ストア圧縮で圧縮することを指定します。 これは、一般的な選択肢です。  
  
COLUMNSTORE_ARCHIVE  
   COLUMNSTORE_ARCHIVE は、テーブルまたはパーティション サイズをより小さなサイズに圧縮します。 などの状況をこのオプションを使用してアーカイブを記憶域のサイズを必要とし、保存と取得に多くの時間に余裕があることができます。  
  
   圧縮の詳細については、「[データ圧縮](../../relational-databases/data-compression/data-compression.md)」を参照してください。  

ON  
   ON オプションを使用すると、パーティション構成、特定のファイル グループ、既定のファイル グループなど、データ ストレージのオプションを指定できます。 ON オプションを指定しない場合、インデックスでは、既存のテーブルの設定パーティションまたはファイル グループ設定が使用されます。  
  
   *partition_scheme_name* **(** *column_name* **)**  
   テーブルのパーティション構成を指定します。 パーティション構成は既にデータベースに存在している必要があります。 パーティション構成を作成するには、「[CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md)」をご覧ください。  
 
   *column_name* には、パーティション インデックスがパーティション分割される対象の列を指定します。 この列は、*partition_scheme_name* で使用されているパーティション関数の引数のデータ型、長さ、有効桁数に一致する必要があります。  

   *filegroup_name*  
   クラスター化列ストア インデックスを格納するファイル グループを指定します。 位置の指定がなく、テーブルがパーティション分割されていない場合は、基になるテーブルまたはビューと同じファイル グループが使用されます。 ファイル グループは既に存在している必要があります。  

   **"** default **"**  
   既定のファイル グループにインデックスを作成するには、"default" または [ default ] を使用します。  
  
   "default" を指定する場合は、現在のセッションに対して QUOTED_IDENTIFIER オプションが ON である必要があります。 QUOTED_IDENTIFIER は既定で ON です。 詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
CREATE [NONCLUSTERED] COLUMNSTORE INDEX  
行ストア テーブルにメモリ内の非クラスター化列ストア インデックスを作成、ヒープまたはクラスター化インデックスとして格納します。 インデックスでは、フィルター選択された条件し、基になるテーブルの列のすべてを含める必要はありません。 列ストア インデックスでは、データのコピーを保存するには、十分な領域が必要です。 更新可能であり、基になるテーブルが変更されると更新されます。 クラスター化インデックスに非クラスター化列ストア インデックスでは、リアルタイム分析の機能を使用できます。  
  
*index_name*  
   インデックスの名前を指定します。 *index_name* はテーブル内で一意にする必要がありますが、データベース内で一意である必要はありません。 インデックス名は、[識別子](../../relational-databases/databases/database-identifiers.md)の規則に従っている必要があります。  
  
 **(** *column*  [ **,**...*n* ] **)**  
    格納する列を指定します。 非クラスター化列ストア インデックスは、1,024年列に制限されます。  
   各列は、列ストア インデックスでサポートされているデータ型である必要があります。 サポートされるデータ型の一覧については、「[制限事項と制約事項](../../t-sql/statements/create-columnstore-index-transact-sql.md#LimitRest)」を参照してください。  

ON [*database_name*. [*schema_name* ] . | *schema_name* . ] *table_name*  
   インデックスが含まれているテーブルの 1 部、2 部、または 3 部構成の名前を指定します。  

WITH DROP_EXISTING = [OFF] | ON  
   DROP_EXISTING = ON 既存のインデックスは削除され、再構築されます。 指定するインデックス名は、現在存在するインデックスと同じにする必要がありますが、インデックス定義は変更できます。 たとえば、異なる列またはインデックス オプションを指定できます。
  
   DROP_EXISTING = OFF 指定するインデックス名が既に存在する場合、エラーが表示されます。 DROP_EXISTING を使用してインデックスの種類を変更することはできません。 旧バージョンと互換性のある構文では、WITH DROP_EXISTING は WITH DROP_EXISTING = ON と同じです。  

MAXDOP = *max_degree_of_parallelism*  
   インデックス操作の間、[max degree of parallelism サーバー構成オプション](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)更新オプションをオーバーライドします。 並列プランの実行で使用されるプロセッサ数を制限するには、MAXDOP を使用します。 最大数は 64 プロセッサです。  
  
   *max_degree_of_parallelism* 値に指定できる値:  
   - 1 - 並列プラン生成を抑制します。  
   - \>1 - 現在のシステム ワークロードに基づいて、並列インデックス操作で使用される最大プロセッサ数を指定の数以下に制限します。 たとえば、MAXDOP が 4 の場合、使用されるプロセッサの数は 4 以下になります。  
   - 0 (既定) - 現在のシステム ワークロードに基づいて、実際の数以下のプロセッサを使用します。  
  
   詳細については、「 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)」を参照してください。  
  
> [!NOTE]  
>  並列インデックス操作は、[!INCLUDE[msC](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各エディションでサポートされる機能の一覧については、「[Editions and Supported Features for SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)」 (SQL Server 2016 のエディションとサポートされる機能) を参照してください。  
  
ONLINE = [ON | OFF]   
   適用対象: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]、非クラスター化インデックスのみ。
ON の場合、インデックスの新しいコピーが構築されている間、非クラスター化インデックスはオンラインの状態を維持し、利用できます。

   OFF の場合、新しいコピーが構築されている間、インデックスは使用できません。 これは非クラスター化インデックスのみであり、ベース テーブルは利用できます。新しいインデックスが完成するまで、非クラスター化インデックスのみクエリの応答に利用されません。 

COMPRESSION_DELAY = **0** | \<delay>[Minutes]  
   適用対象: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。 
  
   行がデルタ行グループに残る期間の下限を指定します。この下限までは、圧縮された行グループに移行できます。 たとえば、行が 120 分間変更されない場合、単票格納形式に圧縮するという顧客がいるかもしれません。 ディスクベース テーブルの列ストア インデックスの場合、行が挿入または更新された時刻は追跡しません。代わりに、行のプロキシとして、デルタ行グループの終了時刻を利用します。 既定の継続時間は 0 分です。 100 万行がデルタ行グループに累積されると、1 行が単票格納に移行されます。その行に終了の印が付きます。  
  
DATA_COMPRESSION  
   指定したテーブル、パーティション番号、またはパーティション範囲に、データ圧縮オプションを指定します。 次のオプションがあります。  
COLUMNSTORE  
   適用対象: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。 非クラスター化列ストア インデックスとクラスター化列ストア インデックスの両方を含む列ストア インデックスにのみ適用されます。 列ストアでは、既定値は、し、ほとんどのパフォーマンスの高い列ストア圧縮で圧縮することを指定します。 これは、一般的な選択肢です。  
  
COLUMNSTORE_ARCHIVE  
   適用対象: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。
非クラスター化列ストア インデックスとクラスター化列ストア インデックスの両方を含む列ストア インデックスにのみ適用されます。 COLUMNSTORE_ARCHIVE は、テーブルまたはパーティション サイズをより小さなサイズに圧縮します。 これは、保存用や、ストレージのサイズを減らす必要があり、しかも保存と取得に時間をかける余裕があるその他の状況で使用できます。  
  
 圧縮の詳細については、「[データ圧縮](../../relational-databases/data-compression/data-compression.md)」を参照してください。  
  
WHERE \<filter_expression> [ AND \<filter_expression> ] 適用対象: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
   フィルター述語が呼び出されると、インデックスに含める行を指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、フィルター選択されたインデックスのデータ行で、フィルター選択された統計情報を作成します。  
  
   フィルター述語では、単純な比較ロジックを使用します。 比較演算子では、NULL リテラルを使用する比較を実行できません。 代わりに、IS NULL 演算子と IS NOT NULL 演算子を使用します。  
  
   次に、`Production.BillOfMaterials` テーブルのフィルター述語の例をいくつか示します。  
   `WHERE StartDate > '20000101' AND EndDate <= '20000630'`    
   `WHERE ComponentID IN (533, 324, 753)`  
   `WHERE StartDate IN ('20000404', '20000905') AND EndDate IS NOT NULL`  
   
   フィルター選択されたインデックスについては、「[フィルター選択されたインデックスの作成](../../relational-databases/indexes/create-filtered-indexes.md)」を参照してください。  
  
ON  
   これらのオプションによって、インデックスが作成されるファイル グループが指定されます。  
  
*partition_scheme_name* **(** *column_name* **)**  
   ファイル グループを定義するパーティション構成を指定します。このファイル グループは、パーティション インデックスのパーティションのマップ先となります。 [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md) を実行し、パーティション構成がデータベース内に存在するようにする必要があります。 
   *column_name* には、パーティション インデックスがパーティション分割される対象の列を指定します。 この列は、*partition_scheme_name* で使用されているパーティション関数の引数のデータ型、長さ、有効桁数に一致する必要があります。 *column_name* は、インデックス定義で指定されている列に限定されません。 列ストア インデックスをパーティション分割するとき、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では、まだ指定されていない場合、パーティション分割列がインデックスの列として追加されます。  
   *partition_scheme_name* または *filegroup* が指定されないまま、テーブルがパーティション分割されると、インデックスは基になるテーブルと同じパーティション分割列を使用して、同じパーティション構造に配置されます。  
   パーティション テーブルの列ストア インデックスは、パーティション固定にする必要があります。  
   インデックスのパーティション分割の詳細については、「[パーティション テーブルとパーティション インデックス](../../relational-databases/partitions/partitioned-tables-and-indexes.md)」を参照してください。  

*filegroup_name*  
   インデックスを作成するファイル グループ名を指定します。 *filegroup_name* の指定がなく、テーブルがパーティション分割されていない場合は、基になるテーブルと同じファイル グループが使用されます。 ファイル グループは既に存在している必要があります。  
 
**"** default **"**  
既定のファイル グループに、指定したインデックスを作成します。  
  
この文脈での default という語はキーワードではありません。 default は、既定ファイル グループの識別子なので、ON **"** default **"** または ON **[** default **]** のように区切る必要があります。 "default" を指定する場合は、現在のセッションに対して QUOTED_IDENTIFIER オプションが ON である必要があります。 これが既定の設定です。 詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
##  <a name="Permissions"></a> Permissions  
 テーブルに対する ALTER 権限が必要です。  
  
##  <a name="GenRemarks"></a> 全般的な解説  
 列ストア インデックスは一時テーブルに作成できます。 テーブルが削除されるかセッションが終了すると、インデックスも削除されます。  
 
## <a name="filtered-indexes"></a>フィルター選択されたインデックス  
フィルター選択されたインデックスは、最適化された非クラスター化インデックスであり、テーブルから選択する行の少ないクエリに適しています。 フィルター選択されたインデックスは、フィルター述語を使用してテーブル内の一部のデータにインデックスを作成します。 フィルター選択されたインデックスを適切に設計すると、クエリのパフォーマンスを向上させ、ストレージ コストとメンテナンス コストを削減することができます。  
  
### <a name="required-set-options-for-filtered-indexes"></a>フィルター選択されたインデックスに必要な SET オプション  
次の条件のいずれかに該当する場合、"必要な値" 列の SET オプションが必要となります。  
- フィルター選択されたインデックスを作成するとき。  
- INSERT、UPDATE、DELETE、MERGE のいずれかの操作で、フィルター選択されたインデックスのデータを変更するとき。  
- クエリ オプティマイザーで、クエリ プランの生成にフィルター選択されたインデックスが使用されるとき。  
  
    |SET オプション|必要な値|既定のサーバー値|既定<br /><br /> OLE DB および ODBC 値|既定<br /><br /> DB-Library 値|  
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
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)] によりエラーが生成され、インデックスのデータを変更していた INSERT ステートメント、UPDATE ステートメント、DELETE ステートメント、または MERGE ステートメントがロールバックされます。  
  
-   Transact-SQL ステートメントの実行プランで、クエリ オプティマイザーがインデックスを無視します。  
  
 フィルター選択されたインデックスについて詳しくは、「[フィルター選択されたインデックスの作成](../../relational-databases/indexes/create-filtered-indexes.md)」をご覧ください。 
  
##  <a name="LimitRest"></a> 制限事項と制約事項  

**列ストア インデックスの各列は、次の一般的なビジネス データ型のいずれかである必要があります。** 
-   datetimeoffset [ ( *n* ) ]  
-   datetime2 [ ( *n* ) ]  
-   DATETIME  
-   smalldatetime  
-   日付  
-   time [ ( *n* ) ]  
-   float [ ( *n* ) ]  
-   real [ ( *n* ) ]  
-   decimal [ ( *precision* [ *, scale* ] **)** ]
-   numeric [ ( *precision* [ *, scale* ] **)** ]    
-   money  
-   SMALLMONEY  
-   BIGINT  
-   ssNoversion  
-   smallint  
-   TINYINT  
-   bit  
-   nvarchar [ ( *n* ) ] 
-   nvarchar(max)  (クラスタ化列ストア インデックスのみの [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] および Premium 層、Standard 層 (S3 以上)、すべての VCore サービス層に適用されます)   
-   nchar [ ( *n* ) ]  
-   varchar [ ( *n* ) ]  
-   varchar(max)  (クラスタ化列ストア インデックスのみの [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] および Premium 層、Standard 層 (S3 以上)、すべての VCore サービス層に適用されます)
-   char [ ( *n* ) ]  
-   varbinary [ ( *n* ) ] 
-   varbinary (max)  (クラスタ化列ストア インデックスのみの [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] および Premium 層、Standard 層 (S3 以上)、すべての VCore サービス層の Azure SQL Database に適用されます)
-   binary [ ( *n* ) ]  
-   uniqueidentifier ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 以降に適用)
  
基になるテーブルに列ストア インデックスはサポートされていないデータ型の列がある場合は、非クラスター化列ストア インデックスには、その列を省略する必要があります。  
  
**以下のいずれかのデータ型を使用する列は、列ストア インデックスに含めることができません。**
-   ntext、text、image  
-   nvarchar(max)、varchar(max)、varbinary(max) ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以前のバージョンに適用、非クラスター化列ストア インデックス) 
-   rowversion (timestamp)  
-   sql_variant  
-   CLR 型 (hierarchyid 型および空間型)  
-   xml  
-   uniqueidentifier ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] に適用)  

**非クラスター化列ストア インデックス**
-   1,024 より多い列を持つことはできません。
-   制約ベースのインデックスとして作成することはできません。 列ストア インデックスを持つテーブルには、一意の制約、主キー制約、外部キー制約を含めることができます。 制約は常に行ストア インデックスで適用されます。 列ストア (クラスター化または非クラスター化) インデックスで制約を適用することはできません。
-   ビューまたはインデックス付きビュー上では作成できません。  
-   スパース列を含めることはできません。  
-   **ALTER INDEX** ステートメントを使用して変更することはできません。 非クラスター化インデックスを変更するには、列ストア インデックスを削除してから再作成する必要があります。 **ALTER INDEX** を使用し、列ストア インデックスを無効にし、再構築できます。  
-   **INCLUDE** キーワードを使用して作成することはできません。  
-   インデックスを並べ替えるための **ASC** または **DESC** キーワードを含めることはできません。 列ストア インデックスは、圧縮アルゴリズムに従って順序付けされます。 並べ替えを行うと、パフォーマンス上の利点の多くが無効になります。  
-   非クラスター化列ストア インデックスに型が nvarchar(max)、varchar(max)、varbinary(max) のラージ オブジェクト (LOB) 列を含めることはできません。 Premium 層、Standard 層 (S3 以上)、およびすべての VCore サービス層で構成されている [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] バージョンと Azure SQL Database 以降で、クラスター化列ストア インデックスのみ LOB 型をサポートしています。 以前のバージョンでは、クラスター化列ストア インデックスと非クラスター化列ストア インデックスで LOB 型をサポートしていません。


 **列ストア インデックスと同時に使用できない機能:**  
-   計算列。 SQL Server 2017 以降、クラスター化列ストア インデックスに、保存されない計算列を含めることができます。 ただし、SQL Server 2017 では、クラスター化列ストア インデックスに、保存される計算列を含めることができません。計算列で非クラスター化インデックスを作成することはできません。 
-   ページと行の圧縮、**vardecimal** ストレージ形式 (列ストア インデックスは既に別の形式で圧縮されているため)。  
-   のレプリケーション  
-   Filestream

クラスター化列ストア インデックスを使用しているテーブルでは、カーソルやトリガーは使用できません。 この制限は、非クラスター化列ストア インデックスには適用されません。非クラスター化列ストア インデックスを使用しているテーブルでは、カーソルとトリガーを使用できます。

**SQL Server 2014 固有の制限事項**  
以下の制限は SQL Server 2014 にのみ適用されます。 このリリースでは、更新可能なクラスター化列ストア インデックスを導入しました。 非クラスター化列ストア インデックスは引き続き読み取り専用でした。  

-   変更の追跡。 読み取り専用のため、非クラスター化列ストア インデックス (NCCI) で変更履歴を使用することはできません。 クラスター化列ストア インデックス (CCI) では機能します。  
-   変更データ キャプチャ。 読み取り専用のため、非クラスター化列ストア インデックス (NCCI) に変更データ キャプチャを使用することはできません。 クラスター化列ストア インデックス (CCI) では機能します。  
-   読み取り可能セカンダリ。 AlwaysOn 可用性グループの読み取り可能セカンダリからクラスター化列ストア インデックス (CCI) にアクセスすることはできません。  読み取り可能セカンダリから非クラスター化列ストア インデックス (NCCI) にアクセスできます。  
-   複数のアクティブな結果セット (MARS)。 SQL Server 2014 では、列ストア インデックスに読み取り専用で接続するために MARS が使用されます。    ただし、SQL Server 2014 では、列ストア インデックスを含むテーブルで DML (データ操作言語) を同時操作するとき、MARS を利用できません。 その場合、 SQL Server は接続を強制終了し、トランザクションを中止します。  
  
 列ストア インデックスのパフォーマンス上の利点と制限の詳細については、「[列ストア インデックス - 概要](../../relational-databases/indexes/columnstore-indexes-overview.md)」をご覧ください。
  
##  <a name="Metadata"></a> メタデータ  
 列ストア インデックス内のすべての列は、付加列としてメタデータに格納されます。 列ストア インデックスにキー列はありません。 列ストア インデックスに関する情報は、次のシステム ビューによって提供されます。  
  
-   [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
-   [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
-   [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)  
-   [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
-   [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
-   [sys.column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)  

##  <a name="convert"></a> 行ストア テーブルを列ストアに変換する例  
  
### <a name="a-convert-a-heap-to-a-clustered-columnstore-index"></a>A. ヒープをクラスター化列ストア インデックスに変換する  
 この例では、テーブルをヒープとして作成してから、cci_Simple という名前のクラスター化 columnstore インデックスに変換します。 こうすることで、テーブル全体のストレージが行ストアから列ストアに変更されます。  
  
```  
CREATE TABLE SimpleTable(  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
GO  
CREATE CLUSTERED COLUMNSTORE INDEX cci_Simple ON SimpleTable;  
GO  
```  
  
### <a name="b-convert-a-clustered-index-to-a-clustered-columnstore-index-with-the-same-name"></a>B. クラスター化インデックスを同じ名前のクラスター化列ストア インデックスに変換する  
 この例では、クラスター化インデックスを持つテーブルを作成し、クラスター化インデックスをクラスター化列ストア インデックスに変換する構文を示します。 こうすることで、テーブル全体のストレージが行ストアから列ストアに変更されます。  
  
```  
CREATE TABLE SimpleTable (  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
GO  
CREATE CLUSTERED INDEX cl_simple ON SimpleTable (ProductKey);  
GO  
CREATE CLUSTERED COLUMNSTORE INDEX cl_simple ON SimpleTable  
WITH (DROP_EXISTING = ON);  
GO  
```  
  
### <a name="c-handle-nonclustered-indexes-when-converting-a-rowstore-table-to-a-columnstore-index"></a>C. 行ストア テーブルを列ストア インデックスに変換するときに、非クラスター化インデックスを処理します。  
 この例では、行ストア テーブルを列ストア インデックスに変換するときに、非クラスター化インデックスを処理する方法を示します。 実際には、以降では、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 特別な操作は不要です。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は新しいクラスター化列ストア インデックスで非クラスター化インデックスを自動的に定義し、再構築します。  
  
 非クラスター化インデックスを削除する場合は、列ストア インデックスを作成する前に、DROP INDEX ステートメントを使用します。 DROP EXISTING オプションは、変換されるクラスター化インデックスのみを削除します。 非クラスター化インデックスは削除されません。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] と [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] では、列ストア インデックスで非クラスター化インデックスを作成できませんでした。 この例は、どのようにを列ストア インデックスを作成する前に、非クラスター化インデックスを削除する必要する以前のリリースで表示されます。  
  
```  
  
--Create the table for use with this example.  
CREATE TABLE SimpleTable (  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
GO  
  
--Create two nonclustered indexes for use with this example  
CREATE INDEX nc1_simple ON SimpleTable (OrderDateKey);  
CREATE INDEX nc2_simple ON SimpleTable (DueDateKey);   
GO  
  
--SQL Server 2012 and SQL Server 2014: you need to drop the nonclustered indexes  
--in order to create the columnstore index.   
  
DROP INDEX SimpleTable.nc1_simple;  
DROP INDEX SimpleTable.nc2_simple;  
  
--Convert the rowstore table to a columnstore index.  
CREATE CLUSTERED COLUMNSTORE INDEX cci_simple ON SimpleTable;   
GO  
  
```  
  
### <a name="d-convert-a-large-fact-table-from-rowstore-to-columnstore"></a>D. 大きいファクト テーブルを行ストアから列ストアに変換する  
 この例では、大きいファクト テーブルを行ストア テーブルから列ストア テーブルに変換する方法を説明します。  
  
 行ストア テーブルを列ストア テーブルに変換するには、次の手順に従います。  
  
1.  まず、この例で使用する小さいテーブルを作成します。  
  
    ```  
    --Create a rowstore table with a clustered index and a non-clustered index.  
    CREATE TABLE MyFactTable (  
        ProductKey [int] NOT NULL,  
        OrderDateKey [int] NOT NULL,  
         DueDateKey [int] NOT NULL,  
         ShipDateKey [int] NOT NULL )  
    )  
    WITH (  
        CLUSTERED INDEX ( ProductKey )  
    );  
  
    --Add a non-clustered index.  
    CREATE INDEX my_index ON MyFactTable ( ProductKey, OrderDateKey );  
    ```  
  
2.  行ストア テーブルからすべての非クラスター化インデックスを削除します。  
  
    ```  
    --Drop all non-clustered indexes  
    DROP INDEX my_index ON MyFactTable;  
    ```  
  
3.  クラスター化インデックスを削除します。  
  
    -   これは、クラスター化列ストア インデックスに変換されるときにインデックスに新しい名前を指定する場合にのみ行ってください。 クラスター化インデックスを削除しない場合は、新しいクラスター化列ストア インデックスに同じ名前が付けられます。  
  
        > [!NOTE]  
        >  インデックスの名前に自分の名前を使用すると記憶しやすくなります。 すべての行ストア クラスター化インデックスは、既定の名前である 'ClusteredIndex_\<GUID>' を使用します。  
  
    ```  
    --Process for dropping a clustered index.  
    --First, look up the name of the clustered rowstore index.  
    --Clustered rowstore indexes always use the DEFAULT name ‘ClusteredIndex_<GUID>’.  
    SELECT i.name   
    FROM sys.indexes i   
    JOIN sys.tables t  
    ON ( i.type_desc = 'CLUSTERED' ) WHERE t.name = 'MyFactTable';  
  
    --Drop the clustered rowstore index.  
    DROP INDEX ClusteredIndex_d473567f7ea04d7aafcac5364c241e09 ON MyDimTable;  
    ```  
  
4.  行ストア テーブルを、クラスター化列ストア インデックスを持つ列ストア テーブルに変換します。  
  
    ```  
    --Option 1: Convert to columnstore and name the new clustered columnstore index MyCCI.  
    CREATE CLUSTERED COLUMNSTORE INDEX MyCCI ON MyFactTable;  
  
    --Option 2: Convert to columnstore and use the rowstore clustered   
    --index name for the columnstore clustered index name.  
    --First, look up the name of the clustered rowstore index.  
    SELECT i.name   
    FROM sys.indexes i  
    JOIN sys.tables t   
    ON ( i.type_desc = 'CLUSTERED' )  
    WHERE t.name = 'MyFactTable';  
  
    --Second, create the clustered columnstore index and   
    --Replace ClusteredIndex_d473567f7ea04d7aafcac5364c241e09  
    --with the name of your clustered index.  
    CREATE CLUSTERED COLUMNSTORE INDEX   
    ClusteredIndex_d473567f7ea04d7aafcac5364c241e09  
     ON MyFactTable  
    WITH DROP_EXISTING = ON;  
    ```  
  
### <a name="e-convert-a-columnstore-table-to-a-rowstore-table-with-a-clustered-index"></a>E. 列ストア テーブルをクラスター化インデックスを持つ行ストア テーブルに変換する  
 列ストア テーブルをクラスター化インデックスを持つ行ストア テーブルに変換するには、CREATE INDEX ステートメントと DROP_EXISTING オプションを使用します。  
  
```  
CREATE CLUSTERED INDEX ci_MyTable   
ON MyFactTable  
WITH ( DROP EXISTING = ON );  
```  
  
### <a name="f-convert-a-columnstore-table-to-a-rowstore-heap"></a>F. 列ストア テーブルを行ストア ヒープに変換する  
 列ストア テーブルを行ストア ヒープに変換するには、クラスター化列ストア インデックスを削除します。  
  
```  
DROP INDEX MyCCI   
ON MyFactTable;  
```  
  

### <a name="g-defragment-by-rebuilding-the-entire-clustered-columnstore-index"></a>G. 全体のクラスター化列ストア インデックスを再構築での断片化を解消します。  
   対象: SQL Server 2014  
  
 クラスター化列ストア インデックス全体を再構築するには、2 つの方法があります。 CREATE CLUSTERED COLUMNSTORE INDEX か [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md) と REBUILD オプションを使用できます。 どちらの方法も、同じ結果が得られます。  
  
> [!NOTE]  
>  SQL Server 2016 以降、この例で説明した方法で再構築せず、ALTER INDEX REORGANIZE を使用します。  
  
```  
--Determine the Clustered Columnstore Index name of MyDimTable.  
SELECT i.object_id, i.name, t.object_id, t.name   
FROM sys.indexes i   
JOIN sys.tables t  
ON (i.type_desc = 'CLUSTERED COLUMNSTORE')  
WHERE t.name = 'RowstoreDimTable';  
  
--Rebuild the entire index by using CREATE CLUSTERED INDEX.  
CREATE CLUSTERED COLUMNSTORE INDEX my_CCI   
ON MyFactTable  
WITH ( DROP_EXISTING = ON );  
  
--Rebuild the entire index by using ALTER INDEX and the REBUILD option.  
ALTER INDEX my_CCI  
ON MyFactTable  
REBUILD PARTITION = ALL  
WITH ( DROP_EXISTING = ON );  
  
```  
  
##  <a name="nonclustered"></a> 非クラスター化列ストア インデックスの例  
  
### <a name="a-create-a-columnstore-index-as-a-secondary-index-on-a-rowstore-table"></a>A. 行ストア テーブルのセカンダリ インデックスとして列ストア インデックスを作成します。  
 この例では、行ストア テーブルに非クラスター化列ストア インデックスを作成します。 このような状況では、1 つだけの列ストア インデックスを作成できます。 列ストア インデックスでは、行ストア テーブル内のデータのコピーが含まれているために、追加のストレージが必要です。 この例では、単純なテーブルとクラスター化インデックスを作成し、非クラスター化列ストア インデックスを作成する構文を次に示します。  
  
```  
CREATE TABLE SimpleTable  
(ProductKey [int] NOT NULL,   
OrderDateKey [int] NOT NULL,   
DueDateKey [int] NOT NULL,   
ShipDateKey [int] NOT NULL);  
GO  
CREATE CLUSTERED INDEX cl_simple ON SimpleTable (ProductKey);  
GO  
CREATE NONCLUSTERED COLUMNSTORE INDEX csindx_simple  
ON SimpleTable  
(OrderDateKey, DueDateKey, ShipDateKey);  
GO  
```  
  
### <a name="b-create-a-simple-nonclustered-columnstore-index-using-all-options"></a>B. すべてのオプションを使用して、単純な非クラスター化 columnstore インデックスを作成します。  
 次の例は、すべてのオプションを使用して非クラスター化列ストア インデックスを作成する構文を示しています。  
  
```  
CREATE NONCLUSTERED COLUMNSTORE INDEX csindx_simple  
ON SimpleTable  
(OrderDateKey, DueDateKey, ShipDateKey)  
WITH (DROP_EXISTING =  ON,   
    MAXDOP = 2)  
ON "default"  
GO  
```  
  
 パーティション テーブルを使用した、より複雑な例については、「[列ストア インデックス - 概要](../../relational-databases/indexes/columnstore-indexes-overview.md)」をご覧ください。  
  
### <a name="c-create-a-nonclustered-columnstore-index-with-a-filtered-predicate"></a>C. フィルター選択された述語で、非クラスター化列ストア インデックスを作成します。  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースの Production.BillOfMaterials テーブルにフィルター選択された非クラスター化列ストア インデックスを作成します。 フィルター述語では、フィルター選択されたインデックスに非キー列を含めることができます。 この例の述語では、EndDate が NULL 以外の行だけを選択します。  
  
```  
IF EXISTS (SELECT name FROM sys.indexes  
    WHERE name = N'FIBillOfMaterialsWithEndDate'   
    AND object_id = OBJECT_ID(N'Production.BillOfMaterials'))  
DROP INDEX FIBillOfMaterialsWithEndDate  
    ON Production.BillOfMaterials;  
GO  
CREATE NONCLUSTERED COLUMNSTORE INDEX "FIBillOfMaterialsWithEndDate"  
    ON Production.BillOfMaterials (ComponentID, StartDate)  
    WHERE EndDate IS NOT NULL;  
  
```  
  
###  <a name="ncDML"></a> D. 非クラスター化列ストア インデックス内のデータを変更する  
   適用対象: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]。
  
 テーブルに非クラスター化列ストア インデックスを作成すると、そのテーブル内のデータは変更できなくなります。 INSERT、UPDATE、DELETE、または MERGE を使用するクエリは失敗し、エラー メッセージが返されます。 テーブル内のデータを追加または変更するには、次のいずれかの操作を行います。  
  
-   列ストア インデックスを無効にするか削除します。 その後、テーブル内のデータを更新できます。 列ストア インデックスを無効にすると、データの更新の終了時に列ストア インデックスを再構築できます。 例を次に示します。  
  
    ```  
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;  
    -- update mytable --  
    ALTER INDEX mycolumnstoreindex on mytable REBUILD  
    ```  
  
-   列ストア インデックスのないステージング テーブルにデータを読み込みます。 ステージング テーブルで列ストア インデックスを構築します。 ステージング テーブルをメイン テーブルの空のパーティションに切り替えます。  
  
-   列ストア インデックスを持つテーブルから空のステージング テーブルにパーティションを切り替えます。 ステージング テーブルに列ストア インデックスがある場合は、列ストア インデックスを無効にします。 更新を実行します。 列ストア インデックスを構築 (または再構築) します。 ステージング テーブルを切り替えて、メイン テーブルの (空になった) パーティションに戻します。  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-change-a-clustered-index-to-a-clustered-columnstore-index"></a>A. クラスター化インデックスをクラスター化列ストア インデックスに変換する  
 DROP_EXISTING = ON で CREATE CLUSTERED COLUMNSTORE INDEX ステートメントを使用すると、次のことができます。  
  
-   クラスター化インデックスをクラスター化列ストア インデックスに変換します。  
  
-   クラスター化列ストア インデックスを再構築します。  
  
 この例では、クラスター化インデックスを含む列ストア テーブルとして xDimProduct テーブルを作成し、CREATE CLUSTERED COLUMNSTORE INDEX を使用して行ストア テーブルから列ストア テーブルにテーブルを変更します。  
  
```  
-- Uses AdventureWorks  
  
IF EXISTS (SELECT name FROM sys.tables  
    WHERE name = N'xDimProduct'  
    AND object_id = OBJECT_ID (N'xDimProduct'))  
DROP TABLE xDimProduct;  
  
--Create a distributed table with a clustered index.  
CREATE TABLE xDimProduct (ProductKey, ProductAlternateKey, ProductSubcategoryKey)  
WITH ( DISTRIBUTION = HASH(ProductKey),  
    CLUSTERED INDEX (ProductKey) )  
AS SELECT ProductKey, ProductAlternateKey, ProductSubcategoryKey FROM DimProduct;  
  
--Change the existing clustered index   
--to a clustered columnstore index with the same name.  
--Look up the name of the index before running this statement.  
CREATE CLUSTERED COLUMNSTORE INDEX <index_name>   
ON xdimProduct   
WITH ( DROP_EXISTING = ON );  
```  
  
### <a name="b-rebuild-a-clustered-columnstore-index"></a>B. クラスター化列ストア インデックスを再構築する  
 この例は先の例を元に作られています。CREATE CLUSTERED COLUMNSTORE INDEX を使用し、cci_xDimProduct という名前の既存のクラスター化列ストア インデックスを再構築します。  
  
```  
--Rebuild the existing clustered columnstore index.  
CREATE CLUSTERED COLUMNSTORE INDEX cci_xDimProduct   
ON xdimProduct   
WITH ( DROP_EXISTING = ON );  
```  
  
### <a name="c-change-the-name-of-a-clustered-columnstore-index"></a>C. クラスター化列ストア インデックスの名前を変更する  
 クラスター化列ストア インデックスの名前を変更するには、既存のクラスター化列ストア インデックスを削除し、新しい名前でインデックスを再作成します。  
  
 この操作は小規模のテーブルかからのテーブルでのみ行うことをお勧めします。 大規模なクラスター化列ストア インデックスを削除し、別の名前で再構築すると長い時間がかかります。  
  
 この例では、先の例の cci_xDimProduct という名前のクラスター化列ストア インデックスを使用します。cci_xDimProduct を削除し、mycci_xDimProduct という名前で再作成します。  
  
```  
--For illustration purposes, drop the clustered columnstore index.   
--The table continues to be distributed, but changes to a heap.  
DROP INDEX cci_xdimProduct ON xDimProduct;  
  
--Create a clustered index with a new name, mycci_xDimProduct.  
CREATE CLUSTERED COLUMNSTORE INDEX mycci_xDimProduct  
ON xdimProduct  
WITH ( DROP_EXISTING = OFF );  
```  
  
### <a name="d-convert-a-columnstore-table-to-a-rowstore-table-with-a-clustered-index"></a>D. 列ストア テーブルをクラスター化インデックスを持つ行ストア テーブルに変換する  
 クラスター化列ストア インデックスを削除し、クラスター化インデックスを作成するという状況もあります。 その場合、行ストア形式でテーブルを保存します。 この例では、クラスター化インデックスが含まれる行ストア テーブルに列ストア テーブルを変換します。同じ名前が使用されます。 データは何も失われません。 すべてのデータが行ストア テーブルに入り、一覧の列はクラスター化インデックスのキー列になります。  
  
```  
--Drop the clustered columnstore index and create a clustered rowstore index.   
--All of the columns are stored in the rowstore clustered index.   
--The columns listed are the included columns in the index.  
CREATE CLUSTERED INDEX cci_xDimProduct    
ON xdimProduct (ProductKey, ProductAlternateKey, ProductSubcategoryKey, WeightUnitMeasureCode)  
WITH ( DROP_EXISTING = ON);  
  
```  
  
### <a name="e-convert-a-columnstore-table-back-to-a-rowstore-heap"></a>E. 列ストア テーブルを行ストア ヒープに戻す  
 [DROP INDEX (SQL Server PDW)](http://msdn.microsoft.com/en-us/f59cab43-9f40-41b4-bfdb-d90e80e9bf32) を使用し、クラスター化列ストア インデックスを削除し、テーブルを行ストア ヒープに変換します。 この例では、cci_xDimProduct テーブルを行ストア ヒープに変換します。 テーブルは引き続き配布されますが、ヒープとして保存されます。  
  
```  
--Drop the clustered columnstore index. The table continues to be distributed, but changes to a heap.  
DROP INDEX cci_xdimProduct ON xdimProduct;  
```  

