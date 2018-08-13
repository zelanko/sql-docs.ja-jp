---
title: sp_spaceused (TRANSACT-SQL) |Microsoft Docs
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 78504222e9dbe50b29868eb935f4948772d8e204
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39533702"
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

[!INCLUDE[sssdw-md](../../includes/sssdw-md.md)]と[!INCLUDE[sspdw-md](../../includes/sspdw-md.md)]、`sp_spaceused`名前付きパラメーターを指定する必要があります (たとえば`sp_spaceused (@objname= N'Table1');`パラメーターの序数位置に依存するのではなく。 

 [  **@objname=**] **'***objname***'** 
   
 領域の使用情報を要求するテーブル、インデックス付きビュー、またはキューの、修飾付きまたは修飾なしの名前を指定します。 引用符は、オブジェクトの修飾名を指定する場合のみ必要です。 データベース名も含めてオブジェクトの完全修飾名を指定した場合は、そのデータベース名は現在のデータベース名であることが必要です。  
場合*objname*が指定されていない、データベース全体の結果が返されます。  
*objname*は**nvarchar (776)**、既定値は NULL です。  
> [!NOTE]  
> [!INCLUDE[sssdw-md](../../includes/sssdw-md.md)] [!INCLUDE[sspdw-md](../../includes/sspdw-md.md)]データベースとテーブルのオブジェクトのみをサポートします。
  
 [ **@updateusage=**] **'***updateusage***'**  
 領域の使用情報の更新に DBCC UPDATEUSAGE を使用するかどうかを示します。 ときに*objname*はステートメントを実行して、データベース全体に対して; でステートメントを実行する場合は、指定されていない*objname*します。 値は、 **true**または**false**します。 *updateusage*は**varchar (5)**、既定値は**false**します。  
  
 [  **@mode=**] **'***モード***'**  
 結果のスコープを示します。 拡張されたテーブルまたはデータベースの*モード*パラメーターで、含めるまたはリモート オブジェクトの部分を除外することができます。 詳細については、「 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)」を参照してください。  
  
 *モード*引数は、次の値であることができます。  
  
|値|説明|  
|-----------|-----------------|  
|ALL|オブジェクトまたはローカル部分およびリモートの部分の両方を含むデータベースの記憶域の統計を返します。|  
|LOCAL_ONLY|オブジェクトまたはデータベースのローカル部分だけの記憶域の統計を返します。 オブジェクトまたはデータベースでない場合 Stretch が有効な場合と同様の統計情報を返します@mode= ALL です。|  
|REMOTE_ONLY|オブジェクトまたはデータベースのリモートの部分のみの記憶域の統計を返します。 このオプションでは、次の条件のいずれかの条件が true の場合、エラーが発生します。<br /><br /> テーブルには、拡大は無効です。<br /><br /> Stretch」の表が有効になっているが、データの移行を有効にしていることはありません。 この場合、リモート テーブルは、スキーマをまだがありません。<br /><br /> ユーザーは、リモート テーブルを削除して手動で。<br /><br /> 返される、成功のステータスをリモート データのアーカイブのプロビジョニングしますが、実際に失敗しました。|  
  
 *モード*は**varchar (11)**、既定値は**N'ALL'** します。  
  
 [  **@oneresultset=**] *oneresultset*  
 1 つの結果セットを返すかどうかを示します。 *Oneresultset*引数は、次の値であることができます。  
  
|値|Description|  
|-----------|-----------------|  
|0|ときに*@objname*が null またはが指定されていない 2 つの結果セットが返されます。 2 つの結果セットでは、既定の動作です。|  
|1|ときに*@objname* = null またはが指定されていない 1 つの結果セットが返されます。|  
  
 *oneresultset*は**ビット**、既定値は**0**します。  

