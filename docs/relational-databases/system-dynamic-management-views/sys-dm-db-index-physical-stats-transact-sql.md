---
title: sys.dm_db_index_physical_stats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_index_physical_stats
- sys.dm_db_index_physical_stats_TSQL
- sys.dm_db_index_physical_stats
- dm_db_index_physical_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_index_physical_stats dynamic management function
- fragmentation [SQL Server]
ms.assetid: d294dd8e-82d5-4628-aa2d-e57702230613
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c6427f786de727f22c3dd74b0dcf91d63b36c4ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004869"
---
# <a name="sysdmdbindexphysicalstats-transact-sql"></a>sys.dm_db_index_physical_stats (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データと、指定したテーブルまたはビューのインデックスのサイズおよび断片化情報を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 インデックスの場合、各パーティションの B ツリーのレベルごとに 1 行のデータが返されます。 ヒープの場合、各パーティションの IN_ROW_DATA アロケーション ユニットごとに 1 行のデータが返されます。 ラージ オブジェクト (LOB) データ、各パーティションの LOB_DATA アロケーション ユニット 1 つの行が返されます。 テーブルに行オーバーフロー データが存在する場合、各パーティションの ROW_OVERFLOW_DATA アロケーション ユニットごとに 1 行のデータが返されます。 XVelocity メモリ最適化列ストア インデックスに関する情報は返されません。  
  
