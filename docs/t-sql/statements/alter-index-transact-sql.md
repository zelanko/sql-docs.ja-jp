---
title: "ALTER INDEX (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: tsql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER INDEX
- ALTER_INDEX_TSQL
dev_langs:
- t-sql
helpviewer_keywords:
- indexes [SQL Server], reorganizing
- ALTER INDEX statement
- indexes [SQL Server], disabling
- online index operations
- index reorganization [SQL Server]
- ALLOW_ROW_LOCKS option
- ALL keyword
- reorganizing indexes
- constraints [SQL Server], indexes
- row locks [SQL Server]
- index rebuilding [SQL Server]
- rebuilding indexes
- locking [SQL Server], indexes
- partitioned indexes [SQL Server], rebuilding
- defragmenting indexes
- disabling indexes
- XML indexes [SQL Server], modifying
- index modifications [SQL Server]
- indexes [SQL Server], modifying
- index options [SQL Server]
- modifying indexes
- index disabling [SQL Server]
- MAXDOP index option, ALTER INDEX statement
- spatial indexes [SQL Server], modifying
- indexes [SQL Server], options
- ALLOW_PAGE_LOCKS option
- page locks [SQL Server]
- index rebuild [SQL Server]
- index reorganize [SQL Server]
ms.assetid: b796c829-ef3a-405c-a784-48286d4fb2b9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: a5bf734d607c6954c1652df9b9814a31b2224740
ms.sourcegitcommit: 0a9c29c7576765f3b5774b2e087852af42ef4c2d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="alter-index-transact-sql"></a>ALTER INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  インデックスの無効化、再構築、再構成によって、またはインデックスに関するオプションの設定によって、既存のテーブルやビュー インデックス (リレーショナルまたは XML) を変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database
  
ALTER INDEX { index_name | ALL } ON <object>  
{  
      REBUILD {  
            [ PARTITION = ALL ] [ WITH ( <rebuild_index_option> [ ,...n ] ) ]   
          | [ PARTITION = partition_number [ WITH ( <single_partition_rebuild_index_option> ) [ ,...n ] ]  
      }  
    | DISABLE  
    | REORGANIZE  [ PARTITION = partition_number ] [ WITH ( <reorganize_option>  ) ]  
    | SET ( <set_index_option> [ ,...n ] )   
    | RESUME [WITH (<resumable_index_options>,[…n])]
    | PAUSE
    | ABORT
}  
[ ; ]  
  
<object> ::=   
{  
    [ database_name. [ schema_name ] . | schema_name. ]   
    table_or_view_name  
}  
  
<rebuild_index_option > ::=  
{  
      PAD_INDEX = { ON | OFF }  
    | FILLFACTOR = fillfactor   
    | SORT_IN_TEMPDB = { ON | OFF }  
    | IGNORE_DUP_KEY = { ON | OFF }  
    | STATISTICS_NORECOMPUTE = { ON | OFF }  
    | STATISTICS_INCREMENTAL = { ON | OFF }  
    | ONLINE = {   
          ON [ ( <low_priority_lock_wait> ) ]   
        | OFF } 
    | RESUMABLE = { ON | OFF } 
    | MAX_DURATION = <time> [MINUTES}     
    | ALLOW_ROW_LOCKS = { ON | OFF }  
    | ALLOW_PAGE_LOCKS = { ON | OFF }  
    | MAXDOP = max_degree_of_parallelism  
    | COMPRESSION_DELAY = {0 | delay [Minutes]}  
    | DATA_COMPRESSION = { NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE }   
        [ ON PARTITIONS ( {<partition_number> [ TO <partition_number>] } [ , ...n ] ) ]  
}  
  
<single_partition_rebuild_index_option> ::=  
{  
      SORT_IN_TEMPDB = { ON | OFF }  
    | MAXDOP = max_degree_of_parallelism  
    | RESUMABLE = { ON | OFF } 
    | MAX_DURATION = <time> [MINUTES}     
    | DATA_COMPRESSION = { NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE} }  
    | ONLINE = { ON [ ( <low_priority_lock_wait> ) ] | OFF }  
}  
  
<reorganize_option>::=  
{  
       LOB_COMPACTION = { ON | OFF }  
    |  COMPRESS_ALL_ROW_GROUPS =  { ON | OFF}  
}  
  
<set_index_option>::=  
{  
      ALLOW_ROW_LOCKS = { ON | OFF }  
    | ALLOW_PAGE_LOCKS = { ON | OFF }  
    | IGNORE_DUP_KEY = { ON | OFF }  
    | STATISTICS_NORECOMPUTE = { ON | OFF }  
    | COMPRESSION_DELAY= {0 | delay [Minutes]}  
}  

<resumable_index_option> ::=
 { 
    MAXDOP = max_degree_of_parallelism
    | MAX_DURATION =<time> [MINUTES]
    | <low_priority_lock_wait>  
 }
 
<low_priority_lock_wait>::=  
{  
    WAIT_AT_LOW_PRIORITY ( MAX_DURATION = <time> [ MINUTES ] ,   
                          ABORT_AFTER_WAIT = { NONE | SELF | BLOCKERS } )  
}  

```  
  
```  
-- Syntax for SQL Data Warehouse and Parallel Data Warehouse 
  
ALTER INDEX { index_name | ALL }  
    ON   [ schema_name. ] table_name  
{  
      REBUILD {  
            [ PARTITION = ALL [ WITH ( <rebuild_index_option> ) ] ] 
          | [ PARTITION = partition_number [ WITH ( <single_partition_rebuild_index_option> )] ] 
      }  
    | DISABLE  
    | REORGANIZE [ PARTITION = partition_number ]  
}  
[;]  

<rebuild_index_option > ::=   
{  
    DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }
        [ ON PARTITIONS ( {<partition_number> [ TO <partition_number>] } [ , ...n ] ) ]   
}

<single_partition_rebuild_index_option > ::=   
{  
    DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
}  
  
