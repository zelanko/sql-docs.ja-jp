---
title: "sys.fn_db_backup_file_snapshots (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/03/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 45010ff2-219f-4086-9ea4-016a6c17cddd
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6b9d7d2c500173213f893c83d10e0a650d90e9ee
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysfndbbackupfilesnapshots-transact-sql"></a>sys.fn_db_backup_file_snapshots (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  データベース ファイルに関連付けられている Azure のスナップショットを返します。 指定したデータベースが存在しない場合、またはデータベース ファイルが、Microsoft Azure Blob ストレージ サービスに格納されていない場合は、行は返されません。 組み合わせてこのシステム関数を使用して、 **sys.sp_delete_backup_file_snapshot**システム ストアド プロシージャを識別し、孤立したバックアップ スナップショットを削除します。 詳細については、「[Azure でのデータベース ファイルのファイル スナップショット バックアップ](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)」を参照してください。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
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
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|file_id|**int**|データベースのファイルの ID です。 NULL 値は許可されません。|  
|snapshot_time|**nvarchar (260)**|REST API では、そのとしてスナップショットのタイムスタンプが返されます。 スナップショットが存在しない場合は、NULL を返します。|  
|snapshot_url|**nvarchar(360)**|ファイルのスナップショットに完全な URL。 スナップショットの場合は NULL を返しますが存在します。|  
  
## <a name="permissions"></a>Permissions  
 データベースに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sp_delete_backup_file_snapshot &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)   
 [sp_delete_backup (Transact-SQL)](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
