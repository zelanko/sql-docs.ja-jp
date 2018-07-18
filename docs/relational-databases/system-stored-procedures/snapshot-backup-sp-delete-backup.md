---
title: sp_delete_backup (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/03/2015
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 808e50ae-ff6e-4520-9ce2-530591d3d59b
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2955570ee99eaa05d9a689ccbe62973af3208d80
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38054449"
---
# <a name="spdeletebackup-transact-sql"></a>sp_delete_backup (TRANSACT-SQL)
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
 *[ @backup_url =] backup_meta_file_url*  
 バックアップ ファイル自体を含む設定の指定したバックアップを構成するすべてのスナップショットを削除する、削除するバックアップの URL です。  
  
 *[ @db_name =] database_name*  
 削除するスナップショットを含むデータベースの名前です。 データベース名が提供される、システムは、指定されたデータベースのバックアップの URL を使用して、バックアップの URL が提供されることを検証の場合[sp_delete_backup_file_snapshot &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)各スナップショットを削除します。 データベース名が指定されていない場合は、このデータベースのチェックは実行されません。  
  
## <a name="permissions"></a>アクセス許可  
 ALTER ANY DATABASE 権限または指定されたデータベースに対する ALTER 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sys.fn_db_backup_file_snapshots &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)   
 [sp_delete_backup_file_snapshot (Transact-SQL)](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)  
  
  
