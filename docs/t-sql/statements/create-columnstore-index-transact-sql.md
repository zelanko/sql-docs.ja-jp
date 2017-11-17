---
title: "列ストア インデックス (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 0fb8883678dad7a62cac9c2109b093ee79e27b27
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="create-columnstore-index-transact-sql"></a>CREATE COLUMNSTORE INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

行ストア テーブルをクラスター化列ストア インデックスに変換するか、非クラスター化列ストア インデックスを作成します。 OLTP ワークロードに効率的にリアルタイムの経営分析を実行する、またはデータ ウェアハウスのワークロードのデータの圧縮とクエリのパフォーマンスを向上させるためには、列ストア インデックスを使用します。  
  
> [!NOTE]  
>  以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]、クラスター化列ストア インデックスとテーブルを作成することができます。   まず行ストア テーブルを作成し、クラスター化列ストア インデックスに変換する必要は不要になったです。  
  
例に進みます。  
-   [行ストア テーブルを列ストアに変換するための例](../../t-sql/statements/create-columnstore-index-transact-sql.md#convert)  
-   [非クラスター化列ストア インデックスの例](../../t-sql/statements/create-columnstore-index-transact-sql.md#nonclustered)  
  
シナリオを参照してください。  
-   [リアルタイム運用分析の列ストア インデックス](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)  
-   [データ ウェアハウスの列ストア インデックス](../../relational-databases/indexes/columnstore-indexes-data-warehouse.md)  
  
詳細情報：  
-   [列ストア インデックス ガイド](../../relational-databases/indexes/columnstore-indexes-overview.md)  
-   [列ストア インデックス機能の概要](../../relational-databases/indexes/columnstore-indexes-what-s-new.md)  
  
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
すべてのデータを圧縮し、列によって格納されるクラスター化列ストア インデックスを作成します。 インデックスにはテーブル内の列がすべて含まれ、テーブル全体が格納されます。 既存のテーブルがヒープまたはクラスター化インデックスの場合は、テーブルはクラスター化列ストア インデックスに変換されます。 テーブルは既にクラスター化列ストア インデックスとして格納されている場合は、既存のインデックスが削除され、再構築されます。  
  
*index_name*  
新しいインデックスの名前を指定します。  
  
テーブルは、クラスター化列ストア インデックスを既に持っている場合、既存のインデックスと同じ名前を指定できます。 または DROP EXISTING オプションを使用するには新しい名前を指定します。  
  
ON [*database_name*です。 [*schema_name* ] です。 | *schema_name*です。 *table_name*  
   クラスター化列ストア インデックスとして格納するテーブルの 1 部、2 部、または 3 部構成の名前を指定します。 場合は、テーブルがヒープまたはクラスター化インデックス、テーブルは行ストアから列ストアに変換します。 テーブルが列ストアで既に場合、このステートメントには、クラスター化列ストア インデックスが再構築します。  
  
のすべてのメンションを  
DROP_EXISTING = [オフ] |ON  
   DROP_EXISTING = ON を使用する既存のクラスター化列ストア インデックスを削除して、新しい列ストア インデックスを作成します。  

   既定では、DROP_EXISTING = OFF インデックス名は、既存の名前と同じが必要です。 指定したインデックス名が既に存在するをエラーが発生します。  
  
MAXDOP = *max_degree_of_parallelism*  
   インデックス操作の間、既存の "並列処理の最大限度" サーバー構成をオーバーライドします。 並列プランの実行で使用されるプロセッサ数を制限するには、MAXDOP を使用します。 最大数は 64 プロセッサです。  
  
   *max_degree_of_parallelism*値を指定できます。  
   - 1 - 並列プラン生成を抑制します。  
   - \>1-指定した数以内の現在のシステム ワークロードに基づいて並列インデックス操作で使用されるプロセッサの最大数を制限します。 たとえば、MAXDOP = 4、使用されるプロセッサの数が 4 個以下です。  
   - 0 (既定) - 現在のシステム ワークロードに基づいて、実際の数以下のプロセッサを使用します。  
  
   詳細については、次を参照してください。 [max degree of parallelism サーバー構成オプションを構成する](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)、および[並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)です。  
 
COMPRESSION_DELAY = **0** | *遅延*[分]  
   適用されます:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。

   ディスク ベース テーブルの場合*遅延*SQL Server を使用すると、圧縮された行グループに圧縮できる前に、デルタ行グループで閉じられた状態で、デルタ行グループがある必要があります (分) の最小数を指定します。 ディスク ベース テーブルの挿入を追跡および更新されないため時間個々 の行に SQL Server を適用の遅延が閉じられた状態で、デルタ行グループ。  
   既定値は、0 分です。  
   COMPRESSION_DELAY を使用する場合の推奨事項を参照してください[リアルタイム運用分析の列ストアの概要](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)です。  
  
DATA_COMPRESSION = COLUMNSTORE |COLUMNSTORE_ARCHIVE  
   適用されます:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。
指定したテーブル、パーティション番号、またはパーティション範囲に、データ圧縮オプションを指定します。 次のオプションがあります。   
COLUMNSTORE  
   列ストアでは、既定値は、し、ほとんどのパフォーマンスの高い列ストア圧縮で圧縮することを指定します。 これは、一般的な選択肢です。  
  
COLUMNSTORE_ARCHIVE  
   COLUMNSTORE_ARCHIVE をさらには、テーブルまたはパーティション サイズを小さく圧縮します。 などの状況をこのオプションを使用してアーカイブを記憶域のサイズを必要とし、保存と取得に多くの時間に余裕があることができます。  
  
   圧縮の詳細については、次を参照してください。[データ圧縮](../../relational-databases/data-compression/data-compression.md)です。  

ON  
   ON オプションを使用すると、パーティション構成、特定のファイル グループ、既定のファイル グループなど、データ ストレージのオプションを指定できます。 ON オプションを指定しない場合、インデックスは、既存のテーブルの設定パーティションまたはファイル グループの設定を使用します。  
  
   *partition_scheme_name* **(** *column_name* **)**  
   テーブルのパーティション構成を指定します。 パーティション構成は既にデータベースに存在している必要があります。 パーティション構成を作成するを参照してください。 [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md)です。  
 
   *column_name*パーティション インデックスがパーティション分割される対象の列を指定します。 この列はデータ型、長さ、一致する必要があります関数および有効桁数の引数のパーティションを*partition_scheme_name*を使用しています。  

   *filegroup_name*  
   クラスター化列ストア インデックスを格納するファイル グループを指定します。 位置の指定がなく、テーブルがパーティション分割されていない場合は、基になるテーブルまたはビューと同じファイル グループが使用されます。 ファイル グループは既に存在している必要があります。  

   **"**既定**"**  
   既定のファイル グループに、インデックスを作成するには、"default"または [既定] を使用します。  
  
   "default" を指定する場合は、現在のセッションに対して QUOTED_IDENTIFIER オプションが ON である必要があります。 QUOTED_IDENTIFIER は既定で ON です。 詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
[非クラスター化] 列ストア インデックスを作成します。  
行ストア テーブルにメモリ内の非クラスター化列ストア インデックスを作成、ヒープまたはクラスター化インデックスとして格納します。 インデックスでは、フィルター選択された条件し、基になるテーブルの列のすべてを含める必要はありません。 列ストア インデックスでは、データのコピーを保存するには、十分な領域が必要です。 更新可能であるし、基になるテーブルが変更されるとは更新します。 クラスター化インデックスに非クラスター化列ストア インデックスでは、リアルタイム分析の機能を使用できます。  
  
*index_name*  
   インデックスの名前を指定します。 *index_name*テーブル内で一意である必要がありますが、データベース内で一意にする必要はありません。 インデックス名の規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 **(** *列*[ **、**.*n* ] **)**  
    格納する列を指定します。 非クラスター化列ストア インデックスは、1,024年列に制限されます。  
   各列は、列ストア インデックスでサポートされているデータ型である必要があります。 参照してください[制限事項と制約](../../t-sql/statements/create-columnstore-index-transact-sql.md#LimitRest)サポートされるデータ型の一覧についてはします。  

ON [*database_name*です。 [*schema_name* ] です。 | *schema_name*です。 *table_name*  
   1 部、2 部、またはインデックスを含むテーブルの 3 部構成の名前を指定します。  

WITH DROP_EXISTING = [オフ] |ON  
   DROP_EXISTING = ON の既存のインデックスを削除および再構築します。 指定するインデックス名は、現在存在するインデックスと同じにする必要がありますが、インデックス定義は変更できます。 たとえば、異なる列またはインデックス オプションを指定できます。
  
   DROP_EXISTING = OFF を指定したインデックス名が既に存在する場合、エラーが表示されます。 DROP_EXISTING を使用してインデックスの種類を変更することはできません。 旧バージョンと互換性のある構文では、WITH DROP_EXISTING は WITH DROP_EXISTING = ON と同じです。  

MAXDOP = *max_degree_of_parallelism*  
   上書き、 [max degree of parallelism サーバー構成オプションを構成する](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)インデックス操作の実行中の構成オプション。 並列プランの実行で使用されるプロセッサ数を制限するには、MAXDOP を使用します。 最大数は 64 プロセッサです。  
  
   *max_degree_of_parallelism*値を指定できます。  
   - 1 - 並列プラン生成を抑制します。  
   - \>1-指定した数以内の現在のシステム ワークロードに基づいて並列インデックス操作で使用されるプロセッサの最大数を制限します。 たとえば、MAXDOP = 4、使用されるプロセッサの数が 4 個以下です。  
   - 0 (既定) - 現在のシステム ワークロードに基づいて、実際の数以下のプロセッサを使用します。  
  
   詳細については、「 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)」を参照してください。  
  
> [!NOTE]  
>  並列インデックス操作はすべてのエディションで使用できない[!INCLUDE[msC](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各エディションでサポートされる機能の一覧については、「[Editions and Supported Features for SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)」 (SQL Server 2016 のエディションとサポートされる機能) を参照してください。  
  
ONLINE = [ON |OFF]   
   適用されます: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]、非クラスター化列ストア インデックスのみにします。
オンラインのまま、非クラスター化列ストア インデックスとインデックスの新しいコピー中に使用できるをビルドすることを指定します。

   オフには、新しいコピーがビルド中には、インデックスが使用するために使用できないことを指定します。 これは、非クラスター化インデックスのみ、ベース テーブルが使用可能な非クラスター化列ストア インデックスのみが新しいインデックスが完了するまで、クエリを満たすために使用されません。 

COMPRESSION_DELAY = **0** | \<遅延 > [分]  
   適用されます:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。 
  
   どのくらいの時間行必要があります内にデルタ行グループが圧縮された行グループへの移行の対象となる下限の境界を指定します。 たとえば、顧客は、120 分間、行が変更されていない場合を使用することから単票形式のストレージ形式に圧縮の対象となるとことができます。 ディスク ベース テーブルに列ストア インデックスの場合は、行が挿入または更新されると、ときに時間を追跡しませんデルタ行グループが終了時間をプロキシとしての行の代わりに使用します。 既定の期間は、0 分です。 行はデルタ行グループで累積された行数を 100万と closed に設定されている列指向の記憶域に移行されます。  
  
DATA_COMPRESSION  
   指定したテーブル、パーティション番号、またはパーティション範囲に、データ圧縮オプションを指定します。 次のオプションがあります。  
COLUMNSTORE  
   適用されます:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。 非クラスター化列ストア インデックスとクラスター化列ストア インデックスの両方を含む列ストア インデックスにのみ適用されます。 列ストアでは、既定値は、し、ほとんどのパフォーマンスの高い列ストア圧縮で圧縮することを指定します。 これは、一般的な選択肢です。  
  
COLUMNSTORE_ARCHIVE  
   適用されます:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。
非クラスター化列ストア インデックスとクラスター化列ストア インデックスの両方を含む列ストア インデックスにのみ適用されます。 COLUMNSTORE_ARCHIVE をさらには、テーブルまたはパーティション サイズを小さく圧縮します。 これは、保存用や、ストレージのサイズを減らす必要があり、しかも保存と取得に時間をかける余裕があるその他の状況で使用できます。  
  
 圧縮の詳細については、次を参照してください。[データ圧縮](../../relational-databases/data-compression/data-compression.md)です。  
  
ここで\<filter_expression > [AND \<filter_expression >] に適用されます:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。
  
   フィルター述語が呼び出されると、インデックスに含める行を指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フィルター選択されたインデックス内のデータ行をフィルター選択された統計を作成します。  
  
   フィルター述語では、単純な比較ロジックを使用します。 比較演算子では、NULL リテラルを使用する比較を実行できません。 代わりに、IS NULL 演算子と IS NOT NULL 演算子を使用します。  
  
   次に、`Production.BillOfMaterials` テーブルのフィルター述語の例をいくつか示します。  
   `WHERE StartDate > '20000101' AND EndDate <= '20000630'`    
   `WHERE ComponentID IN (533, 324, 753)`  
   `WHERE StartDate IN ('20000404', '20000905') AND EndDate IS NOT NULL`  
   
   フィルター選択されたインデックスについては、次を参照してください。 [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)です。  
  
ON  
   これらのオプションは、インデックスが作成されるファイル グループを指定します。  
  
*partition_scheme_name* **(** *column_name* **)**  
   パーティション インデックスのパーティションのマップ先となるファイル グループを定義するパーティション構成を指定します。 パーティション構成は実行することによって、データベース内に存在する必要があります[CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md)です。 
   *column_name*パーティション インデックスがパーティション分割される対象の列を指定します。 この列はデータ型、長さ、一致する必要があります関数および有効桁数の引数のパーティションを*partition_scheme_name*を使用しています。 *column_name*インデックス定義内の列に限定されません。 列ストア インデックスをパーティション分割するとき、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では、まだ指定されていない場合、パーティション分割列がインデックスの列として追加されます。  
   場合*partition_scheme_name*または*filegroup*が指定されていないと、テーブルがパーティション分割、インデックスは基になるテーブルとして同じのパーティション分割列を使用して、同じパーティション構成に配置されます。  
   パーティション テーブルの列ストア インデックスは、パーティション固定にする必要があります。  
   インデックスのパーティション分割の詳細については、次を参照してください。 [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md)です。  

*filegroup_name*  
   インデックスを作成するファイル グループ名を指定します。 場合*filegroup_name*が指定されていないテーブルがパーティション分割されていないと、インデックスが、基になるテーブルと同じファイル グループを使用します。 ファイル グループは既に存在している必要があります。  
 
**"**既定**"**  
既定のファイル グループに、指定したインデックスを作成します。  
  
この文脈での default という語はキーワードではありません。 既定のファイル グループの識別子を指定しのように区切る必要があります**"**既定**"**または ON **[**既定**]**です。 "default" を指定する場合は、現在のセッションに対して QUOTED_IDENTIFIER オプションが ON である必要があります。 これが既定の設定です。 詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
##  <a name="Permissions"></a> アクセス許可  
 テーブルに対する ALTER 権限が必要です。  
  
##  <a name="GenRemarks"></a>全般的な解説  
 一時テーブルでは、列ストア インデックスを作成できます。 テーブルが削除されるかセッションが終了すると、インデックスも削除されます。  
 
## <a name="filtered-indexes"></a>フィルター選択されたインデックス  
フィルター選択されたインデックスは、最適化された非クラスター化インデックスであり、テーブルから選択する行の少ないクエリに適しています。 フィルター選択されたインデックスは、フィルター述語を使用してテーブル内の一部のデータにインデックスを作成します。 フィルター選択されたインデックスを適切に設計すると、クエリのパフォーマンスを向上させ、ストレージ コストとメンテナンス コストを削減することができます。  
  
### <a name="required-set-options-for-filtered-indexes"></a>フィルター選択されたインデックスに必要な SET オプション  
次の条件のいずれかに該当する場合、"必要な値" 列の SET オプションが必要となります。  
- フィルター選択されたインデックスを作成するとき。  
- INSERT、UPDATE、DELETE、MERGE のいずれかの操作で、フィルター選択されたインデックスのデータを変更するとき。  
- フィルター選択されたインデックスは、クエリ プランを生成するために、クエリ オプティマイザーによって使用されます。  
  
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
  
##  <a name="LimitRest"></a> 制限事項と制約事項  

**次の一般的なビジネス データ型の 1 つの列ストア インデックス内の各列があります。** 
-   datetimeoffset [(  *n*  )]  
-   datetime2 [(  *n*  )]  
-   datetime  
-   smalldatetime  
-   date  
-   時間 [(  *n*  )]  
-   float [(  *n*  )]  
-   real [(  *n*  )]  
-   decimal [(*精度*[ *、小数点以下桁数*] **)** ]
-   数値 [(*精度*[ *、小数点以下桁数*] **)** ]    
-   money  
-   smallmoney  
-   bigint  
-   int  
-   smallint  
-   tinyint  
-   bit  
-   nvarchar [(  *n*  )] 
-   nvarchar (max) (対象[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]およびクラスター化列ストア インデックスのみに Azure SQL データベース premium の価格レベルを)   
-   nchar [(  *n*  )]  
-   varchar [(  *n*  )]  
-   varchar (max) (対象[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]およびクラスター化列ストア インデックスのみに Azure SQL データベース premium の価格レベルを)
-   char [(  *n*  )]  
-   varbinary [(  *n*  )] 
-   varbinary (max) (対象[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]およびクラスター化列ストア インデックスのみに Azure SQL データベース premium の価格レベルを)
-   バイナリ [(  *n*  )]  
-   一意識別子 (対象[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]およびそれ以降)
  
基になるテーブルに列ストア インデックスはサポートされていないデータ型の列がある場合は、非クラスター化列ストア インデックスには、その列を省略する必要があります。  
  
**列ストア インデックスには、次のデータ型のいずれかを使用する列を含めることができません。**
-   ntext、text、image  
-   nvarchar (max)、varchar (max)、および varbinary (max) (対象[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以前のバージョン、および非クラスター化列ストア インデックス) 
-   rowversion (timestamp)  
-   sql_variant  
-   CLR 型 (hierarchyid 型および空間型)  
-   xml  
-   一意識別子 (対象[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)])  

**非クラスター化列ストア インデックス:**
-   1,024 より多い列を持つことはできません。  
-   非クラスター化列ストア インデックスを持つテーブルには一意の制約、主キー制約、または外部キー制約を含めることができますが、非クラスター化列ストア インデックスに制約を含めることはできません。  
-   ビューまたはインデックス付きビュー上では作成できません。  
-   スパース列を含めることはできません。  
-   使用して変更することはできません、 **ALTER INDEX**ステートメントです。 非クラスター化インデックスを変更するには、列ストア インデックスを削除してから再作成する必要があります。 使用することができます**ALTER INDEX**を無効にし、列ストア インデックスを再構築します。  
-   使用して作成することはできません、 **INCLUDE**キーワード。  
-   含めることはできません、 **ASC**または**DESC**インデックスを並べ替えるためのキーワードです。 列ストア インデックスは、圧縮アルゴリズムに従って順序付けされます。 並べ替えを行うと、パフォーマンス上の利点の多くが無効になります。  
-   型 nvarchar (max)、varchar (max)、および varbinary (max) のラージ オブジェクト (LOB) 列を非クラスター化列ストア インデックスに含めることはできません。 以降ではクラスター化列ストア インデックスは、LOB 型をサポート、専用[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]バージョンと Azure SQL データベースの premium 価格レベルで構成します。 以前のバージョンはサポートされていません LOB 型と非クラスター化列ストア インデックスに注意してください。


 **列ストア インデックスは、次の機能と組み合わせることはできません。**  
-   計算列。 SQL Server 2017 から始めて、クラスター化列ストア インデックスは保存されない計算列を含めることができます。 ただし、SQL Server 2017、クラスター化列ストア インデックスが保存される計算列を含めることはできませんし、計算列で非クラスター化インデックスを作成することはできません。 
-   ページおよび行の圧縮と**vardecimal**ストレージ形式の (列ストア インデックスは、異なる形式で既に圧縮)。  
-   レプリケーション  
-   Filestream

クラスター化列ストア インデックスを含むテーブルには、カーソルやトリガーを使うことはできません。 この制限は、非クラスター化列ストア インデックスには適用されません。非クラスター化列ストア インデックスを含むテーブルには、カーソルとトリガーを使用できます。

**SQL Server 2014 の具体的な制限事項**  
これらの制限は、SQL Server 2014 にのみ適用されます。 このリリースで更新可能なクラスター化列ストア インデックスが導入されました。 非クラスター化列ストア インデックスが読み取り専用でした。  

-   変更の追跡します。 変更は読み取り専用なので、非クラスター化列ストア インデックス (NCCI) で追跡を使用することはできません。 クラスター化列ストア インデックス (CCI) の使用します。  
-   変更データ キャプチャをします。 読み取り専用であるために、非クラスター化列ストア インデックス (NCCI) についてデータ キャプチャの変更を使用することはできません。 クラスター化列ストア インデックス (CCI) の使用します。  
-   読み取り可能セカンダリ。 クラスター化されたクラスター化列ストア インデックス (CCI) は、常に OnReadable 可用性グループの読み取り可能セカンダリからアクセスできません。  非クラスター化列ストア インデックス (NCCI) は、読み取り可能なセカンダリからアクセスできます。  
-   複数のアクティブな結果セット (MARS)。 SQL Server 2014 では、列ストア インデックスを持つテーブルへの読み取り専用接続を MARS を使用します。    ただし、SQL Server 2014 は、列ストア インデックスを持つテーブルでの同時実行データ操作言語 (DML) 操作の MARS をできません。 この場合、SQL Server は、接続を終了し、トランザクションを中止します。  
  
 パフォーマンス上の利点と列ストア インデックスの制限事項については、次を参照してください。[列ストア インデックスの概要](../../relational-databases/indexes/columnstore-indexes-overview.md)です。
  
##  <a name="Metadata"></a> メタデータ  
 列ストア インデックス内のすべての列は、付加列としてメタデータに格納されます。 列ストア インデックスにキー列はありません。 列ストア インデックスに関する情報は、次のシステム ビューによって提供されます。  
  
-   [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
-   [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
-   [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)  
-   [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
-   [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
-   [sys.column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)  

##  <a name="convert"></a>行ストア テーブルを列ストアに変換するための例  
  
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
 この例では、行ストア テーブルを列ストア インデックスに変換するときに、非クラスター化インデックスを処理する方法を示します。 実際には、以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]特別な操作は不要です。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]自動的に定義し、新しいクラスター化列ストア インデックスに非クラスター化インデックスを再構築します。  
  
 非クラスター化インデックスを削除する場合は、列ストア インデックスを作成する前に、DROP INDEX ステートメントを使用します。 DROP EXISTING オプションは、変換されるクラスター化インデックスのみを削除します。 非クラスター化インデックスは削除されません。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]と[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、列ストア インデックスに非クラスター化インデックスを作成できませんでした。 この例は、どのようにを列ストア インデックスを作成する前に、非クラスター化インデックスを削除する必要する以前のリリースで表示されます。  
  
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
  
    -   これは、クラスター化列ストア インデックスに変換されるときにインデックスに新しい名前を指定する場合にのみ行ってください。 クラスター化インデックスを削除しない場合、新しいクラスター化列ストア インデックスは同じ名前を持ちます。  
  
        > [!NOTE]  
        >  インデックスの名前に自分の名前を使用すると記憶しやすくなります。 すべての行ストア クラスター化インデックスは、これは既定の名前を使用して ' clusteredindex _\<GUID >' です。  
  
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
   適用されます SQL Server 2014。  
  
 クラスター化列ストア インデックス全体を再構築するには、2 つの方法があります。 クラスター化列ストア インデックスの作成を使用するか、 [ALTER INDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-index-transact-sql.md)と REBUILD オプション。 どちらの方法も、同じ結果が得られます。  
  
> [!NOTE]  
>  ALTER INDEX REORGANIZE を使用してこの例で説明した方法で再構築ではなく、SQL Server 2016 で開始します。  
  
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
  
##  <a name="nonclustered"></a>非クラスター化列ストア インデックスの例  
  
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
  
 例についてより複雑なパーティション分割されたテーブルを使用して、次を参照してください。[列ストア インデックスの概要](../../relational-databases/indexes/columnstore-indexes-overview.md)です。  
  
### <a name="c-create-a-nonclustered-columnstore-index-with-a-filtered-predicate"></a>C. フィルター選択された述語で、非クラスター化列ストア インデックスを作成します。  
 次の例では、フィルター選択された非クラスター化列ストア インデックスを作成の Production.BillOfMaterials テーブルに対して、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。 フィルター述語では、フィルター選択されたインデックスに非キー列を含めることができます。 この例の述語では、EndDate が NULL 以外の行だけを選択します。  
  
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
   適用されます:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]です。
  
 テーブルに非クラスター化列ストア インデックスを作成すると、そのテーブル内のデータは変更できなくなります。 INSERT、UPDATE、DELETE、または MERGE を持つクエリは失敗し、エラー メッセージが返されます。 テーブル内のデータを追加または変更するには、次のいずれかの操作を行います。  
  
-   列ストア インデックスを無効にするか削除します。 その後、テーブル内のデータを更新できます。 列ストア インデックスを無効にすると、データの更新の終了時に列ストア インデックスを再構築できます。 例を次に示します。  
  
    ```  
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;  
    -- update mytable --  
    ALTER INDEX mycolumnstoreindex on mytable REBUILD  
    ```  
  
-   列ストア インデックスのないステージング テーブルにデータを読み込みます。 ステージング テーブルで列ストア インデックスを構築します。 ステージング テーブルをメイン テーブルの空のパーティションに切り替えます。  
  
-   列ストア インデックスを持つテーブルから空のステージング テーブルにパーティションを切り替えます。 ステージング テーブルに列ストア インデックスがある場合は、列ストア インデックスを無効にします。 更新を実行します。 列ストア インデックスを構築 (または再構築) します。 ステージング テーブルを切り替えて、メイン テーブルの (空になった) パーティションに戻します。  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-change-a-clustered-index-to-a-clustered-columnstore-index"></a>A. クラスター化列ストア インデックスをクラスター化インデックスを変更します。  
 CREATE CLUSTERED COLUMNSTORE INDEX ステートメントを with DROP_EXISTING を使用して = ON にすることができます。  
  
-   クラスター化列ストア インデックスにクラスター化インデックスを変更します。  
  
-   クラスター化列ストア インデックスを再構築します。  
  
 この例では、クラスター化インデックスを含む行ストア テーブルとして xDimProduct テーブルを作成し、行ストア テーブルから列ストア テーブルにテーブルを変更するクラスター化列ストア インデックスの作成を使用します。  
  
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
  
### <a name="b-rebuild-a-clustered-columnstore-index"></a>B. クラスター化列ストア インデックスを再構築します。  
 ビルド前の例で、この例は、cci_xDimProduct と呼ばれる、既存のクラスター化列ストア インデックスを再構築するのに CREATE CLUSTERED COLUMNSTORE INDEX を使用します。  
  
```  
--Rebuild the existing clustered columnstore index.  
CREATE CLUSTERED COLUMNSTORE INDEX cci_xDimProduct   
ON xdimProduct   
WITH ( DROP_EXISTING = ON );  
```  
  
### <a name="c-change-the-name-of-a-clustered-columnstore-index"></a>C. クラスター化列ストア インデックスの名前を変更します。  
 クラスター化列ストア インデックスの名前を変更するに、既存のクラスター化列ストア インデックスを削除し、新しい名前のインデックスの再作成します。  
  
 のみ、小さなテーブル、または空のテーブルでこの操作を行うことをお勧めします。 大規模なクラスター化列ストア インデックスを削除し、別の名前で再構築に時間がかかります。  
  
 この例では、前の例から cci_xDimProduct クラスター化列ストア インデックスを使用して、cci_xDimProduct クラスター化列ストア インデックスを削除し、名前 mycci_xDimProduct でクラスター化列ストア インデックスを作成し直します。  
  
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
 クラスター化列ストア インデックスを削除して、クラスター化インデックスを作成するような状況である可能性があります。 これは、行ストア形式でテーブルを格納します。 この例では、同じ名前のクラスター化インデックスを持つ行ストア テーブルに列ストア テーブルに変換します。 すべてのデータは失われます。 すべてのデータは、行ストア テーブルに移動し、示されている列のクラスター化インデックスのキー列になります。  
  
```  
--Drop the clustered columnstore index and create a clustered rowstore index.   
--All of the columns are stored in the rowstore clustered index.   
--The columns listed are the included columns in the index.  
CREATE CLUSTERED INDEX cci_xDimProduct    
ON xdimProduct (ProductKey, ProductAlternateKey, ProductSubcategoryKey, WeightUnitMeasureCode)  
WITH ( DROP_EXISTING = ON);  
  
```  
  
### <a name="e-convert-a-columnstore-table-back-to-a-rowstore-heap"></a>E. 列ストア テーブルを行ストア ヒープに変換します。  
 使用して[DROP INDEX (SQL Server PDW)](http://msdn.microsoft.com/en-us/f59cab43-9f40-41b4-bfdb-d90e80e9bf32)クラスター化列ストア インデックスを削除し、テーブルを行ストア ヒープに変換します。 この例では、cci_xDimProduct テーブルを行ストア ヒープに変換します。 配布するテーブルが続行されますが、ヒープとして格納されます。  
  
```  
--Drop the clustered columnstore index. The table continues to be distributed, but changes to a heap.  
DROP INDEX cci_xdimProduct ON xdimProduct;  
```  