[ **@include_total_xtp_storage**] **'***include_total_xtp_storage***'**  
**適用対象:** [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)]、[!INCLUDE[sssds-md](../../includes/sssds-md.md)]します。  
  
 ときに@oneresultset= 1、パラメーター @include_total_xtp_storage MEMORY_OPTIMIZED_DATA ストレージの列が 1 つの結果セットに含まれて かどうかを決定します。 既定値は 0、つまり、既定では (この場合、パラメーターを省略すると) XTP 列は、結果セットに含まれません。  

## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 場合*objname*を省略するの値*oneresultset*は 0、現在のデータベースのサイズ情報を提供する次の結果セットが返されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|現在のデータベース名。|  
|**database_size**|**varchar(18)**|現在のデータベースのサイズ (MB 単位)。 **database_size**データとログの両方のファイルが含まれます。|  
|**未割り当ての領域**|**varchar(18)**|データベース オブジェクト用に予約されていないデータベースの領域。|  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**reserved**|**varchar(18)**|データベース内でオブジェクトによって割り当てられた領域の合計。|  
|**data**|**varchar(18)**|データの使用領域の合計。|  
|**index_size**|**varchar(18)**|インデックスの使用領域の合計。|  
|**未使用**|**varchar(18)**|データベース内でオブジェクト用に予約されており、使用されていない領域の合計。|  
  
 場合*objname*を省略するの値*oneresultset*は 1 です。 現在のデータベースのサイズ情報を提供する次の 1 つの結果セットが返されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|現在のデータベース名。|  
|**database_size**|**varchar(18)**|現在のデータベースのサイズ (MB 単位)。 **database_size**データとログの両方のファイルが含まれます。|  
|**未割り当ての領域**|**varchar(18)**|データベース オブジェクト用に予約されていないデータベースの領域。|  
|**reserved**|**varchar(18)**|データベース内でオブジェクトによって割り当てられた領域の合計。|  
|**data**|**varchar(18)**|データの使用領域の合計。|  
|**index_size**|**varchar(18)**|インデックスの使用領域の合計。|  
|**未使用**|**varchar(18)**|データベース内でオブジェクト用に予約されており、使用されていない領域の合計。|  
  
 場合*objname*を指定すると、指定したオブジェクトの次の結果セットが返されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|領域の使用情報を要求したオブジェクトの名前。<br /><br /> オブジェクトのスキーマ名は返されません。 スキーマ名が必要な場合は、使用、 [sys.dm_db_partition_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md)または[sys.dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)動的管理ビューに対応するサイズ情報を取得します。|  
|**rows**|**char(20)**|テーブルに含まれる行数。 指定されたオブジェクトがある場合、[!INCLUDE[ssSB](../../includes/sssb-md.md)]キューでは、この列は、キュー内のメッセージの数を示します。|  
|**reserved**|**varchar(18)**|予約領域の合計量*objname*します。|  
|**data**|**varchar(18)**|内のデータによって使用される領域の合計量*objname*します。|  
|**index_size**|**varchar(18)**|インデックスで使用される領域の合計量*objname*します。|  
|**未使用**|**varchar(18)**|予約された領域の合計量*objname*が使用されていません。|  
 
パラメーターが指定されていない場合、既定のモードになります。 次の結果セットには、ディスク上のデータベース サイズの詳細情報が返されます。 

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|現在のデータベース名。|  
|**database_size**|**varchar(18)**|現在のデータベースのサイズ (MB 単位)。 **database_size**データとログの両方のファイルが含まれます。 データベースに MEMORY_OPTIMIZED_DATA ファイル グループがある場合は、すべてのチェックポイント ファイルのディスク上の合計サイズ、ファイル グループに含めます。|  
|**未割り当ての領域**|**varchar(18)**|データベース オブジェクト用に予約されていないデータベースの領域。 データベースに MEMORY_OPTIMIZED_DATA ファイル グループがある場合は、状態 PRECREATED とチェックポイント ファイルのディスク上の合計サイズ、ファイル グループに含めます。|  