```    
## <a name="arguments"></a>引数  
 *index_name*  
 インデックスの名前。 インデックス名は、テーブルまたはビュー内では一意である必要がありますが、データベース内で一意である必要はありません。 インデックス名の規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 ALL  
 インデックスの種類に関係なく、テーブルまたはビューに関連付けられているすべてのインデックスを指定します。 1 つ以上のインデックスがオフラインまたは読み取り専用のファイル グループにあるか、指定した操作が 1 つ以上のインデックスの種類に許可されていない場合、ALL を指定するとステートメントは失敗します。 次の表は、インデックス操作と、許可されないインデックスの種類の一覧です。  
  
|この操作をすべて、キーワードを使用します。|テーブル内に存在すると操作が失敗するインデックスの種類|  
|----------------------------------------|----------------------------------------|  
|REBUILD WITH ONLINE = ON|XML インデックス<br /><br /> 空間インデックス<br /><br /> 列ストア インデックス:**に適用されます:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) と[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。|  
|REBUILD PARTITION = *partition_number*|非パーティション インデックス、XML インデックス、空間インデックス、または無効化されたインデックス|  
|REORGANIZE|ALLOW_PAGE_LOCKS が OFF に設定されたインデックス|  
|REORGANIZE PARTITION = *partition_number*|非パーティション インデックス、XML インデックス、空間インデックス、または無効化されたインデックス|  
|IGNORE_DUP_KEY = ON|XML インデックス<br /><br /> 空間インデックス<br /><br /> 列ストア インデックス:**に適用されます:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) と[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。|  
|ONLINE = ON|XML インデックス<br /><br /> 空間インデックス<br /><br /> 列ストア インデックス:**に適用されます:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) と[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。|
| 再開可能な = ON  | サポートされていません、再開可能なインデックス**すべて**キーワード。 <br /><br /> **適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]) と[!INCLUDE[ssSDS](../../includes/sssds-md.md)] |   
  
> [!WARNING]
>  詳細についてはオンラインで実行できるインデックス操作についてを参照してください。[オンライン インデックス操作のガイドライン](../../relational-databases/indexes/guidelines-for-online-index-operations.md)です。

 パーティションで ALL を指定した場合、= *partition_number*、すべてのインデックスを固定する必要があります。 つまり、すべてのインデックスは、等価パーティション関数に基づいてパーティション分割されます。 パーティションを持つすべてを使用すると、同じすべてのインデックス パーティションと*partition_number*を再構築または再構成します。 パーティション インデックスの詳細については、「 [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md)」を参照してください。  
  
 *database_name*  
 データベースの名前です。  
  
 *schema_name*  
 テーブルまたはビューが属するスキーマの名前を指定します。  
  
 *table_or_view_name*  
 インデックスに関連付けられているテーブルまたはビューの名前を指定します。 表示するには、インデックスのレポート オブジェクトを使用して、 [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)カタログ ビューです。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]3 部構成の名前形式 database_name をサポートしています。[schema_name] .table_or_view_name、database_name が現在のデータベースまたは database_name が tempdb であり、table_or_view_name が # で始まる。  
  
 REBUILD [ WITH **(**\<rebuild_index_option> [ **,**... *n*]**)** ]  
 同じ列、インデックスの種類、一意性属性、および並べ替え順に従って、インデックスを再構築します。 この句は等価[DBCC DBREINDEX](../../t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md)です。 REBUILD では、無効化されたインデックスが有効になります。 クラスター化インデックスを再構築しても、キーワード ALL を指定しない限り、関連付けられている非クラスター化インデックスは再構築されません。 既存のインデックス オプションで格納されている値をインデックス オプションが指定されていない場合[sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)適用されます。 値が格納されていないインデックス オプションについて**sys.indexes**オプションの引数の定義に示されている既定値が適用されます。  
  
 ALL を指定した場合で、基になるテーブルがヒープの場合、テーブルは再構築操作の影響を受けません。 テーブルに関連付けられている非クラスター化インデックスは再構築されます。  
  
 データベース復旧モデルが一括ログ復旧モデルまたは単純復旧モデルのいずれかに設定されている場合、再構築操作のログへの記録は最小限にできます。  
  
> [!NOTE]
>  プライマリ XML インデックスを再構築するとき、基になるユーザー テーブルはインデックス操作の間使用できなくなります。  
  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。
  
 列ストア インデックスの場合、再構築操作。  
  
1.  並べ替え順序を使用しません。  
  
2.  再構築が行われている間、テーブルまたはパーティションを排他的にロックします。  データは、NOLOCK、RCSI または SI を使用する場合でも、「オフライン」であり、再構築中に使用できません。  
  
3.  すべてのデータを列ストアに再圧縮します。 再構築が行われている間、列ストア インデックスのコピーが 2 つ存在します。 再構築が完了したら、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により、元の列ストア インデックスが削除されます。  
  
 列ストア インデックスの再構築の詳細については、次を参照してください[列ストア インデックスの最適化。](../../relational-databases/indexes/columnstore-indexes-defragmentation.md)  
  
PARTITION  

**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
 インデックスの 1 つのパーティションのみを再構築または再構成します。 パーティションを指定できません*index_name*パーティション インデックスではありません。  
  
 PARTITION = ALL により、すべてのパーティションが再構築されます。  
  
> [!WARNING]
>  固定されていないインデックスをパーティションが 1, 000 個以上あるテーブルに作成または再構築することは可能ですが、サポートされていません。 このような操作を行うと、操作中にパフォーマンスが低下したりメモリが過度に消費される可能性があります。 パーティションの数が 1, 000 個を超えた場合は、固定されたインデックスのみを使用することをお勧めします。  
  
 *partition_number*  
   
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。
  
 再構築または再構成するパーティション インデックスのパーティション番号を指定します。 *partition_number*変数を参照できる定数式です。 ユーザー定義型の変数または関数およびユーザー定義関数を含むこれらは参照できませんが、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 *partition_number*存在する必要がありますと、ステートメントは失敗します。  
  
 WITH **(**\<single_partition_rebuild_index_option>**)**  
   
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
 SORT_IN_TEMPDB、MAXDOP、および DATA_COMPRESSION は、1 つのパーティションを再構築するときに指定できるオプションを示します (パーティション =  *n* )。 XML インデックスは、単一のパーティションの再構築操作では指定できません。  
  
 DISABLE  
 インデックスを無効とマークし、[!INCLUDE[ssDE](../../includes/ssde-md.md)]で使用されないようにします。 どのインデックスも無効にできます。 無効になったインデックスのインデックス定義は、基になるインデックス データがなくてもシステム カタログに残ります。 クラスター化インデックスを無効にすると、基になるテーブル データをユーザーのアクセスができなくなります。 インデックスを有効にするには、ALTER INDEX REBUILD または CREATE INDEX WITH DROP_EXISTING を使用します。 詳細については、次を参照してください。[無効にするインデックスと制約](../../relational-databases/indexes/disable-indexes-and-constraints.md)と[Enable Indexes and Constraints](../../relational-databases/indexes/enable-indexes-and-constraints.md)です。  
  
 行ストア インデックスを再構成します。  
 行ストア インデックスの場合は、REORGANIZE をインデックスのリーフ レベルを再編成を指定します。  再構成操作は次のとおりです。  
  
-   常にオンラインで実行されます。 つまり、ALTER INDEX REORGANIZE トランザクション中は、長期にわたって他をブロックするテーブル ロックは保持されず、基になるテーブルへのクエリまたは更新を続行できます。  
  
-   無効なインデックスの許可されていません  
  
-   ALLOW_PAGE_LOCKS が OFF に設定されている場合は許可されません。  
  
-   いないロールバックされたトランザクション内で実行され、トランザクションがロールバックされます。  
  
REORGANIZE WITH **(** LOB_COMPACTION = { **ON** | OFF } **)**  
 行ストア インデックスに適用されます。  
  
LOB_COMPACTION = ON  
  
-   これらのラージ オブジェクト (LOB) データ型のデータが含まれているすべてのページを圧縮することを指定します。 image、text、ntext、varchar (max)、nvarchar (max)、varbinary (max)、および xml です。 このデータを圧縮すると、ディスク上のデータ サイズが削減できます。  
  
-   クラスター化インデックスのテーブルに含まれているすべての LOB 列が圧縮されます。  
  
-   非クラスター化インデックス、インデックスに非キー (付加) 列であるすべての LOB 列が圧縮されます。  
  
-   [すべて再構成] は、すべてのインデックスに対して LOB_COMPACTION を実行します。 インデックスごとに、クラスター化インデックス、基になるテーブル、または付加列非クラスター化インデックス内のすべての LOB 列が圧縮されます。  
  
LOB_COMPACTION = OFF  
  
-   ラージ オブジェクト データを含むページは圧縮されません。  
  
-   OFF の指定は、ヒープには影響しません。  
  
列ストア インデックスを再構成します。  
REORGANIZE はオンラインで実行します。  
  
列ストア インデックスの場合は、REORGANIZE は、列ストアに圧縮された行グループと各閉じられたデルタ行グループを圧縮します。  
  
-   閉じられたデルタ行グループの圧縮行グループに移動するためには、再編成は必要はありません。 バック グラウンドの組ムーバー (TM) プロセスは、閉じられたデルタ行グループを圧縮する定期的に起動します。 組ムーバーが遅延しているときに、REORGANIZE を使用することをお勧めします。 REORGANIZE は、行グループをより積極的に圧縮できます。  
  
-   すべてのオープンとクローズの行グループを圧縮するには、再編成と (COMPRESS_ALL_ROW_GROUPS) オプションはこのセクションの内容を参照してください。  
  
列ストア インデックスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](2016年以降) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]REORGANIZE は、次の追加の最適化最適化オンラインを実行します。  
  
-   物理的に行の 10% 以上が論理的に削除されたときに、行グループから行を削除します。 削除されたバイトは、物理メディアで再利用されます。 たとえば、100 K を行の削除を 100万行の圧縮された行グループには、SQL Server は、削除された行を削除し、900 k 行と行グループを再圧縮します。 削除された行を削除することで、記憶域に保存されます。  
  
-   1,024,576 行の最大値は行グループあたりの行数を増やすには 1 つまたは複数の圧縮された行グループを結合します。 たとえば、一括インポートした 102,400 行のバッチを 5 5 の圧縮行グループが表示されます。 REORGANIZE を実行する場合は、サイズ 512,000 行の圧縮された行グループの 1 にこれらの行グループがマージを取得します。 これによりが存在しなかったディクショナリのサイズやメモリの制限を前提としています。  
  
-   10% 以上の行が論理的に削除された行グループ、SQL Server は 1 つまたは複数の行グループと、この行グループを結合する再試行してください。    たとえば、500,000 行で 1 行グループが圧縮されて、行グループ 21 は、最大 1,048, 576 行の圧縮します。  行グループ 21 409,830 行が削除された行の 60% があります。 SQL Server では、これら 2 つの行グループを 909,830 行を持つ新しい行グループを圧縮を組み合わせることを優先します。  
  
REORGANIZE WITH ( COMPRESS_ALL_ROW_GROUPS = { ON | **OFF** } )  

 **適用されます:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]) と[!INCLUDE[ssSDS](../../includes/sssds-md.md)]

COMPRESS_ALL_ROW_GROUPS は、開くまたは CLOSED のデルタ行グループ、列ストアに強制的に移動する方法を提供します。 このオプションを使用して、デルタ行グループを空にする、列ストア インデックスを再構築する必要はありません。  これと組み合わせる、他の削除とマージ最適化機能は、ほとんどの状況でインデックスを再構築は必要なくなりました。    

-   サイズと終了 (開く) の状態に関係なく、列ストアに、すべての行グループを強制します。  
  
-   オフには、列ストアに CLOSED 行グループのすべてを強制します。  
  
SET **(** \<set_index option> [ **,**... *n*] **)**  
 インデックスを再構築または再構成しないでインデックス オプションを指定します。 無効化されたインデックスには、SET は指定できません。  
  
PAD_INDEX = { ON | OFF }  
   
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
 インデックスの埋め込みを指定します。 既定値は OFF です。  
  
 ON  
 FILLFACTOR で指定される空き領域のパーセンテージが、インデックスの中間レベルのページに適用されます。 Fill factor で格納されている値で PAD_INDEX を ON に設定されて、同時に FILLFACTOR が指定されていない場合[sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)を使用します。  
  
 OFF または*fillfactor*が指定されていません  
 中間レベルのページは、ほぼ全容量が使用されます。 この場合、中間ページのキーのセットに基づき、インデックスに割り当てることのできる 1 行以上の最大サイズが収まる分の領域は残されます。  
  
 詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)」を参照してください。  
  
FILLFACTOR = *fillfactor*  
 
 **適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。
  
 どの程度を示すパーセンテージを指定します、[!INCLUDE[ssDE](../../includes/ssde-md.md)]インデックスの作成または変更時に各インデックス ページのリーフ レベルを作成する必要があります。 *fillfactor* 1 から 100 までの整数値にする必要があります。 既定値は 0 です。 Fill factor 値 0 と 100 は、すべての点で同じです。  
  
 明示的な FILLFACTOR 設定値は、インデックスの初回作成時または再構築時のみ適用されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]ページ内の空き領域の指定された割合動的に保持しません。 詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)」を参照してください。  
  
 表示するには、fill factor 設定を使用して**sys.indexes**です。  
  
> [!IMPORTANT]
>  [!INCLUDE[ssDE](../../includes/ssde-md.md)]ではクラスター化インデックスの作成時にデータが再分配されるため、FILLFACTOR 値を使用してクラスター化インデックスを作成または変更すると、データ用のストレージ領域のサイズに影響が生じます。  
  
 SORT_IN_TEMPDB = { ON | **OFF** }  
 
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
 並べ替えの結果を格納するかどうかを示す**tempdb**です。 既定値は OFF です。  
  
 ON  
 インデックスの構築に使用される並べ替えの中間結果が格納されている**tempdb**です。 場合**tempdb**は、異なるディスク セットに、ユーザー データベースよりも、インデックスを作成するために必要な時間が削減されます。 インデックスの構築中に使用されるディスク領域のサイズは増加します。  
  
 OFF  
 中間の並べ替え結果はインデックスと同じデータベースに格納されます。  
  
 並べ替え操作が必要でない場合、または並べ替えをメモリ内で実行できる場合は、SORT_IN_TEMPDB オプションは無視されます。  
  
 詳細については、次を参照してください。[インデックスの SORT_IN_TEMPDB オプション](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)です。  
  
 IGNORE_DUP_KEY **=** { ON | OFF }  
 挿入操作で、一意のインデックスに重複するキー値を挿入しようとした場合のエラー応答を指定します。 IGNORE_DUP_KEY オプションは、インデックスが作成または再構築された後の挿入操作のみに適用されます。 既定値は OFF です。  
  
 ON  
 重複したキー値が一意のインデックスに挿入されると、警告メッセージが表示されます。 一意性制約に違反する行のみが失敗します。  
  
 OFF  
 重複したキー値が一意のインデックスに挿入されると、エラー メッセージが表示されます。 INSERT 操作全体がロールバックされます。  
  
 ビューに作成されたインデックス、一意でないインデックス、XML インデックス、空間インデックス、およびフィルター選択されたインデックスの IGNORE_DUP_KEY を ON に設定できません。  
  
 IGNORE_DUP_KEY を表示する[sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)です。  
  
 旧バージョンと互換性のある構文では、WITH IGNORE_DUP_KEY は WITH IGNORE_DUP_KEY = ON と同じです。  
  
 STATISTICS_NORECOMPUTE **=** { ON | OFF }  
 分布統計を再計算するかどうかを指定します。 既定値は OFF です。  
  
 ON  
 古い統計情報は、自動的には再計算されません。  
  
 OFF  
 自動統計更新が有効です。  
  
 自動統計更新を復元するには、STATISTICS_NORECOMPUTE を OFF に設定するか、NORECOMPUTE 句を指定せずに UPDATE STATISTICS を実行します。  
  
> [!IMPORTANT]
> 分布統計の自動再計算を無効にすると、クエリ オプティマイザーで、テーブルに関連するクエリの最適実行プランが選択されなくなる場合があります。  
  
 STATISTICS_INCREMENTAL = { ON | **OFF** }  
 ときに**ON**、作成される統計は、パーティションごとの統計はします。 ときに**OFF**、統計ツリーが削除されると[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]統計が再計算します。 既定値は**OFF**です。  
  
 パーティションごとの統計がサポートされていない場合、このオプションは無視され、警告が生成されます。 次の種類の統計では、増分統計がサポートされていません。  
  
-   ベース テーブルにパーティションで固定されていないインデックスを使用して作成された統計。  
-   Always On の読み取り可能なセカンダリ データベースに対して作成された統計。  
-   読み取り専用のデータベースに対して作成された統計。  
-   フィルター選択されたインデックスに対して作成された統計。  
-   ビューに対して作成された統計。  
-   内部テーブルに対して作成された統計。  
-   空間インデックスまたは XML インデックスを使用して作成された統計。  
 
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
 オンライン **=**  {ON |**OFF** } \<rebuild_index_option に適用する >  
 インデックス操作時に、基になるテーブルや関連するインデックスをクエリやデータ変更で使用できるかどうかを指定します。 既定値は OFF です。  
  
 XML インデックスまたは空間インデックスの場合、ONLINE = OFF だけがサポートされます。ONLINE を ON に設定すると、エラーが発生します。  
  
> [!NOTE]
>  オンラインでのインデックス操作は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションで使用できるわけではありません。 各エディションでサポートされている機能の一覧については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[エディションとサポートされる機能[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)と[エディションとサポートされる機能の SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md)です。  
  
 ON  
 長期のテーブル ロックは、インデックス操作の間は保持されません。 インデックス操作の主なフェーズでは、基になるテーブル、インテント共有 (IS) ロックのみが保持されます。 これによって、基になるテーブルおよびインデックスに対してクエリや更新を続けることができます。 操作の開始時、非常に短い時間、ソース オブジェクトでは共有 (S) ロックが保持されます。 操作の終了時、非クラクタ化インデックスが作成される場合は、短い時間、ソース オブジェクト上で S ロックが保持されます。また、クラスター化インデックスがオンラインで作成または削除されるか、クラスター化または非クラスター化インデックスが再構築される場合は、SCH-M (スキーマ修正) ロックが取得されます。 インデックスがローカルの一時テーブルに作成される場合、ONLINE は ON にできません。  
  
 OFF  
 テーブル ロックは、インデックス操作の間適用されます。 オフラインのインデックス操作で、クラスター化インデックス、空間インデックス、XML インデックスの作成、再構築、削除を行う場合や、非クラスター化インデックスの再構築、削除を行う場合は、テーブルで Sch-M (スキーマ修正) ロックが取得されます。 このため、操作中は、すべてのユーザーは基になるテーブルにアクセスできません。 非クラスター化インデックスを作成するオフライン インデックス操作では、テーブルの共有 (S) ロックが取得されます。 この場合は、基になるテーブルに対して更新は許可されませんが、SELECT ステートメントなどの読み取り操作は許可されます。  
  
 詳細については、次を参照してください。[オンライン インデックス操作しくみ](../../relational-databases/indexes/how-online-index-operations-work.md)です。  
  
 インデックスは、グローバル一時テーブル上のインデックスを含めてオンラインで再構築できます。ただし、次のインデックスは例外です。  
  
-   XML インデックス数  
  
-   ローカル一時テーブル上のインデックス  
  
-   パーティション インデックスのサブセット (パーティション インデックス全体の再構築はオンラインで実行できます)  

-  [!INCLUDE[ssSDS](../../includes/sssds-md.md)]V12、およびより前のバージョンの SQL Server より前[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、許可されていない、`ONLINE`オプションをクラスター化インデックスの構築またはベース テーブルが含まれている場合は、操作を再構築**varchar (max)**または**varbinary(max)**列です。

再開可能な **=**  {ON |**OFF**}

**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]) と[!INCLUDE[ssSDS](../../includes/sssds-md.md)]   

 オンライン インデックス操作が再開可能かどうかを指定します。

 インデックス操作は再開可能な状態です。

 インデックスをオフは、操作は再開可能な状態ではありません。

MAX_DURATION **=** *time* **[MINUTES]** used with **RESUMABLE = ON** (requires **ONLINE = ON**).
 
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]) と[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 

時間を示します (分単位で指定された整数値)、再開可能なオンライン インデックス操作が一時停止する前に実行します。 

ALLOW_ROW_LOCKS **=** { **ON** | OFF }  
 
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
 行ロックを許可するかどうかを指定します。 既定値は ON です。  
  
 ON  
 インデックスにアクセスするとき、行ロックが許可されます。 いつ行ロックを使用するかは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]によって決定されます。  
  
 OFF  
 行ロックは使用されません。  
  
ALLOW_PAGE_LOCKS **=** { **ON** | OFF }  
  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。
  
 ページ ロックを許可するかどうかを指定します。 既定値は ON です。  
  
 ON  
 インデックスにアクセスするとき、ページ ロックが許可されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]ページ ロックを使用する場合を決定します。  
  
 OFF  
 ページ ロックは使用されません。  
  
> [!NOTE]
>  ALLOW_PAGE_LOCKS を OFF に設定した場合、インデックスを再構成することはできません。  
  
 MAXDOP  **=**  max_degree_of_parallelism  
 
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
 上書き、**並列処理の次数の最大**インデックス操作の実行中の構成オプション。 詳細については、「 [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)」を参照してください。 並列プランの実行で使用されるプロセッサ数を制限するには、MAXDOP を使用します。 最大数は 64 プロセッサです。  
  
> [!IMPORTANT]
>  MAXDOP オプションはすべての XML インデックスで構文的にサポートされていますが、空間インデックスまたはプライマリ XML インデックスの場合、現在の ALTER INDEX では単一のプロセッサのみが使用されます。  
  
 *max_degree_of_parallelism*を指定できます。  
  
 1  
 並列プラン生成を抑制します。  
  
 \>1  
 並列インデックス操作で使用される最大プロセッサ数を、指定した数に制限します。  
  
 0 (既定値)  
 現在のシステム ワークロードに基づいて、実際の数以下のプロセッサを使用します。  
  
 詳細については、「 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)」を参照してください。  
  
> [!NOTE]
> 並列インデックス操作はすべてのエディションで使用できない[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 各エディションでサポートされている機能の一覧については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[エディションとサポートされる機能[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)です。  
  
 COMPRESSION_DELAY  **=**  { **0** |*期間 [分]* }  
 この機能は、使用可能な開始[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
 ディスク ベース テーブルでは、SQL Server を使用すると、圧縮された行グループに圧縮できる前に、遅延はデルタ行グループで閉じられた状態で、デルタ行グループがある必要があります (分) の最小数を指定します。 ディスク ベース テーブルの挿入を追跡および更新されないため時間個々 の行に SQL Server を適用の遅延が閉じられた状態で、デルタ行グループ。  
既定値は、0 分です。  
  
 既定値は、0 分です。  
  
 リアルタイム運用分析のため、列ストア インデックスを参照してください、COMPRESSION_DELAY を使用する場合の推奨事項についてはします。  
  
 DATA_COMPRESSION  
 指定したインデックス、パーティション番号、またはパーティション範囲に、データ圧縮オプションを指定します。 次のオプションがあります。  
  
 なし  
 インデックスまたは指定したパーティションが圧縮されません。 これは、列ストア インデックスには適用されません。  
  
 ROW  
 行の圧縮を使用して、インデックスまたは指定したパーティションが圧縮されます。 これは、列ストア インデックスには適用されません。  
  
 PAGE  
 ページの圧縮を使用して、インデックスまたは指定したパーティションが圧縮されます。 これは、列ストア インデックスには適用されません。  
  
 COLUMNSTORE  
   
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。
  
 非クラスター化列ストア インデックスとクラスター化列ストア インデックスの両方を含む列ストア インデックスにのみ適用されます。 COLUMNSTORE は、COLUMNSTORE_ARCHIVE オプションで圧縮されたインデックスまたは指定のパーティションを解凍するように指定します。 復元されるデータは、すべての列ストア インデックスに使用された列ストア圧縮を使用して引き続き圧縮されます。  
  
 COLUMNSTORE_ARCHIVE  
  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。
  
 非クラスター化列ストア インデックスとクラスター化列ストア インデックスの両方を含む列ストア インデックスにのみ適用されます。 COLUMNSTORE_ARCHIVE は、指定したパーティションをより小さなサイズにさらに圧縮します。 これは、保存用や、ストレージのサイズを減らす必要があり、しかも保存と取得に時間をかける余裕があるその他の状況で使用できます。  
  
 圧縮の詳細については、次を参照してください。[データ圧縮](../../relational-databases/data-compression/data-compression.md)です。  
  
 ON PARTITIONS **(** { \<partition_number_expression> | \<range> } [**,**...n] **)**  
    
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。 
  
 DATA_COMPRESSION 設定を適用するパーティションを指定します。 インデックスがパーティション分割されていない場合に ON PARTITIONS 引数を使用すると、エラーが発生します。 ON PARTITIONS 句を指定しないと、パーティション インデックスのすべてのパーティションに対して DATA_COMPRESSION オプションが適用されます。  
  
 \<partition_number_expression > 次のように指定することができます。  
  
-   ON PARTITIONS (2) などのように、1 つのパーティションの番号を指定します。  
  
-   ON PARTITIONS (1, 5) などのように、複数のパーティションのパーティション番号をコンマで区切って指定します。  
  
-   範囲と個別のパーティションの両方を提供: ON PARTITIONS (2、4, 6 TO 8)。  
  
 \<範囲 > パーティション番号など、to で区切って指定できます: ON PARTITIONS (6 TO 8)。  
  
 さまざまなパーティションにさまざまな種類のデータ圧縮を設定するには、次のように DATA_COMPRESSION オプションを複数回指定します。  
  
```sql  
REBUILD WITH   
(  
DATA_COMPRESSION = NONE ON PARTITIONS (1),   
DATA_COMPRESSION = ROW ON PARTITIONS (2, 4, 6 TO 8),   
DATA_COMPRESSION = PAGE ON PARTITIONS (3, 5)  
);  
```  
  
 オンライン **=**  {ON |**OFF** } \<single_partition_rebuild_index_option に適用 >  
 かどうか、インデックスまたは基になるテーブルのインデックス パーティションの再構築オンラインまたはオフラインを指定します。 場合**リビルド**はオンラインで実行 (**ON**) このテーブルのデータはクエリやデータの変更、インデックス操作中に使用します。  既定値は**OFF**です。  
  
 ON  
 長期のテーブル ロックは、インデックス操作の間は保持されません。 インデックス操作の主要フェーズの期間、ソース テーブルではインテント共有 (IS) ロックのみが保持されます。 先頭のインデックスの再構築し、オンライン インデックス再構築の最後に、テーブルに対する SCH-M ロックのテーブルで S ロックが必要です。 どちらのロックも短いメタデータ ロックですが、特に Sch-M ロックは、すべてのブロックしているトランザクションの完了を待機する必要があります。 待機中、Sch-M ロックは、同じテーブルにアクセスするためにこのロックの後に待機している他のすべてのトランザクションをブロックします。  
  
> [!NOTE]
>  オンライン インデックス再構築が設定できる、 *low_priority_lock_wait*オプションのこのセクションで後述します。  
  
 OFF  
 テーブル ロックは、インデックス操作の間適用されます。 このため、操作中は、すべてのユーザーは基になるテーブルにアクセスできません。  
  
 WAIT_AT_LOW_PRIORITY を併用**ONLINE = ON**のみです。  
 
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。
  
 オンライン インデックス再構築では、このテーブルに対する操作がブロックされるまで待機する必要があります。 **WAIT_AT_LOW_PRIORITY**オンライン インデックス再構築操作が他の操作を続行しながら、オンライン インデックス構築操作が待機している、優先度の低いロックを待つことを示します。 省略すると、 **WAIT AT LOW PRIORITY**オプションに相当`WAIT_AT_LOW_PRIORITY (MAX_DURATION = 0 minutes, ABORT_AFTER_WAIT = NONE)`です。 詳細については、次を参照してください。 [WAIT_AT_LOW_PRIORITY](alter-index-transact-sql.md)です。 
  
 MAX_DURATION = *time* **[MINUTES]**  
  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。
  
 オンライン インデックス再構築のロックが、DDL コマンドの実行時に低い優先度で待機する時間 (分単位で指定した整数値) です。 操作がブロックされている場合、 **MAX_DURATION**のいずれかの時間、 **ABORT_AFTER_WAIT**動作が実行されます。 **MAX_DURATION**時間は分、および、word では常に**分**を省略できます。  
 
 ABORT_AFTER_WAIT = [**NONE** | **SELF** | **BLOCKERS** } ]  
   
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。
  
 なし  
 通常の (標準) 優先度のロックを待機し続けます。  
  
 SELF  
 いずれのアクションも行わずに、現在実行中のオンライン インデックス再構築の DDL 操作を終了します。  
  
 BLOCKERS  
 オンライン インデックス再構築の DDL 操作をブロックしているすべてのユーザー トランザクションを強制終了して、操作を続行できるようにします。 **ブロッカー**オプションは、ログインには必要と**ALTER ANY CONNECTION**権限です。  
 
 RESUME 
 
**適用されます**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]  

手動でまたはエラーのために一時停止しているインデックス操作を再開します。

MAX_DURATION の併用**再開可能 ON を =**

 
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]) と[!INCLUDE[ssSDS](../../includes/sssds-md.md)]

時間 (分単位で指定された整数値)、再開可能なオンライン インデックス操作が再開された後に実行します。 時間が切れると、まだ実行されている場合、再開操作が一時停止します。

WAIT_AT_LOW_PRIORITY を併用**再開可能 = ON**と**ONLINE = ON**です。  
  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]) と[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 
  
 このテーブルに対するブロック操作の待機を一時停止した後は、オンラインのインデックスの再構築を再開しています。 **WAIT_AT_LOW_PRIORITY**オンライン インデックス再構築操作が他の操作を続行しながら、オンライン インデックス構築操作が待機している、優先度の低いロックを待つことを示します。 省略すると、 **WAIT AT LOW PRIORITY**オプションに相当`WAIT_AT_LOW_PRIORITY (MAX_DURATION = 0 minutes, ABORT_AFTER_WAIT = NONE)`です。 詳細については、次を参照してください。 [WAIT_AT_LOW_PRIORITY](alter-index-transact-sql.md)です。 


一時停止
 
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]) と[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 
  
再開可能なオンライン インデックス再構築の操作を一時停止します。

中止

**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]) と[!INCLUDE[ssSDS](../../includes/sssds-md.md)]   

再開可能として宣言されている、実行中または一時停止中のインデックス操作を中止します。 明示的に実行する必要がある、**中止**コマンドが終了、再開可能なインデックス操作を再構築します。 障害または一時停止、再開可能なインデックス操作の実行を終了しません代わりに、不定の一時停止状態で、操作に任せます。
  
## <a name="remarks"></a>解説  
 インデックスをパーティションに再分割するか別のファイル グループに移動する場合、ALTER INDEX は使用できません。 このステートメントは、列の追加や削除、または列の順序変更など、インデックス定義の変更には使用できません。 これらの操作を実行するには、CREATE INDEX を DROP_EXISTING 句と共に使用します。  
  
 オプションを明示的に指定しない場合は、現在の設定が適用されます。 たとえば、REBUILD 句で FILLFACTOR 設定を指定しなかった場合、再構築処理では、システム カタログに格納されている FILL FACTOR 値が使用されます。 現在のインデックス オプションの設定を表示する[sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)です。  
  
> [!NOTE]
> ONLINE、MAXDOP、および SORT_IN_TEMPDB の値は、システム カタログに格納されません。 インデックス ステートメントでオプション値を指定しない限り、各オプションの既定値が使用されます。
  
 マルチプロセッサ コンピューター上では、ALTER INDEX REBUILD は他のクエリと同様、自動的に使用プロセッサの数を増やしてインデックスの変更に関連するスキャンや並べ替え操作を実行します。 実行すると ALTER INDEX REORGANIZE を LOB_COMPACTION の有無、**並列処理の次数の最大**値は 1 つのスレッド操作します。 詳細については、「 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)」を参照してください。  
  
 インデックスのあるファイル グループがオフラインまたは読み取り専用に設定されていると、インデックスを再構成または再構築することはできません。 キーワード ALL を指定した場合で、1 つ以上のインデックスがオフラインまたは読み取り専用のファイル グループにある場合、ステートメントは失敗します。  
  
## <a name="rebuilding-indexes"></a>インデックスの再構築  
 インデックスの再構築では、インデックスを削除し再作成します。 この操作では、断片化をなくし、指定されているか既に存在する FILL FACTOR 設定に基づいてページを圧縮することによりディスク領域を取り戻した後、連続するページにインデックス行を再び並べ替えます。 ALL を指定した場合、テーブル上のすべてのインデックスが、1 回のトランザクションで削除され再構築されます。 FOREIGN KEY 制約は、前もって削除しておく必要はありません。 128 以上のエクステントがあるインデックスを再構築すると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では、トランザクションがコミットされるまで実際のページの割り当て解除とそれに関連するロックが延期されます。  
  
 小さなインデックスを再構築または再構成しても、多くの場合、断片化が解消することはありません。 小さなインデックスのページは、混合エクステントに格納される場合もあります。 混合エクステントは最大 8 つのオブジェクトで共有されるため、小さなインデックスを再構成または再構築しても、その断片化は解消されない場合があります。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降では、パーティション インデックスが作成または再構築された場合、テーブル内のすべての行をスキャンして統計を作成することはできません。 代わりに、クエリ オプティマイザーが既定のサンプリング アルゴリズムを使用して統計を生成します。 テーブル内のすべての行をスキャンしてパーティション インデックスの統計を作成するには、FULLSCAN 句で CREATE STATISTICS または UPDATE STATISTICS を使用します。  
  
 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、非クラスター化インデックスを再構築することで、ハードウェア障害により発生した不一致を修正できる場合がありました。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]後で、まだことができます、非クラスター化インデックスをオフラインの再構築して、インデックスとクラスター化インデックス間の不一致を修復するとします。 オンラインでインデックスを再構築する場合、既存の非クラスター化インデックスを基に再構築が行われるので、不一致を維持してしまい非クラスター化インデックスの不一致を修復できません。 オフラインでインデックスを再構築すると、強制的にクラスター化インデックス (ヒープ) のスキャンがなされ、不一致が解消されることがあります。 クラスター化インデックスからの再構築を保証するため、非クラスター化インデックスを削除および再作成します。 不一致を解消する場合、以前のバージョンと同様に影響を受けたデータをバックアップから復元することをお勧めします。ただし、非クラスター化インデックスをオフラインで再構築しても、インデックスの不一致を修復できます。 詳細については、「[DBCC CHECKDB (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)」を参照してください。  
  
 クラスター化列ストア インデックスを再構築する際、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は以下のように動作します。  
  
1.  再構築が行われている間、テーブルまたはパーティションを排他的にロックします。 再構築の間、データは "オフライン" になって使用できません。  
  
2.  テーブルから論理的に削除された行を物理的に削除することで、列ストアをデフラグします。削除されたバイトは物理メディアで再利用されます。  
  
3.  元の列ストア インデックスから、デルタストアを含むすべてのデータを読み取ります。 データを新しい行グループに結合し、行グループを列ストアに圧縮します。  
  
4.  再構築中に、物理メディア上の領域を要求して列ストア インデックスのコピーを 2 つ格納します。 再構築が完了すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は元のクラスター化列ストア インデックスを削除します。  
  
## <a name="reorganizing-indexes"></a>インデックスを再構成します。  
 インデックスの再構成では、最小のシステム リソースが使用されます。 この操作では、リーフ レベル ページをリーフ ノードの論理順序 (左から右) に合わせて物理的に並べ替えることにより、テーブルやビュー上にあるクラスター化および非クラスター化インデックスのリーフ レベルをデフラグします。 再構成でも、インデックス ページは圧縮されます。 圧縮は既存の FILL FACTOR 値に基づいて行われます。 表示するには、fill factor 設定を使用して[sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)です。  
  
 ALL を指定した場合、テーブル上のクラスター化および非クラスター化両方のリレーショナル インデックスと XML インデックスが再構成されます。 ALL を指定した場合は、いくつかの制限が適用されます。「引数」の ALL の定義を参照してください。  
  
 詳細については、「 [インデックスの再編成と再構築](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)」を参照してください。  
  
## <a name="disabling-indexes"></a>インデックスを無効にします。  
 インデックスを無効化すると、ユーザーはインデックスにアクセスできなくなり、クラスター化インデックスの場合は基になるテーブル データにもアクセスできなくなります。 インデックス定義はシステム カタログに残ります。 ビュー上で非クラスター化インデックスまたはクラスター化インデックスを物理的に無効にすると、インデックス データが削除されます。 クラスター化インデックスを無効にすると、データにアクセスできなくなりますが、データはインデックスが削除または再構築されるまで B ツリーに残ります。このデータは管理されません。 有効または無効なインデックスの状態を表示するクエリ、 **is_disabled**内の列、 **sys.indexes**カタログ ビューです。  
  
 テーブルがトランザクション レプリケーション パブリケーション内にある場合、主キー列に関連付けられているインデックスを無効にすることはできません。 これらのインデックスはレプリケーションで必要です。 インデックスを無効にするには、まずパブリケーションからテーブルを削除する必要があります。 詳細については、「[Publish Data and Database Objects](../../relational-databases/replication/publish/publish-data-and-database-objects.md)」(データとデータベース オブジェクトのパブリッシュ) をご覧ください。  
  
 インデックスを有効にするには、ALTER INDEX REBUILD ステートメントまたは CREATE INDEX WITH DROP_EXISTING ステートメントを使用します。 ONLINE オプションが ON に設定されていると、無効化されたクラスター化インデックスを再構築できません。 詳細については、「 [インデックスと制約の無効化](../../relational-databases/indexes/disable-indexes-and-constraints.md)」を参照してください。  
  
## <a name="setting-options"></a>オプションの設定  
 特定のインデックスに対して、再構築または再構成を行わずに ALLOW_ROW_LOCKS、ALLOW_PAGE_LOCKS、IGNORE_DUP_KEY および STATISTICS_NORECOMPUTE オプションを設定できます。 変更された値はすぐにインデックスに適用されます。 これらの設定を表示する**sys.indexes**です。 詳細については、「 [インデックス オプションの設定](../../relational-databases/indexes/set-index-options.md)」を参照してください。  
  
### <a name="row-and-page-locks-options"></a>行およびページ ロック オプション  
 ALLOW_ROW_LOCKS = ON かつ ALLOW_PAGE_LOCK = ON の場合は、インデックスにアクセスするとき、行レベル、ページ レベル、およびテーブル レベルのロックが許可されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]適切なロックを選択し、行またはページ ロックからテーブル ロックのロックをエスカレートすることができます。  
  
 ALLOW_ROW_LOCKS = OFF かつ ALLOW_PAGE_LOCK = OFF の場合は、インデックスにアクセスするときにテーブル レベルのロックだけが許可されます。  
  
 行またはページ ロック オプションが設定されている場合に ALL を指定すると、この設定はすべてのインデックスに適用されます。 基になるテーブルがヒープの場合、この設定は次のように適用されます。  
  
|||  
|-|-|  
|ALLOW_ROW_LOCKS = ON または OFF|ヒープおよび関連する非クラスター化インデックスに適用。|  
|ALLOW_PAGE_LOCKS = ON|ヒープおよび関連する非クラスター化インデックスに適用。|  
|ALLOW_PAGE_LOCKS = OFF|非クラスター化インデックスに完全に適用。 この場合、非クラスター化インデックスではすべてのページ ロックが許可されません。 ヒープでは、ページに対して共有 (S)、更新 (U) および排他 (X) ロックだけが許可されなくなります。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]内部処理用にインテント ページ ロック (IS、IU または IX) を引き続き取得できます。|  
  
## <a name="online-index-operations"></a>オンライン インデックス操作  
 インデックスを再構築する場合で ONLINE オプションが ON に設定されている場合、クエリおよびデータ変更で、基になるオブジェクト、テーブルおよび関連インデックスを使用できます。 1 つのパーティションに存在するインデックスの一部をオンラインで再構築することもできます。 排他テーブル ロックは、変更処理中の非常に短い時間だけ保持されます。  
  
 インデックスの再構成は、常にオンラインで実行されます。 この処理ではロックが長期間保持されないので、実行中のクエリや更新はブロックされません。  
  
 同じテーブルまたはテーブル パーティションでのオンライン インデックス操作は、次の場合のみ同時に実行できます。  
  
-   複数の非クラスター化インデックスを作成する。  
-   同じテーブルで異なるインデックスを再構成する。  
-   同じテーブルで重複しないインデックスを再構築する間、別のインデックスを再構成する。  
  
 その他すべてのオンライン インデックス操作は、同時に実行しようとしても失敗します。 たとえば、同じテーブル上で同時に複数のインデックスを再構築したり、同じテーブルで既存のインデックスを再構築する間に新しいインデックスを作成することはできません。  

### <a name="resumable-indexes"></a>再開可能なインデックス操作

**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]) と[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 

オンライン インデックス再構築は、再開可能を使用して再開可能として指定 = ON オプション。 
-  再開可能なオプションで指定されたインデックスのメタデータは保持されず、現在の DDL ステートメントの実行中にのみ適用されます。  再開可能ではそのため、= ON 句でアップロードを有効にする明示的に指定する必要があります。
-  2 つの異なる MAX_DURATION オプションに注意してください。 Low_priority_lock_wait に関連する 1 つと、再開可能に関連する他のオプションを = です。
   -  再開可能 MAX_DURATION オプションはサポートされて = ON オプションまたは**low_priority_lock_wait**引数オプションです。 
   -  再開可能なオプションの MAX_DURATION には、インデックスの再構築される時間間隔を指定します。 この時間が使用されるインデックスの再構築が一時停止するか、またはの実行を完了します。 ユーザーは、一時停止しているインデックスの再構築を再開できる場合を決定します。 **時間**MAX_DURATION を分単位でと低 0 分より大きいか等しい 1 週間 (7 * 24 * 60 = 10080 分) である必要があります。 インデックス操作に長い一時停止を持つは、特定のテーブルで DML パフォーマンスに影響を与える可能性だけでなくどちらもデータベースのディスク容量のインデックスを作成元と新しく作成されたものが必要なは、ディスク スペースと DML 操作中に更新する必要があります。 MAX_DURATION オプションを省略すると、その完了するまで、またはエラーが発生するまで、インデックス操作は続行されます。 
-   \<Low_priority_lock_wait > 引数オプションでは、SCH-M ロックでブロックされたときに、インデックス操作を続行する方法を決定することができます。
 
-  同じパラメーターを持つ元の ALTER INDEX REBUILD ステートメントを再実行すると、一時停止中のインデックス再構築操作が再開されます。 インデックスの再開の ALTER ステートメントを実行しても一時停止中のインデックス再構築の操作を再開できます。
-  SORT_IN_TEMPDB = ON 再開可能なインデックスのオプションがサポートされていません 
-  再開可能で、DDL コマンド = ON は、明示的なトランザクションの内部実行ことはできません (の一部にすることはできません begin tran. コミット ブロック) します。
-  一時停止されているインデックス操作だけでは、再開します。
-  一時停止しているインデックス操作を再開するときに新しい値の MAXDOP 値を変更できます。  MAXDOP が指定されていない場合は最後の MAXDOP 値を取得、一時停止しているインデックス操作を再開するとき。 MAXDOP オプションが指定されていないすべてのインデックス再構築操作の場合は、既定値を取得します。
- インデックス操作をすぐに一時停止、継続的なコマンド (CTRL + C) を停止するまたは ALTER INDEX を一時停止コマンドまたは KILL を実行することができます*session_id*コマンド。 コマンドが一時停止された後再開できるように再開オプションを使用します。
-  中止コマンドが、元のインデックス再構築がホストされているし、インデックス操作を中止するセッションを強制終了します。  
-  追加のリソースには必要ありませんを除き、再開可能なインデックスの再構築です。
   -    インデックスを一時停止されているときに時間も含めて、構築されるインデックスを保持するために必要な追加領域
   -    すべての DDL 変更を防止 DDL の状態
-  インデックス一時停止フェーズ中に、ゴーストのクリーンアップが実行されているが、インデックスの実行中に一時停止されます。   
再開可能なインデックス再構築操作の次の機能が無効になっています
   -    再開可能では無効になっているインデックスを再構築はサポートされていない = ON
   -    ALTER INDEX REBUILD の ALL コマンド
   -    インデックスの再構築を使用して ALTER TABLE  
   -    DDL コマンドを"RESUMEABLE = ON"明示的なトランザクション内で実行することはできません (の一部にすることはできません begin tran. コミット ブロック)
   -    キー列としてインデックスには、計算をまたはタイムスタンプ列を再構築します。
-   インデックスの再構築がこの操作の開始中に SCH-M ロックを必要とベース テーブルに LOB 列の再開可能なクラスター化が含まれている場合に
   -    SORT_IN_TEMPDB = ON 再開可能なインデックスのオプションがサポートされていません 

> [!NOTE]
> DDL コマンドは、完了、一時停止か、失敗するまで実行されます。 コマンドが一時停止、場合に、操作が一時停止していると、インデックスの作成が完了しなかったことを示すエラーが発行されます。 現在のインデックスの状態の詳細についてから取得できます[sys.index_resumable_operations](../../relational-databases/system-catalog-views/sys-index-resumable-operations.md)です。 として前に、障害が発生した場合、エラーが発行されますもします。 

 詳しくは、「 [Perform Index Operations Online](../../relational-databases/indexes/perform-index-operations-online.md)」をご覧ください。  
  
 ### <a name="waitatlowpriority-with-online-index-operations"></a>オンライン インデックス操作と WAIT_AT_LOW_PRIORITY  
  
 オンライン インデックス再構築の DDL ステートメントを実行するには、特定のテーブルで実行されているすべてのアクティブなブロック トランザクションが完了する必要があります。 オンライン インデックス再構築を実行すると、このテーブルに対する実行の開始が準備できているすべての新しいトランザクションがブロックされます。 オンライン インデックス再構築のロックの期間は非常に短いですが、特定のテーブルに対して開かれているすべてのトランザクションの完了を待機し、新しいトランザクションの開始をブロックすることで、スループットに大きな影響を与える場合があり、ワークロードの速度低下またはタイムアウトを引き起こしたり、基になるテーブルへのアクセスが大幅に制限されたりします。 **WAIT_AT_LOW_PRIORITY**オプションでは、DBA がオンラインのインデックスが再構築、3 つのオプションのいずれかを選択することができますに必要な S ロックおよび SCH-M ロックを管理します。 待機時間の実行中に、すべての 3 つのケースで ( `(MAX_DURATION = n [minutes])` )、ブロッキング アクティビティがない、待機せず、オンライン インデックス再構築をすぐに実行および DDL ステートメントが完了します。  
  
## <a name="spatial-index-restrictions"></a>空間インデックスに関する制限  
 空間インデックスを再構築するとき、基になるユーザー テーブルはインデックス操作の間使用できなくなります。これは、空間インデックスがスキーマ ロックを保持するためです。  
  
 ユーザー テーブルの PRIMARY KEY 制約は、そのテーブルの列に空間インデックスが定義されているときは変更できません。 PRIMARY KEY 制約を変更する場合は、初めにテーブルのすべての空間インデックスを削除してください。 PRIMARY KEY 制約を変更した後、各空間インデックスを再作成できます。  
  
 単一のパーティションの再構築操作では、空間インデックスを指定できません。 ただし、パーティションの完全な再構築では、空間インデックスを指定できます。  
  
 BOUNDING_BOX や GRID など、空間インデックス固有のオプションを変更するには、DROP_EXISTING = ON を指定する CREATE SPATIAL INDEX ステートメントを使用するか、空間インデックスを削除して新しく作成します。 例については、「 [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-spatial-index-transact-sql.md)」の「解説」をご覧ください。  
  
## <a name="data-compression"></a>Data Compression  
 データ圧縮の詳細については、「 [データの圧縮](../../relational-databases/data-compression/data-compression.md)」を参照してください。  
  
 影響を評価するページと行の圧縮を変更するは、テーブル、インデックス、またはパーティションを使用して、 [sp_estimate_data_compression_savings](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md)ストアド プロシージャです。  
  
パーティション インデックスには次の制限が適用されます。  
  
-   使用すると`ALTER INDEX ALL ...`、圧縮設定の 1 つのパーティション テーブルに変更することはできません固定されていないインデックスです。  
-   The ALTER INDEX \<index> ...REBUILD PARTITION ... 構文は、そのインデックスの指定のパーティションを再構築します。  
-   The ALTER INDEX \<index> ...REBUILD WITH ... 構文は、そのインデックスのすべてのパーティションを再構築します。  
  
## <a name="statistics"></a>統計  
 実行すると**ALTER INDEX ALL しています.** テーブルにのみ、統計情報に関連付けられたインデックスが更新されます。 (インデックスではなく) テーブルで作成されている自動または手動の統計は更新されません。  
  
## <a name="permissions"></a>権限  
 ALTER INDEX を実行するには、少なくとも、テーブルまたはビューの ALTER 権限が必要です。  
  
## <a name="version-notes"></a>バージョンのメモ  
  
-  [!INCLUDE[ssSDS](../../includes/sssds-md.md)]ファイル グループと filestream オプションを使用しません。  
-  列ストア インデックスがより前のバージョンをご利用いただけません[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]です。 
-  再開可能なインデックス操作は、使用可能な開始[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]と[!INCLUDE[ssSDS](../../includes/sssds-md.md)]   
  
## <a name="basic-syntax-example"></a>基本構文例:   
  
```sql 
ALTER INDEX index1 ON table1 REBUILD;  
  
