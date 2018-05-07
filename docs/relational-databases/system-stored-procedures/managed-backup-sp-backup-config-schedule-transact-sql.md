---
title: managed_backup.sp_backup_config_schedule (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_backup_config_schedule_TSQL
- managed_backup.sp_backup_config_schedule
- managed_backup.sp_backup_config_schedule_TSQL
- sp_backup_config_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- managed_backup.sp_backup_config_schedule
- sp_backup_config_schedule
ms.assetid: 82541160-d1df-4061-91a5-6868dd85743a
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8ebeca4b0a1c9079f8786303207bcbae4dfe74c3
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="managedbackupspbackupconfigschedule-transact-sql"></a>managed_backup.sp_backup_config_schedule (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  自動またはカスタム スケジュールのオプションの構成[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]です。  
    
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```vb  
EXEC managed_backup.sp_backup_config_schedule   
    [@database_name = ] 'database_name'
    ,[@scheduling_option = ] {'Custom' | 'System'}  
    ,[@full_backup_freq_type = ] {'Daily' | 'Weekly'}  
    ,[@days_of_week = ] 'days_of_the_week'  
    ,[@backup_begin_time = ] 'begin time of the backup window'  
    ,[@backup_duration = ] 'backup window length'  
    ,[@log_backup_freq = ] 'frequency of log backup'  
```  
  
##  <a name="Arguments"></a> 引数  
 @database_name  
 有効にするためのデータベース名は、特定のデータベースでのバックアップを管理します。 NULL の場合、または *、し、この管理対象のバックアップは、サーバー上のすべてのデータベースに適用します。  
  
 @scheduling_option  
 バックアップ スケジュールのシステム管理の対象には、'System' を指定します。 カスタム スケジュールをその他のパラメーターで定義されている 'Custom' を指定します。  
  
 @full_backup_freq_type  
 頻度の種類の管理対象のバックアップ操作で、'毎日' または '毎週' に設定することができます。  
  
 @days_of_week  
 バックアップの曜日と@full_backup_freq_type週 1 回に設定されています。 '月曜日' のような完全な文字列の名前を指定します。  複数の 1 日の名をパイプで区切って指定できます。 たとえば N'Monday |水曜日 |金曜日 ' です。  
  
 @backup_begin_time  
 バックアップ ウィンドウの開始時刻です。 バックアップは開始されません。 外部の組み合わせで定義されている時間枠で@backup_begin_timeと@backup_durationです。  
  
 @backup_duration  
 バックアップの時間帯の期間。 によって定義される時間枠中にバックアップが完了することの保証がないことに注意してください@backup_begin_timeと@backup_durationです。 この時間帯で開始されるウィンドウの期間を超えるバックアップ操作はキャンセルできません。  
  
 @log_backup_freq  
 これにより、トランザクション ログ バックアップの頻度が決まります。 これらのバックアップは、データベースのバックアップに指定されたスケジュールではなく、一定の間隔で発生します。 @log_backup_freq 分または時間単位でき、0 が有効でないことを示しますログ バックアップ。 ログ バックアップを無効にするとだけ適用することが単純復旧モデルを含むデータベース。  
  
> [!NOTE]  
>  復旧モデルは、完全に単純なものから変更された場合は、0 以外の値を 0 から log_backup_freq を再構成する必要があります。  
  
## <a name="return-code-value"></a>リターン コード値  
 0 (成功) または 1 (失敗)  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 メンバーシップが必要**db_backupoperator**データベース ロール、 **ALTER ANY CREDENTIAL**アクセス許可、および**EXECUTE**に対するアクセス許可**sp_deletebackuphistory**ストアド プロシージャです。  
  
## <a name="see-also"></a>参照  
 [managed_backup.sp_backup_config_basic (TRANSACT-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup.sp_backup_config_advanced &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)  
  
  
