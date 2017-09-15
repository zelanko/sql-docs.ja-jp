---
title: "index_option (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- index_option
ms.assetid: 8a14f12d-2fbf-4036-b8b2-8db3354e0eb7
caps.latest.revision: 68
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: e7563f9fe992dcf4f9308cccbf11f6310b7925a7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/08/2017

---
# <a name="alter-table-indexoption-transact-sql"></a>ALTER TABLE index_option (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  使用して作成される制約定義の一部であるインデックスに適用できるオプションのセットを示す[ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
{   
    PAD_INDEX = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | IGNORE_DUP_KEY = { ON | OFF }  
  | STATISTICS_NORECOMPUTE = { ON | OFF }  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | SORT_IN_TEMPDB = { ON | OFF }   
  | ONLINE = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
  | DATA_COMPRESSION = { NONE |ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
      [ ON PARTITIONS ( { <partition_number_expression> | <range> }   
      [ , ...n ] ) ]  
  | ONLINE = { ON [ ( <low_priority_lock_wait> ) ] | OFF }  
}  
  
<range> ::=   
<partition_number_expression> TO <partition_number_expression>  
  
<single_partition_rebuild__option> ::=  
{  
    SORT_IN_TEMPDB = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
  | DATA_COMPRESSION = {NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE } }  
  | ONLINE = { ON [ ( <low_priority_lock_wait> ) ] | OFF }  
}  
  