ALTER INDEX ALL ON table1 REBUILD;  
  
ALTER INDEX ALL ON dbo.table1 REBUILD;  
```

## <a name="examples-columnstore-indexes"></a>例: 列ストア インデックス  
 これらの例は、列ストア インデックスに適用されます。  
  
### <a name="a-reorganize-demo"></a>A. デモを再構成します。  
 この例では、ALTER INDEX REORGANIZE コマンドの動作方法を示します。  複数の行グループと REORGANIZE が行グループを結合する方法を次に示しますあるテーブルを作成します。  
  
```sql  
-- Create a database   
CREATE DATABASE [ columnstore ];  
GO  
  
-- Create a rowstore staging table  
CREATE TABLE [ staging ] (  
     AccountKey              int NOT NULL,  
     AccountDescription      nvarchar (50),  
     AccountType             nvarchar(50),  
     AccountCodeAlternateKey     int  
     )  
  
-- Insert 10 million rows into the staging table.   
DECLARE @loop int  
DECLARE @AccountDescription varchar(50)  
DECLARE @AccountKey int  
DECLARE @AccountType varchar(50)  
DECLARE @AccountCode int  
  
SELECT @loop = 0  
BEGIN TRAN  
    WHILE (@loop < 300000)   
      BEGIN  
        SELECT @AccountKey = CAST (RAND()*10000000 as int);  
        SELECT @AccountDescription = 'accountdesc ' + CONVERT(varchar(20), @AccountKey);  
        SELECT @AccountType = 'AccountType ' + CONVERT(varchar(20), @AccountKey);  
        SELECT @AccountCode =  CAST (RAND()*10000000 as int);  
  
        INSERT INTO  staging VALUES (@AccountKey, @AccountDescription, @AccountType, @AccountCode);  
  
        SELECT @loop = @loop + 1;  
    END  
