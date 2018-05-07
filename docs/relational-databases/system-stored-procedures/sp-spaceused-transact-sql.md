---
title: sp_spaceused (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_spaceused_TSQL
- sp_spaceused
dev_langs:
- TSQL
helpviewer_keywords:
- sp_spaceused
ms.assetid: c6253b48-29f5-4371-bfcd-3ef404060621
caps.latest.revision: 62
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b9e5b528afe048052b3709886a85d7ab6b853777
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spspaceused-transact-sql"></a>sp_spaceused (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  現在のデータベースのテーブル、インデックス付きビュー、または [!INCLUDE[ssSB](../../includes/sssb-md.md)] キューで使用されている、行数、ディスクの予約領域、およびディスク使用領域を表示します。また、データベース全体で使用されているディスクの予約領域とディスク使用領域を表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_spaceused [[ @objname = ] 'objname' ]   
[, [ @updateusage = ] 'updateusage' ]  
[, [ @mode = ] 'mode' ]  
[, [ @oneresultset = ] oneresultset ]  
[, [ @include_total_xtp_storage = ] include_total_xtp_storage ]
```  
  
## <a name="arguments"></a>引数  

[!INCLUDE[sssdw-md](../../includes/sssdw-md.md)]と[!INCLUDE[sspdw-md](../../includes/sspdw-md.md)]、`sp_spaceused`名前付きパラメーターを指定する必要があります (たとえば`sp_spaceused (@objname= N'Table1');`パラメーターの序数位置によって証明書利用者のではなくです。 

 [  **@objname=**] **'***objname***'** 
   
 領域の使用情報を要求するテーブル、インデックス付きビュー、またはキューの、修飾付きまたは修飾なしの名前を指定します。 引用符は、オブジェクトの修飾名を指定する場合のみ必要です。 データベース名も含めてオブジェクトの完全修飾名を指定した場合は、そのデータベース名は現在のデータベース名であることが必要です。  
場合*objname*が指定されていない、データベース全体の結果が返されます。  
*objname*は**nvarchar (776)**、既定値は NULL です。  
> [!NOTE]  
> [!INCLUDE[sssdw-md](../../includes/sssdw-md.md)] [!INCLUDE[sspdw-md](../../includes/sspdw-md.md)]のみデータベースとテーブルのオブジェクトをサポートします。
  
 [ **@updateusage=**] **'***updateusage***'**  
 領域の使用情報の更新に DBCC UPDATEUSAGE を使用するかどうかを示します。 ときに*objname*はデータベース全体に対して、ステートメントが実行; でステートメントを実行するそれ以外の場合、指定されていない*objname*です。 値は、 **true**または**false**です。 *updateusage*は**varchar (5)**、既定値は**false**です。  
  
 [  **@mode=**] **'***モード***'**  
 結果のスコープを示します。 または、データベースのストレッチされたテーブル、*モード*パラメーターでは、含めるまたはリモート オブジェクトの部分を除外することができます。 詳細については、「 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)」を参照してください。  
  
 *モード*引数は、次の値を持つことができます。  
  
|値|Description|  
|-----------|-----------------|  
|ALL|オブジェクトまたはローカル部分およびリモートの部分の両方を含むデータベースの記憶域の統計を返します。|  
|LOCAL_ONLY|オブジェクトまたはデータベースのローカル部分だけの記憶域の統計を返します。 返す場合と同様の統計情報の場合は、オブジェクトまたはデータベースがストレッチが有効な@mode= ALL です。|  
|REMOTE_ONLY|オブジェクトまたはデータベースのリモートの部分のみの記憶域の統計を返します。 このオプションでは、次の条件のいずれかの条件が true の場合、エラーが発生します。<br /><br /> テーブルには、拡大は無効です。<br /><br /> Stretch」の表が有効になっているが、データの移行を有効にしていません。 この場合、リモート テーブルは、スキーマをまだがありません。<br /><br /> ユーザーは、リモート テーブルを削除して手動で。<br /><br /> 返される、成功のステータスをリモート データのアーカイブのプロビジョニングしますが、実際に失敗しました。|  
  
 *モード*は**varchar (11)**、既定値は**N'ALL'** です。  
  
 [  **@oneresultset=**] *oneresultset*  
 1 つの結果セットを返すかどうかを示します。 *Oneresultset*引数は、次の値を持つことができます。  
  
|値|説明|  
|-----------|-----------------|  
|0|ときに*@objname*が null またはが指定されていない 2 つの結果セットが返されます。 2 つの結果セットは、既定の動作です。|  
|1|ときに*@objname* = null またはが指定されていない 1 つの結果セットが返されます。|  
  
 *oneresultset*は**ビット**、既定値は**0**します。  

[ **@include_total_xtp_storage**] **'***include_total_xtp_storage***'**  
**適用されます:** [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)]、[!INCLUDE[sssds-md](../../includes/sssds-md.md)]です。  
  
 ときに@oneresultset= 1、パラメーター @include_total_xtp_storage MEMORY_OPTIMIZED_DATA ストレージの列が 1 つの結果セットに含まれて かどうかを決定します。 既定値は 0 の場合は、既定で (場合は、パラメーターを省略すると)、XTP 列は、結果セットに含まれません。  

## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 場合*objname*を省略した場合の値と*oneresultset*は 0、現在のデータベースのサイズ情報を提供する次の結果セットが返されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|現在のデータベース名。|  
|**database_size**|**varchar(18)**|現在のデータベースのサイズ (MB 単位)。 **database_size**データおよびログ ファイル両方にはが含まれています。|  
|**未割り当ての領域**|**varchar(18)**|データベース オブジェクト用に予約されていないデータベースの領域。|  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**reserved**|**varchar(18)**|データベース内でオブジェクトによって割り当てられた領域の合計。|  
|**data**|**varchar(18)**|データの使用領域の合計。|  
|**index_size**|**varchar(18)**|インデックスの使用領域の合計。|  
|**未使用**|**varchar(18)**|データベース内でオブジェクト用に予約されており、使用されていない領域の合計。|  
  
 場合*objname*を省略した場合の値と*oneresultset* 1 に設定されて現在のデータベースのサイズ情報を提供する次の 1 つの結果セットが返されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|現在のデータベース名。|  
|**database_size**|**varchar(18)**|現在のデータベースのサイズ (MB 単位)。 **database_size**データおよびログ ファイル両方にはが含まれています。|  
|**未割り当ての領域**|**varchar(18)**|データベース オブジェクト用に予約されていないデータベースの領域。|  
|**reserved**|**varchar(18)**|データベース内でオブジェクトによって割り当てられた領域の合計。|  
|**data**|**varchar(18)**|データの使用領域の合計。|  
|**index_size**|**varchar(18)**|インデックスの使用領域の合計。|  
|**未使用**|**varchar(18)**|データベース内でオブジェクト用に予約されており、使用されていない領域の合計。|  
  
 場合*objname*を指定すると、指定したオブジェクトの次の結果セットが返されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|領域の使用情報を要求したオブジェクトの名前。<br /><br /> オブジェクトのスキーマ名は返されません。 スキーマ名が必要な場合は、使用、 [sys.dm_db_partition_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md)または[sys.dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)動的管理ビューと同じサイズ情報を取得します。|  
|**rows**|**char(20)**|テーブルに含まれる行数。 指定されたオブジェクトがある場合、[!INCLUDE[ssSB](../../includes/sssb-md.md)]キュー、この列は、キュー内のメッセージの数を示します。|  
|**reserved**|**varchar(18)**|予約領域の量の合計*objname*です。|  
|**data**|**varchar(18)**|内のデータによって使用される領域の合計金額*objname*です。|  
|**index_size**|**varchar(18)**|インデックスで使用される領域の合計容量*objname*です。|  
|**未使用**|**varchar(18)**|予約された領域の合計金額*objname*が使用されていません。|  
 
これは、パラメーターが指定されていない場合、既定のモードです。 次の結果セットには、ディスク上のデータベース サイズの詳細情報が返されます。 

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|現在のデータベース名。|  
|**database_size**|**varchar(18)**|現在のデータベースのサイズ (MB 単位)。 **database_size**データおよびログ ファイル両方にはが含まれています。 データベースに MEMORY_OPTIMIZED_DATA ファイル グループがある場合、ファイル グループにすべてのチェックポイント ファイルのディスク上の合計サイズを含めます。|  
|**未割り当ての領域**|**varchar(18)**|データベース オブジェクト用に予約されていないデータベースの領域。 データベースに MEMORY_OPTIMIZED_DATA ファイル グループがある場合は、状態 PRECREATED とチェックポイント ファイルの合計のディスク上のサイズ、ファイル グループに含めます。|  

データベース内のテーブルで使用される領域: (この結果セットが反映されないメモリ最適化テーブルでは、ディスク使用量の会計がのテーブルが存在しないため) 

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**reserved**|**varchar(18)**|データベース内でオブジェクトによって割り当てられた領域の合計。|  
|**data**|**varchar(18)**|データの使用領域の合計。|  
|**index_size**|**varchar(18)**|インデックスの使用領域の合計。|  
|**未使用**|**varchar(18)**|データベース内でオブジェクト用に予約されており、使用されていない領域の合計。|

次の結果セットが返される**場合のみ**データベースには、少なくとも 1 つのコンテナーと、MEMORY_OPTIMIZED_DATA ファイル グループには。 

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**xtp_precreated**|**varchar(18)**|状態 (KB 単位) の PRECREATED とチェックポイント ファイルの合計サイズ。 全体として、データベース内の未割り当て領域にカウントします。 [など 600,000 KB 事前作成されたチェックポイント ファイルの場合は、この列に含まれる ' 600000 KB']|  
|**xtp_used**|**varchar(18)**|UNDER CONSTRUCTION、アクティブ、およびマージ ターゲット (KB 単位) の状態を持つチェックポイント ファイルの合計サイズ。 これは、メモリ最適化テーブルのデータをアクティブに使用されるディスク領域です。|  
|**xtp_pending_truncation**|**varchar(18)**|状態 (KB 単位) の WAITING_FOR_LOG_TRUNCATION とチェックポイント ファイルの合計サイズ。 これは、ログの切り捨てが発生したら、クリーンアップ処理を待機しているチェックポイント ファイルに使用されるディスク領域です。|

場合*objname*は省略すると、oneresultset の値は 1、および*include_total_xtp_storage* 1 に設定されて現在のデータベースのサイズ情報を提供する次の 1 つの結果セットが返されます。 場合`include_total_xtp_storage`は 0 (既定)、最後の 3 つの列は省略されます。 

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|現在のデータベース名。|  
|**database_size**|**varchar(18)**|現在のデータベースのサイズ (MB 単位)。 **database_size**データおよびログ ファイル両方にはが含まれています。 データベースに MEMORY_OPTIMIZED_DATA ファイル グループがある場合、ファイル グループにすべてのチェックポイント ファイルのディスク上の合計サイズを含めます。|
|**未割り当ての領域**|**varchar(18)**|データベース オブジェクト用に予約されていないデータベースの領域。 データベースに MEMORY_OPTIMIZED_DATA ファイル グループがある場合は、状態 PRECREATED とチェックポイント ファイルの合計のディスク上のサイズ、ファイル グループに含めます。|  
|**reserved**|**varchar(18)**|データベース内でオブジェクトによって割り当てられた領域の合計。|  
|**data**|**varchar(18)**|データの使用領域の合計。|  
|**index_size**|**varchar(18)**|インデックスの使用領域の合計。|  
|**未使用**|**varchar(18)**|データベース内でオブジェクト用に予約されており、使用されていない領域の合計。|
|**xtp_precreated**|**varchar(18)**|状態 (KB 単位) の PRECREATED とチェックポイント ファイルの合計サイズ。 データベース内の未割り当て領域に、全体としてカウントされます。 データベースには、少なくとも 1 つのコンテナーと、memory_optimized_data ファイル グループがない場合は、NULL を返します。 *この列はのみが含まれる場合@include_total_xtp_storage= 1*です。| 
|**xtp_used**|**varchar(18)**|UNDER CONSTRUCTION、アクティブ、およびマージ ターゲット (KB 単位) の状態を持つチェックポイント ファイルの合計サイズ。 これは、メモリ最適化テーブルのデータをアクティブに使用されるディスク領域です。 データベースには、少なくとも 1 つのコンテナーと、memory_optimized_data ファイル グループがない場合は、NULL を返します。 *この列はのみが含まれる場合@include_total_xtp_storage= 1*です。| 
|**xtp_pending_truncation**|**varchar(18)**|状態 (KB 単位) の WAITING_FOR_LOG_TRUNCATION とチェックポイント ファイルの合計サイズ。 これは、ログの切り捨てが発生したら、クリーンアップ処理を待機しているチェックポイント ファイルに使用されるディスク領域です。 データベースには、少なくとも 1 つのコンテナーと、memory_optimized_data ファイル グループがない場合は、NULL を返します。 この列はのみが含まれる場合`@include_total_xtp_storage=1`です。|

## <a name="remarks"></a>解説  
 **database_size**の合計よりも大きいは常に**予約** + **未割り当て領域**ログ ファイルのサイズが含まれていますが、 **に予約されて**と**unallocated_space**データ ページのみを検討してください。  
  
 XML インデックスとフルテキスト インデックスによって使用されているページに含まれる**index_size**両方の結果セットです。 ときに*objname*を指定すると、XML インデックスとオブジェクトのフルテキスト インデックスのページが合計でもカウント**予約**と**index_size**結果。  
  
 領域の使用状況は、データベースまたはなど、空間インデックスの領域サイズの列を持つオブジェクトの計算**database_size**、**予約**、および**index_size**が含まれます空間インデックスのサイズ。  
  
 ときに*updateusage*を指定すると、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]スキャン データは、データベース内のページし、いずれかによりに必要な修正を行い、 **sys.allocation_units**と**sys.partitions**カタログ ビューの各テーブルで使用されるストレージ領域に関してです。 たとえば、インデックスを削除した後、テーブルの領域情報が最新ではない場合はその修正が行われます。 *updateusage*大きなテーブルやデータベースで実行に時間がかかることができます。 使用して*updateusage*疑われる場合が正しくない値が返されると、プロセス、できないその他のユーザーまたはプロセスに悪影響を与えるデータベース内のみです。 DBCC UPDATEUSAGE は、別に実行することもできます。  
  
> [!NOTE]  
>  ドロップまたは大規模なインデックスを再構築またはドロップまたは大規模なテーブルを切り捨てるしたときに、[!INCLUDE[ssDE](../../includes/ssde-md.md)]トランザクションがコミットされた後に、まで、実際のページの割り当て解除と、関連するロックを延期します。 削除操作が延期された場合、割り当てられた領域は、すぐには解放されません。 によって返される値ではそのため、 **sp_spaceused**すぐ削除するか切り捨てたラージ オブジェクトが使用可能な実際のディスク領域を反映されません。  
  
## <a name="permissions"></a>権限  
 **sp_spaceused** の実行権限は、 **public** ロールに与えられています。 **@updateusage** パラメーターを指定できるのは、**db_owner** 固定データベース ロールのメンバーだけです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-displaying-disk-space-information-about-a-table"></a>A. テーブルに関するディスク領域情報を表示する  
 次の例では、レポートのディスク領域の情報、`Vendor`テーブルとインデックス。  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_spaceused N'Purchasing.Vendor';  
GO  
```  
  
### <a name="b-displaying-updated-space-information-about-a-database"></a>B. データベースに関する更新領域情報を表示する  
 次の例では、現在のデータベースで使用されている領域情報を要約し、省略可能なパラメーター `@updateusage` を使用して最新の値を取得します。  
  
```sql  
USE AdventureWorks008R2;  
GO  
EXEC sp_spaceused @updateusage = N'TRUE';  
GO  
```  
  
### <a name="c-displaying-space-usage-information-about-the-remote-table-associated-with-a-stretch-enabled-table"></a>C. Stretch が有効なテーブルに関連付けられている領域の使用法、リモート テーブルに関する情報を表示します。  
 次の例を使用して、Stretch が有効なテーブルに関連付けられているリモート テーブルで使用される領域をまとめたもの、 **@mode**リモート ターゲットを指定する引数。 詳細については、「 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)」を参照してください。  
  
