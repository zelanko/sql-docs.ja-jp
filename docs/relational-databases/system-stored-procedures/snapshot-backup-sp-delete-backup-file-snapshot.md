---
title: sp_delete_backup_file_snapshot (TRANSACT-SQL) |Microsoft Docs
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5afe5530-a404-4fa5-af3c-bc7c3ca43ce6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fd88ab54a8ab87be0601565c73e4e84a87790357
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032791"
---
# <a name="spdeletebackupfilesnapshot-transact-sql"></a>sp_delete_backup_file_snapshot (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  指定されたデータベースには、指定されたバックアップ スナップショットを削除します。 組み合わせてこのシステム ストアド プロシージャを使用して、 **sys.fn_db_backup_file_snapshots**バックアップ スナップショットが孤立してシステム関数を識別し、削除します。 詳細については、「 [Azure でのデータベース ファイルのファイル スナップショット バックアップ](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)」を参照してください。  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_delete_backup_file_snapshot  
    [ @db_name = ] N’<database_name>  
    , [ @snapshot_url = ] N’<snapshot_url>  
```  
  
## <a name="arguments"></a>引数  
 *[ @db_name =] database_name*  
 削除された、Unicode 文字列として指定する、スナップショットを含むデータベースの名前です。  
  
 *[ @snapshot_url =] snapshot_url*  
 削除された、Unicode 文字列として指定する、スナップショットの URL です。  
  
## <a name="permissions"></a>アクセス許可  
 ALTER ANY DATABASE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sys.fn_db_backup_file_snapshots &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup (Transact-SQL)](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
