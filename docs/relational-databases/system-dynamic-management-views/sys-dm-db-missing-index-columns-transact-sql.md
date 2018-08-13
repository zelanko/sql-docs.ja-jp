---
title: sys.dm_db_missing_index_columns (Transact SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_missing_index_columns_TSQL
- sys.dm_db_missing_index_columns_TSQL
- sys.dm_db_missing_index_columns
- dm_db_missing_index_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_missing_index_columns dynamic management function
- missing indexes feature [SQL Server], sys.dm_db_missing_index_columns dynamic management function
ms.assetid: 3b24e5ed-0c79-47e5-805c-a0902d0aeb86
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 65f48f853fca55961a69e4e6905e5fa148cf739f
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39560192"
---
# <a name="sysdmdbmissingindexcolumns-transact-sql"></a>sys.dm_db_missing_index_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  空間インデックス以外のインデックスが欠落しているデータベース テーブル列に関する情報を返します。 **sys.dm_db_missing_index_columns**は、動的管理関数。  

## <a name="syntax"></a>構文  
  
```  
  
sys.dm_db_missing_index_columns(index_handle)  
```  
  
## <a name="arguments"></a>引数  
 *index_handle*  
 欠落インデックスを一意に識別する整数値です。 次の動的管理オブジェクトから取得できます。  
  
 [sys.dm_db_missing_index_details &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)  
  
 [sys.dm_db_missing_index_groups &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**column_id**|**int**|列の ID です。|  
|**column_name**|**sysname**|テーブル列の名前。|  
|**column_usage**|**varchar(20)**|クエリでの列の使用方法。 使用可能な値とその説明のとおり。<br /><br /> 等価性: 列は、等しいかどうか、フォームを表す述語に貢献します。 <br />                        *table.column* = *constant_value*<br /><br /> 非等値: 列に作用などの非等値を表す述語形式の述語: *table.column* > *constant_value*。 "=" 以外の比較演算子はすべて、不等値を表します。<br /><br /> インクルード: 列は、述語を評価するために使用されませんが、クエリをカバーするなどの理由により使用されます。|  
  
## <a name="remarks"></a>コメント  
 によって返される情報**sys.dm_db_missing_index_columns**クエリは、クエリ ・ オプティマイザーによって最適化され、永続化されていない場合に更新されます。 までに限り、欠落インデックスの情報が保持される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。 欠落インデックスの情報を、サーバーの再利用後も保持する場合は、データベース管理者が情報のバックアップ コピーを定期的に作成する必要があります。  
  
## <a name="transaction-consistency"></a>トランザクションの一貫性  
 トランザクションでテーブルを作成または削除する場合、削除されたオブジェクトに関する欠落インデックス情報を含む行は、トランザクションの一貫性を保持するためこの動的管理オブジェクトから削除されます。  
  
## <a name="permissions"></a>アクセス許可  
 この動的管理関数をクエリするには、VIEW SERVER STATE 権限、または VIEW SERVER STATE が暗黙的に与えられる権限が許可されている必要があります。  
  
## <a name="examples"></a>使用例  
 に対してクエリを実行する次の使用例、`Address`テーブルが表示され、クエリを使用してを実行し、`sys.dm_db_missing_index_columns`動的管理ビューは、インデックスのないテーブルの列を返すにします。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, StateProvinceID, PostalCode  
FROM Person.Address  
WHERE StateProvinceID = 9;  
GO  
SELECT mig.*, statement AS table_name,  
    column_id, column_name, column_usage  
FROM sys.dm_db_missing_index_details AS mid  
CROSS APPLY sys.dm_db_missing_index_columns (mid.index_handle)  
INNER JOIN sys.dm_db_missing_index_groups AS mig ON mig.index_handle = mid.index_handle  
ORDER BY mig.index_group_handle, mig.index_handle, column_id;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.dm_db_missing_index_details &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sys.dm_db_missing_index_groups &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [sys.dm_db_missing_index_group_stats &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
