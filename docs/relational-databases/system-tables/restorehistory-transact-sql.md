---
title: "restorehistory (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- restorehistory
- restorehistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restorehistory system table
ms.assetid: 9140ecc1-d912-4d76-ae70-e2a857da6d44
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 23a73eb1e9f0b442c01f053e960f2f48e54a2740
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="restorehistory-transact-sql"></a>restorehistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  復元操作ごとに 1 行のデータを格納します。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**int**|各復元操作を識別する一意な識別番号。 ID、主キー。|  
|**restore_date**|**datetime**|復元操作の完了日時。 NULL を指定できます。|  
|**destination_database_name**|**nvarchar(128)**|復元操作の対象となるデータベース名。 NULL を指定できます。|  
|**user_name**|**nvarchar(128)**|復元操作を実行したユーザー名。 NULL を指定できます。|  
|**backup_set_id**|**int**|復元されるバックアップ セットを識別する一意な識別番号。 参照**backupset (backup_set_id)**です。|  
|**restore_type**|**char(1)**|復元操作の種類。<br /><br /> D = データベース<br /><br /> F = ファイル<br /><br /> G = ファイル グループ<br /><br /> I = 差分<br /><br /> L = ログ<br /><br /> V = 検証のみ<br /><br /> NULL を指定できます。|  
|**replace**|**bit**|復元操作に REPLACE オプションが指定されたかどうか。<br /><br /> 1 = 指定あり<br /><br /> 0 = 指定なし<br /><br /> NULL を指定できます。<br /><br /> データベースをデータベース スナップショットに戻す場合は、0 だけを選択できます。|  
|**復旧 (recovery)**|**bit**|復元操作に RECOVERY または NORECOVERY オプションが指定されたかどうか。<br /><br /> 1 = RECOVERY<br /><br /> NULL を指定できます。<br /><br /> データベースは、データベース スナップショットに戻す、ときに、唯一のオプションは 1 です。<br /><br /> 0 = NORECOVERY|  
|**restart**|**bit**|復元操作に RESTART オプションが指定されたかどうか。<br /><br /> 1 = 指定あり<br /><br /> 0 = 指定なし<br /><br /> NULL を指定できます。<br /><br /> データベースをデータベース スナップショットに戻す場合は、0 だけを選択できます。|  
|**stop_at**|**datetime**|データベースが復元された時刻。 NULL を指定できます。|  
|**device_count**|**tinyint**|復元操作に関係したデバイスの数。 この数は、バックアップのメディア ファミリの数よりも小さい値になります。 NULL を指定できます。<br /><br /> データベースをデータベース スナップショットに戻す場合、この値は常に 1 になります。|  
|**stop_at_mark_name**|**nvarchar(128)**|名前付きマークを含むトランザクションへの復旧。 NULL を指定できます。<br /><br /> データベースをデータベース スナップショットに戻す場合、この値は NULL になります。|  
|**stop_before**|**bit**|名前付きマークを含むトランザクションが復旧に含まれたかどうか。<br /><br /> 0 = マーク付きのトランザクションの前で復旧中止。<br /><br /> 1 = マーク付きのトランザクションも復旧された。<br /><br /> NULL を指定できます。<br /><br /> データベースをデータベース スナップショットに戻す場合、この値は NULL になります。|  
  
## <a name="remarks"></a>解説  
 次の表では他のバックアップと履歴テーブルの行の数を減らすためには、実行、 [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)ストアド プロシージャです。  
  
## <a name="see-also"></a>参照  
 [バックアップと復元のテーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefile &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/restorefile-transact-sql.md)   
 [restorefilegroup &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)   
 [システム テーブルと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
