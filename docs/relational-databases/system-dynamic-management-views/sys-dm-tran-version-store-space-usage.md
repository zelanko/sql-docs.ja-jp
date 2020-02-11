---
title: dm_tran_version_store_space_usage (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: savjani
ms.author: pariks
manager: ajayj
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2a4fac732f784a401206f37fb2af9d3d8e0688ba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68262662"
---
# <a name="sysdm_tran_version_store_space_usage-transact-sql"></a>dm_tran_version_store_space_usage (Transact-sql)
[!INCLUDE[tsql-appliesto-2016sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2016sp2-asdb-xxxx-xxx-md.md)]

各データベースのバージョンストアレコードで使用される tempdb 内の領域の合計を表示するテーブルを返します。 **dm_tran_version_store_space_usage**は、個別のバージョンストアレコード間を移動せず、データベースごとに tempdb で使用される集計バージョンストアの領域を返すため、効率的で実行コストがかかりません。
  
バージョン管理された各レコードは、追跡情報や状態情報と共に、バイナリデータとして格納されます。 データベース テーブル内のレコードと同様、バージョン ストア レコードは 8,192 バイトのページに格納されます。 レコードが 8,192 バイトを超える場合は、2 つのレコードに分割されます。  
  
バージョン付きのレコードはバイナリとして格納されるため、異なるデータベースからの異なる照合順序に関する問題はありません。 SQL Server インスタンス内のデータベースのバージョンストアの使用領域に基づいて、tempdb のサイズを監視および計画するには、 **dm_tran_version_store_space_usage**を使用します。
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|データベースのデータベース ID。|  
|**reserved_page_count**|**bigint**|データベースのバージョンストアレコードの tempdb に予約されているページの合計数。|  
|**reserved_space_kb**|**bigint**|データベースのバージョンストアレコードの tempdb で使用されている合計領域 (kb 単位)。|  
  
## <a name="permissions"></a>アクセス許可  
で[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]は、 `VIEW SERVER STATE`権限が必要です。   

## <a name="examples"></a>例  
次のクエリを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス内の各データベースのバージョンストアによって、tempdb で消費された領域を調べることができます。 
  
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
 [トランザクション関連の動的管理ビューおよび関数 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