COMMIT  
  
-- Create a table for the clustered columnstore index  
  
CREATE TABLE cci_target (  
     AccountKey              int NOT NULL,  
     AccountDescription      nvarchar (50),  
     AccountType             nvarchar(50),  
     AccountCodeAlternateKey int  
     )  
  
-- Convert the table to a clustered columnstore index named inxcci_cci_target;  
```sql
CREATE CLUSTERED COLUMNSTORE INDEX idxcci_cci_target ON cci_target;  
```  
  
 TABLOCK オプションを使用すると、並列で行を挿入できます。 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]TABLOCK を使用する場合、INSERT INTO 操作が並列で実行できます。  
  
```sql  
INSERT INTO cci_target WITH (TABLOCK) 
SELECT TOP 300000 * FROM staging;  
```  
  
 開いているデルタ行グループの数を表示するには、このコマンドを実行します。 行グループの数は、並列処理の次数に依存します。  
  
```sql  
SELECT *   
FROM sys.dm_db_column_store_row_group_physical_stats   
WHERE object_id  = object_id('cci_target');  
```  
  
 すべての CLOSED と OPEN 行グループを列ストアに強制的にこのコマンドを実行します。  
  
```sql  
ALTER INDEX idxcci_cci_target ON cci_target REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
```  
  
 このコマンドを再実行して、小さな行グループが圧縮された行グループの 1 つにマージされたことが表示されます。  
  
