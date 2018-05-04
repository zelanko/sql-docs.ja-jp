---
title: sys.dm_db_missing_index_groups (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 39
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f4497354a1209190940e56bad88b81447aa31d7d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmdbmissingindexgroups-transact-sql"></a>sys.dm_db_missing_index_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  空間インデックスを除く、特定の欠落インデックス グループに含まれている欠落インデックスに関する情報を返します。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、動的管理ビューは、データベースの包含に影響を与えるまたはユーザーがアクセスを他のデータベースに関する情報が公開される情報を公開できません。 この情報が公開されないように、接続されたテナントに属していないデータを含む行はすべてフィルターで除外されます。  
   
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**index_group_handle**|**int**|欠落インデックス グループの識別子|  
|**index_handle**|**int**|指定されたグループに属する、欠落インデックス**index_group_handle**です。<br /><br /> インデックス グループには、インデックスが 1 つだけ含まれます。|  
  
## <a name="remarks"></a>解説  
 によって返される情報**sys.dm_db_missing_index_groups**クエリは、クエリ オプティマイザーによって最適化され、永続化されていないときに更新されます。 欠落インデックスの情報が保持されるまで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。 欠落インデックスの情報を、サーバーの再利用後も保持する場合は、データベース管理者が情報のバックアップ コピーを定期的に作成する必要があります。  
  
 出力結果セットの列はどちらもキーではありませんが、組み合わせるとインデックス キーになります。  
  
## <a name="permissions"></a>権限  
 この動的管理ビューをクエリには、VIEW SERVER STATE 権限または VIEW SERVER STATE 権限を暗示すべての権限にユーザーを許可する必要があります。  
  
## <a name="see-also"></a>参照  
 [sys.dm_db_missing_index_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys.dm_db_missing_index_details &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sys.dm_db_missing_index_group_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
