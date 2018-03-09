---
title: "sys.dm_db_log_info (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sys.dm_db_log_info
- sys.dm_db_log_info_TSQL
- dm_db_log_info
- dm_db_log_info_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_log_info dynamic management view
ms.assetid: f6b40060-c17d-472f-b0a3-3b350275d487
caps.latest.revision: "4"
author: savjani
ms.author: pariks
manager: ajayj
ms.workload: Inactive
ms.openlocfilehash: 661647715d2fcff3a4821250dfaa65e0fea07d6e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="sysdmdbloginfo-transact-sql"></a>sys.dm_db_log_info (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

返します[仮想ログ ファイル (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch)トランザクション ログの情報です。 すべてのトランザクション ログ ファイルは、テーブルの出力に結合されますに注意してください。 出力内の各行は、トランザクション ログに VLF を表し、その VLF をログに関連する情報を提供します。

## <a name="syntax"></a>構文  
  
```  
sys.dm_db_log_info ( database_id )  
```  
## <a name="arguments"></a>引数  
 *database_id* |NULL |既定値  
 データベースの ID です。 *database_id*は**int**です。有効な入力値は、データベース、NULL、または既定の ID 番号です。 既定値は NULL です。 NULL および DEFAULT は同じ値に現在のデータベースのコンテキストでします。
 
 現在のデータベースの VLF 情報を返すには NULL を指定します。

 組み込み関数は、 [DB_ID](../../t-sql/functions/db-id-transact-sql.md)を指定できます。 使用する場合`DB_ID`データベース名を指定せず、現在のデータベースの互換性レベルを 90 以上でなければなりません。  

## <a name="table-returned"></a>返されるテーブル  

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|データベース ID。|
|file_id|**smallint**|トランザクション ログのファイル id。|  
|vlf_begin_offset|**bigint** |位置のオフセット、[仮想ログ ファイル (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch)トランザクション ログ ファイルの先頭からです。|
|vlf_size_mb |**float** |[仮想ログ ファイル (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch)サイズ (MB)、小数点以下 2 桁に丸められます。|     
|vlf_sequence_number|**bigint** |[仮想ログ ファイル (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch)シーケンス番号が作成された順序で。 ログ ファイルに Vlf を一意に識別するために使用します。|
|vlf_active|**bit** |示すかどうか[仮想ログ ファイル (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch)使用されていますか。 <br />0 - VLF 使用されていません。<br />1-VLF はアクティブです。|
|vlf_status|**int** |状態、[仮想ログ ファイル (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch)です。 使用可能な値が含まれます <br />0 - VLF がアクティブではありません。 <br />1-VLF が初期化されますが、使用されていません。 <br /> 2-VLF はアクティブです。|
|vlf_parity|**tinyint** |パリティ[仮想ログ ファイル (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch)です。内部的には、使用すると、VLF 内でログの末尾を決定します。|
|vlf_first_lsn|**nvarchar(48)** |[ログ シーケンス番号 (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch)の最初のログ レコードの[仮想ログ ファイル (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch)です。|
|vlf_create_lsn|**nvarchar(48)** |[ログ シーケンス番号 (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch)ログの記録を作成した、[仮想ログ ファイル (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch)です。|

## <a name="remarks"></a>解説
 `sys.dm_db_log_info`動的管理関数は、`DBCC LOGINFO`ステートメントです。 
 
## <a name="permissions"></a>アクセス許可  
 必要があります、`VIEW DATABASE STATE`データベースの権限です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-determing-databases-in-a-sql-server-instance-with-high-number-of-vlfs"></a>A. Vlf の数が多いと、SQL Server インスタンス内のデータベースの決定
次のクエリでは、ログ ファイルは、データベースの起動、復元、および復旧時間が低下する可能性が 100 を超える Vlf を使用してデータベースを決定します。

```sql
SELECT [name], COUNT(l.database_id) AS 'vlf_count' 
FROM sys.databases s
CROSS APPLY sys.dm_db_log_info(s.database_id) l
GROUP BY [name]
HAVING COUNT(l.database_id) > 100
```

### <a name="b-determing-the-status-of-last-vlf-in-transaction-log-before-shrinking-the-log-file"></a>B. 最後の状態を求める`VLF`ログ ファイルを圧縮する前にトランザクション ログに

トランザクション ログを確認してトランザクション ログが圧縮できる場合に shrinkfile を実行する前に最新の VLF のステータスを確認するのには、次のクエリを使用できます。

```sql
USE AdventureWorks2016
GO

SELECT TOP 1 DB_NAME(database_id) AS "Database Name", file_id, vlf_size_mb, vlf_sequence_number, vlf_active, vlf_status
FROM sys.dm_db_log_info(DEFAULT)
ORDER BY vlf_sequence_number DESC
```


## <a name="see-also"></a>参照  
[動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[データベース関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_log_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)   
[sys.dm_db_log_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md)