<low_priority_lock_wait>::=  
{  
    WAIT_AT_LOW_PRIORITY ( MAX_DURATION = <time> [ MINUTES ] ,   
                           ABORT_AFTER_WAIT = { NONE | SELF | BLOCKERS } )   
}  
```  
  
## <a name="arguments"></a>引数  
 PAD_INDEX ** = ** {ON |**OFF** }  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 インデックスの埋め込みを指定します。 既定値は OFF です。  
  
 ON  
 FILLFACTOR で指定される空き領域のパーセンテージが、インデックスの中間レベルのページに適用されます。  
  
 OFF または*fillfactor*が指定されていません  
 中間レベル ページは、中間ページの一連のキーを考慮しつつ、インデックスが持つことのできる最大サイズの行が少なくとも 1 つ格納できる領域を残して、ほぼ容量いっぱいに使用されます。  
  
 FILLFACTOR ** = ** *fillfactor*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 どの程度を示すパーセンテージを指定します、[!INCLUDE[ssDE](../../includes/ssde-md.md)]インデックスの作成または変更時に各インデックス ページのリーフ レベルを作成する必要があります。 1 ～ 100 の整数値を指定する必要があります。 既定値は 0 です。  
  
> [!NOTE]  
>  FILL FACTOR 値 0 と 100 は、すべての面でまったく同じ結果になります。  
  
 IGNORE_DUP_KEY ** = ** {ON |**OFF** }  
 挿入操作で、一意のインデックスに重複するキー値を挿入しようとした場合のエラー応答を指定します。 IGNORE_DUP_KEY オプションは、インデックスが作成または再構築された後の挿入操作のみに適用されます。 オプションも何も起こりませんの実行時に[CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)、 [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)、または[更新](../../t-sql/queries/update-transact-sql.md)です。 既定値は OFF です。  
  
 ON  
 警告メッセージは、重複するキー値が一意のインデックスに挿入するときに発生します。 一意性制約に違反する行だけが失敗します。  
  
 OFF  
 エラー メッセージは、重複するキー値が一意のインデックスに挿入するときに発生します。 INSERT 操作全体がロールバックされます。  
  
 ビューに作成されたインデックス、一意でないインデックス、XML インデックス、空間インデックス、およびフィルター選択されたインデックスの IGNORE_DUP_KEY を ON に設定できません。  
  
 IGNORE_DUP_KEY を表示する[sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)です。  
  
 旧バージョンと互換性のある構文では、WITH IGNORE_DUP_KEY は WITH IGNORE_DUP_KEY = ON と同じです。  
  
 STATISTICS_NORECOMPUTE ** = ** {ON |**OFF** }  
 統計を再計算するかどうかを指定します。 既定値は OFF です。  
  
 ON  
 古い統計情報は、自動的には再計算されません。  
  
 OFF  
 自動統計更新が有効です。  
  
 ALLOW_ROW_LOCKS ** = ** { **ON** |オフ}  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 行ロックを許可するかどうかを指定します。 既定値は ON です。  
  
 ON  
 インデックスにアクセスするとき、行ロックが許可されます。 いつ行ロックを使用するかは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]によって決定されます。  
  
 OFF  
 行ロックは使用されません。  
  
 ALLOW_PAGE_LOCKS ** = ** { **ON** |オフ}  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ページ ロックを許可するかどうかを指定します。 既定値は ON です。  
  
 ON  
 ページにアクセスするとき、行ロックが許可されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]ページ ロックを使用する場合を決定します。  
  
 OFF  
 ページ ロックは使用されません。  
  
 SORT_IN_TEMPDB ** = ** {ON |**OFF** }  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 並べ替え結果を格納するかどうかを示す**tempdb**です。 既定値は OFF です。  
  
 ON  
 インデックスの構築に使用される並べ替えの中間結果が格納されている**tempdb**です。 場合、インデックスの作成に必要な時間が削減**tempdb**が別のユーザー データベースのディスク セットにします。 インデックスの構築中に使用されるディスク領域のサイズは増加します。  
  
 OFF  
 中間の並べ替え結果はインデックスと同じデータベースに格納されます。  
  
 オンライン** = ** {ON |**OFF** }  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 インデックス操作時に、基になるテーブルや関連するインデックスをクエリやデータ変更で使用できるかどうかを指定します。 既定値は OFF です。 REBUILD は ONLINE 操作として実行できます。  
  
> [!NOTE]  
>  一意な非クラスター化インデックスはオンラインで作成できません。 これには、UNIQUE 制約または PRIMARY KEY 制約によって作成されるインデックスが含まれます。  
  
 ON  
 長期のテーブル ロックは、インデックス操作の間は保持されません。 インデックス操作の主なフェーズでは、基になるテーブル、インテント共有 (IS) ロックのみが保持されます。 これにより、基になるテーブルやインデックスに対するクエリや更新を続行できます。 操作の開始時、非常に短い時間ですが、ソース オブジェクトの共有 (S) ロックが保持されます。 操作の終了時、短い時間ですが、非クラクタ化インデックスが作成される場合は、ソース オブジェクト上で共有 (S) ロックの取得が行われます。また、クラスター化インデックスがオンラインで作成または削除され、クラスター化または非クラスター化インデックスが再構築される場合は、SCH-M (スキーマ修正) ロックが取得されます。 オンライン インデックス ロックは短いメタデータ ロックですが、特に Sch-M ロックは、このテーブルに対するすべてのブロックしているトランザクションの完了を待機する必要があります。 待機中、Sch-M ロックは、同じテーブルにアクセスするためにこのロックの後に待機している他のすべてのトランザクションをブロックします。 インデックスがローカルの一時テーブルに作成される場合、ONLINE は ON にできません。  
  
> [!NOTE]  
>  オンライン インデックス再構築が設定できる、 *low_priority_lock_wait*オプションのこのセクションで後述します。 *low_priority_lock_wait*オンライン インデックス再構築中に S および SCH-M ロックの優先順位を管理します。  
  
 OFF  
 テーブル ロックは、インデックス操作の間適用されます。 このため、操作中は、すべてのユーザーは基になるテーブルにアクセスできません。 クラスター化インデックスを作成、再構築、または削除するオフライン インデックス操作や、非クラスター化インデックスを再構築または削除するオフライン インデックス操作では、テーブルのスキーマ修正 (Sch-M) ロックが取得されます。 このため、操作中は、すべてのユーザーは基になるテーブルにアクセスできません。 非クラスター化インデックスを作成するオフライン インデックス操作では、テーブルの共有 (S) ロックが取得されます。 この場合は、基になるテーブルに対して更新は許可されませんが、SELECT ステートメントなどの読み取り操作は許可されます。  
  
 詳細については、次を参照してください。[オンライン インデックス操作しくみ](../../relational-databases/indexes/how-online-index-operations-work.md)です。  
  
> [!NOTE]  
>  オンラインでのインデックス操作は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
 MAXDOP ** = ** *max_degree_of_parallelism*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 上書き、**並列処理の次数の最大**インデックス操作の実行中の構成オプション。 詳細については、「 [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)」を参照してください。 並列プランの実行で使用されるプロセッサ数を制限するには、MAXDOP を使用します。 最大数は 64 プロセッサです。  
  
 *max_degree_of_parallelism*を指定できます。  
  
 - 1 - 並列プランの生成を抑制します。  
 - \>1 - 指定した数に、並列インデックス操作で使用されるプロセッサの最大数を制限します。  
 - 0 (既定) - 実際のプロセッサ数か、現在のシステム ワークロードに基づいて数が少ない。  
  
 詳細については、「 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)」を参照してください。  
  
> [!NOTE]  
>  並列インデックス操作はすべてのエディションで使用できない[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
 DATA_COMPRESSION  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 指定したテーブル、パーティション番号、またはパーティション範囲に、データ圧縮オプションを指定します。 次のオプションがあります。  
  
 なし  
 テーブルまたは指定したパーティションが圧縮されません。 行ストア テーブルにのみ適用され、列ストア テーブルには適用されません。  
  
 ROW  
 行の圧縮を使用して、テーブルまたは指定したパーティションが圧縮されます。 行ストア テーブルにのみ適用され、列ストア テーブルには適用されません。  
  
 PAGE  
 ページの圧縮を使用して、テーブルまたは指定したパーティションが圧縮されます。 行ストア テーブルにのみ適用され、列ストア テーブルには適用されません。  
  
 COLUMNSTORE  
 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 列ストア テーブルにのみ適用されます。 COLUMNSTORE は、COLUMNSTORE_ARCHIVE オプションで圧縮されたパーティションを解凍するように指定します。 データを復元すると、列ストア インデックスは、すべての列ストア テーブルに使用される列ストア圧縮で圧縮するに続行します。  
  
 COLUMNSTORE_ARCHIVE  
 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 クラスター化列ストア インデックスを使用して格納されているテーブルである、列ストア テーブルにのみ適用されます。 COLUMNSTORE_ARCHIVE をさらに小さいサイズに指定されたパーティションが圧縮されます。 これは、保存用や、ストレージの使用量を減らす必要があり、しかも保存と取得に時間をかける余裕があるその他の状況で使用できます。  
  
 圧縮の詳細については、次を参照してください。[データ圧縮](../../relational-databases/data-compression/data-compression.md)です。  
  
パーティションで**(** { \<partition_number_expression > |\<範囲 >}[ **,**...* n * ] **)** **対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。  
  
 DATA_COMPRESSION 設定を適用するパーティションを指定します。 テーブルがパーティション分割されていない場合、ON PARTITIONS 引数には、エラーが生成されます。 ON PARTITIONS 句が指定されていない場合は、パーティション テーブルのすべてのパーティションに DATA_COMPRESSION オプションが適用されます。  
  
\<partition_number_expression > 次のように指定することができます。  
  
-   数、パーティションをたとえば提供: ON PARTITIONS (2)。  
-   ON PARTITIONS (1, 5) などのように、複数のパーティションのパーティション番号をコンマで区切って指定します。  
-   ON PARTITIONS (2, 4, 6 TO 8) などのように、範囲と個別のパーティションの両方を指定します。  
  
\<範囲 > パーティション番号など、to で区切って指定できます: ON PARTITIONS (6 TO 8)。  
  
 さまざまなパーティションにさまざまな種類のデータ圧縮を設定するには、次のように DATA_COMPRESSION オプションを複数回指定します。  
  
```sql  
--For rowstore tables  
REBUILD WITH   
(  
DATA_COMPRESSION = NONE ON PARTITIONS (1),   
DATA_COMPRESSION = ROW ON PARTITIONS (2, 4, 6 TO 8),   
DATA_COMPRESSION = PAGE ON PARTITIONS (3, 5)  
)  
  
