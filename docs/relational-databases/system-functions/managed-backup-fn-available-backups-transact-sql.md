---
title: "managed_backup.fn_available_backups (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- smart_admin.fn_available_backups
- smart_admin.fn_available_backups_TSQL
- fn_available_backups_TSQL
- fn_available_backups
dev_langs: TSQL
helpviewer_keywords:
- fn_available_backups
- smart_admin.fn_available_backups
ms.assetid: 7aa84474-16e5-49bd-a703-c8d1408ef107
caps.latest.revision: "15"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 09946d24bbf8f3895894f77e64794d536668efe8
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="managedbackupfnavailablebackups-transact-sql"></a>managed_backup.fn_available_backups (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  指定されたデータベースに使用可能なバックアップ ファイルの 0 行、1 行、または複数の行から成るテーブルを返します。 返されるバックアップ ファイルがによって作成されたバックアップ[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]です。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```tsql  
managed_backup.fn_available_backups ([@database_name = ] 'database name')  
```  
  
##  <a name="Arguments"></a> 引数  
 @database_name  
 データベースの名前。 @database_nameは nvarchar (512)。  
  
## <a name="table-returned"></a>返されるテーブル  
 テーブルには、一意のクラスター化制約 (database_guid、backup_start_date、および first_lsn, backup_type) があります。   
データベースを削除してから再作成すると、すべてのデータベースのバックアップ セットが返されます。 出力は、各データベースを一意に識別する database_guid に従って並べ替えられます。   
LSN にギャップがある場合は、ログ チェーンが中断されていることを意味します。その場合、テーブルには、欠落した各 LSN セグメントに対して特別な行が含まれます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|Backup_path|NVARCHAR(260) COLLATE Latin1_General_CI_AS_KS_WS|バックアップ ファイルの URL。|  
|backup_type|NVARCHAR (6)|データベース バックアップの場合は "DB"、ログ バックアップの場合は "LOG"。|  
|expiration_date|DATETIME|このファイルが削除されることが予想される日付。 これは、指定された保有期間内の特定の時点にデータベースを復旧する機能に基づいて設定されます。|  
|database_guid|UNIQUEIDENTIFIER|指定されたデータベースの GUID 値。  GUID はデータベースを一意に識別します。|  
|first_lsn|NUMERIC(25, 0)|バックアップ セット内の先頭または最も古いログ レコードのログ シーケンス番号。 NULL にすることができます。|  
|last_lsn|NUMERIC(25, 0)|バックアップ セットの次のログ レコードのログ シーケンス番号。 NULL にすることができます。|  
|backup_start_date|DATETIME|バックアップ操作が開始された日付と時刻。|  
|backup_finish_date|NVARCHAR(128)|バックアップ操作が終了した日付と時刻。|  
|machine_name|NVARCHAR(128)|SQL Server のインスタンスがインストールされ、実行中コンピューターの名前[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]です。|  
|last_recovery_fork_id|UNIQUEIDENTIFIER|最後の復旧分岐の ID 番号。|  
|first_recovery_fork_id|UNIQUEIDENTIFIER|最初の復旧分岐の ID。 データ バックアップの場合、first_recovery_fork_guid の値は last_recovery_fork_guid と同じです。|  
|fork_point_lsn|NUMERIC(25, 0)|first_recovery_fork_id が last_recovery_fork_id に等しくない場合は、分岐ポイントのログ シーケンス番号。 これらが同じである場合、この値は NULL になります。|  
|availability_group_guid|UNIQUEIDENTIFIER|データベースが Alwayson データベースの場合は、これは、可用性グループの GUID。 それ以外の場合は、NULL になります。|  
  
## <a name="return-code-value"></a>リターン コード値  
 0 (成功) または 1 (失敗)。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 必要があります**選択**この関数に対する権限。  
  
## <a name="examples"></a>使用例  
 次の例では、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]によってバックアップされた、データベース "MyDB" の使用可能なすべてのバックアップの一覧を表示します。  
  
```  
SELECT *   
FROM managed_backup.fn_available_backups ('MyDB')  
  
```  
  
## <a name="see-also"></a>参照  
 [Microsoft Azure への SQL Server マネージ バックアップ](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)   
 [Microsoft Azure に格納されたバックアップからの復元](../../relational-databases/backup-restore/restoring-from-backups-stored-in-microsoft-azure.md)  
  
  
