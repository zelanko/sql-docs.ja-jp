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
ms.openlocfilehash: b7250943f4e92d60888a75d9e577388f3cc6b1ed
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbloginfo-transact-sql"></a>sys.dm_db_log_info (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

返します`VLF`トランザクション ログ ファイルの情報です。 (すべてのログ ファイルは、テーブルの出力に結合されます。) 出力に各行を表す、`VLF`トランザクション ログにし、その VLF をログに関連する情報を提供します。

## <a name="syntax"></a>構文  
  
```  
sys.dm_db_log_info ( database_id )  
```  
## <a name="arguments"></a>引数  
 *database_id* |NULL |既定値  
 データベースの ID です。 *database_id*は**int**です。有効な入力値は、データベース、NULL、または既定の ID 番号です。 既定値は NULL です。 NULL および DEFAULT は同じ値に現在のデータベースのコンテキストでします。
 
 NULL を返すを指定する`VLF`については、現在のデータベースです。

 組み込み関数は、 [DB_ID](../../t-sql/functions/db-id-transact-sql.md)を指定できます。 データベース名を指定しないで DB_ID を使用する場合、現在のデータベースの互換性レベルが 90 以上である必要があります。  

## <a name="table-returned"></a>返されるテーブル  

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|データベース ID。|
|file_id|**smallint**|トランザクション ログのファイル id。|  
|vlf_begin_offset|**bigint** |位置のオフセット、`VLF`トランザクション ログ ファイルの先頭からです。|
|vlf_size_mb |**float** |`VLF`サイズ (mb) は、小数点以下 2 桁に丸められます。|     
|vlf_sequence_number|**bigint** |`VLF`作成された順序でシーケンス番号。 一意に識別するために使用`VLFs`ログ ファイルにします。|
|vlf_active|**bit** |か VLF は使用中かどうかを示します。 <br />0 - vlf 使用されていません。<br />1 -`VLF`がアクティブです。|
|vlf_status|**int** |状態、`VLF`です。 使用可能な値が含まれます <br />0 -`VLF`がアクティブでないです。 <br />1-vlf が初期化されますが、使用されていません。 <br /> 2 -`VLF`がアクティブです。|
|vlf_parity|**tinyint** |パリティ`VLF`です。内でログの末尾を内部的に使用される、`VLF`です。|
|vlf_first_lsn|**nvarchar(48)** |最初のログ レコードの LSN、`VLF`です。|
|vlf_create_lsn|**nvarchar(48)** |LSN のログ レコードの作成、`VLF`です。|

## <a name="remarks"></a>解説
 `sys.dm_db_log_info`動的管理関数は、`DBCC LOGINFO`ステートメントです。 
 
## <a name="permissions"></a>Permissions  
 必要があります、`VIEW DATABASE STATE`データベースの権限です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-determing-databases-in-a-sql-server-instance-with-high-number-of-vlfs"></a>A. 大量の SQL Server インスタンス内のデータベースの決定`VLFs`
次のクエリが 100 以上を使用してデータベースを決定`VLFs`ログ ファイルでは、データベースの起動、復元、および復旧時間に影響を与えます。

```sql
SELECT name,count(l.database_id) as 'vlf_count' from sys.databases s
cross apply sys.dm_db_log_info(s.database_id) l
group by name
having count(l.database_id)> 100
```

### <a name="b-determing-the-status-of-last-vlf-in-transaction-log-before-shrinking-the-log-file"></a>B. 最後の状態を求める`VLF`ログ ファイルを圧縮する前にトランザクション ログに

最後の状態を判断する次のクエリを使用できる`VLF`トランザクション ログを確認してトランザクション ログが圧縮できるかどうかに shrinkfile を実行する前にします。

```sql
USE <database name>
GO

SELECT top 1 DB_NAME(database_id) as "Database Name",file_id,vlf_size_mb,vlf_sequence_number, vlf_active, vlf_status
from sys.dm_db_log_info(DEFAULT)
order by vlf_sequence_number desc
```


## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_db_log_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)    
  