```sql  
USE StretchedAdventureWorks2016  
GO  
EXEC sp_spaceused N'Purchasing.Vendor', @mode = 'REMOTE_ONLY'  
```  
  
### <a name="d-displaying-space-usage-information-for-a-database-in-a-single-result-set"></a>D. セットを 1 つの結果で、データベースの領域の使用状況の情報を表示します。  
 次の例では、1 つの結果セット内の現在のデータベース領域の使用状況概要を示します。  
  
```sql  
USE AdventureWorks2016  
GO  
EXEC sp_spaceused @oneresultset = 1  
```  

### <a name="e-displaying-space-usage-information-for-a-database-with-at-least-one-memoryoptimized-file-group-in-a-single-result-set"></a>E. 1 つの結果セット内に少なくとも 1 つのメモリ最適化ファイル グループとデータベースの領域使用状況情報を表示します。 
 次の例は、1 つの結果セット内の少なくとも 1 つのメモリ最適化ファイル グループと現在のデータベースの領域使用状況をまとめたものです。
 
```sql
USE WideWorldImporters
GO
EXEC sp_spaceused @updateusage = 'FALSE', @mode = 'ALL', @oneresultset = '1', @include_total_xtp_storage = '1';
GO
``` 

### <a name="f-displaying-space-usage-information-for-a-memoryoptimized-table-object-in-a-database"></a>F. データベースのメモリ最適化テーブルのオブジェクトの領域使用状況情報を表示しています。
 次の例は、メモリ最適化テーブル内のオブジェクトには、少なくとも 1 つのメモリ最適化ファイル グループと現在のデータベース領域の使用状況をまとめたものです。
 
```sql
USE WideWorldImporters
GO
EXEC sp_spaceused
@objname = N'VehicleTemparatures',
@updateusage = 'FALSE',
@mode = 'ALL',
@oneresultset = '0',
@include_total_xtp_storage = '1';
GO
```  

## <a name="see-also"></a>参照  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [DBCC UPDATEUSAGE &#40;TRANSACT-SQL&#41;](../../t-sql/database-console-commands/dbcc-updateusage-transact-sql.md)   
 [SQL Server Service Broker (SQL Server Service Broker)](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [sys.allocation_units &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