```sql  
ALTER INDEX idxcci_cci_target ON cci_target REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
```  
  
### <a name="b-compress-closed-delta-rowgroups-into-the-columnstore"></a>B. 閉じられたデルタ行グループを列ストアに圧縮します。  
 この例は、REORGANIZE オプションを圧縮閉じられたデルタ行グループはそれぞれ、列ストアに圧縮された行グループとします。   これは必要ありませんが、組ムーバーが十分に高速の CLOSED 行グループを圧縮しない場合に便利です。  
  
```sql  
-- Uses AdventureWorksDW  
-- REORGANIZE all partitions  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE;  
  
-- REORGANIZE a specific partition  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE PARTITION = 0;  
```  
  
### <a name="c-compress-all-open-and-closed-delta-rowgroups-into-the-columnstore"></a>C. 列ストアにすべて開くと終了のデルタ行グループを圧縮します。  
 **適用されます:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]) と[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 
  
 コマンドを再編成 (COMPRESS_ALL_ROW_GROUPS = ON) compreses が各を開き、圧縮された行グループと列ストアにデルタ行グループを終了します。 これは、デルタストアを空にして、強制的にすべての行を列ストアに圧縮します。 これは、これらの操作が 1 つまたは複数のデルタストアの行を格納するために、多くの挿入操作を実行した後に特に便利です。  
  
 REORGANIZE は、行の最大数までの行グループを入力する行グループを結合\<1,024,576 を = です。 そのため、オープンとクローズのすべての行グループを圧縮するときにするために終了しない圧縮された行グループのみに、いくつかの行を持つ多数のです。 圧縮サイズを小さくし、クエリのパフォーマンスを向上させるできるだけにいっぱいになっている行グループができます。  
  
```sql  
-- Uses AdventureWorksDW2016  
-- Move all OPEN and CLOSED delta rowgroups into the columnstore.  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
  
-- For a specific partition, move all OPEN AND CLOSED delta rowgroups into the columnstore  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE PARTITION = 0 WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
```  
  
### <a name="d-defragment-a-columnstore-index-online"></a>D. 列ストア インデックスをオンラインの最適化します。  
 適用されません。[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]と[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]です。  
  
 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]REORGANIZE が列ストアにデルタ行グループを圧縮以上です。 また、オンラインでの最適化を実行します。 最初に、行グループ内の行の 10% 以上が削除されたときに物理的に削除された行を削除することで、列ストアのサイズが軽減されます。  次を 1,024,576 行の行グループあたりの最大値持つ大規模な行グループを形成する行グループを結合します。  すべての行グループを変更しても再圧縮します。  
  