データベース内のテーブルで使用される領域: (この結果セットには反映されません、メモリ最適化テーブルのディスク使用量のテーブルのアカウンティングが存在しないため) 

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**reserved**|**varchar(18)**|データベース内でオブジェクトによって割り当てられた領域の合計。|  
|**data**|**varchar(18)**|データの使用領域の合計。|  
|**index_size**|**varchar(18)**|インデックスの使用領域の合計。|  
|**未使用**|**varchar(18)**|データベース内でオブジェクト用に予約されており、使用されていない領域の合計。|

次の結果セットが返される**場合にのみ**を少なくとも 1 つのコンテナーと、MEMORY_OPTIMIZED_DATA ファイル グループ、データベースには。 

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**xtp_precreated**|**varchar(18)**|チェックポイント ファイルと状態 (KB 単位) の PRECREATED の合計サイズ。 全体として、データベース内の未割り当て領域考慮されます。 [たとえば、600,000 KB 事前作成されたチェックポイント ファイルの場合は、この列を含む 600000 ' KB']|  
|**xtp_used**|**varchar(18)**|状態 UNDER CONSTRUCTION、アクティブ、およびサポート技術情報でのマージ ターゲット チェックポイント ファイルの合計サイズ。 これは、メモリ最適化テーブルのデータを積極的に使用されるディスク領域です。|  
|**xtp_pending_truncation**|**varchar(18)**|チェックポイント ファイルと状態 (KB 単位) の WAITING_FOR_LOG_TRUNCATION の合計サイズ。 これは、ログが切り捨て後のクリーンアップを待機しているチェックポイント ファイルに使用されるディスク領域です。|

場合*objname*は省略すると、oneresultset の値は 1、および*include_total_xtp_storage*は 1 です。 現在のデータベースのサイズ情報を提供する次の 1 つの結果セットが返されます。 場合`include_total_xtp_storage`は 0 (既定)、最後の 3 つの列は省略します。 

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|現在のデータベース名。|  
|**database_size**|**varchar(18)**|現在のデータベースのサイズ (MB 単位)。 **database_size**データとログの両方のファイルが含まれます。 データベースに MEMORY_OPTIMIZED_DATA ファイル グループがある場合は、すべてのチェックポイント ファイルのディスク上の合計サイズ、ファイル グループに含めます。|
|**未割り当ての領域**|**varchar(18)**|データベース オブジェクト用に予約されていないデータベースの領域。 データベースに MEMORY_OPTIMIZED_DATA ファイル グループがある場合は、状態 PRECREATED とチェックポイント ファイルのディスク上の合計サイズ、ファイル グループに含めます。|  
|**reserved**|**varchar(18)**|データベース内でオブジェクトによって割り当てられた領域の合計。|  
|**data**|**varchar(18)**|データの使用領域の合計。|  
|**index_size**|**varchar(18)**|インデックスの使用領域の合計。|  
|**未使用**|**varchar(18)**|データベース内でオブジェクト用に予約されており、使用されていない領域の合計。|
|**xtp_precreated**|**varchar(18)**|チェックポイント ファイルと状態 (KB 単位) の PRECREATED の合計サイズ。 これは、データベース内の未割り当て領域には全体としてカウントされます。 データベースが少なくとも 1 つのコンテナーと、memory_optimized_data ファイル グループを持っていない場合は、NULL を返します。 *この列にのみが含まれる場合@include_total_xtp_storage= 1*します。| 
|**xtp_used**|**varchar(18)**|状態 UNDER CONSTRUCTION、アクティブ、およびサポート技術情報でのマージ ターゲット チェックポイント ファイルの合計サイズ。 これは、メモリ最適化テーブルのデータを積極的に使用されるディスク領域です。 データベースが少なくとも 1 つのコンテナーと、memory_optimized_data ファイル グループを持っていない場合は、NULL を返します。 *この列にのみが含まれる場合@include_total_xtp_storage= 1*します。| 
|**xtp_pending_truncation**|**varchar(18)**|チェックポイント ファイルと状態 (KB 単位) の WAITING_FOR_LOG_TRUNCATION の合計サイズ。 これは、ログが切り捨て後のクリーンアップを待機しているチェックポイント ファイルに使用されるディスク領域です。 データベースが少なくとも 1 つのコンテナーと、memory_optimized_data ファイル グループを持っていない場合は、NULL を返します。 この列にのみが含まれる場合`@include_total_xtp_storage=1`します。|

