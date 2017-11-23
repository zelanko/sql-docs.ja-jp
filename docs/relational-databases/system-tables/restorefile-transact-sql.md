---
title: "restorefile (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- restorefile
- restorefile_TSQL
dev_langs: TSQL
helpviewer_keywords:
- restorefile system table
- restoring files [SQL Server], restorefile system table
- file restores [SQL Server], restorefile system table
ms.assetid: 8e40145a-8559-4abe-8e2a-39b818928009
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 803b8ec7682c1d3b40f339f1aef9c144e307053e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="restorefile-transact-sql"></a>restorefile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  復元されたファイルごとに 1 行のデータを格納します。復元されたファイルには、ファイル グループ名から間接的に復元されたものも含まれます。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**int**|対応する復元操作を特定するための一意な識別番号。 参照**restorehistory (restore_history_id)**です。|  
|**file_number が**|**numeric(10,0)**|復元されたファイルのファイル識別番号。 この番号は、各データベースの中で一意であることが必要です。 NULL にすることができます。<br /><br /> データベース スナップショットの状態にデータベースを戻すとき、この値は完全な復元を行う場合と同じ方法で設定されます。|  
|**destination_phys_drive**|**nvarchar (260)**|ファイルの復元先のドライブまたはパーティション。 NULL にすることができます。<br /><br /> データベース スナップショットの状態にデータベースを戻すとき、この値は完全な復元を行う場合と同じ方法で設定されます。|  
|**destination_phys_name**|**nvarchar (260)**|ファイルの復元先のファイル名。ドライブやパーティション情報は含みません。 NULL にすることができます。<br /><br /> データベース スナップショットの状態にデータベースを戻すとき、この値は完全な復元を行う場合と同じ方法で設定されます。|  
  
## <a name="remarks"></a>解説  
 次の表では他のバックアップと履歴テーブルの行の数を減らすためには、実行、 [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)ストアド プロシージャです。  
  
## <a name="see-also"></a>参照  
 [バックアップと復元のテーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefilegroup &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)   
 [restorehistory &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/restorehistory-transact-sql.md)   
 [システム テーブルと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