> [!NOTE]
> 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]、列ストア インデックスを再構築する必要はなくなりましたほとんどの状況で REORGANIZE は物理的に削除された行を削除し、行グループのマージ以降。 COMPRESS_ALL_ROW_GROUPS オプションは、以前、再構築でのみ実行でしたが、列ストアにすべて開くまたは CLOSED のデルタ行グループを強制します。 REORGANIZE はオンラインであり、操作が発生すると、クエリを継続できるようにバック グラウンドで発生します。  
  
```sql  
-- Uses AdventureWorks  
-- Defragment by physically removing rows that have been logically deleted from the table, and merging rowgroups.  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REORGANIZE;  
```  
  
### <a name="e-rebuild-a-clustered-columnstore-index-offline"></a>E. オフラインのクラスター化列ストア インデックスを再構築します。  
適用されます: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)])   
  
> [!TIP]
> 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]し、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、ALTER INDEX REBUILD の代わりに ALTER INDEX REORGANIZE を使用することをお勧めします。  
  
> [!NOTE]
> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]と[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]REORGANIZE は、列ストアに CLOSED 行グループの圧縮にのみ使用します。 唯一の方法を最適化操作を実行して、列ストアに強制的にすべてのデルタ行グループには、インデックスを再構築します。  
  
 この例では、クラスター化列ストア インデックスを再構築し、すべてのデルタ行グループ、列ストアに強制的に移動する方法を示します。 この最初の手順では、クラスター化列ストア インデックスを含む FactInternetSales2 テーブルを準備し、最初の 4 つの列にデータを挿入します。  
  