## <a name="remarks"></a>コメント  
 **database_size**はの合計よりも大きい**予約** + **未割り当て領域**、ログ ファイルのサイズが含まれているため、 **に予約されています**と**unallocated_space**データ ページのみを検討してください。  
  
 XML インデックスおよびフルテキスト インデックスで使用されるページが含まれている**index_size**両方の結果セット。 ときに*objname*を指定すると、XML インデックスとオブジェクトのフルテキスト インデックスのページは、合計でもカウント**予約**と**index_size**結果。  
  
 データベースまたは領域サイズの列、空間インデックスをなどが含まれるオブジェクトの領域の使用状況を計算するかどうか**database_size**、**予約**、および**index_size**が含まれます空間インデックスのサイズ。  
  
 ときに*updateusage*が指定されている、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]スキャン データがデータベース内のページし、いずれかの修正に必要な**sys.allocation_units**と**sys.partitions**カタログ ビューの各テーブルで使用されるストレージ領域に関してです。 たとえば、インデックスを削除した後、テーブルの領域情報が最新ではない場合はその修正が行われます。 *updateusage*大きなテーブルやデータベースで実行に時間がかかることができます。 使用*updateusage*疑われる場合が正しくない値が返されるとプロセス、できないその他のユーザーまたはプロセスに悪影響を与える、データベース内のみです。 DBCC UPDATEUSAGE は、別に実行することもできます。  
  
> [!NOTE]  
>  ドロップまたは大きなインデックスを再構築または削除や、大規模なテーブルを切り捨てる、[!INCLUDE[ssDE](../../includes/ssde-md.md)]トランザクションがコミットされた後に、まで、実際のページの割り当て解除と、関連するロックを延期します。 削除操作が延期された場合、割り当てられた領域は、すぐには解放されません。 によって返される値ではそのため、 **sp_spaceused**直後使用可能な実際のディスク領域は削除するか切り捨てたラージ オブジェクトで反映しない可能性があります。  
  
## <a name="permissions"></a>アクセス許可  
 **sp_spaceused** の実行権限は、 **public** ロールに与えられています。 **@updateusage** パラメーターを指定できるのは、**db_owner** 固定データベース ロールのメンバーだけです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-displaying-disk-space-information-about-a-table"></a>A. テーブルに関するディスク領域情報を表示する  
 次の例のディスク領域情報の報告、`Vendor`テーブルとインデックス。  
  
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

### <a name="e-displaying-space-usage-information-for-a-database-with-at-least-one-memoryoptimized-file-group-in-a-single-result-set"></a>E. 1 つの結果セットに少なくとも 1 つのメモリ最適化ファイル グループで、データベースの容量利用情報を表示します。 
 次の例では、1 つの結果セット内の少なくとも 1 つのメモリ最適化ファイル グループと現在のデータベース領域の使用状況をまとめたものです。
 
```sql
USE WideWorldImporters
GO
EXEC sp_spaceused @updateusage = 'FALSE', @mode = 'ALL', @oneresultset = '1', @include_total_xtp_storage = '1';
GO
``` 

### <a name="f-displaying-space-usage-information-for-a-memoryoptimized-table-object-in-a-database"></a>F. データベースのメモリ最適化テーブルのオブジェクトの容量利用情報を表示しています。
 次の例は、少なくとも 1 つのメモリ最適化ファイル グループと現在のデータベースでメモリ最適化テーブル オブジェクトの領域の使用状況をまとめたものです。
 
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
  
  
