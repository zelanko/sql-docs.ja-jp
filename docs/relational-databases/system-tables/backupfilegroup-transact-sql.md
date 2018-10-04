---
title: backupfilegroup (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backupfilegroup_TSQL
- backupfilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- filegroups [SQL Server], backupfilegroup system table
- backupfilegroup system table
ms.assetid: d26e8fbe-f5c5-4e10-b2bd-0d8e16ea21f9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b1d7cc485899a7f8173552788471ef6ec45ce49c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832980"
---
# <a name="backupfilegroup-transact-sql"></a>backupfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  バックアップ時に、データベース内のファイル グループごとに 1 行のデータを格納します。 **backupfilegroup**に格納されている場合は、 **msdb**データベース。  
  
> [!NOTE]  
>  **Backupfilegroup**テーブルは、データベースのバックアップ セットのないファイル グループの構成を示しています。 ファイルがバックアップ セットに含めるかどうかを特定するには、使用、 **is_present**の列、 [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md)テーブル。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**backup_set_id**|**int**|ファイル グループが含まれているバックアップ セット。|  
|**name**|**sysname**|ファイル グループの名前。|  
|**filegroup_id**|**int**|ファイル グループの ID。データベースで一意の値です。 対応する**data_space_id**で**sys.filegroups**します。|  
|**filegroup_guid**|**uniqueidentifier**|ファイル グループのグローバル一意識別子。 NULL にすることができます。|  
|**type**|**char(2)**|コンテンツの種類。次のいずれかです。<br /><br /> FG = "Rows" ファイル グループ<br /><br /> SL = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ ファイル グループ|  
|**type_desc**|**nvarchar(60)**|関数の種類の説明。次のいずれかです。<br /><br /> ROWS_FILEGROUP<br /><br /> SQL_LOG_FILEGROUP |  
|**is_default**|**bit**|CREATE TABLE または CREATE INDEX でファイル グループが指定されていない場合に使用される、既定のファイル グループ。|  
|**is_readonly**|**bit**|1 = ファイル グループは読み取り専用です。|  
|**log_filegroup_guid**|**uniqueidentifier**|NULL にすることができます。|  
  
## <a name="remarks"></a>コメント  
  
> [!IMPORTANT]  
>  異なるデータベースに同じファイル グループ名が存在することもあります。ただし、各ファイル グループは独自の GUID を持っています。 そのため、 **(backup_set_id, filegroup_guid)** 内のファイル グループを識別する一意のキー **backupfilegroup**します。  
  
 RESTORE VERIFYONLY FROM *backup_device* WITH LOADHISTORY の列に設定、 **backupmediaset**メディア セット ヘッダーから適切な値を持つテーブル。  
  
 このテーブルおよびその他のバックアップと履歴テーブルの行の数を減らすためには、実行、 [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)ストアド プロシージャ。  
  
## <a name="see-also"></a>参照  
 [バックアップし、復元テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [システム テーブル &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