```sql  
-- Uses AdventureWorksDW  
  
CREATE TABLE dbo.FactInternetSales2 (  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
  
CREATE CLUSTERED COLUMNSTORE INDEX cci_FactInternetSales2  
ON dbo.FactInternetSales2;  
  
INSERT INTO dbo.FactInternetSales2  
SELECT ProductKey, OrderDateKey, DueDateKey, ShipDateKey  
FROM dbo.FactInternetSales;  
  
SELECT * FROM sys.column_store_row_groups;  
```  
  
 1 つ開いている行グループ、つまり、結果を表示する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は多くの行のデータを列ストアに移動して、行グループを終了する前に追加するまで待機します。 次のステートメントは、列ストアに強制的にすべての行をクラスター化列ストア インデックスを再構築します。  
  
```sql  
ALTER INDEX cci_FactInternetSales2 ON FactInternetSales2 REBUILD;  
SELECT * FROM sys.column_store_row_groups;  
```  
  
 SELECT ステートメントの結果は行グループが圧縮されていることを示しています。つまり、行グループの列セグメントは圧縮され、列ストアに格納されます。  
  
### <a name="f-rebuild-a-partition-of-a-clustered-columnstore-index-offline"></a>F. オフラインのクラスター化列ストア インデックスのパーティションを再構築します。  
 **適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)])  
 
 大規模なクラスター化列ストア インデックスのパーティションを再構築するには、パーティション オプションで ALTER INDEX REBUILD を使用します。 この例では、12 のパーティションが再構築します。 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]REORGANIZE と再構築を置き換えることをお勧めします。  
  
```sql  
ALTER INDEX cci_fact3   
ON fact3  
REBUILD PARTITION = 12;  
```  
  
