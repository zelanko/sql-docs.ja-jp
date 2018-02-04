---
title: "sys.dm_db_missing_index_details (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_missing_index_details
- dm_db_missing_index_details
- sys.dm_db_missing_index_details_TSQL
- dm_db_missing_index_details_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- missing indexes feature [SQL Server], sys.dm_db_missing_index_details dynamic management view
- sys.dm_db_missing_index_details dynamic management view
ms.assetid: ced484ae-7c17-4613-a3f9-6d8aba65a110
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c10432f27701da1b3a99176df6797317051d2ec2
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmdbmissingindexdetails-transact-sql"></a>sys.dm_db_missing_index_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  空間インデックスを除く、欠落インデックスに関する詳細情報を返します。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、動的管理ビューは、データベースの包含に影響を与えるまたはユーザーがアクセスを他のデータベースに関する情報が公開される情報を公開できません。 この情報が公開されないように、接続されたテナントに属していないデータを含む行はすべてフィルターで除外されます。  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**index_handle**|**int**|特定の欠落インデックスの識別子。 識別子はサーバー内で一意です。 **index_handle**は、このテーブルのキー。|  
|**database_id**|**smallint**|欠落インデックスを含むテーブルがあるデータベースの識別子。|  
|**object_id**|**int**|インデックスが欠落しているテーブルの識別子。|  
|**equality_columns**|**nvarchar (4000)**|次の形式の等値述語に使用できる列のコンマ区切り一覧。<br /><br /> *table.column* =*constant_value*|  
|**inequality_columns**|**nvarchar (4000)**|次の形式のような不等値述語に使用できる列のコンマ区切り一覧。<br /><br /> *table.column* > *constant_value*<br /><br /> "=" 以外の比較演算子はすべて、不等値を表します。|  
|**included_columns**|**nvarchar (4000)**|クエリの包括列として必要な列のコンマ区切り一覧。 カバリングの詳細については付加列を参照してくださいまたは[作成付加列インデックスの](../../relational-databases/indexes/create-indexes-with-included-columns.md)します。<br /><br /> メモリ最適化インデックス (ハッシュの両方とメモリ最適化非クラスター化)、無視**included_columns**です。 テーブルのすべての列が各メモリ最適化インデックスに含まれています。|  
|**statement**|**nvarchar (4000)**|インデックスが欠落しているテーブルの名前。|  
  
## <a name="remarks"></a>解説  
 によって返される情報**sys.dm_db_missing_index_details**クエリは、クエリ オプティマイザーによって最適化され、永続化されていないときに更新されます。 欠落インデックスの情報が保持されるまで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。 欠落インデックスの情報を、サーバーの再利用後も保持する場合は、データベース管理者が情報のバックアップ コピーを定期的に作成する必要があります。  
  
 欠落インデックス グループの特定の欠落インデックスを決定するは、クエリを実行することができます、 **sys.dm_db_missing_index_groups**動的管理を使用してこれ表示**sys.dm_db_missing_index_details**に基づいて、 **index_handle**列です。  
  
## <a name="using-missing-index-information-in-create-index-statements"></a>CREATE INDEX ステートメントでの欠落インデックス情報の使用  
 によって返される情報を変換する**sys.dm_db_missing_index_details**非等値列の前と一緒にメモリ最適化テーブルとディスク ベース両方のインデックスを CREATE INDEX ステートメント、等値列を配置する必要がインデックスのキーをもらう必要があります。 付加列は、INCLUDE 句を使用して CREATE INDEX ステートメントに追加します。 等値の列の有効な順序を決定するには、選択度の最も高い列を左の先頭に指定し、選択度が高い順に並べます。  
  
 メモリ最適化インデックスの詳細については、次を参照してください。[メモリ最適化テーブルのインデックス](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)です。  
  
## <a name="transaction-consistency"></a>トランザクションの一貫性  
 トランザクションでテーブルを作成または削除する場合、削除されたオブジェクトに関する欠落インデックス情報を含む行は、トランザクションの一貫性を保持するためこの動的管理オブジェクトから削除されます。  
  
## <a name="permissions"></a>権限  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。  
  
## <a name="see-also"></a>参照  
 [sys.dm_db_missing_index_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys.dm_db_missing_index_groups &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [sys.dm_db_missing_index_group_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
