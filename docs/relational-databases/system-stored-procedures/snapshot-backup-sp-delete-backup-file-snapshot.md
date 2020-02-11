---
title: sp_delete_backup_file_snapshot (Transact-sql) |Microsoft Docs
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.custom: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5afe5530-a404-4fa5-af3c-bc7c3ca43ce6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cf376712d51f542f6da5eaa8e89b53779eda0c07
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67941833"
---
# <a name="sp_delete_backup_file_snapshot-transact-sql"></a>sp_delete_backup_file_snapshot (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  指定されたデータベースから、指定されたバックアップスナップショットを削除します。 このシステムストアドプロシージャを、 **fn_db_backup_file_snapshots**システム関数と組み合わせて使用して、孤立したバックアップスナップショットを特定および削除します。 詳細については、「 [Azure でのデータベース ファイルのスナップショット バックアップ](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)」をご覧ください。  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_delete_backup_file_snapshot  
    [ @db_name = ] N'<database_name>  
    , [ @snapshot_url = ] N'<snapshot_url>  
```  
  
## <a name="arguments"></a>引数  
 *[ @db_name =] database_name*  
 削除するスナップショットを含むデータベースの名前を Unicode 文字列として指定します。  
  
 *[ @snapshot_url =] snapshot_url*  
 削除するスナップショットの URL を Unicode 文字列として指定します。  
  
## <a name="permissions"></a>アクセス許可  
 ALTER ANY DATABASE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [fn_db_backup_file_snapshots &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
