---
title: sys.dm_db_missing_index_groups (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_missing_index_groups
- sys.dm_db_missing_index_groups_TSQL
- dm_db_missing_index_groups
- dm_db_missing_index_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_missing_index_groups dynamic management view
- missing indexes feature [SQL Server], sys.dm_db_missing_index_groups dynamic management view
ms.assetid: 9cc00acd-d83d-49f8-be72-5b2aebed246b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f205632359b7bd40f446ced41cccdf43e984709b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62507790"
---
# <a name="sysdmdbmissingindexgroups-transact-sql"></a>sys.dm_db_missing_index_groups (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  この DMV は、空間インデックスを除く、特定のインデックスのグループで不足しているインデックスに関する情報を返します。 
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]では、動的管理ビューでデータベースの包含に影響を与える情報を公開することや、ユーザーがアクセスできる他のデータベースに関する情報を公開することはできません。 この情報を公開することを避けるため、接続されているテナントに属していないデータが含まれるすべての行はフィルターで除外します。  
   
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**index_group_handle**|**int**|欠落インデックス グループを識別します。|  
|**index_handle**|**int**|指定されたグループに属する、欠落インデックス**index_group_handle**します。<br /><br /> インデックス グループには、インデックスが 1 つだけ含まれます。|  
  
## <a name="remarks"></a>コメント  
 によって返される情報**sys.dm_db_missing_index_groups**クエリが、クエリ オプティマイザーによって最適化されて永続化されていないときに更新されます。 欠落インデックスの情報が保持されるのは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の再起動までです。 欠落インデックスの情報を、サーバーの再利用後も保持する場合は、データベース管理者が情報のバックアップ コピーを定期的に作成する必要があります。  
  
 Output の結果セットの列はどちらもが、キーがインデックス キーを形成します。  

  >[!NOTE]
  >この DMV の結果セットは、600 行に制限されます。 各行には、1 つの欠落インデックスが含まれています。 まで 600 を超える欠落したインデックスがあれば、新しいものを表示できるように、既存の欠落したインデックスに対処する必要があります。
  
## <a name="permissions"></a>アクセス許可  
 この動的管理ビューを照会するには、VIEW SERVER STATE 権限または VIEW SERVER STATE 権限が暗黙的にすべてのアクセス権にユーザーを許可する必要があります。  
  
## <a name="see-also"></a>参照  
 [sys.dm_db_missing_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys.dm_db_missing_index_details &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sys.dm_db_missing_index_group_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
