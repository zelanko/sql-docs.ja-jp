---
title: sys.fn_db_backup_file_snapshots (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/03/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 45010ff2-219f-4086-9ea4-016a6c17cddd
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7845ef36347d9131ed6991674b4e09b23ee34155
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670436"
---
# <a name="sysfndbbackupfilesnapshots-transact-sql"></a>sys.fn_db_backup_file_snapshots (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  データベース ファイルに関連付けられている Azure のスナップショットを返します。 指定したデータベースが存在しない場合、またはデータベース ファイルが、Microsoft Azure Blob ストレージ サービスに格納されていない場合は、行は返されません。 組み合わせてこのシステム関数を使用して、 **sys.sp_delete_backup_file_snapshot**システム ストアド プロシージャを識別し、孤立したバックアップ スナップショットを削除します。 詳細については、「 [Azure でのデータベース ファイルのファイル スナップショット バックアップ](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_db_backup_file_snapshots   
   [ ( database_name ) ]  
```  
  
## <a name="arguments"></a>引数  
 *Database_name*  
 クエリ対象のデータベースの名前です。 NULL の場合、この関数は、現在のデータベースのスコープ内で実行されます。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|file_id|**int**|データベースのファイルの ID です。 NULL 値は許可されません。|  
|snapshot_time|**nvarchar(260)**|REST API では、そのとしてスナップショットのタイムスタンプが返されます。 スナップショットが存在しない場合は、NULL を返します。|  
|snapshot_url|**nvarchar(360)**|ファイルのスナップショットに完全な URL。 スナップショットの場合は NULL を返しますが存在します。|  
  
## <a name="permissions"></a>アクセス許可  
 データベースに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sp_delete_backup_file_snapshot &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)   
 [sp_delete_backup (Transact-SQL)](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