### <a name="g-change-a-clustered-columstore-index-to-use-archival-compression"></a>G. 保存用圧縮を使用する columstore のクラスター化インデックスを変更します。  
 適用されません。[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
 COLUMNSTORE_ARCHIVE データ圧縮オプションを使用して、さらに、クラスター化列ストア インデックスのサイズを小さくことができます。 これは、安価なストレージを保持する以前のデータに対する実用性です。 のみを使用してこれが多くの場合、以降にアクセスされないデータを圧縮解除が通常の列ストア圧縮でよりも遅いことをお勧めします。  
  
 次の例では、保存用圧縮を使用するクラスター化列ストア インデックスを再構築し、次に保管用圧縮を削除する方法を示します。 最終結果では、列ストア圧縮のみを使用します。  
  
```sql  
--Prepare the example by creating a table with a clustered columnstore index.  
CREATE TABLE SimpleTable (  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL  
);  
  
CREATE CLUSTERED INDEX cci_SimpleTable ON SimpleTable (ProductKey);  
  
CREATE CLUSTERED COLUMNSTORE INDEX cci_SimpleTable  
ON SimpleTable  
WITH (DROP_EXISTING = ON);  
  
--Compress the table further by using archival compression.  
ALTER INDEX cci_SimpleTable ON SimpleTable  
REBUILD  
WITH (DATA_COMPRESSION = COLUMNSTORE_ARCHIVE);  
  
--Remove the archive compression and only use columnstore compression.  
ALTER INDEX cci_SimpleTable ON SimpleTable  
REBUILD  
WITH (DATA_COMPRESSION = COLUMNSTORE);  
GO  
```  
  
## <a name="examples-rowstore-indexes"></a>例: 行ストア インデックス  
  
### <a name="a-rebuilding-an-index"></a>A. インデックスを再構築する  
 次の例で、単一のインデックスを再構築、`Employee`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```sql  
ALTER INDEX PK_Employee_EmployeeID ON HumanResources.Employee REBUILD;  
```  
  
### <a name="b-rebuilding-all-indexes-on-a-table-and-specifying-options"></a>B. テーブルですべてのインデックスを再構築し、オプションを指定する  
 次の例は、キーワードを指定`ALL`です。 これにより、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースの Production.Product テーブルに関連付けられたすべてのインデックスが再構築されます。 3 つのオプションが指定されます。  
  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
```sql  
ALTER INDEX ALL ON Production.Product  
REBUILD WITH (FILLFACTOR = 80, SORT_IN_TEMPDB = ON, STATISTICS_NORECOMPUTE = ON);  
```  
  
次の例は、優先度の低いロック オプションを含めて ONLINE オプションを追加し、行の圧縮オプションを追加します。  
  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
```sql  
ALTER INDEX ALL ON Production.Product  
REBUILD WITH   
(  
    FILLFACTOR = 80,   
    SORT_IN_TEMPDB = ON,  
    STATISTICS_NORECOMPUTE = ON,  
    ONLINE = ON ( WAIT_AT_LOW_PRIORITY ( MAX_DURATION = 4 MINUTES, ABORT_AFTER_WAIT = BLOCKERS ) ),   
    DATA_COMPRESSION = ROW  
);  
```  
  
### <a name="c-reorganizing-an-index-with-lob-compaction"></a>C. LOB 圧縮を行いインデックスを再構成する  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースの単一のクラスター化インデックスを再構成します。 インデックスではリーフ レベルに LOB データ型が含まれるので、このステートメントではラージ オブジェクト データを含むすべてのページが圧縮されます。 既定値が ON であるため、WITH (LOB_COMPACTION) オプションの指定は必須ではありません。  
  
```sql  
ALTER INDEX PK_ProductPhoto_ProductPhotoID ON Production.ProductPhoto REORGANIZE WITH (LOB_COMPACTION);  
```  
  
### <a name="d-setting-options-on-an-index"></a>D. インデックスにオプションを設定する  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースのインデックス `AK_SalesOrderHeader_SalesOrderNumber` にいくつかのオプションを設定します。  
  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
```sql  
ALTER INDEX AK_SalesOrderHeader_SalesOrderNumber ON  
    Sales.SalesOrderHeader  
SET (  
    STATISTICS_NORECOMPUTE = ON,  
    IGNORE_DUP_KEY = ON,  
    ALLOW_PAGE_LOCKS = ON  
    ) ;  
GO
```  
  
### <a name="e-disabling-an-index"></a>E. インデックスを無効にする  
 次の例は、非クラスター化インデックスを無効になります、`Employee`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```sql  
ALTER INDEX IX_Employee_ManagerID ON HumanResources.Employee DISABLE;
```  
  
### <a name="f-disabling-constraints"></a>F. 制約を無効化する  
 次の例で主キー インデックスを無効にすると、PRIMARY KEY 制約を無効になります、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。 基になるテーブルに対する FOREIGN KEY 制約は自動的に無効になり、警告メッセージが表示されます。  
  
```sql  
ALTER INDEX PK_Department_DepartmentID ON HumanResources.Department DISABLE;  
```  
  
結果セットでは、次の警告メッセージが返されます。  
  
```  
Warning: Foreign key 'FK_EmployeeDepartmentHistory_Department_DepartmentID'  
on table 'EmployeeDepartmentHistory' referencing table 'Department'  
was disabled as a result of disabling the index 'PK_Department_DepartmentID'.
```  
  
### <a name="g-enabling-constraints"></a>G. 制約を有効にする  
 次の例では、例 F で無効にした PRIMARY KEY および FOREIGN KEY 制約を有効にします。  
  
PRIMARY KEY 制約は、PRIMARY KEY インデックスを再構築することにより有効にできます。  
  
```sql  
ALTER INDEX PK_Department_DepartmentID ON HumanResources.Department REBUILD;  
```  
  
次に FOREIGN KEY 制約を有効にします。  
  
```sql  
ALTER TABLE HumanResources.EmployeeDepartmentHistory  
CHECK CONSTRAINT FK_EmployeeDepartmentHistory_Department_DepartmentID;  
GO  
```  
  
### <a name="h-rebuilding-a-partitioned-index"></a>H. パーティション インデックスを再構築する  
 次の例には、1 つのパーティション、パーティション番号が再構築`5`、パーティション インデックスの`IX_TransactionHistory_TransactionDate`で、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。 パーティション 5 はオンラインで再構築され、優先度の低いロックの 10 分間の待機時間が、インデックスの再構築操作によって取得された各ロックに個別に適用されます。 この期間中に、インデックスの再構築を完了するためのロックを取得できない場合は、再構築操作のステートメントが中止されます。  
  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) および[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
```sql  
-- Verify the partitioned indexes.  
SELECT *  
FROM sys.dm_db_index_physical_stats (DB_ID(),OBJECT_ID(N'Production.TransactionHistory'), NULL , NULL, NULL);  
GO  
--Rebuild only partition 5.  
ALTER INDEX IX_TransactionHistory_TransactionDate  
ON Production.TransactionHistory  
REBUILD Partition = 5   
   WITH (ONLINE = ON (WAIT_AT_LOW_PRIORITY (MAX_DURATION = 10 minutes, ABORT_AFTER_WAIT = SELF)));  
GO  
```  
  
### <a name="i-changing-the-compression-setting-of-an-index"></a>I. インデックスの圧縮設定を変更する  
 次の例では、非パーティション行ストア テーブルのインデックスを再構築します。  
  
```sql
ALTER INDEX IX_INDEX1   
ON T1  
REBUILD   
WITH (DATA_COMPRESSION = PAGE);  
GO  
```  
  
追加のデータ圧縮例については、次を参照してください。[データ圧縮](../../relational-databases/data-compression/data-compression.md)です。  
 
### <a name="j-online-resumable-index-rebuild"></a>J. 再開可能なオンラインのインデックス再構築

**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]) と[!INCLUDE[ssSDS](../../includes/sssds-md.md)]   

 次の例では、再開可能なオンラインのインデックス再構築を使用する方法を示します。 

1. MAXDOP で再開可能な操作として、オンライン インデックス再構築を実行 = 1 です。

   ```sql
   ALTER INDEX test_idx on test_table REBUILD WITH (ONLINE=ON, MAXDOP=1, RESUMABLE=ON) ;
   ```

2. 同じを実行するコマンドをもう一度 (上記参照)、インデックス操作が一時停止された後に自動的に再開されますインデックス再構築操作。

3. 240 分に設定された MAX_DURATION 再開可能な操作として、オンライン インデックス再構築を実行します。

   ```sql
   ALTER INDEX test_idx on test_table REBUILD WITH (ONLINE=ON, RESUMABLE=ON, MAX_DURATION=240) ; 
   ```
4. 再開可能な実行中のオンライン インデックス再構築を一時停止します。

   ```sql
   ALTER INDEX test_idx on test_table PAUSE ;
   ```   
5. MAXDOP の新しい値を指定する再開操作が 4 に設定するように実行されたインデックスの再構築のオンラインのインデックスの再構築を再開します。

   ```sql
   ALTER INDEX test_idx on test_table RESUME WITH (MAXDOP=4) ;
   ```
6. インデックスのオンライン再構築となり、再開可能として実行されたオンライン インデックス再構築操作を再開します。 MAXDOP は 2 に設定、240 分、10 分間、ロック待機でブロックされている、インデックスの場合、resmumable として実行されているインデックスの実行時間を設定し、その後、すべてのブロックを強制終了します。 

   ```sql
      ALTER INDEX test_idx on test_table  
         RESUME WITH (MAXDOP=2, MAX_DURATION= 240 MINUTES, 
         WAIT_AT_LOW_PRIORITY (MAX_DURATION=10, ABORT_AFTER_WAIT=BLOCKERS)) ;
   ```      
7. 実行中または一時停止中は再開可能なインデックス再構築操作を中止します。

   ```sql
   ALTER INDEX test_idx on test_table ABORT ;
   ``` 
  
## <a name="see-also"></a>参照  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [空間インデックス &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-spatial-index-transact-sql.md)   
 [XML インデックス &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-xml-index-transact-sql.md)   
 [DROP INDEX &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-index-transact-sql.md)   
 [インデックスと制約を無効にします。](../../relational-databases/indexes/disable-indexes-and-constraints.md)   
 [XML インデックス &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)   
 [オンラインのインデックス操作を実行します。](../../relational-databases/indexes/perform-index-operations-online.md)   
 [Reorganize し、インデックスを再構築](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
