---
title: sys.dm_tran_version_store_space_usage (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/30/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_version_store_space_usage_TSQL
- sys.dm_tran_version_store_space_usage
- dm_tran_version_store_space_usage
- dm_tran_version_store_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_version_store_space_usage dynamic management view
ms.assetid: 7ab44517-0351-4f91-bdd9-7cf940f03c51
caps.latest.revision: 10
author: savjani
ms.author: pariks
manager: ajayj
ms.workload: Inactive
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 0f46c84abe0c62c36f76a3bc8d02576d30357e19
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmtranversionstorespaceusage-transact-sql"></a>sys.dm_tran_version_store_space_usage (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

データベースごとにバージョン ストア レコードで使用する tempdb の領域の合計を表示するテーブルを返します。 **sys.dm_tran_version_store_space_usage**は効率的かつ実行するには、個々 のバージョン ストア レコードから移動しないを返しますが tempdb データベースごとに使用されるバージョン ストアの領域を集計できません高価です。
  
各バージョン レコードは、いくつかの追跡または状態の情報と共に、バイナリ データとして格納されます。 データベース テーブル内のレコードと同様、バージョン ストア レコードは 8,192 バイトのページに格納されます。 レコードが 8,192 バイトを超える場合は、2 つのレコードに分割されます。  
  
バージョン レコードはバイナリとして格納されるので、複数のデータベースの照合順序が異なっていても問題にはなりません。 使用して**sys.dm_tran_version_store_space_usage** tempdb のサイズ、SQL Server インスタンスにデータベースのバージョン ストアの領域使用率に基づくを監視して計画します。
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|データベースのデータベース ID。|  
|**reserved_page_count**|**bigint**|Tempdb のバージョンで予約済みページの合計数は、データベースのレコードを格納します。|  
|**reserved_space_kb**|**bigint**|バージョンの tempdb のキロバイトで使用される領域の合計は、データベースのレコードを格納します。|  
  
## <a name="permissions"></a>権限  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   

## <a name="examples"></a>使用例  
 内の各データベースのバージョン ストアによって、tempdb で使用される領域を判断する次のクエリを使用できる、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。 
  
```sql  
SELECT 
  DB_NAME(database_id) as 'Database Name',
  reserved_page_count,
  reserved_space_kb 
FROM sys.dm_tran_version_store_space_usage;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Database Name            reserved_page_count reserved_space_kb  
------------------------ -------------------- -----------  
msdb                      0                    0             
AdventureWorks2016        10                   80             
AdventureWorks2016DW      0                    0             
WideWorldImporters        20                   160             
```
 
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [トランザクション関連の動的管理ビューおよび関数  &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