--For columnstore tables  
REBUILD WITH   
(  
DATA_COMPRESSION = COLUMNSTORE ON PARTITIONS (1, 3, 5),   
DATA_COMPRESSION = COLUMNSTORE_ARCHIVE ON PARTITIONS (2, 4, 6 TO 8)  
)  
```  
  
**\<single_partition_rebuild__option >**  
 ほとんどの場合、インデックスの再構築では、パーティション インデックスのすべてのパーティションを再構築します。 次のオプションを 1 つのパーティションに適用した場合は、すべてのパーティションの再構築は行われません。  
  
-   SORT_IN_TEMPDB  
-   MAXDOP  
-   DATA_COMPRESSION  
  
**low_priority_lock_wait**  
 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 A**スイッチ**またはオンライン インデックス再構築は、このテーブルに対するブロック操作がないとすぐに完了するとします。 *WAIT_AT_LOW_PRIORITY*ことを示す、**スイッチ**またはオンライン インデックス再構築操作が直ちに完了できない、待機しています。 操作では、他の操作を続行するための DDL ステートメントと競合するロックを保持する、優先度の低いロックを保持します。 省略すると、 **WAIT AT LOW PRIORITY**オプションに相当`WAIT_AT_LOW_PRIORITY ( MAX_DURATION = 0 minutes, ABORT_AFTER_WAIT = NONE)`です。  
  
MAX_DURATION =*時間*[**分**]  
 待機時間 (分単位で指定された整数値) を**スイッチ**DDL コマンドを実行するときに取得する必要があります、オンライン インデックス再構築のロックが待機するか。 スイッチまたはオンライン インデックス再構築の操作は、直ちに完了しようとします。 操作がブロックされている場合、 **MAX_DURATION**のいずれかの時間、 **ABORT_AFTER_WAIT**アクションを実行します。 **MAX_DURATION**時間は分、および、word では常に**分**を省略できます。  
  
ABORT_AFTER_WAIT = [**NONE** | **SELF** | **ブロッカー** }]  
 なし  
 引き続き、**スイッチ**またはオンラインのインデックス (通常の優先順位を使用して) ロックの優先順位を変更することがなく操作を再構築します。  
  
SELF  
 終了、**スイッチ**またはオンライン インデックス再構築の DDL 操作が操作を行わず、現在実行中です。  
  
BLOCKERS  
 現在の妨げとなるすべてのユーザー トランザクションを強制終了、**スイッチ**またはオンライン インデックス操作を続行するための DDL 操作を再構築します。  
 ブロックが必要です、 **ALTER ANY CONNECTION**権限です。  
  
## <a name="remarks"></a>解説  
 インデックス オプションの詳細については、次を参照してください。 [CREATE INDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [column_constraint & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-table-column-constraint-transact-sql.md)   
 [computed_column_definition & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-table-computed-column-definition-transact-sql.md)   
 [table_constraint & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-table-table-constraint-transact-sql.md)  
  
 

