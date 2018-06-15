---
title: backupmediafamily (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- backupmediafamily
- backupmediafamily_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backupmediafamily system table
- backup media [SQL Server], backupmediafamily system table
ms.assetid: ee16de24-3d95-4b2e-a094-78df2514d18a
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: da7d59170e9ed3ed9a1808e03e792474c22afddd
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258368"
---
# <a name="backupmediafamily-transact-sql"></a>backupmediafamily (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  メディア ファミリごとに 1 行のデータを格納します。 メディア ファミリがミラー化されたメディア セット内にある場合は、メディア セット内のミラーごとに個別の行が格納されます。 次の表は、 **msdb**データベース。  
    
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**media_set_id**|**int**|このファミリがメンバーとして属しているメディア セットを識別する、一意な識別番号。 参照 **(media_set_id)**|  
|**family_sequence_number**|**tinyint**|メディア セット内でのこのメディア ファミリの位置。|  
|**media_family_id**|**uniqueidentifier**|メディア ファミリを識別する一意な識別番号。 NULL を指定できます。|  
|**media_count**|**int**|メディア ファミリ内のメディア数。 NULL を指定できます。|  
|**logical_device_name**|**nvarchar(128)**|バックアップ デバイスの名前**sys.backup_devices.name**です。 これは、一時バックアップ デバイスの場合 (永続的なバックアップ デバイスに存在するのではなく**sys.backup_devices**) の値**logical_device_name** null です。|  
|**physical_device_name**|**nvarchar(260)**|バックアップ デバイスの物理名。 NULL を指定できます。 このフィールドは、バックアップと復元のプロセス間で共有されます。 元のバックアップ先のパスまたは復元の元のソース パスを含めること可能性があります。 に応じてかどうかのバックアップまたは復元最初に発生したデータベースのサーバーにします。 ファイルのバックアップを同じから連続して復元メモでは、復元時にその場所に関係なく、パスは更新されません。 このため、 **physical_device_name**使用復元パスを表示するフィールドを使用できません。|  
|**device_type**|**tinyint**|バックアップ デバイスの種類。<br /><br /> 2 = ディスク<br /><br /> 5 = テープ<br /><br /> 7 = 仮想デバイス<br /><br /> 9 = azure ストレージ<br /><br /> 105 = パーマネントなバックアップ デバイス。<br /><br /> NULL を指定できます。<br /><br /> すべての永続的なデバイス名とデバイス番号は含まれて**sys.backup_devices**です。|  
|**physical_block_size**|**int**|メディア ファミリを記述するために使用される物理ブロック サイズ。 NULL を指定できます。|  
|**mirror**|**tinyint**|ミラー数 (0 ～ 3)。|  
  
## <a name="remarks"></a>解説  
 RESTORE VERIFYONLY FROM *backup_device* WITH LOADHISTORY の列に設定、 **backupmediaset**メディア セット ヘッダーから適切な値を持つテーブルです。  
  
 次の表では他のバックアップと履歴テーブルの行の数を減らすためには、実行、 [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)ストアド プロシージャです。  
  
## <a name="see-also"></a>参照  
 [バックアップし、復元テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [システム テーブル &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