> [!IMPORTANT]
> 照会する場合は**sys.dm_db_index_physical_stats** Always On をホストするサーバー インスタンスで[読み取り可能セカンダリ レプリカ](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)、再実行のブロック問題が発生する可能性があります。 これは、この動的管理ビューが、指定したユーザー テーブルまたはビューで IS ロックを獲得することが原因です。IS ロックは、そのユーザー テーブルまたはビューの X ロックに関して REDO スレッドの要求をブロックする可能性があります。  
  
 **sys.dm_db_index_physical_stats**メモリ最適化インデックスに関する情報は返されません。 メモリ最適化インデックスの使用方法については、[sys.dm_db_xtp_index_stats & #40 を参照してください。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md)  
  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.dm_db_index_physical_stats (   
    { database_id | NULL | 0 | DEFAULT }  
  , { object_id | NULL | 0 | DEFAULT }  
  , { index_id | NULL | 0 | -1 | DEFAULT }  
  , { partition_number | NULL | 0 | DEFAULT }  
  , { mode | NULL | DEFAULT }  
)  
```  
  
## <a name="arguments"></a>引数  
 *database_id* | NULL | 0 | DEFAULT  
 データベースの ID です。 *database_id*は**smallint**します。 有効な入力値は、データベースの ID 番号、NULL、0、または DEFAULT です。 既定値は 0 です。 このコンテキストでは、NULL、0、および DEFAULT は同じ値になります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのすべてのデータベースに関する情報を返すには NULL を指定します。 NULL を指定する場合*database_id*の場合は NULL を指定することも必要があります。 *object_id*、 *index_id*、および*partition_number*します。  
  
 組み込み関数[DB_ID](../../t-sql/functions/db-id-transact-sql.md)を指定できます。 データベース名を指定しないで DB_ID を使用する場合、現在のデータベースの互換性レベルが 90 以上である必要があります。  
  
 *object_id* | NULL | 0 | DEFAULT  
 テーブルのオブジェクト id またはインデックス ビューをオンします。 *object_ID* は **int**です。  
  
 有効な入力値は、テーブルおよびビューの ID 番号、NULL、0、または DEFAULT です。 既定値は 0 です。 このコンテキストでは、NULL、0、および DEFAULT は同じ値になります。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]、有効な入力値は、service broker のキュー名、またはキューの内部テーブル名にも含まれます。 既定のパラメーターが適用されます (つまりすべてのオブジェクト、すべてのインデックスなど)、結果セット内のすべてのキューの断片化情報が含まれています。  
  
 NULL を指定すると、指定されたデータベース内にあるすべてのテーブルとビューに関する情報が返されます。 NULL を指定する場合*object_id*の場合は NULL を指定することも必要があります。 *index_id*と*partition_number*します。  
  
 *index_id* | 0 | NULL | -1 | DEFAULT  
 インデックスの ID です。 *index_id*は**int**します。場合、有効な値は 0、インデックスの ID 番号*object_id*ヒープ、NULL、-1、または DEFAULT です。 既定では-1 です。 NULL、-1、および既定値はこのコンテキストで同じ値になります。  
  
 ベース テーブルまたはビューのすべてのインデックスの情報を返す NULL を指定します。 NULL を指定する場合*index_id*の場合は NULL を指定することも必要があります。 *partition_number*します。  
  
 *partition_number* | NULL | 0 | DEFAULT  
 オブジェクトのパーティション番号です。 *partition_number*は**int**します。有効な値は、 *partion_number*のインデックスまたはヒープ、NULL、0、または DEFAULT です。 既定値は 0 です。 このコンテキストでは、NULL、0、および DEFAULT は同じ値になります。  
  
 NULL を指定すると、所有するオブジェクトのすべてのパーティションに関する情報が返されます。  
  
 *partition_number*は 1 から始まります。 非パーティション インデックスまたはヒープに*partition_number*を 1 に設定します。  
  
 *mode* | NULL | DEFAULT  
 モードの名前を指定します。 *モード*統計情報を取得するために使用されるスキャン レベルを指定します。 *モード*は**sysname**します。 有効な入力値は DEFAULT、NULL、LIMITED、SAMPLED、DETAILED です。 既定値 (NULL) は制限されています。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|database_id|**smallint**|テーブルまたはビューのデータベース ID。|  
|object_id|**int**|テーブルまたはインデックスがビューのオブジェクト ID。|  
|index_id|**int**|インデックスのインデックス ID。<br /><br /> 0 = ヒープ。|  
|partition_number|**int**|所有するオブジェクト内の 1 から始まるパーティション番号テーブル、ビュー、またはインデックスです。<br /><br /> 1 = パーティション分割されていないインデックスまたはヒープ。|  
|index_type_desc|**nvarchar(60)**|インデックスの種類の説明です。<br /><br /> HEAP<br /><br /> クラスター化インデックス<br /><br /> NONCLUSTERED INDEX<br /><br /> プライマリ XML インデックス<br /><br /> EXTENDED INDEX<br /><br /> XML INDEX<br /><br /> 列ストア マッピング インデックス (内部)<br /><br /> 列ストアの DELETEBUFFER インデックス (内部)<br /><br /> 列ストアの DELETEBITMAP インデックス (内部)|  
|hobt_id で|**bigint**|ヒープまたはインデックスまたはパーティションの B ツリー ID。<br /><br /> ユーザー定義のインデックスの hobt_id でを返すだけはこれも内部列ストア インデックスの hobt_id でを返します。|  
|alloc_unit_type_desc|**nvarchar(60)**|アロケーション ユニットの種類の説明。<br /><br /> IN_ROW_DATA<br /><br /> LOB_DATA<br /><br /> ROW_OVERFLOW_DATA<br /><br /> LOB_DATA アロケーション ユニットには、型の列に格納されているデータが含まれています**テキスト**、 **ntext**、**イメージ**、 **varchar (max)** 、 。**nvarchar (max)** 、 **varbinary (max)** 、および**xml**します。 詳細については、「[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)」を参照してください。<br /><br /> ROW_OVERFLOW_DATA アロケーション ユニットには、型の列に格納されているデータが含まれています**varchar (n)** 、 **nvarchar (n)** 、 **varbinary (n)** 、および**sql _。バリアント**行外に出されました。|  
|index_depth|**tinyint**|インデックス レベルの数です。<br /><br /> 1 = ヒープ、LOB_DATA または ROW_OVERFLOW_DATA アロケーション ユニット。|  
|index_level|**tinyint**|インデックスの現在のレベル。<br /><br /> インデックスのリーフ レベルの場合は 0 がヒープ、LOB_DATA または ROW_OVERFLOW_DATA アロケーション ユニット。<br /><br /> 非リーフ インデックス レベルの場合は 0 より大きい。 *index_level*インデックスのルート レベルで最大になります。<br /><br /> インデックスの非リーフ レベルはのみ処理されるときに*モード*= 詳細。|  
|avg_fragmentation_in_percent|**float**|インデックスの論理的な断片化、または IN_ROW_DATA アロケーション ユニットでのヒープのエクステントの断片化。<br /><br /> 値は、に対する比率として計測され、複数のファイルを考慮します。 論理的な断片化とエクステントの断片化の定義については、「解説」を参照してください。<br /><br /> LOB_DATA および ROW_OVERFLOW_DATA アロケーション ユニットは 0 です。<br /><br /> NULL の場合にヒープ*モード*= SAMPLED。|  
|fragment_count|**bigint**|IN_ROW_DATA アロケーション ユニットのリーフ レベルでフラグメントの数。 フラグメントの詳細については、「解説」を参照してください。<br /><br /> インデックスの非リーフ レベル、および LOB_DATA または ROW_OVERFLOW_DATA アロケーション ユニットでは NULL になります。<br /><br /> NULL の場合にヒープ*モード*= SAMPLED。|  
|avg_fragment_size_in_pages|**float**|IN_ROW_DATA アロケーション ユニットのリーフ レベルにおける、フラグメントあたりのページの平均数。<br /><br /> インデックスの非リーフ レベル、および LOB_DATA または ROW_OVERFLOW_DATA アロケーション ユニットでは NULL になります。<br /><br /> NULL の場合にヒープ*モード*= SAMPLED。|  
|page_count|**bigint**|インデックスまたはデータ ページの合計数。<br /><br /> インデックスで IN_ROW_DATA アロケーション ユニットで b ツリーの現在のレベルにおけるインデックス ページの合計数。<br /><br /> ヒープの場合、IN_ROW_DATA アロケーション ユニット内のデータ ページの合計数。<br /><br /> LOB_DATA または ROW_OVERFLOW_DATA アロケーション ユニット ユニット、アロケーション ユニット内のページの合計数。|  
|avg_page_space_used_in_percent|**float**|すべてのページで使用される使用可能なデータ ストレージ領域の割合の平均値。<br /><br /> インデックスでは、平均は、IN_ROW_DATA アロケーション ユニットで b ツリーの現在のレベルに適用されます。<br /><br /> ヒープでは、IN_ROW_DATA アロケーション ユニットに含まれるすべてのデータ ページの平均になります。<br /><br /> LOB_DATA または ROW_OVERFLOW_DATA アロケーション ユニット ユニット、アロケーション ユニット内のすべてのページの平均値。<br /><br /> ときに、NULL*モード*LIMITED を = です。|  
|record_count|**bigint**|レコードの合計数。<br /><br /> インデックスでは、レコードの合計数は、IN_ROW_DATA アロケーション ユニットで b ツリーの現在のレベルに適用されます。<br /><br /> ヒープの場合、IN_ROW_DATA アロケーション ユニット内のレコードの合計数。<br /><br /> **注:** ヒープの場合、この関数から返されるレコードの数と一致しない SELECT COUNT を実行して返される行の数 (\*)、ヒープに対して。 これは、1 行に複数のレコードが含まれる場合があるためです。 たとえば、更新の状況によっては、更新操作の結果として転送元レコードと転送先レコードが 1 つのヒープ行に含まれることがあります。 また、大きな LOB 行のほとんどは、LOB_DATA ストレージ内で複数のレコードに分割されます。<br /><br /> LOB_DATA または ROW_OVERFLOW_DATA アロケーション ユニットでは、アロケーション ユニット全体でのレコードの合計数になります。<br /><br /> ときに、NULL*モード*LIMITED を = です。|  
|ghost_record_count|**bigint**|アロケーション ユニットで、非実体クリーンアップ タスクによる削除の準備ができているゴースト レコードの数。<br /><br /> IN_ROW_DATA アロケーション ユニット内のインデックスの非リーフ レベルは 0 です。<br /><br /> ときに、NULL*モード*LIMITED を = です。|  
|version_ghost_record_count|**bigint**|アロケーション ユニットで未処理のスナップショット分離トランザクションで保持されるゴースト レコードの数。<br /><br /> IN_ROW_DATA アロケーション ユニット内のインデックスの非リーフ レベルは 0 です。<br /><br /> ときに、NULL*モード*LIMITED を = です。|  
|min_record_size_in_bytes|**int**|最小レコード サイズ (バイト単位)。<br /><br /> インデックスでは、レコードの最小サイズは、IN_ROW_DATA アロケーション ユニットで b ツリーの現在のレベルに適用されます。<br /><br /> ヒープでは、IN_ROW_DATA アロケーション ユニットに含まれる最小レコード サイズになります。<br /><br /> LOB_DATA または ROW_OVERFLOW_DATA アロケーション ユニットでは、アロケーション ユニット全体での最小レコード サイズになります。<br /><br /> ときに、NULL*モード*LIMITED を = です。|  
|max_record_size_in_bytes|**int**|最大レコード サイズ (バイト単位)。<br /><br /> インデックスでは、IN_ROW_DATA アロケーション ユニットに含まれる B ツリーの現在のレベルでの最大レコード サイズになります。<br /><br /> ヒープの場合、IN_ROW_DATA アロケーション ユニットの最大レコード サイズ。<br /><br /> LOB_DATA または ROW_OVERFLOW_DATA アロケーション ユニット ユニット、完全なアロケーション ユニットの最大レコード サイズ。<br /><br /> ときに、NULL*モード*LIMITED を = です。|  
|avg_record_size_in_bytes|**float**|平均レコード サイズ (バイト単位)。<br /><br /> インデックスでは、IN_ROW_DATA アロケーション ユニットに含まれる B ツリーの現在のレベルでの平均レコード サイズになります。<br /><br /> ヒープの場合、IN_ROW_DATA アロケーション ユニットの平均レコード サイズ。<br /><br /> LOB_DATA または ROW_OVERFLOW_DATA アロケーション ユニット ユニット、完了のアロケーション ユニットの平均レコード サイズ。<br /><br /> ときに、NULL*モード*LIMITED を = です。|  
|forwarded_record_count|**bigint**|別のデータの場所への転送ポインターを持つ、ヒープ内の転送されたレコード数 (この状態は、更新中に、新しい行を格納できる十分なスペースが元の場所にない場合に発生します)。<br /><br /> ヒープの IN_ROW_DATA アロケーション ユニット以外のアロケーション ユニットでは NULL になります。<br /><br /> NULL の場合にヒープ*モード*= LIMITED。|  
|compressed_page_count|**bigint**|圧縮されたページ数。<br /><br /> ヒープの場合、新しく割り当てられたページはページ圧縮されません。 ヒープは、2 つの特殊な条件、つまりデータを一括インポートする場合、またはヒープを再構築する場合に、ページ圧縮されます。 ページ割り当てが発生する通常の DML 操作では、ページ圧縮されません。 compressed_page_count の値が目標のしきい値を超えた場合は、ヒープを再構築してください。<br /><br /> クラスター化インデックスを含むテーブルの場合、compressed_page_count の値はページ圧縮の効果を示します。|  
|hobt_id で|BIGINT|**適用対象:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョンまで](https://go.microsoft.com/fwlink/p/?LinkId=299658))、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。<br /><br /> 列ストア インデックスの場合のみ、これは、パーティションの内部列ストア データを追跡する行セットの ID です。 行セットには、データがヒープとしてストアドまたはバイナリ ツリー。 親の列ストア インデックスと同じインデックス ID があります。 詳細については、次を参照してください。 [sys.internal_partitions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-partitions-transact-sql.md)します。<br /><br /> NULL の場合|  
|column_store_delete_buffer_state|TINYINT|**適用対象:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョンまで](https://go.microsoft.com/fwlink/p/?LinkId=299658))、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = OPEN<br /><br /> 2 = のドレイン<br /><br /> 3 = フラッシュ<br /><br /> 4 = インベントリから削除<br /><br /> 5 = 準備完了|  
|column_store_delete_buff_state_desc||**適用対象:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョンまで](https://go.microsoft.com/fwlink/p/?LinkId=299658))、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。<br /><br /> 無効です - 親インデックスは列ストア インデックスはありません。<br /><br /> Deleters を開くし、スキャナーは、これを使用します。<br /><br /> ドレイン中 - deleters ドレインが、スキャナーが引き続き使用します。<br /><br /> フラッシュのバッファーが閉じられ、バッファー内の行が削除のビットマップに書き込まれています。<br /><br /> 削除のビットマップに書き込まれた RETIRING - 閉じた削除バッファーの行が、バッファーが切り捨てられていないスキャナーによってまだ使用されています。 新しいスキャナーは、開いているバッファーが十分であるため、中止のバッファーを使用する必要はありません。<br /><br /> 準備ができたら、この削除バッファーが使用できるようにします。|  
  
## <a name="remarks"></a>コメント  
 sys.dm_db_index_physical_stats 動的管理関数は、DBCC SHOWCONTIG ステートメントの代わりに使用できます。  
  
## <a name="scanning-modes"></a>スキャン モード  
 関数が実行されるモードによって、関数で使用する統計データを取得するためのスキャンのレベルが決まります。 *モード*LIMITED、SAMPLED、または詳細として指定されます。 関数は、テーブルまたはインデックスの指定パーティションを構成するアロケーション ユニット、ページ チェーンをスキャンします。 sys.dm_db_index_physical_stats には、インテント共有 (IS) テーブル ロックのみで実行するモードに関係なく必要があります。  
  
 LIMITED モードは最も高速なモードで、スキャンするページ数は最小です。 インデックスでは、B ツリーの親レベルのページ (リーフ レベルより上のページ) だけがスキャンされます。 ヒープでは、関連付けられた PFS ページおよび IAM ページが調べられます。LIMITED モードではヒープのデータ ページがスキャンされます。  
  
 LIMITED モードでは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]は B ツリーの非リーフ ページとヒープの IAM および PFS ページのみをスキャンするので、compressed_page_count は NULL です。 SAMPLED モードを使用して、compressed_page_count の推定値を取得し、compressed_page_count の実際の値を取得する詳細モードを使用します。 SAMPLED モードでは、インデックスまたはヒープ内のすべてのページの 1% サンプルに基づいて統計を返します。 SAMPLED モードの結果は近似と見なす必要があります。 インデックスまたはヒープのページが 10,000 未満の場合、詳細モードは、サンプルではなく使用されます。  
  
 DETAILED モードではすべてのページがスキャンされ、すべての統計が返されます。  
  
 モードより多くの作業が各モードで実行されるため、詳細、LIMITED から段階的に遅くなります。 テーブルまたはインデックスの断片化レベルのサイズをすばやく計測するには、LIMITED モードを使用します。 最も高速でと、インデックスの IN_ROW_DATA アロケーション ユニット内の各非リーフ レベルの行は返されません。  
  
## <a name="using-system-functions-to-specify-parameter-values"></a>システム関数によるパラメーター値の指定  
 使用することができます、[!INCLUDE[tsql](../../includes/tsql-md.md)]関数[DB_ID](../../t-sql/functions/db-id-transact-sql.md)と[OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md)の値を指定する、 *database_id*と*object_id*パラメーター。 ただし、これらの関数に無効な値を渡すと、意図しない結果が生じる可能性があります。 たとえば、スペルが正しいか存在しないために、データベースまたはオブジェクト名が見つからない場合、どちらの関数は NULL を返します。 sys.dm_db_index_physical_stats 関数では、NULL 値はすべてのデータベースまたはすべてのオブジェクトを指定するワイルドカード値として解釈されます。  
  
 さらに、OBJECT_ID 関数が処理されるは、sys.dm_db_index_physical_stats 関数と呼びます。 そのため、現在のデータベースのコンテキストで評価する前に、データベースではなくで指定された*database_id*します。 この動作により、OBJECT_ID 関数で NULL 値が返される場合があります。または、オブジェクト名が現在のデータベースのコンテキストと指定したデータベースの両方に存在する場合は、エラー メッセージが返されることがあります。 次の例は、こうした意図しない結果を示すものです。  
  
```  
USE master;  
GO  
-- In this example, OBJECT_ID is evaluated in the context of the master database.   
-- Because Person.Address does not exist in master, the function returns NULL.  
-- When NULL is specified as an object_id, all objects in the database are returned.  
-- The same results are returned when an object that is not valid is specified.  
SELECT * FROM sys.dm_db_index_physical_stats  
    (DB_ID(N'AdventureWorks'), OBJECT_ID(N'Person.Address'), NULL, NULL , 'DETAILED');  
GO  
-- This example demonstrates the results of specifying a valid object name  
-- that exists in both the current database context and  
-- in the database specified in the database_id parameter of the   
-- sys.dm_db_index_physical_stats function.  
-- An error is returned because the ID value returned by OBJECT_ID does not  
-- match the ID value of the object in the specified database.  
CREATE DATABASE Test;  
GO  
USE Test;  
GO  
CREATE SCHEMA Person;  
GO  
CREATE Table Person.Address(c1 int);  
GO  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.dm_db_index_physical_stats  
    (DB_ID(N'Test'), OBJECT_ID(N'Person.Address'), NULL, NULL , 'DETAILED');  
GO  
-- Clean up temporary database.  
DROP DATABASE Test;  
GO  
```  
  
### <a name="best-practice"></a>推奨事項  
 DB_ID または OBJECT_ID を使用する場合は、必ず有効な ID が返されるようにしてください。 たとえば、OBJECT_ID を使用するときに名前を指定 3 部など`OBJECT_ID(N'AdventureWorks2012.Person.Address')`、または sys.dm_db_index_physical_stats 関数で使用する前に、関数によって返される値をテストします。 次の例 A と B は、データベースとオブジェクト Id を指定する安全な方法を示します。  
  
## <a name="detecting-fragmentation"></a>断片化の検出  
 断片化は、テーブルとテーブルに定義されたインデックスに対して、INSERT、UPDATE、DELETE ステートメントによるデータ変更が行われる過程で発生します。 これらの変更がない均等に分散テーブルとインデックスの行、されるため、各ページのゆとりが時間の経過と共に変わることができます。 このような断片化があるときに、クエリでテーブルのインデックスの一部または全部をスキャンしようとすると、余分なページの読み取りが必要になり、 データの並列スキャンの妨げになります。  
  
 インデックスまたはヒープの断片化レベルは、avg_fragmentation_in_percent 列で確認できます。 ヒープの場合は、この値は、ヒープのエクステントの断片化を表します。 インデックスの場合、この値はインデックスの論理的な断片化を表します。 DBCC SHOWCONTIG では、どちらの場合も断片化計算アルゴリズムにまたがる複数のファイル ストレージを検討してくださいし、異なり、そのため、正確では。  
  
 **論理的な断片化**  
  
 これは、インデックスのリーフ ページの順序のページの割合です。 順序が不正なページとは、インデックスに割り当てられている次の物理的なページと、現在のリーフ ページの*次ページ* ポインターが示すページが異なるページのことです。  
  
 **エクステントの断片化**  
  
 これは、ヒープのリーフ ページでの順序不定なエクステントの割合です。 順序が無効なエクステントとは、ヒープの現在のページを含むエクステントの物理的な位置が、前のページを含むエクステントの直後でない状態のエクステントを指します。  
  
 最大のパフォーマンスを得るには、avg_fragmentation_in_percent の値をできるだけ 0 に近くする必要があります。 ただし、0% から 10% から値許容される場合があります。 再構築、再構成、再作成など、断片化を解消するためのさまざまな手段を使用することによって、この値を下げることができます。 インデックスの断片化の程度を分析する方法の詳細については、次を参照してください。 [Reorganize and Rebuild Indexes](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)します。  
  
## <a name="reducing-fragmentation-in-an-index"></a>インデックスの断片化の解消  
 断片化がクエリのパフォーマンスの影響を与えることがある方法でインデックスが断片化されている場合は、断片化を削減するための 3 つの選択肢があります。  
  
-   クラスター化インデックスを削除し、再作成する。  
  
     クラスター化インデックスを再作成すると、データが再分配され、データ ページにデータが満たされます。 ページのゆとりのレベルは、CREATE INDEX の FILLFACTOR オプションを使用して構成できます。 このメソッドで短所は、操作がアトミックであると、インデックスが、削除中にオフラインであり、サイクルを再作成するには。 インデックスの作成が中断されると、インデックスは再作成されません。 詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)」を参照してください。  
  
-   論理的な順序でインデックスのリーフ レベル ページの順序を変更するのにには、ALTER INDEX REORGANIZE、DBCC INDEXDEFRAG の置換を使用します。 これは、オンライン操作であるため、インデックスの値は、ステートメントの実行中に使用できます。 操作を中断しても、それまでに完了した作業は失われません。 このメソッドの欠点は、ことはないことと、ジョブのデータを再構成するインデックスの再構築操作と、統計は更新しません。  
  
-   オンラインまたはオフラインのインデックス再構築するのにには、ALTER INDEX REBUILD、DBCC DBREINDEX の置換を使用します。 詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)」を参照してください。  
  
 断片化だけでは再構成またはインデックスを再構築するための十分な理由ではありません。 断片化の影響は主には、インデックスのスキャンまで、ページの先行読み取りのスループットが低下します。 これは、応答時間の遅れの原因となります。 断片化したテーブルまたはインデックスでのクエリのワークロードにスキャンが関係していない場合、ワークロードは主に単一参照のため、断片化を解消しても効果はありません。
  
> [!NOTE]  
>  DBCC SHRINKFILE または DBCC SHRINKDATABASE を実行している場合は、インデックスが部分的または完全に移動された場合、圧縮操作中に断片化が生じる可能性があります。 そのため場合、圧縮操作を実行する必要があります、行う必要があります、断片化が削除される前にします。  
  
## <a name="reducing-fragmentation-in-a-heap"></a>ヒープの断片化の解消  
 ヒープのエクステントの断片化を減らすためには、テーブルにクラスター化インデックスを作成し、インデックスを削除します。 これによって、クラスター化インデックスの作成中にデータが再分配されます。 この操作では、データベースの空き領域の分布を考慮に入れて、可能な限り最適化も行われます。 クラスター化インデックスがヒープを再作成し、削除されると、データは移動されませんし、最適位置のままになります。 これらの操作を実行する方法については、次を参照してください。 [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)と[DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md)します。  
  
> [!CAUTION]  
>  テーブルでクラスター化インデックスを作成して削除すると、そのテーブルのすべての非クラスター化インデックスが 2 回再構築されます。  
  
## <a name="compacting-large-object-data"></a>ラージ オブジェクト データの圧縮  
 既定では、ALTER INDEX REORGANIZE ステートメントは、ラージ オブジェクト (LOB) データを含むページを圧縮します。 空の場合と、LOB ページの割り当ては解除されず、ため、このデータを圧縮すると、多くの LOB データが削除された、または LOB 列が削除された場合にディスク領域の使用が向上できます。  
  
 指定されたクラスター化インデックスを再構成するには、クラスター化インデックスに含まれているすべての LOB 列が圧縮されます。 非クラスター化インデックスを再構成すると、そのインデックス内で非キー列 (付加列) となっているすべての LOB 列が圧縮されます。 ステートメントで ALL を指定した場合は、指定したテーブルまたはビューに関連付けられているすべてのインデックスが再構成されます。 さらに、クラスター化インデックス、基になるテーブル、または付加列非クラスター化インデックスに関連付けられているすべての LOB 列が圧縮されます。  
  
## <a name="evaluating-disk-space-use"></a>ディスク領域の使用を評価します。  
 avg_page_space_used_in_percent 列には、ページのゆとりが示されます。 ディスク領域の使用を最適にするには、ランダムな挿入があまり行われないインデックスの場合はこの値を 100% に近づけます。 ただし、ランダムな挿入を備え、完全なページのインデックスは、ページ分割数の増加があります。 断片化が大きくなります。 そのため、ページ分割を軽減するために、値は 100% 未満を指定する必要があります。 FILLFACTOR オプションを指定してインデックスを再構築すると、ページのゆとりをインデックスのクエリ パターンに合わせて変更できます。 Fill factor の詳細については、次を参照してください。[インデックスの Fill Factor の指定](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)します。 また、ALTER INDEX REORGANIZE は最後に指定された FILLFACTOR までページが埋まるよう、インデックスを圧縮します。 これにより、avg_space_used_in_percent の値は増加します。 ALTER INDEX REORGANIZE はページのゆとりを調整できないことに注意してください。 代わりに、インデックスの再構築を実行する必要があります。  
  
## <a name="evaluating-index-fragments"></a>インデックスのフラグメントの評価  
 フラグメントは、アロケーション ユニットの同じファイル内の物理的に連続するリーフ ページの構成されます。 1 つのインデックスには少なくとも 1 つのフラグメントが含まれます。 インデックスが持つことのできるフラグメントの最大数は、インデックスのリーフ レベルのページ数と同じです。 フラグメントが大きいほど、同じ数のページの読み取りに必要なディスクの I/O が少なくなります。 したがって、avg_fragment_size_in_pages 値が大きいほど、範囲スキャンのパフォーマンスは向上します。 avg_fragment_size_in_pages と avg_fragmentation_in_percent の値は、互いに反比例します。 したがって、再構築またはインデックスを再構成する必要があります断片化の量を減らす、フラグメント サイズを増やします。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 クラスター化列ストア インデックスのデータは返されません。  
  
## <a name="permissions"></a>アクセス許可  
 次の権限が必要です。  
  
-   データベース内で指定したオブジェクトに対する CONTROL 権限。  
  
-   @ のオブジェクトのワイルドカードを使用して指定したデータベース内のすべてのオブジェクトに関する情報を返す VIEW DATABASE STATE 権限*object_id*= NULL。  
  
-   データベースのワイルドカード @ を使用して、すべてのデータベースに関する情報を返す VIEW SERVER STATE 権限*database_id* = NULL。  
  
 VIEW DATABASE STATE 権限を許可すると、特定のオブジェクトに対して CONTROL 権限が拒否されていたとしても、データベース内のすべてのオブジェクトを取得することができます。  
  
 VIEW DATABASE STATE 権限を拒否すると、特定のオブジェクトに対する CONTROL 権限が許可されていたとしても、そのデータベース内のどのオブジェクトも取得できません。 ときに、データベースのワイルドカード @*database_id*= NULL を指定すると、データベースを省略するとします。  
  
 詳細については、次を参照してください。[動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-information-about-a-specified-table"></a>A. 指定されたテーブルに関する情報を返す  
 次の例では、`Person.Address` テーブルのすべてのインデックスとパーティションについて、サイズと断片化の統計を返します。 スキャン モードに設定されて`'LIMITED'`最適なパフォーマンスと返される統計を制限します。 このクエリを実行するには、少なくとも `Person.Address` テーブルに対する CONTROL 権限が必要です。  
  
```  
DECLARE @db_id SMALLINT;  
DECLARE @object_id INT;  
  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');  
  
IF @db_id IS NULL  
BEGIN;  
    PRINT N'Invalid database';  
END;  
ELSE IF @object_id IS NULL  
BEGIN;  
    PRINT N'Invalid object';  
END;  
ELSE  
BEGIN;  
    SELECT * FROM sys.dm_db_index_physical_stats(@db_id, @object_id, NULL, NULL , 'LIMITED');  
END;  
GO  
  
```  
  
### <a name="b-returning-information-about-a-heap"></a>B. ヒープに関する情報を返す  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースのヒープ `dbo.DatabaseLog` に関するすべての統計を返します。 行が返されるテーブルに LOB データが含まれているため、`LOB_DATA`アロケーション ユニットに返される行に加えて、`IN_ROW_ALLOCATION_UNIT`ヒープのデータ ページを格納しています。 このクエリを実行するには、少なくとも `dbo.DatabaseLog` テーブルに対する CONTROL 権限が必要です。  
  
```  
DECLARE @db_id SMALLINT;  
DECLARE @object_id INT;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.dbo.DatabaseLog');  
IF @object_id IS NULL   
BEGIN;  
    PRINT N'Invalid object';  
END;  
ELSE  
BEGIN;  
    SELECT * FROM sys.dm_db_index_physical_stats(@db_id, @object_id, 0, NULL , 'DETAILED');  
END;  
GO  
  
```  
  
### <a name="c-returning-information-for-all-databases"></a>C. すべてのデータベースの情報を返す  
 次の例のインスタンス内のすべてのテーブルとインデックスのすべての統計情報を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ワイルドカードを指定することによって`NULL`すべてのパラメーター。 このクエリを実行するには、VIEW SERVER STATE 権限が必要です。  
  
```  
SELECT * FROM sys.dm_db_index_physical_stats (NULL, NULL, NULL, NULL, NULL);  
GO  
  
```  
  
### <a name="d-using-sysdmdbindexphysicalstats-in-a-script-to-rebuild-or-reorganize-indexes"></a>D. スクリプトで sys.dm_db_index_physical_stats を使用するインデックスの再構成または再構築  
 次の例は、自動的に再構成またはを 10% で、平均断片化を持つ、データベース内のすべてのパーティションを再構築します。 このクエリを実行するには、VIEW DATABASE STATE 権限が必要です。 この例では、データベース名を指定せずに `DB_ID` を 1 番目のパラメーターとして指定しています。 エラーが、現在のデータベースの互換性レベルが 80 以下の場合に生成されます。 このエラーを解決するには、`DB_ID()` を有効なデータベース名で置き換えます。 データベース互換性レベルの詳細については、次を参照してください。 [ALTER DATABASE 互換性レベル&#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)します。  
  
```  
-- Ensure a USE <databasename> statement has been executed first.  
SET NOCOUNT ON;  
DECLARE @objectid int;  
DECLARE @indexid int;  
DECLARE @partitioncount bigint;  
DECLARE @schemaname nvarchar(130);   
DECLARE @objectname nvarchar(130);   
DECLARE @indexname nvarchar(130);   
DECLARE @partitionnum bigint;  
DECLARE @partitions bigint;  
DECLARE @frag float;  
DECLARE @command nvarchar(4000);   
-- Conditionally select tables and indexes from the sys.dm_db_index_physical_stats function   
-- and convert object and index IDs to names.  
SELECT  
    object_id AS objectid,  
    index_id AS indexid,  
    partition_number AS partitionnum,  
    avg_fragmentation_in_percent AS frag  
INTO #work_to_do  
FROM sys.dm_db_index_physical_stats (DB_ID(), NULL, NULL , NULL, 'LIMITED')  
WHERE avg_fragmentation_in_percent > 10.0 AND index_id > 0;  
  
-- Declare the cursor for the list of partitions to be processed.  
DECLARE partitions CURSOR FOR SELECT * FROM #work_to_do;  
  
-- Open the cursor.  
OPEN partitions;  
  
-- Loop through the partitions.  
WHILE (1=1)  
    BEGIN;  
        FETCH NEXT  
           FROM partitions  
           INTO @objectid, @indexid, @partitionnum, @frag;  
        IF @@FETCH_STATUS < 0 BREAK;  
        SELECT @objectname = QUOTENAME(o.name), @schemaname = QUOTENAME(s.name)  
        FROM sys.objects AS o  
        JOIN sys.schemas as s ON s.schema_id = o.schema_id  
        WHERE o.object_id = @objectid;  
        SELECT @indexname = QUOTENAME(name)  
        FROM sys.indexes  
        WHERE  object_id = @objectid AND index_id = @indexid;  
        SELECT @partitioncount = count (*)  
        FROM sys.partitions  
        WHERE object_id = @objectid AND index_id = @indexid;  
  
-- 30 is an arbitrary decision point at which to switch between reorganizing and rebuilding.  
        IF @frag < 30.0  
            SET @command = N'ALTER INDEX ' + @indexname + N' ON ' + @schemaname + N'.' + @objectname + N' REORGANIZE';  
        IF @frag >= 30.0  
            SET @command = N'ALTER INDEX ' + @indexname + N' ON ' + @schemaname + N'.' + @objectname + N' REBUILD';  
        IF @partitioncount > 1  
            SET @command = @command + N' PARTITION=' + CAST(@partitionnum AS nvarchar(10));  
        EXEC (@command);  
        PRINT N'Executed: ' + @command;  
    END;  
  
-- Close and deallocate the cursor.  
CLOSE partitions;  
DEALLOCATE partitions;  
  
-- Drop the temporary table.  
DROP TABLE #work_to_do;  
GO  
  
```  
  
### <a name="e-using-sysdmdbindexphysicalstats-to-show-the-number-of-page-compressed-pages"></a>E. sys.dm_db_index_physical_stats を使用して、ページ圧縮されたページの数を表示する  
 次の例では、表示し、行のページとページの圧縮と、ページの合計数を比較する方法を示します。 この情報は、インデックスまたはテーブルの圧縮を提供する特典を使用できます。  
  
```  
SELECT o.name,  
    ips.partition_number,  
    ips.index_type_desc,  
    ips.record_count, ips.avg_record_size_in_bytes,  
    ips.min_record_size_in_bytes,  
    ips.max_record_size_in_bytes,  
    ips.page_count, ips.compressed_page_count  
FROM sys.dm_db_index_physical_stats ( DB_ID(), NULL, NULL, NULL, 'DETAILED') ips  
JOIN sys.objects o on o.object_id = ips.object_id  
ORDER BY record_count DESC;  
```  
  
### <a name="f-using-sysdmdbindexphysicalstats-in-sampled-mode"></a>F. SAMPLED モードで sys.dm_db_index_physical_stats を使用する  
 次の例では、SAMPLED モードが DETAILED モードの結果とは異なる概算値に返す方法を示します。  
  
```  
CREATE TABLE t3 (col1 int PRIMARY KEY, col2 varchar(500)) WITH(DATA_COMPRESSION = PAGE);  
GO  
BEGIN TRAN  
DECLARE @idx int = 0;  
WHILE @idx < 1000000  
BEGIN  
    INSERT INTO t3 (col1, col2)   
    VALUES (@idx,   
    REPLICATE ('a', 100) + CAST (@idx as varchar(10)) + REPLICATE ('a', 380))  
    SET @idx = @idx + 1  
END  
COMMIT;  
GO  
SELECT page_count, compressed_page_count, forwarded_record_count, *   
FROM sys.dm_db_index_physical_stats (db_id(),   
    object_id ('t3'), null, null, 'SAMPLED');  
SELECT page_count, compressed_page_count, forwarded_record_count, *   
FROM sys.dm_db_index_physical_stats (db_id(),   
    object_id ('t3'), null, null, 'DETAILED');  
```  
  
### <a name="g-querying-service-broker-queues-for-index-fragmentation"></a>G. インデックスの断片化の service broker キューのクエリを実行します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
 次の例では、server broker のキューの断片化を照会する方法を示します。  
  
```  
--Using queue internal table name   
select * from sys.dm_db_index_physical_stats (db_id(), object_id ('sys.queue_messages_549576996'), default, default, default)   
  
--Using queue name directly  
select * from sys.dm_db_index_physical_stats (db_id(), object_id ('ExpenseQueue'), default, default, default)  
  
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [インデックス関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys.dm_db_index_usage_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md)   
 [sys.dm_db_partition_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md)   
 [sys.allocation_units &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)   
 [システム ビュー &#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  

