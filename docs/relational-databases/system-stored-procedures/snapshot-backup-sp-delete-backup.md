---
title: "sp_delete_backup (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/03/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 808e50ae-ff6e-4520-9ce2-530591d3d59b
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 46bffa49e3d1586fe0639758b8d38c340f8933ea
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="snapshot-backup---spdeletebackup"></a>スナップショット バックアップ - sp_delete_backup
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  すべてのスナップショットとスナップショット バックアップが、指定されたデータベースから設定を構成するバックアップ ファイルを削除します。 このシステム ストアド プロシージャは、スナップショットのバックアップ セットを管理するための唯一の推奨される方法です。 詳細については、「 [Azure でのデータベース ファイルのファイル スナップショット バックアップ](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_delete_backup   
    [ @backup_url = ] backup_metadata_file_url  
    ,[ [ @db_name = ] database_name | NULL ]  
```  
  
## <a name="arguments"></a>引数  
 *[ @backup_url = ] backup_meta_file_url*  
 バックアップ ファイル自体を含む設定の指定したバックアップを構成するすべてのスナップショットを削除する、削除するバックアップの URL です。  
  
 *[ @db_name = ] database_name*  
 削除するスナップショットを含むデータベースの名前です。 システムには、指定されたバックアップの URL が指定されたデータベースのバックアップの URL で使用していることを確認、データベース名を指定すると、 [sp_delete_backup_file_snapshot &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)各スナップショットを削除します。 データベース名が指定されていない場合は、このデータベースのチェックは実行されません。  
  
## <a name="permissions"></a>権限  
 ALTER ANY DATABASE 権限または指定されたデータベースに対する ALTER 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sys.fn_db_backup_file_snapshots &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup_file_snapshot (Transact-SQL)](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)  
  
  
