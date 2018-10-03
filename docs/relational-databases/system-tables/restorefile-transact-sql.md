---
title: restorefile (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- restorefile
- restorefile_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restorefile system table
- restoring files [SQL Server], restorefile system table
- file restores [SQL Server], restorefile system table
ms.assetid: 8e40145a-8559-4abe-8e2a-39b818928009
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7414ca1c7d3ef3455aeb3b41c677ebc946a0e3d3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806815"
---
# <a name="restorefile-transact-sql"></a>restorefile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  復元されたファイルごとに 1 行のデータを格納します。復元されたファイルには、ファイル グループ名から間接的に復元されたものも含まれます。 このテーブルに格納されます、 **msdb**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**int**|対応する復元操作を特定するための一意な識別番号。 参照**restorehistory (restore_history_id)** します。|  
|**file_number**|**numeric(10,0)**|復元されたファイルのファイル識別番号。 この番号は、各データベースの中で一意であることが必要です。 NULL にすることができます。<br /><br /> データベース スナップショットの状態にデータベースを戻すとき、この値は完全な復元を行う場合と同じ方法で設定されます。|  
|**destination_phys_drive**|**nvarchar(260)**|ファイルの復元先のドライブまたはパーティション。 NULL にすることができます。<br /><br /> データベース スナップショットの状態にデータベースを戻すとき、この値は完全な復元を行う場合と同じ方法で設定されます。|  
|**destination_phys_name**|**nvarchar(260)**|ファイルの復元先のファイル名。ドライブやパーティション情報は含みません。 NULL にすることができます。<br /><br /> データベース スナップショットの状態にデータベースを戻すとき、この値は完全な復元を行う場合と同じ方法で設定されます。|  
  
## <a name="remarks"></a>コメント  
 このテーブルおよびその他のバックアップと履歴テーブルの行の数を減らすためには、実行、 [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)ストアド プロシージャ。  
  
## <a name="see-also"></a>参照  
 [バックアップし、復元テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefilegroup &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)   
 [restorehistory &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/restorehistory-transact-sql.md)   
 [システム テーブル &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
