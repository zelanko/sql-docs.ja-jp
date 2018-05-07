---
title: sys.dm_db_missing_index_columns (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: dmv's
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
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 568d909d993f3978c9b5f754b063d6357d51af8c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmdbmissingindexcolumns-transact-sql"></a>sys.dm_db_missing_index_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  空間インデックス以外のインデックスが欠落しているデータベース テーブル列に関する情報を返します。 **sys.dm_db_missing_index_columns**動的管理関数です。  

## <a name="syntax"></a>構文  
  
```  
  
sys.dm_db_missing_index_columns(index_handle)  
```  
  
## <a name="arguments"></a>引数  
 *index_handle*  
 欠落インデックスを一意に識別する整数値です。 次の動的管理オブジェクトから取得できます。  
  
 [sys.dm_db_missing_index_details &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)  
  
 [sys.dm_db_missing_index_groups &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**column_id**|**int**|列の ID です。|  
|**column_name**|**sysname**|テーブル列の名前。|  
|**column_usage**|**varchar(20)**|クエリでの列の使用方法。 使用可能な値とその説明です。<br /><br /> 等値: 列は、フォームの等しいかどうかを表す述語に使用できます。 <br />                        *table.column* = *constant_value*<br /><br /> 非等値: 列貢献不等、たとえば、述語にフォームの述語: *table.column* > *constant_value*です。 "=" 以外の比較演算子はすべて、不等値を表します。<br /><br /> INCLUDE: 列は述語の評価には使用されませんが、クエリをカバーするたとえば、別の理由から、使用されます。|  
  
## <a name="remarks"></a>解説  
 によって返される情報**sys.dm_db_missing_index_columns**クエリは、クエリ オプティマイザーによって最適化され、永続化されていないときに更新されます。 欠落インデックスの情報が保持されるまで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。 欠落インデックスの情報を、サーバーの再利用後も保持する場合は、データベース管理者が情報のバックアップ コピーを定期的に作成する必要があります。  
  
## <a name="transaction-consistency"></a>トランザクションの一貫性  
 トランザクションでテーブルを作成または削除する場合、削除されたオブジェクトに関する欠落インデックス情報を含む行は、トランザクションの一貫性を保持するためこの動的管理オブジェクトから削除されます。  
  
## <a name="permissions"></a>権限  
 この動的管理関数をクエリするには、VIEW SERVER STATE 権限、または VIEW SERVER STATE が暗黙的に与えられる権限が許可されている必要があります。  
  
## <a name="examples"></a>使用例  
 次の例は、に対するクエリを実行、`Address`テーブルし、を使用してクエリを実行し、`sys.dm_db_missing_index_columns`動的管理ビューのインデックスが欠落しているテーブルの列を返します。  
  
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
 [sys.dm_db_missing_index_details &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sys.dm_db_missing_index_groups &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [sys.dm_db_missing_index_group_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
